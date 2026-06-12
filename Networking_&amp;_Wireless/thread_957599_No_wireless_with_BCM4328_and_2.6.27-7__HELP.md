---
title: "No wireless with BCM4328 and 2.6.27-7  HELP?"
date: 2008-10-24
forum: Networking &amp; Wireless
---

### Post by slugicide on 2008-10-24
I've been looking all over but I can't figure out how to get wireless working with Intrepid (new kernel).  The driver manager says I've got a b43 driver installed, but it's obviously the wrong one, as network manager only gives me the option of a VPN connection.

Can anyone point me in the right direction?

---

### Post by Ayuthia on 2008-10-24
> **slugicide said:**
> I've been looking all over but I can't figure out how to get wireless working with Intrepid (new kernel).  The driver manager says I've got a b43 driver installed, but it's obviously the wrong one, as network manager only gives me the option of a VPN connection.

Can anyone point me in the right direction?

Try going into System->Administration->Hardware Drivers and disable the Broadcom b43 driver and enable the Broadcom STA (wl) driver.  Once you have done that and if it still does not work, please try (will only work for the current session):
```
modprobe -r b43 ssb ndiswrapper bcm43xx wl
sudo modprobe wl
sudo ifconfig eth1 up
sudo ifconfig wlan0 up
sudo iwlist scan
```
I have added to ifconfig commands in there.  Only one of them should work.  The other one will produce an error.

---

### Post by slugicide on 2008-10-24
There is no STA to choose.

---

### Post by Ayuthia on 2008-10-24
Can you do the following for me:
```
sudo updatedb
sudo locate wl.ko
uname -a
```
The first two commands will update the search database and then look for the wl driver.  The third command will help me see what kernel version and if you are using 32 or 64-bit.

---

### Post by slugicide on 2008-10-24
rodney@rodney-laptop:~$ sudo updatedb
rodney@rodney-laptop:~$ sudo locate wl.ko
rodney@rodney-laptop:~$ uname -a
Linux rodney-laptop 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux
rodney@rodney-laptop:~$ 

Previously I'd been able to use wireless from this kernel, but not from 2.6.27, but I was told I needed to get rid of ndiswrapper, and after I did so, I no longer have wireless.

---

### Post by Ayuthia on 2008-10-24
> **slugicide said:**
> rodney@rodney-laptop:~$ sudo updatedb
rodney@rodney-laptop:~$ sudo locate wl.ko
rodney@rodney-laptop:~$ uname -a
Linux rodney-laptop 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux
rodney@rodney-laptop:~$ 

Previously I'd been able to use wireless from this kernel, but not from 2.6.27, but I was told I needed to get rid of ndiswrapper, and after I did so, I no longer have wireless.

If you are using 2.6.24-19, you will need to run an update so that you can get to 2.6.24-21 (where the wl module will appear in linux-restricted-modules) or else you will need to follow the instructions in the first post of this link (where you also posted):
[http://ubuntuforums.org/showthread.php?t=896713](http://ubuntuforums.org/showthread.php?t=896713)

---

### Post by slugicide on 2008-10-25
Update and then upgrade doesn't upgrade the kernel to 2.6.24.21.  Is it not the standard apt-get update, apt-get upgrade thing. 
Also,
That thread doesn't address BCM4328.  Do you think it will still work?

---

### Post by Ayuthia on 2008-10-25
> **slugicide said:**
> Update and then upgrade doesn't upgrade the kernel to 2.6.24.21.  Is it not the standard apt-get update, apt-get upgrade thing. 
Also,
That thread doesn't address BCM4328.  Do you think it will still work?
It should work for your card.  There are people with the 4328 card that are using the driver.

You are not able to update to 2.6.24-21 from the apt-get update, apt-get upgrade?  The release for this kernel was made just recently.

---

