---
title: "installing driver for broadcom (BCM5751) on Ubuntu 7.10"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by its_figaro on 2008-05-29
Hello,

I'm running Ubuntu 7.10 as a Live CD on another laptop.  I'm trying to wirelessly connect to the internet but cannot.  I believe this is because my PCI card is a Broadcom BCM5751, which the Live CD doesn't have the driver for.  I have downloaded a driver ('Linux tg3' from [http://www.broadcom.com/support/ethernet_nic/netxtreme_desktop.php](http://www.broadcom.com/support/ethernet_nic/netxtreme_desktop.php)), and transferred it to the laptop's desktop.

I then tried following several recommended steps from these forums, each to no avail.
1) [http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear) This process failed at stage 3:
'sudo apt-get install bcm43xx-fwcutter'
produced a response of
'Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package bcm43xx[NOTE: or bcm57xx]-fwcutter'

A Synaptic Package Manager search for the driver returned no results.

2) [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff?highlight=%28c571nr%29#head-bc33832c0547766a33c3a84f13f971ca757b2851](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff?highlight=%28c571nr%29#head-bc33832c0547766a33c3a84f13f971ca757b2851)
This process failed at the last part of stage 1:
'echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist'
produced a response of
'blacklist bcm43xx'

'sudo apt-get install ndiswrapper-utils-1.9'
produced a very long response, involving unpacking and setting up ndiswrapper.

However,
'mkdir ~/bcm43xx; cd ~/bcm43xx'
produced the response
'mkdir: cannot create directory '/home/ubuntu/bcm43xx': File exists
bash: cd~/bcm43xx: No such file or directory'

Can anyone help?  I'd love to switch to Ubuntu but I feel like I'm sinking here!

---

### Post by its_figaro on 2008-05-30
>>bump<<
:-p

please help!!

---

### Post by Jæd on 2008-06-01
> **stat said:**
> I tried using ubuntu 7.10 this week but fell down at the 'proprietry software needed for the wireless card' stage :(  no success on the ubuntu community forums... if any kind linux souls could look at my problem it'd be really appreciated!!  I'm still really wanting to give linux a go but i've hit a complete dead wall and need some help :(

the problem's detailed here: [http://ubuntuforums.org/showthread.php?t=811678](http://ubuntuforums.org/showthread.php?t=811678)

Have you tried this on Hardy 8.04...? Your problem seems to be relatedto the fact you can't find the first package. A quick check shows it exists on 8.04 :

```

apt-cache search bcm43xx-fwcutter
bcm43xx-fwcutter - Utility for extracting Broadcom 43xx firmware

```

Also, using the Live CD isn't a good way to install drivers. All your changes will be wiped at next boot.

---

### Post by its_figaro on 2008-06-01
[QUOTE=Jæd]Have you tried this on Hardy 8.04...?[/QUOTE]
nope, I only have the CD for 7.10.  I'll see if I can download a Live CD version of 8.04

[QUOTE=Jæd]Your problem seems to be relatedto the fact you can't find the first package.[/QUOTE]
Not sure what 'the first package' refers to...

[QUOTE=Jæd]Also, using the Live CD isn't a good way to install drivers. All your changes will be wiped at next boot[/QUOTE]I want to be confident all the drivers etc will run smoothly before I format/repartition :)

thanks for your advice Jæd, I'll look into getting 8.04.  Would still welcome any suggestions for how to deal with this on 7.10, seems a shame to admit defeat!

---

