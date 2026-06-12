---
title: "Couldn't find a place to store the imported certificate"
date: 2016-10-29
forum: Networking &amp; Wireless
---

### Post by Matrix01 on 2016-10-29
[h=6]Midori can't open the webpage to sign in WIFI.

error message is like this;[/h][h=6][/h][ATTACH=CONFIG]271860[/ATTACH]

this article is from their web;
[h=6]Error granting trust: Couldn't find a place to store the imported certificate[/h][COLOR=#666666][FONT=Open Sans]No key store is available or it's incorrectly setup. By default GNOME keyring can do this. Under Xfce it is recommended to enable “GNOME services” under “Session and Startup settings”. To make sure, that the output of “gnome-keyring –startup” is correctly sent to the environment, you can add “export `gnome-keyring-daemon –start`” to .xinitrc.
[http://midori-browser.org/faqs/#security_features](http://midori-browser.org/faqs/#security_features)

Does this fix problem?
[/FONT][/COLOR]

---

