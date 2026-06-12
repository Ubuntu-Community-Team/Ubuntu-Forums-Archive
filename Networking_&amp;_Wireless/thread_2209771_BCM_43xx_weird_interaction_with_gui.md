---
title: "BCM 43xx weird interaction with gui"
date: 2014-03-07
forum: Networking &amp; Wireless
---

### Post by Hytekrednek on 2014-03-07
I know that most posts talk about there wireless not working but I have an unusual problem.  12.04LTS loads great, got wired internet, recognizes I have wireless but needs to install third party software.  I tell it to install the drivers for the BCM 43xx wireless that I have and then all hell breaks loose.  First it takes a very long time to complete and then when it is finishing up the install my video and gui go to hell and I can't read the screen.  Looks like squiggles covering the screen. Just wondering if this has happened to anyone before.  My laptop is a Dell Inspiron 9100.  I just want to make the old girl useful again.  It has never let me down and keeps on going like the energizer bunny.  It followed me to the gulf and back when I was in the Navy so want to keep her going.

James

---

### Post by phidia on 2014-03-07
Because there are sixty three pages devoted to BCM 43xx at the forums I didn't read them all but perhaps something [there]("http://ubuntuforums.org/showthread.php?t=1604868") helps?

---

### Post by chili555 on 2014-03-07
> recognizes I have wireless but needs to install third party software.In some cases, the 'Additional Drivers' tool installs the wrong driver and, as you see, things go sour! In order to correct the problem, it is necessary to verify your exact device. Please open a terminal Ctrl+Alt+t and run and post:```
lspci -nn -d 14e4:
```Once we know your exact device, we'll propose a solution.

Thank you for your service to the country!

---

### Post by Hytekrednek on 2014-03-07
OK will do, I'm on my windows laptop at the moment and will need to pull the information from the dell.  Thanks for help in advance.  I appreciate the the Thank you for service.  My pleasure.

James

---

### Post by Hytekrednek on 2014-03-07
Here is the information on my Controller

Network controller [0280]: Broadcom Corporation BCM4309 802.11abg Wireless Network Controller [14e4:4324] (rev 03)

Well there you have it.  My other one is Broadcom BCM4401 100Base-T and it work perfect.

James

---

### Post by chili555 on 2014-03-07
Please get a temporary wired ethernet connection and open a terminal and do:```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```Detach the ethernet, reboot and give us a good report.

If the terminal reports that bcmwl-kernel-source is not installed so not removed, just continue. After we get this fixed, ignore the bad advice given by the 'Additional Drivers' tool.

---

### Post by Hytekrednek on 2014-03-08
Sweet will try this today.  Thanks for all the help.

James

---

### Post by Hytekrednek on 2014-03-08
Woohoo I have wireless now. chili555 you are the MAN.  Thank you for all of the help.  I appreciate it.

James

---

### Post by chili555 on 2014-03-08
Awesome! Glad it's working. Please use thread tools at the top to mark Solved.

---

