---
title: "Wifi Driveres without Ethernet connection for Dell Inspiron 1520 Ubuntu 14.04"
date: 2014-11-15
forum: Networking &amp; Wireless
---

### Post by dkc.com on 2014-11-15
Hi,

I have a Dell Inspiron 1520 and just installed Ubuntu 14.04 LTS. Wifi is not working and _**I don't have the option to connect to ethernet**_. I do have another laptop with working wifi connection. Is there anyways I can download the required driver on another laptop and copy it to the new machine?

Please help.

dkc

:(

---

### Post by chili555 on 2014-11-15
I love a challenge.

Please tell us more about your wireless device by opening a terminal Ctrl+Alt+t and run:```
lspci -nn | grep 0280
rfkill list all
```Thanks.

---

### Post by dkc.com on 2014-11-15
Hi chili555,

Thanks for the quick reply.

This is what I get when I run the code you suggested.

```
akc@akc-Inspiron-1520:~$ lspci -nn | grep 0280 
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01) 
akc@akc-Inspiron-1520:~$ rfkill list all 
0: hci0: Bluetooth 
	Soft blocked: no 
	Hard blocked: no 
```

(My reply was delayed as I had to run the code in one pc and copy the results to other one without net.)

---

### Post by Rob Sayer on 2014-11-15
You may well be able to install a driver but you'll need to find out what wireless adapter you have.

Enter this in terminal and post results in [CODE] tags:
sudo lshw -c network

Though I suspect it may be a broadcom card, and they can be pesky.

Here's a decent guide to broadcom drivers:

http://wireless.kernel.org/en/users/Drivers/b43

But that of course assumes you actually have a broadcom wireless, which you may not.

I had a quick look and there's a bunch of stuff relating to your dell in askubuntu and here, but they all seemed to be for older ubuntu releases.

When doing this kind of thing do NOT assume that a solution for older Ubuntu releases work for yours.  They often don't.

---

### Post by chili555 on 2014-11-15
What a lucky dawg you are! It's actually pretty easy. I guess I'll have to wait another day for a real challenge!

My good friend Wild Man has it outlined here: [http://ubuntuforums.org/showthread.php?t=2168816&p=12762259#post12762259](http://ubuntuforums.org/showthread.php?t=2168816&p=12762259#post12762259)

Post back if it doesn't go perfectly.

---

### Post by dkc.com on 2014-11-15
Well, my system was hang on the last command but I waited for a while. Then long-pressed the power button to restart and when it restarted, it worked.

---

### Post by dkc.com on 2014-11-15
Thanks rob for the help but the issue is solved now with the help of the method showed by chili555. :p

---

### Post by peter211 on 2015-10-09
Hi this doesn't seem to be working for me. Any chance you can help. I have the same answer from your first of two commands above but the second command nothing. 
Thank you

---

### Post by chili555 on 2015-10-09
> **peter211 said:**
> Hi this doesn't seem to be working for me. Any chance you can help. I have the same answer from your first of two commands above but the second command nothing. 
Thank youIf you have the same hardware as above, namely:> Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)Then, without any other way to connect to the internet, follow the process here to install the needed firmware: [http://ubuntuforums.org/showthread.php?t=2168816&p=12762259#post12762259](http://ubuntuforums.org/showthread.php?t=2168816&p=12762259#post12762259)

Reboot and you should be all set.

---

