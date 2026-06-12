---
title: "DWL-G630, ndiswrapper and no NIC - Toshiba Satellite"
date: 2006-10-11
forum: Networking &amp; Wireless
---

### Post by Metz on 2006-10-11
Okay, I have something of a tricky problem.

I've had a Toshiba Satellite donated to the cause that is my ever expanding collection of Ubuntu machines.

It's set to dual boot Win2K and Dapper 6.06LTS. However, this machine has no NIc in it or any kind. I'm running a D-Link DWL-G630 pcmcia card, and I'm attempting to get this working. Question is, how the hell to I install ndiswrapper, when I can't 'apt-get' it, as I have no internet connection.

Any ideas ?!

Chicken and Egg, anyone !? :)

---

### Post by ajgreeny on 2006-10-11
In theory you could download the package file to another comp with internet access, and transfer it to your toshiba laptop then install with *sudo dpkg-install* .  If there are dependencies however you will also need to note them and do the same to get them onto the toshiba.

---

### Post by tturrisi on 2006-10-11
Do NOT use ndiswrapper with the DWLG630!
It has an Atheros chipset and requires the Madwifi drivers.
Install madwifi by:
0. somehow get onto the Net
1. run Synaptic package Mngr  (system > admin > synaptic)
2. enable all repositories in synaptic
3. update using the update button in synaptic
4. install the linux-restricted-modules that match your currrent kernel
5. reboot

madwifi is in the restricted-modules package

---

### Post by Metz on 2006-10-11
Thanks tturrisi. Saw your reply in the other thead re: using Madwifi.

Problem is....I simply can't get net access on that machine. It has no built in NIC, so I have no choice but to get the wifi working.

It really is chicken and egg :(

---

### Post by tturrisi on 2006-10-11
You could download the deb to a different comp & burn to cd, then use gdebi to install it on the laptop.

---

### Post by Haim on 2006-12-21
I am in the same boat.

Careful with your card.  Check the revision number on it.

I think C and D revisions are Atheros, before that another one.

I have rev E which is a ralink 2500 chipset (I think).  This should be using rt2500 or the new 2x00 drivers, but I haven't the skills to compile the damn think against the kernal.....could follow how-tos IF i had net access, but again with the chicken and the egg.

Hamish

---

### Post by Haim on 2006-12-27
I take it all back.

The Rev E is a rt61 chip set

Got it to work with this howto [http://www.ubuntuforums.org/showthread.php?t=296822](http://www.ubuntuforums.org/showthread.php?t=296822)

If you are a different revision this won't work for you.

---

