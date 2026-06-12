---
title: "No internet connection after fresh 14.04lts"
date: 2014-05-14
forum: Networking &amp; Wireless
---

### Post by matt108 on 2014-05-14
Hi folks,

I have an Dell E1505 that I just installed a fresh 14.04.  While the ethernet cable does work with the usb boot, after install I see no network connections hard-wired or wifi.

lshw -C network    is saying that the networks are unclaimed?

Any advice or ideas would be greatly appreciated!  Scouring the forums for an answer was exciting at first . . . . now I have spent more time than I would like to admit . . . . . .

Thanks in advance!

---

### Post by Hadaka on 2014-05-14
Hi matt, please post the output of..

```
lspci -n | egrep '0200|0280' | awk '{print$3}'
```

thanks.

---

### Post by matt108 on 2014-05-14
Thanks for the quick reponse!

Here is what I get:

code:

it@it:~$ lspci -n | egrep '0200|0280' | awk '{print$3}'
14e4:170c
14e4:4311
it@it:~$

---

### Post by Hadaka on 2014-05-14
Hi matt-108 and welcome to the forums.

please hook up your ethernet cable and do..

```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo modprobe b44
```
BOOT...your wired connection should now be working.
still connected to the internet by cable..please do..
```
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
your wireless should be now working.

*If this worked like it should...
How to mark SOLVED [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by matt108 on 2014-05-15
Hadaka,

Thank you so much!!! 

This worked beautifully!

I really appreciate it!

---

### Post by Hadaka on 2014-05-15
Glad that worked for you !

---

