---
title: "No Wireles connection in Compaq V63707TU Notebook"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by arnov007 on 2008-08-13
Hey guys,

I recently installed Ubuntu 8.04.1 in my Compaq V6307TU Notebook along with Windows XP. Since I am new to Linux it's becoming very difficult for me to connect to wireless. Our IP Address is : 192.168.0.1 and Port: 8080. I have Broadcom 802.11 b/g wlan inbuilt in the notebook. Now how do I connect to net. Also I am facing problem in installing files and codecs.

---

### Post by Kevbert on 2008-08-13
What's the Broadcom model ?  You can check this by going to Application-Accessories-Terminal and typing in 
```
lspci
```
Near the bottom will be your Broadcom adapter chipset and version.  Please post it here.
Regarding codecs.  There's a useful piece of software called Quickstart which will download and set them up, see my signature and click on the link.

---

### Post by Ayuthia on 2008-08-13
You have a few options if you have a Broadcom card.  You might start with this link for your wireless:
[http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754)
It will provide you instructions on how to get the b43 driver to work.  If it does not work, you can then go to the NDISwrapper install instructions which is posted in the second paragraph.

Here is a link for getting some of the codecs:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

You can also try installing ubuntu-restricted-extras.  It also has some of the stuff that you might be looking for.  Once you follow the instructions for Medibuntu, you should be able to install the applications through Synaptic.

---

### Post by Ayuthia on 2008-08-13
> **Kevbert said:**
> What's the Broadcom model ?  You can check this by going to Application-Accessories-Terminal and typing in 
```
lspci
```
Near the bottom will be your Broadcom adapter chipset and version.  Please post it here.
Regarding codecs.  There's a useful piece of software called Quickstart which will download and set them up, see my signature and click on the link.

If you do provide the lspci, can you instead use this command:
```
lspci -nnm
```
It will help provide more info about your card.

---

### Post by arnov007 on 2008-08-14
> **Ayuthia said:**
> If you do provide the lspci, can you instead use this command:
```
lspci -nnm
```
It will help provide more info about your card.

Posting within 30 min!!

---

### Post by arnov007 on 2008-08-14
> **Ayuthia said:**
> If you do provide the lspci, can you instead use this command:
```
lspci -nnm
```
It will help provide more info about your card.

Network Controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev.01)

Ethernet Controller: Intel Corporation PRO/100 VE Network Connection (rev 02)

Now Please anybody tell me how to get started with it??

---

### Post by Kevbert on 2008-08-14
Hi. It looks like you can use the B43 firmware.  Please take a look at this [[COLOR="Red"]post[/COLOR]]("http://ubuntuforums.org/showpost.php?p=5469730&postcount=13").

---

