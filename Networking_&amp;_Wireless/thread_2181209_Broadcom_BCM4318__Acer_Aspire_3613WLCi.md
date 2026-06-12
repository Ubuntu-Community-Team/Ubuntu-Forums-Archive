---
title: "Broadcom BCM4318 / Acer Aspire 3613WLCi"
date: 2013-10-16
forum: Networking &amp; Wireless
---

### Post by heroquestelf on 2013-10-16
I have an Acer Aspire 3613WLCi that uses a Broadcom internal wireless card. It was working about a week ago... when I made the mistake of installing some update or the other (I'm pretty novice with Linux) and it stopped working. I am currently running Ubuntu 13.04.

I ran the lspci -nn | grep 0280 command and got the following result: "Broadcom Corporation BCM4318 [Airforce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)"

Now, I havd NdisWrapper on my machine. It recognizes that the bcmwl5 wireless hardware is present on the system, and theoretically the driver is installed, but I still have no signal. 

Recently I found a page that suggested the following fix: "sudo apt-get install firmware-b43-installer"

I ran this command, and the computer did *something*, but still I have no wireless.

Mind you, it bears mentioning again that it was working a week ago before I applied the update.. and I'm not real sure what exactly I updated.

I'm not a newbie to Ubuntu, but I'm very much a novice. Any help you guys could give me would be greatly appreciated.

Also, my "Subsystem" is listed as AMBIT Microsystem Corp. Aspire 3022WLMi, 5024WLMi, 5020 [1468:0311]

Can someone help me please?

---

### Post by Hadaka on 2013-10-17
Hi, please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe b43
```
got wireless?

---

### Post by heroquestelf on 2013-10-18
the first thing I got was  

"sudo :unknown group: et
sudo: unable to initialize policy plugin"

I tried the command a second time to make sure that I had typed it in correctly and I got

"sudo: apt: command not found"

Also, I installed 13.10 last night, hoping it would solve the problem. It hasn't.

I rebooted the machine and tried the command again, and this time I got 

"E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock administration directory (/var/lib/dpkg/), is another process using it?"

---

### Post by westie457 on 2013-10-18
Here is a tip, copy and paste the commands that Hadaka posted. They are 100% correct.

The error you got for dpkg happened because something else was using that directory, probably Update Manager was running in the background.

---

### Post by Hadaka on 2013-10-18
Hi, please COPY and paste these commands..
```
sudo rm /var/lib/dpkg/lock
```
then do..
```
sudo apt-get update
sudo apt-get upgrade
```
*These may take some time...once finished then do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe b43
```
thanks.

---

### Post by heroquestelf on 2013-10-18
wham bam thank ya mam!!!
You guys are the best!!

---

### Post by Hadaka on 2013-10-18
Glad that worked for you !!
enjoy.

---

