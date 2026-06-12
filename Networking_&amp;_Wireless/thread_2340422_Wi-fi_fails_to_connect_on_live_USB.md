---
title: "Wi-fi fails to connect on live USB"
date: 2016-10-18
forum: Networking &amp; Wireless
---

### Post by xthehunter on 2016-10-18
**EDIT 21pm: Alright guys, I've settled for another solution that doesn't involve Ubuntu. The mods can close this thread if they want to. Thanks to all those that read this, even thought you couldn't give a solution since I couldn't post any technical log for the reasons stated above.**


Hi. I'm trying to use a live USB ubuntu to fix Windows. The hard drive is too full to install Ubuntu, so it must be a live CD/thumb drive. The problem is, there are some internet tools I need to do that and the wi-fi isn't working. Most solutions I found seem to only work on installed Ubuntu, not in a live-only setting.

The network manager finds the connections just fine, but fails every attempt to connect.

I made the live USB yesterday so it must be updated enough.

I can't transmit any text/data between this computer and the one with the problem for 2 reasons:
1) No working internet on the problem PC.
2) My only thumb-drive is the one I used to make the live USB.

EDIT: Now it apparently connects but cannot browse web pages. Not sure if other web functions are working or not.

---

### Post by Hadaka on 2016-10-19
Hi, do you have a wired ethernet connection??
Let's see if it's loading the correct driver, open a terminal ctrl/alt/t and do..
```
lspci -n | awk '/0280/ {print$3}'
```
then do..
```
lsusb | grep -v root
```
*Note
from my machine "lsusb | grep -v root" prints this..
[Bus 001 Device 002: ID [COLOR=#ff0000]148f:2573[/COLOR] Ralink Technology, Corp. RT2501/RT2573 [COLOR=#ff0000]Wireless[/COLOR] Adapter]
all we need you post is the number YOUR wifi wireless usb reports. same construct..XXXX:XXXX
Thanks

---

### Post by Bucky Ball on 2016-10-19
> **xthehunter said:**
> Alright guys, I've settled for another solution that doesn't involve Ubuntu. The mods can close this thread if they want to.

And closed. No longer a Ubuntu issue. :)

---

