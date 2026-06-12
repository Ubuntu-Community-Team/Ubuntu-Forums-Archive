---
title: "Ubuntu 18.04 LTS Wifi Trouble"
date: 2018-07-21
forum: Networking &amp; Wireless
---

### Post by oguzhanuslu on 2018-07-21
Hi all,
Two days ago I installed Ubuntu on my computer. My computer is showing me that 'here is no WiFi devices found'.
I read [https://ubuntuforums.org/showthread.php?t=2392454](https://ubuntuforums.org/showthread.php?t=2392454) and tried these codes but they didn't work.

---

### Post by westie457 on 2018-07-21
Hello oguzhanuslu, you have not given us much to work with.

Go here and follow the instructions on how obtain and post a wireless info report. [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

### Post by oguzhanuslu on 2018-07-21
I don't have a wired connection sir

---

### Post by westie457 on 2018-07-21
Okay, let us try a different approach.
What is the make and model of your computer and are you dual-booting with Windows?

---

### Post by oguzhanuslu on 2018-07-22
HP BA010NT. Only Ubuntu

---

### Post by westie457 on 2018-07-22
Assuming you have access to another computer (a friend, library or an internet-cafe) or can connect to the internet with a cell phone follow method 2 at this link. [https://ubuntuforums.org/showthread.php?t=2082305&p=12350385&viewfull=1#post12350385](https://ubuntuforums.org/showthread.php?t=2082305&p=12350385&viewfull=1#post12350385)

If you cannot do the above open a terminal, type in and run ```
lspci -nn
lsusb
rfkill list
```
To save on typing the output of the 1st command, the line with 'Network controller' might be enough for us to work with. Please include the number in [] brackets, it will look something like this:- [168c:0036]
The second command output should only be needed if nothing shows in the 1st command.
With the 3rd command only list the sections that have yes against them

---

