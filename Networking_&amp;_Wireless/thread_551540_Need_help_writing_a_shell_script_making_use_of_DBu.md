---
title: "Need help writing a shell script making use of DBus"
date: 2007-09-15
forum: Networking &amp; Wireless
---

### Post by F-3582 on 2007-09-15
The following issue happens to me frequently:

I start my computer, auto-started application tries to make use of the internet, internet is not present because there's no WLAN available, application locks up for half a minute before noticing the missing connection. Usually my PC also takes three more minutes to boot up in that case.

I'd like to write a nice little shell script which just checks for an available connection and starts those applications, if there is. In any other case it shall just quit silently.

The problem is: I don't know how to poll Dbus for the NetworkManager status. Could someone please lend me a hand? If there are easier ways than using DBus for checking my connection, I'd appreciate those, too.

---

