---
title: "QualComm QCA61x4A wireless and 16.04"
date: 2017-11-14
forum: Networking &amp; Wireless
---

### Post by pegruder on 2017-11-14
Hey folks.  I've picked up a new Yoga 920 and went for a dual boot with windows and ubuntu.  For the life of me I can't get wifi to work.  It shows up but is listed as disabled.  Windows lists the adapter detected as a QCA61x4A.  I've tried various things on previous posts including: [https://ubuntuforums.org/showthread.php?t=2323812](https://ubuntuforums.org/showthread.php?t=2323812) and I still haven't been able to get it working.  Out of everything I've done I'm not sure what output you folks would need to assist.  Any help is apreciated!

$ lspci -nn | grep -i Net
6b:00.0 Network controller [0280]: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter [168c:003e] (rev 32)

---

### Post by pegruder on 2017-11-15
Sorry folks - out of frustration I completely skipped the sticky post.  Here is the pastebin: 

[http://paste.ubuntu.com/25971733/](http://paste.ubuntu.com/25971733/)

Hopefully someone can assist.  Thanks in advance.

---

### Post by jeremy31 on 2017-11-16
Lets reinstall the firmware from the repos
```
sudo apt-get install --reinstall linux-firmware
```
Your wifi shows a hard block
```
echo "blacklist ideapad-laptop" | sudo tee /etc/modprobe.d/ideapad-laptop.conf
```
Then disable wifi power management
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
Reboot

---

### Post by pegruder on 2017-11-16
> **jeremy31 said:**
> Lets reinstall the firmware from the repos
```
sudo apt-get install --reinstall linux-firmware
```
Your wifi shows a hard block
```
echo "blacklist ideapad-laptop" | sudo tee /etc/modprobe.d/ideapad-laptop.conf
```
Then disable wifi power management
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
Reboot

You sir - have saved the day!  I am now typing this reply via onboard wifi!  I noticed the hard block but I was confused as I thought that meant a hardware switch was set, which if the Yoga 920 has one - I haven't been able to find it.  I dont see a hard switch or any Fn key switch.  In any event it works and I am extremely grateful!  Any idea what causes the hard block?

---

### Post by jeremy31 on 2017-11-17
Please use the thread tools menu near the top of the page to "mark as solved"

---

### Post by CCgirl6690 on 2018-09-07
> **jeremy31 said:**
> Please use the thread tools menu near the top of the page to "mark as solved"

Hi jeremy i have the same laptop but abit newer.  But my Wifi card on windows device manager shows  Intel AC 9560. Im having some issues with it on Ubuntu 18.04 It somestimes connects sometimes doesnt. and it shows a Question mark instead showing bars in top bar. . Can you please help me find driver for it Please?  Thank you

---

