---
title: "Broadcom driver help needed"
date: 2015-11-02
forum: Networking &amp; Wireless
---

### Post by dellboy56 on 2015-11-02
So I just cleaned installed Ubuntu and I got the bcmwl from Ubuntu via my other computer download with trusty right problem is it tells me cd needs to be mounted to media /CD-ROM how do I do that please thanks I would love it if you could comment cause this I need so I can install my sta Broadcom driver as I don't got ethernet

---

### Post by ajgreeny on 2015-11-02
Please use more helpful thread titles than "Help me" as you will get much more help if you say what the problem is in the title.

I have edited it this time for you.

See [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110) and
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by slickymaster on 2015-11-02
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by Hadaka on 2015-11-02
Hi, we need some information to help you get the correct driver,
on the computer that is not working, the one you need the driver for
open a terminal...ctrl/alt/t.. then COPY and paste these 2 commands
one at a time,
```
lspci -n | awk '/0280/{print $3}'
rfkill list all
```
post the output.

---

### Post by dellboy56 on 2015-11-02
[http://postimg.org/image/palrfd4sd/](http://postimg.org/image/palrfd4sd/) that's the pic probs to small for you anyway it says 1434:432b
with 1: hci0: Bluetooth soft blocked yes hard blocked no

---

### Post by Hadaka on 2015-11-02
Hi, this is an excellent link for your problem and there are
2 choices, read carefully and decide which one you want to
try. Both will load the driver you need. beyond this i have no
further suggestions or advice. good luck.

[http://askubuntu.com/questions/523458/unable-to-connect-to-any-wifi-in-ubuntu-14-04/523568#523568](http://askubuntu.com/questions/523458/unable-to-connect-to-any-wifi-in-ubuntu-14-04/523568#523568)

---

### Post by westie457 on 2015-11-02
@Hadaka

You may want to edit the link because it results in 'Page not found'

At the moment no further suggestions.

---

