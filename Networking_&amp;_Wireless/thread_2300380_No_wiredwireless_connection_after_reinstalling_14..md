---
title: "No wired/wireless connection after reinstalling 14.04 on a Dell Inspiron 1520"
date: 2015-10-25
forum: Networking &amp; Wireless
---

### Post by Ghostsafe on 2015-10-25
Hi,

[TABLE]
[TR]
[TD="class: votecell"]          

              [/TD]
              [TD="class: postcell"]        After re-installing 14.04 on my Dell Inspiron 1520 laptop I found  that I could no longer get a wired/wireless internet connection. I vaguely recall  that I had a problem connecting when I first installed 14.04  but I don't recall what I did to correct it.
 
This other thread [http://ubuntuforums.org/showthread.php?t=2256818](http://ubuntuforums.org/showthread.php?t=2256818) had the _exact_ same problem with the same hardware but the solution didn't work for me (unless I didn't do it right).

Any thoughts?

Thanks in advance.



[/TD]
[/TR]
[/TABLE]

---

### Post by Hadaka on 2015-10-25
Hi,please open a terminal  ctrl/alt/t then COPY
and paste..
```
lspci -n | awk '/0280/{print$3}'
```
post the output,
thanks.

---

### Post by Ghostsafe on 2015-10-25
Hi,

Thanks for the quick response.

I did the above and got:

14e4:4311

---

### Post by wildmanne39 on 2015-10-25
Please do:
```
sudo apt-get remove --purge bcmwl-kernel-source
```
Reboot and your wired connection should be working then do:
```
sudo apt-get install firmware-b43-installer
```
Reboot disable wired or unplug and wireless should work.
Thanks

---

### Post by Hadaka on 2015-10-25
Please do as Wild Man suggests and when online also do..

```
sudo apt-get update && sudo apt-get uprade
```
this will bring your security and other features up to date.
Let it run untill it completes,,,it may take some time depending
on your type of connection
also do,,
```
sudo apt-get autoremove && sudo apt-get autoclean
```
this will clean up files from the update and correcting the driver,

finally,,ignore any offer of proprietary driver as it will be incorrect and
you will be right back where you started,
thanks

---

### Post by Ghostsafe on 2015-10-25
Thanks so much you guys, both my wireless and wired connections are working!

Your speedy help is very much appreciated.

---

