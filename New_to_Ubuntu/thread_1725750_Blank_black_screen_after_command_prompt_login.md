---
title: "Blank black screen after command prompt login"
date: 2011-04-10
forum: New to Ubuntu
---

### Post by crackfoxx on 2011-04-10
I am relatively new to Ubuntu and am having problems installing/launching.

I have recently installed Ubuntu 10.10 Desktop edition within my Windows 7 system using the WUBI installer.  

After completing installation and rebooting the system, I selected  to launch from Ubuntu, which took me to a command prompt screen asking for user login and password.  After logging in successfully (in command prompt), I enter **startx** to boot them system and I am then given a blank black screen which I cant get past. 

Does this mean I have not installed correctly?  How do I get past this command prompt screen into the GUI?  I have tried ctrl+alt+f7, but did not work.

Any ideas/suggestions as to what I'm doing wrong would be hugely appreciated.:)

---

### Post by Rubi1200 on 2011-04-10
Hi and welcome to the forums :-)

You may need to set some parameter as this sounds like a graphics issue:
[http://ubuntuforums.org/showpost.php?p=10089820&postcount=8](http://ubuntuforums.org/showpost.php?p=10089820&postcount=8)

---

### Post by crackfoxx on 2011-04-11
Thanks rubi, I think it is because of a graphics issue. I am seeing an error saying no screen detected when trying to boot in normal mode.

Do I need to install the proprietary drivers to support the graphics?  I can run on failsafe graphics mode but cannot connect to the internet to install the drivers as the network drivers are not present either.

Or do I need to edit the boot settings?

Sorry if this is really basic.

---

### Post by Rubi1200 on 2011-04-11
Please post the full specifications for the computer including graphics and wireless cards.

Thanks.

---

### Post by crackfoxx on 2011-04-12
I have Windows7 64bit with Intel HD graphics card, and a Dell DW1501 Wireless-N WLAN Half-Mini Card wireless adapter.

Let me know if any further system information is needed.

Again, your help is really appreciated,
Thanks

---

### Post by crackfoxx on 2011-04-12
...running Ubuntu 10.10 desktop version on a laptop.

Cheers,

---

### Post by bcbc on 2011-04-12
Check this out: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/600453](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/600453)

---

### Post by crackfoxx on 2011-04-16
Thanks, I have downloaded the kernel which apparently solves the problem.  Could you post some information on how to install this kernel from disk/usb?

Also, when running failsafe graphics mode, there is no network driver. The appropriate driver does not appear to be on the installation CD in synaptic package manager. How can I install the network driver without an internet connection?  

Am I able to download files through windows on another computer and transfer on USB?

Cheers

---

### Post by crackfoxx on 2011-04-17
I managed to download the wireless network driver in failsafe graphics mode on wired connection so now have internet connectivity.

Still unable to boot in normal mode tho :(

---

### Post by bcbc on 2011-04-17
I would assume that if you have the *.deb files you just have to install them. Double clicking while viewing files in Nautilus will open them up in software centre, or "sudo dpkg -i *.deb"  from command line (assuming they are the only .deb's in the current directory).

If it's unclear I'd ask on that bug report.

---

### Post by crackfoxx on 2011-04-18
Thanks bcbc, that worked fine.  However, when I try to boot using programs such as backtrack, it automatically boots using the previous kernel which had the graphical problems.

How can I select the new kernel file to run as default?

---

### Post by bcbc on 2011-04-18
You could try something like startupmanager. Or manually set the default by modifying /etc/default/grub.

There is something new I haven't tried yet for grub2: [http://ubuntuforums.org/showthread.php?p=10340183#post10340183](http://ubuntuforums.org/showthread.php?p=10340183#post10340183)

---

### Post by crackfoxx on 2011-04-24
Got the updated kernel working fine. New issues have arisen regarding connecting wirelessly. but I guess thats for another post.

Thanks again for all your help :)

---

