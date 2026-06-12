---
title: "wireless problem. any ideas?"
date: 2011-03-04
forum: New to Ubuntu
---

### Post by Martynwills on 2011-03-04
Hi


I´ve just dual boot installed ubuntu 10.4

I have no wireless connection on Ubuntu. But it is working on the Windows 7  side of the partition.

The wireless buton on my laptop is on, but on the Ubuntu desktop the Network manager has no wireless network options and no wireless networks detected.

Any suggestions?

---

### Post by Hippytaff on 2011-03-04
Can you post the output of these commands? open a terminal (CTRL+ALT+T) and do
```
lspci | grep -i wireless
``` or if it is a usb effort
```
lsusb 
```The output of these is also very usefule for diagnosing wireless issues```
ifconfig
``````
lshw -C network
```in the mean time doing
```

sudo rfkill unblock all

```and
```
ifconfig iw0 up
``` is always worth a punt.

As an aside - if you type each of these commands thus```
lspci | grep -i wireless >> wireless.txt
``````
iwconfig >> wireless.txt
``` etc etc they will be put into a nice text file which might be easier to copy and paste back to us, in code tag's ;-)

---

### Post by TeoBigusGeekus on 2011-03-04
Have you searched in Administration>System>Additional drivers for any restricted drivers for your card?

---

### Post by Martynwills on 2011-03-04
> **Hippytaff said:**
> Can you post the output of these commands? open a terminal (CTRL+ALT+T) and do
```
lspci | grep -i wireless
``` or if it is a usb effort
```
lsusb 
```The output of these is also very usefule for diagnosing wireless issues```
ifconfig
``````
lshw -C network
```in the mean time doing
```

sudo rfkill unblock all

```and
```
ifconfig iw0 up
``` is always worth a punt.

As an aside - if you type each of these commands thus```
lspci | grep -i wireless >> wireless.txt
``````
iwconfig >> wireless.txt
``` etc etc they will be put into a nice text file which might be easier to copy and paste back to us, in code tag's ;-)

Sorry what&#347; the symbol you put between lspci and grep in the first line?

And how do I get info from the terminal on my other computer to this one i&#7743; connecting to the web on to post up for you to look at??

---

### Post by Martynwills on 2011-03-04
> **TeoBigusGeekus said:**
> Have you searched in Administration>System>Additional drivers for any restricted drivers for your card?

When Ilook at System>administration th eoption is hardware drivers and when I select this I get a stop sign saying ¨Downloading package index failed please check your network status. Most drivers will not be available.¨

WhenI close that it says searching for available drivers and then comes up with an empty box which says ¨No proprietary drivers are in use on this system¨?

---

### Post by Hippytaff on 2011-03-04
> Sorry what&#347; the symbol you put between lspci and grep in the first line?

And how do I get info from the terminal on my other computer to this one  i&#7743; connecting to the web on to post up for you to look at??It depends what your keyboard layout is (it's a nightmare finding it sometimes) it might be easier to copy and paste it (CTRL+Shift+V to paste into a terminal)

---

### Post by Martynwills on 2011-03-04
> **Hippytaff said:**
> It depends what your keyboard layout is (it's a nightmare finding it sometimes) it might be easier to copy and paste it (CTRL+Shift+V to paste into a terminal)

Hi. Thanks Hippytaff. I finally got the terminal command you suggested to work and notice the word broadcom. A previous search had suggested driver update issues for this, so I plugged it straight into the modem and the driver appeared. Followed it through and all sorted now.

Cheers mate.

SOLVED.

---

### Post by Hippytaff on 2011-03-04
Excellent...Good work :-)

---

