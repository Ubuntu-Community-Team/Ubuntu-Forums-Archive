---
title: "No wireless internet"
date: 2011-09-07
forum: New to Ubuntu
---

### Post by bmperrington on 2011-09-07
Hi. I was recently sent here by a nice gentleman on yahoo answers, and he told me i could get more help here then anywhere else (like yahoo answers).

IM RUNNING UBUNTU 11.04!

Here's my problem:

I cannot get a wireless internet connection on Ubuntu! (Note that i am an absolute beginner to all of this, i have no clue what im doing!!)

Im using windows 7 starter and running Ubuntu along with it. I was told to look at wwhat wwindiws and ubuntu saw my ethernet controller(?) as and heres what they said:

Windwos: 
Atheros AR8132 PCI-E Fast Ethernet controller (NDIS 6.20)

Ubuntu:
Ethernet Controller: Atheros Communications AR8132 Fast Ethernet (REV C0)

I had no clue what to do wwith this information but apparently both wwwindows and ubuntu find my etherent controller to be the same(?).

My next step was browsing the internet and this is what i found and did:

Open Terminal (i just recently found out how to do that) and type in : LSHW
then if you find it says "Configuration:...driver=" then SOMETHING (my ethernet controller? firmware? i dont know) is installed. mine didnt say stufff like that so then i went and did this: "System - administration- update manager" and i updated. it changed nothing wwith my no wirelss connection.

Im guessing i have to download and install the driver for the atheros AR8132 ethernet controller? i browsed the internet but came up short on that one. So noww i dont knoww wwhat to do anymore. 

All i ask is this to be explained to me, help me get wireless internet... and where to download the driver software for my ethernet controller thing.

Oh! another note: my WIRED CONNECTION works (when i hooked it up to the router) and also wwhen i click on the ionternet icon it tells me i have missing firmware around where it says wireless connections and stuff....

---

### Post by ubudog on 2011-09-07
First off, welcome to the forums!  I know it can be difficult at first.  Can you see any wireless networks when you click on the signal bars?

Have you tried looking in "Additional Drivers" for a wireless card driver?  It can be opened by clicking on the Dash (the Ubuntu logo in the top left corner), then by searching for "Drivers".  Can you take a screenshot of that window and upload it?

---

### Post by gandaran on 2011-09-07
> Ethernet Controller: Atheros Communications AR8132 Fast Ethernet (REV C0)
this is the ethernet device not the wireless and doesn't need any driver as it is working.
to find the wireless device type in terminal
```
lspci
```
then look for the networking/wireless controller, paste the results here so we can help you install the correct driver.

---

### Post by ubudog on 2011-09-07
> **gandaran said:**
> this is the ethernet device not the wireless and doesn't need any driver as it is working.
to find the wireless device type in terminal
```
lspci
```
then look for the networking/wireless controller, paste the results here so we can help you install the correct driver.

+1

There may be drivers available at the manufacturer's website.

---

### Post by wildmanne39 on 2011-09-07
Hi, welcome to the forum! please run these commands and post the results here:
```
lspci -nn | grep 0280
```
```
sudo lshw -C network
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

