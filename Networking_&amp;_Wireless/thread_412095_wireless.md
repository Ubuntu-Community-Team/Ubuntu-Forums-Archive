---
title: "wireless"
date: 2007-04-17
forum: Networking &amp; Wireless
---

### Post by peter_1 on 2007-04-17
Help, My first time with linux! I managed to install printer but I don't manage to conect to the internet!!!
Where do you see all the available networks which you can see in windows?

Anybody!!!!!!?????:guitar: :guitar:

---

### Post by Floppyjoe on 2007-04-17
> **peter_1 said:**
> Help, My first time with linux! I managed to install printer but I don't manage to conect to the internet!!!
Where do you see all the available networks which you can see in windows?

Anybody!!!!!!?????:guitar: :guitar:

What version of Ubuntu are you using?
Network-manager is one program that will show you the available wireless networks.

---

### Post by jonallport on 2007-04-17
Hi Peter, welcome to the exciting world of open-source.

In a nutshell you need iwconfig and iwscan (in a terminal)

E.g. Let's say your wireless card is ath0 (you can find the right one with 'iwconfig', no args and look for cards with wireless extensions.

'ifconfig ath0 up' - makes sure your wireless card is available for looking around with
'iwscan ath0 list' - looks for networks in range and outputs the details thereof
'iwconfig ath0 essid mynetathome' - associates with the mynetathome network
'iwconfig ath0 enc restricted abcdef0123' - use WEP with key abcdef0123
'dhclient ath0' - get an ip address

Or, for the less brave there are a number of graphical applets (available via the add/remove programs util) which are quite like the WZC tools you'll be used to in Windows.

PS. this is dragged from memory 'cos I'm tip-tappa-typing on my WinXP machine - take the man pages' word for it, not mine!

Hope this has been of some small help.

---

