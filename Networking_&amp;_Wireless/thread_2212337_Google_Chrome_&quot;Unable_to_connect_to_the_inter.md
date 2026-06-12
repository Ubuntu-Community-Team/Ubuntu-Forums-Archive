---
title: "Google Chrome &quot;Unable to connect to the internet&quot; ... but all other browsers can"
date: 2014-03-20
forum: Networking &amp; Wireless
---

### Post by peter-j-oconnell on 2014-03-20
HI all,
This is driving me crazy - on Ubuntu 13.10 64 bit with google-chrome-stable 33.0.1750.149-1, 33.0.1750.152-1) I get 
"Unable to connect to the internet"
Its a lie - Firefox, chromium, wget, anything else works fine - There is nothing wrong with the interwebs.
I have uninstalled and re-installed the package but to no avail. Does anyone have any other ideas ?
Thanks,
Pete

---

### Post by bapoumba on 2014-03-20
Does it also happen if you make a new user ?

---

### Post by peter-j-oconnell on 2014-03-23
I just created a new user and yes - the same happens..weird thing is if I  hit the "more" button in Chrome the error is:

DNS_PROBE_FINISHED_NO_INTERNET

This should not happen because I have told the host to use a http/https proxy for all traffic. I know there is no direct connection to the internet hence I have specified the proxy server. Other browsers adhere to this setting.
Weird thing is it was working..I have also tried deleting ~/.config/google-chrome/* to no avail...cluthching at straws now :)

---

### Post by bapoumba on 2014-03-24
Please try, in the firefox setup or prefs, network item (sorry, I'm not on my ubuntu setup so I cannot give a detailed path to this menu) to tick "auto-discover proxy settings" or "auto-discover network settings" or similar wording.
In my univ, the computer rooms are behind a proxy. Chrome handles it fine. FF only handles it when this option is ticked. Please do not ask me why :)

---

