---
title: "Ubuntu 11.04 and RTL8188CE Wifi"
date: 2011-07-29
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2011-07-29
Hi! I'm using a (newly custom built :D) computer with an ASUS PCE-N15 Wifi card, which according to lspci uses the RTL8188CE chipset. Now, after buying this card I read a lot of bad things about this chipset on the internet when it comes to Linux. However, I'd like to give it a sporting chance before I send it back from whence it came. . .

My problem is this. The card worked out of the box when I installed Ubuntu 11.04 64 bit, but I began to notice that the card only works every other minute. Seriously, I opened up System Monitor, and the card will work for exactly one minute, then for another minute it won't send or receive anything. The connection isn't dropped, but no packets are sent or received. And when the card is working, it's slow. iwconfig shows that my connection is 57 Mbps, and this is an 802.11N card that's advertised to run at 300Mbps.

lspci -v tells me that it's using the rtl8192ce module as a driver, and lsmod is showing several other modules like cfg80211, mac80211, and rtlwifi on which it is dependent. I've read about the Realtek proprietary drivers online, and it would seem that the linux drivers are crap.

My question is this. . . Does anyone own a Realtek wifi card and have it working reliably at a satisfactory speed? 

Thanks in advance!

---

### Post by marquivon on 2011-07-30
Realtek has released a new set of [rtl8188ce drivers for Kernel 2.6.35 and later]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&ProdID=272&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE") (released on 26 July 2011).

Follow the steps mentioned in the "readme" file. Hope that works for you.

Also, you may need to do this prior to running the above steps

1. Open a console
2. Type sudo apt-get install build-essential linux-headers-`uname -r`

You may not need this when there is a new kernel update in Ubuntu 11.04. But if it works now, and then doesn't work in the new kernel update, then you'd have to reinstall the drivers again. Possibly it'll be resolved in 11.10.

---

### Post by pi.boy.travis on 2011-07-30
> **marquivon said:**
> Realtek has released a new set of [rtl8188ce drivers for Kernel 2.6.35 and later]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&ProdID=272&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE") (released on 26 July 2011).

Follow the steps mentioned in the "readme" file. Hope that works for you.

Also, you may need to do this prior to running the above steps

1. Open a console
2. Type sudo apt-get install build-essential linux-headers-`uname -r`

You may not need this when there is a new kernel update in Ubuntu 11.04. But if it works now, and then doesn't work in the new kernel update, then you'd have to reinstall the drivers again. Possibly it'll be resolved in 11.10.

I'll give those a try and report back. I tried the version on their product page but the performance was no different.

---

### Post by cblanquer on 2012-01-13
Hi, 
I have now myself the same issue on Ubuntu 11.10 under kernel 3.xx.
So this is not solved yet in the main kernel stream.
I am going to try installing the Realtek drivers as well. 
Thanks for the tips here.

---

### Post by joshuafcole on 2012-03-09
Not to necro-post or anything, but same exact issue here. Tried compiling and installing the RTL8188CE drivers from scratch and installing them. No bloody dice. I really don't want to have to send them back, since they were cheap, I'm on a budget, and I'll get saddled with shipping... but I do need working wireless cards. Can anybody advise me on this? I'm pretty capable with code and linux hacking, so I'm game for anything you'd like me to try in the name of science. I just need a response soon before I send these back (probably this upcoming Monday).

---

### Post by kirusoft on 2012-03-14
If you got slow connexion, difficult connexion, slow speed etc.
Here is the command to fix it.

My card was : Intel Corporation Centrino Wireless-N 1030
My Distro : Ubuntu 11.04
Kernel : 2.6.38-13-generic x86_64

So how to fix ?

first test if its work :
**sudo rmmod -f iwlagn**
[B]sudo modprobe iwlagn 11n_disable=1
sudo iwconfig wlan0 power off[/B]

It’s work? Then how to make it permanent? 
**gksudo gedit /etc/modprobe.d/iwlagn.conf**
Add this to the file :
```
options iwlagn 11n_disable=1
```
Save & Close Gedit
Then :
**gksudo gedit /etc/pm/power.d/wireless**
Add this to the file :
```
#!/bin/sh
iwconfig wlan0 power off
```
Save and quit gedit
You need to make the script executable :
**sudo chmod +x /etc/pm/power.d/wireless**

Hope it’s help. It’s helped me a lot my Wifi working fine now. :)

---

### Post by fleamour on 2012-03-14
I had similar Realtek card.  Blacklisting the default Ubuntu driver was key:

[http://fleamour.wordpress.com/2012/03/07/realtek-rtl8188cu-based-chip-usb-nic/](http://fleamour.wordpress.com/2012/03/07/realtek-rtl8188cu-based-chip-usb-nic/)

---

