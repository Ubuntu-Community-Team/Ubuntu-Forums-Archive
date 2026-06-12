---
title: "wireless doesn't connect"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by vallvi on 2010-05-01
Hi,
I would like to upgrade to 10.04, but I'm worried that I won't be able to get connected through my wireles. When I run the 10.04 live CD, it detects my card (D-Link, DWA-140, rt2870), it detects my network, but when I try to connect it doesn't accept my WEP password and asks for it over and over again.

I had the same problem when I installed 9.10, that's why I downgraded to 9.04 - which is what I'm using now, and which connects with no problem. I attached the output of dmesg when trying to connect with the live CD, if that's of any help.

Could anyone help me please? I would really like to upgrade.

Thnx

---

### Post by Peter09 on 2010-05-01
Have you got a wired connection available. Also can you post the output of the command 

```
lshw -C network
```

Some wireless cards need an connection to the Internet to download drivers after you have done the install.

---

### Post by Peter09 on 2010-05-01
If it gives you problems here is a link to someone who got it working in Lucid

[http://kubuntuforums.net/forums/index.php?topic=3111362.new](http://kubuntuforums.net/forums/index.php?topic=3111362.new)

---

### Post by zeekoman on 2010-05-01
It seems that there's a problem with RT2870/RT3070 chipsets and their device IDs. I don't think the problem is that you don't have the drivers. There's a post about it here:

[http://ubuntuforums.org/showthread.php?t=1342593](http://ubuntuforums.org/showthread.php?t=1342593)
[SIZE=5][/SIZE]

---

### Post by vallvi on 2010-05-01
Thanks, Peter,

Attached is the lspc output (and some others, just in case). The lsmod seems to indicate that the rt2800usb driver is installed (but not in use)?

From other posts here, I understood that my usb card should work out of the box? I don't have access to a wired conection now (I would need to run out & buy a loong cable!)

any suggestions on what I should do?

Thnx

---

### Post by Peter09 on 2010-05-01
Did you note this comment in the linked thread

> 
								 								
							 							 							duuude u rock!! i got it working..i blacklisted  the rt2x00** from /etc/modprobe.d/blacklist.conf and the device is  working now...


---

### Post by vallvi on 2010-05-01
oki,
will check that out tonite & let you know
thanks!

---

### Post by coolman98 on 2010-05-01
hope you get it working i had wireless problems myself.

---

### Post by vallvi on 2010-05-06
Yes!!
That did the trick. Just by blacklisting rt2x00usb as explained here:
[http://ubuntuforums.org/showthread.php?t=1342593](http://ubuntuforums.org/showthread.php?t=1342593)
I Installed 10.04 & am on-line now. Thanks so much for the suggestion

Now: stupid question: how do I mark this thread as 'solved'?

---

### Post by Peter09 on 2010-05-06
SOLVED ...
 
I think its in 'Thread Tools' at the top of the thread.

---

