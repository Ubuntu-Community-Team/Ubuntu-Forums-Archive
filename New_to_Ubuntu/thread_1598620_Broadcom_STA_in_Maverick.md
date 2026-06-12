---
title: "Broadcom STA in Maverick"
date: 2010-10-16
forum: New to Ubuntu
---

### Post by rvgsd on 2010-10-16
Hi, 

I did a clean install of Maverick today (32 bit on a 64 bit machine with PAE - Dell studio 1558). Its awesome.
But Whenever I try to activate the Broadcom Wireless STA drivers from System>Administration>Hardware Drivers, it gives me an error saying could not be installed.
I have attached the log file.
Here are some other outputs from terminal:
```

$lspci -n | grep 14e4
03:00.0 0280: 14e4:4727 (rev 01)

$lspci -vnn | grep 14e4
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g LP-PHY [14e4:4727] (rev 01)
```I checked it with [http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices)
but not sure if I understand.

Earlier I had 10.04 (32 bit), and the wireless on it worked perfectly fine.

Can anyone help??

---

### Post by sandyd on 2010-10-16
> **rvgsd said:**
> Hi, 

I did a clean install of Maverick today (32 bit on a 64 bit machine with PAE - Dell studio 1558). Its awesome.
But Whenever I try to activate the Broadcom Wireless STA drivers from System>Administration>Hardware Drivers, it gives me an error saying could not be installed.
I have attached the log file.
Here are some other outputs from terminal:
```

$lspci -n | grep 14e4
03:00.0 0280: 14e4:4727 (rev 01)

$lspci -vnn | grep 14e4
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g LP-PHY [14e4:4727] (rev 01)
```I checked it with [http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices)
but not sure if I understand.

Earlier I had 10.04 (32 bit), and the wireless on it worked perfectly fine.

Can anyone help??
are you connected to the internet?
if yes,
```

sudo apt-get install bcmwl-kernel-source
```

---

### Post by rvgsd on 2010-10-16
Tried that. Its already installed.
```
bcmwl-kernel-source is already the newest version.
```
It works on 10.04 but not on 10.10, should I downgrade the kernel or something??

---

### Post by Jetso on 2010-10-16
I had a similar problem and a user on another forum helped me. Here is the post: [http://www.linuxquestions.org/questions/linux-newbie-8/actually-installing-a-tar-gz-broadcom-bcm4312-833412/page2.html](http://www.linuxquestions.org/questions/linux-newbie-8/actually-installing-a-tar-gz-broadcom-bcm4312-833412/page2.html). Do what the user "Drakeo" does, and it should work! Although you will have to completely re-install the system :(

---

### Post by rvgsd on 2010-10-16
Reinstall!! wow, I hope there is a better way..! someone help!!

---

### Post by bkratz on 2010-10-17
May not be much help, but since you use the PAE kernel you may want to read this bug report

[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/576502](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/576502)

---

### Post by Jetso on 2010-10-17
> **rvgsd said:**
> Reinstall!! wow, I hope there is a better way..! someone help!!

I know what you mean. The re-install was fine with me though, because I had never used Linux, or even anything before Windows before I tried Ubuntu, and the internet didn't work. So I had no important files, programs, etc. that I needed. I wish I could help you out, but I tried several ways and they didn't work. I had was in the same series too... BCM4312... :(

---

### Post by waynefoutz on 2010-10-17
> **Jetso said:**
> I had a similar problem and a user on another forum helped me. Here is the post: [http://www.linuxquestions.org/questions/linux-newbie-8/actually-installing-a-tar-gz-broadcom-bcm4312-833412/page2.html](http://www.linuxquestions.org/questions/linux-newbie-8/actually-installing-a-tar-gz-broadcom-bcm4312-833412/page2.html). Do what the user "Drakeo" does, and it should work! Although you will have to completely re-install the system :(


I just read this thread. The user got his card working by simply toggling the power switch to it on his Dell laptop. The re-install was totally unnecessary.

---

### Post by Jetso on 2010-10-17
That user was me! The switch had nothing to do with it, I think it thought bcmwl-kernel-source was installed, but it wasn't and wouldn't let me uninstall it with out giving me an error.

---

### Post by sandyd on 2010-10-17
> **rvgsd said:**
> Tried that. Its already installed.
```
bcmwl-kernel-source is already the newest version.
```It works on 10.04 but not on 10.10, should I downgrade the kernel or something??
```

sudo modprobe wl
```

---

### Post by fbobraga on 2010-10-17
I ran thought something similar in lucid with my brother's laptop (a DELL Vostro 13"), and removing the *blacklist bcm43xx* from */etc/modprobe.d/blacklist.conf* back the things to normal (before this change, even the restricted drivers don't shows up in the "System" > "Administration" > "Hardware Drivers").

---

### Post by rvgsd on 2010-10-17
Thanks for all the help guys. I installed the Generic kernel image, and the wireless works fine with it. With PAE it doesn't. Seems that this bug is there for the past few releases as well, though for me wireless worked with PAE in 10.04. 
The funny thing is I had a wired connection while installing 10.10, and it chose the PAE-kernel by itself.

---

### Post by bkratz on 2010-10-17
Glad you got it working! You might go to the tools and mark it [soved] in case it helps someone else.

---

### Post by rvgsd on 2010-10-17
Well, I wouldn't mark it as [SOLVED] yet. I got it working with the Non PAE Kernel, but now my system shows only 3 GB of RAM when I have 4 GB. I cannot go for the 64 bit install, as I use some softwares which only work in the 32 bit Install. Having(i.e. being detected in this case) less RAM especially sucks when I use VirtualBox.
I'll be waiting for a solution to this!!

---

### Post by rmtatum on 2010-10-17
I found a solution that worked on my roommate's laptop.

First, uninstall all b43 and bcmwl packages (including the bcmwl-modaliases package).

Reboot.

Then run the following command:

```
sudo apt-get install bcmwl-kernel-source firmware-b43-lpphy-installer
```

---

### Post by rvgsd on 2010-10-20
Hi all, 
Yesterday I did a system update through the system manager. It updated the PAE kernel, I did this in terminal and I saw a "installing bcmwl" statement in the middle. I restarted the system to see that the wireless now works perfectly with the PAE kernel! Open source rocks.. :)  Thanks to the person who fixed this! 
Anyone facing this problem, just run the update manager and you should be good!

---

