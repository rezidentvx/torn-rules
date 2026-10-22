```
The use of scripts, extensions, applications, or any other software is permitted only when they rely on data from our API or from a page that you have manually loaded and are actively viewing. Such software must not make additional non-API requests to Torn, scrape pages that are not currently being viewed, attempt to bypass CAPTCHA protections, or extract data from unfocused pages to send elsewhere, generate alerts, or draw attention to itself or another window. Any software that makes non-API requests which are not directly and manually initiated by the user is prohibited and may be tracked. Furthermore, releasing software with malicious or undisclosed functionality is strictly forbidden, and developers of API-based tools are required to comply with the acceptable usage terms outlined [here](https://www.torn.com/api.html#).
```

>[!warning] Citations Needed
>At the moment, some content below is conventional wisdom. However, inclusion of these items is still held to the same strict confidence standard as the rest of this project, and citations will be added retroactively.

# Unfair Advantage
This rule was explicitly added with the intent of eliminating unfair advantages[^4]. This is still a factor in its enforcement, but the definition remains unclear.

# Actively Viewing
> The use of scripts, extensions, applications, or any other software is permitted only when they rely on data ~~from our API or~~ from a page that you have manually loaded and **are actively viewing**.

An actively viewed page is defined[^1] as:
> \[...\] in the foreground, visible, and being directly interacted with by the player. Merely having a page loaded in a background tab, minimized window, separate monitor, or left open for extended periods does not constitute active viewing

This is satisfied by checking whether the page is focused--i.e., with `document.hasFocus()`--before performing any action (read or write) on the page.[^8]

# Scraping
> Such software must not make additional non-API requests to Torn, **scrape pages that are not currently being viewed**, attempt to bypass CAPTCHA protections, or **extract data from unfocused pages to send elsewhere, generate alerts, or draw attention to itself or another window**.

Scraping is defined[^1] as:
> \[...\] extracting data from a page in order to: send to another system or page; call attention to the target or any other page; generate alerts or notifications of any type. In general, changing the visual appearance of a page in a way that doesn’t cause additional non-API requests or serve primarily as a means of drawing attention to that page is _not_ considered scraping.

As suggested by the rule and scraping definition, none of this applies when using the API as a datasource.[^9]

The restriction on sending data to another system depends on purpose. Extraction for meaningful data processing would "most likely" be considered scraping, but trivial things like visual changes (which are already generally exempted[^1]) "would most likely not".[^8]

# WebSockets
Fetching data from the WebSocket--"whether by observing the WebSocket or the effect of changes made via the WebSocket (eg by observing changes to the DOM)"--is governed by the [[Scripting Abuse#Scraping|scraping]] rules.[^1]

# Interaction
The player must perform 1 action per non-API request to Torn[^4]. For example, it is legal to populate input fields automatically as this occurs only in the client, but the player must manually trigger the submission.

This includes page loads, which submit a request to Torn servers despite not necessarily being a game interaction.

## Player Actions
Legal player actions to trigger network requests include:
- Clicking a button
- Keypress
	- Holding the key does not count as additional inputs

Scripts may interpret an input however you wish. This enables such things as spamming the same key to perform various actions.
# Same-Page Rule
Non-API requests must be sent from the same page on which they would naturally occur.

For example, it is legal for a script to trigger a revive from the hospital page or a user's profile, but not the market page.
# Key Usage
You may not "use keys you're not supposed to have access or permission to"[^5]. This includes keys that have been shared publicly or otherwise indirectly acquired; the owner must still consent to its use.[^5]

The key owner must also consent to how the key and data will be used[^6], even for public data[^11]. Exceeding agreed usage terms equates to usage without consent.
This consent cannot be obtained via hidden terms[^7]:
> People need to be very clearly aware of what their keys are being used for and a small clause buried in a privacy policy doesn't sufficiently override the clause for acceptable usage in our own terms.

Keys cannot be shared without the owner's consent.[^2][^7]

Changes to the service that affect key usage (such as new features) require reobtaining consent, though implementation is up to the service owner.[^11] It is legal to manage consent for each feature separately and only obtain consent for what has changed.[^11]

## Terms of Service
Any "script, userscript, sheet, extension, API service, bot, 3rd party website or any other API tool" must provide a ToS following the guidelines provided in the API docs[^2]. This is just a standard for conveying the information needed for a user's consent.

Alternative formats for this disclosure have been approved, but review is needed for their inclusion here.

Some services have been grandfathered or otherwise exempted from this requirement.

# Approval
IceBlueFire \[776\] and Velthir \[2100673\][^10] are the designated staff for rulings on scripting rules and script reviews. While this authority is established regularly by Admins, a ruling that something *is* legal is unreliable[^3]. See [[Bug and Exploit Abuse#Approval]].


[^1]: 26/01/26 - bogie \[148747\]: [Updated Rules Page: Scripting & Scraping](https://www.torn.com/forums.php#/p=threads&f=1&t=16534470)
[^2]: Staff: [API Docs](https://www.torn.com/api.html#)
[^3]: 19/09/19 - bogie \[148747\]: [Malicious scripts](https://www.torn.com/forums.php#/p=threads&f=1&t=16119253) following [the Elims spyware incident](https://www.torn.com/forums.php#/p=threads&f=2&t=16119076)
[^4]: 10/03/17 - Chedburn \[1\]: [New rule addition - Scripting abuse](https://www.torn.com/forums.php#/p=threads&f=1&t=16000717)
[^5]: 23/06/26 - IceBlueFire \[776\]: Private mail #282015230
[^6]: 26/07/22 - bogie \[148747\]: [Forum comment](https://www.torn.com/forums.php#/p=threads&f=2&t=16285134&b=0&a=0&start=860&to=22654795) on MaGnO \[51498\] abusing keys for mugging
[^7]: 19/01/25 - bogie \[148747\]: [Forum comment](https://www.torn.com/forums.php#/p=threads&f=2&t=16444691&b=0&a=0&to=25568992) on rDacted \[2670953\]'s violation from using Glasnost \[1844049\]'s backend
[^8]: 26/01/26 - TestPedroDev \[3613560\]: [Forum comment](https://www.torn.com/forums.php#/p=threads&f=2&t=16534472&b=0&a=0&start=60&to=26918685) on focus checks and scraping
[^9]: 26/01/26 - TestPedroDev \[3613560\]: [Forum comment](https://www.torn.com/forums.php#/p=threads&f=2&t=16534472&b=0&a=0&start=120&to=26919236) on using the API for notifications
[^10]: 20/08/25 - bogie \[148747\]: [New staff script moderator](https://www.torn.com/forums.php#/p=threads&f=2&t=16495952)
[^11]: 09/05/25 - splent \[2088243\]: [Forum comment](https://www.torn.com/forums.php#/p=threads&f=2&t=16468770&b=0&a=0&start=140&to=25940795) on service consent
