---
title: "Wifi Won't Connect Anymore?"
date: 2013-09-21
forum: Networking &amp; Wireless
---

### Post by youngtrapntg on 2013-09-21
Hi, I've having trouble with my wifi on my Acer Aspire running 13.04. It's had no trouble with wifi before this, and still scans for all the networks around here. For some reason though, it won't connect to my home connection anymore. It will scan and scan, but won't connect to the internet. I tried searching for an answer on the forum, but the problems don't seem to be the same and the solutions don't work.

---

### Post by Hadaka on 2013-09-21
Hi, please post the output of..
```
lspci -nn | grep 0280
lsmod
rfkill list all
```
thanks.

---

### Post by youngtrapntg on 2013-09-21
I'm using a different computer to respond, but nothing is hard or soft blocked, and the network controller came up as Broadcom BCM43225

---

### Post by Hadaka on 2013-09-21
ok, I'm going to need a little more information to help you.
please do..
```
lsmod | egrep 'wl|brcmsmac'
```
tell me if it shows...wl or brcmsmac
then do..
```
lspci -nn | grep 0280
```
i need the 14e4 number [14e4XXXX]
thanks.

---

### Post by youngtrapntg on 2013-09-21
It shows brcmsmac in red on each line, and it returns 14e4:4357.  Thanks

---

### Post by Hadaka on 2013-09-21
Hi, give this a try.
```
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -rf brcmsmac
sudo modprobe -v brcmsmac
```
then do..
```
dmesg | grep -i brcms
```
any glaring errors?

---

### Post by youngtrapntg on 2013-09-21
Strange, it guess it was router issues, even though there were other functioning devices on the same network. Thanks anyway

---

### Post by Hadaka on 2013-09-22
Great !, glad you found the problem.
please mark your thread solved.
How to->[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
thanks.

---

### Post by youngtrapntg on 2013-09-25
Now I'm having the same issue, if it is router related, I cannot understand why the computer I am on now is able to connect to it, but it seems to correlate with router problems

---

### Post by varunendra on 2013-09-25
Let's blame the driver once again (why, because we can ;)), and try another one. Assuming you have a wired connection available, please do -
```
sudo apt-get install linux-firmware-nonfree
sudo modprobe -rv b43 brcmsmac
sudo modprobe -v b43
```
Any improvement?

If not, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

