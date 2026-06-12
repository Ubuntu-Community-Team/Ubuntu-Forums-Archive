---
title: "USB Modem stops after NVidia driver updtae"
date: 2006-12-12
forum: Networking &amp; Wireless
---

### Post by phatdad on 2006-12-12
I have a USB modem- Sagem. I had it up and running in Edgy. I then started messing around trying to install a driver for my Nvidia card. I then rebooted, and am now offered 2 kernel choices in GRUB. The 2.6.17-10 generic has x issues and won't boot into desktop. The other, 2.6.17-10-386 boots fine but the modem has stopped working.
I noted that my kernel was now 2.6.17-10-386, so have managed to get the right headers installed, as they where 2.6.17-10 generic. Using the ueagle 1.3 to build drivers, as done previously, I gaet as 
   $ sudo modprobe ueagle-atm 
and I get an error. On a windows machine here, but it said something about an unrecognised or unexpected symbol in the module.
Please help
edit- this is from my terminal-
dad@dad-desktop:~$ sudo modprobe ueagle-atm
FATAL: Error inserting ueagle_atm (/lib/modules/2.6.17-10-386/extra/ueagle-atm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
dad@dad-desktop:~$ dmesg
[17179569.184000] Linux version 2.6.17-10-386 (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 Fri Oct 13 18:41:40 UTC 2006 (Ubuntu 2.6.17-10.33-386)
  then miles of things, this error mentioned a few times
[17179956.960000] [eagle-usb] ADSL device removed
[17179956.964000] [eagle-usb] driver unloaded
[17180067.876000] usb 2-2: USB disconnect, address 2
[17180081.116000] usb 2-2: new full speed USB device using uhci_hcd and address 3
[17180081.264000] usb 2-2: configuration #1 chosen from 1 choice
[17180081.364000] ueagle_atm: disagrees about version of symbol usbatm_usb_probe
[17180081.364000] ueagle_atm: Unknown symbol usbatm_usb_probe
[17180081.372000] ueagle_atm: disagrees about version of symbol usbatm_usb_probe
[17180081.372000] ueagle_atm: Unknown symbol usbatm_usb_probe
[17180563.568000] ueagle_atm: disagrees about version of symbol usbatm_usb_probe
[17180563.568000] ueagle_atm: Unknown symbol usbatm_usb_probe
[17180843.384000] ueagle_atm: disagrees about version of symbol usbatm_usb_probe
[17180843.384000] ueagle_atm: Unknown symbol usbatm_usb_probe
please help!

---

### Post by aces21 on 2006-12-14
Did you remove the eagle-usb and usb-atm modules from your new kernel? I recall having a similar problem before when changing kernel and removing those two modules solved it.

---

### Post by redbullpeter on 2006-12-14
I think last nights kernel update may have something to do with this.

I have ubuntu installed on notebook with SIS integrated graphics. Everything was working perfectly and this morning - poof it all stopped.

I did a fresh install with kernel updates and my sagem fast 800 still refuses to work. I've removed eagle-usb modules completely but no avail.

I'll do a fresh install without updates until I buy an ethernet adsl router. ](*,) 

Sigh.

Peter

---

### Post by ped on 2006-12-15
Same problem here after kernel update:

[17180010.040000] ueagle_atm: disagrees about version of symbol usbatm_usb_probe
[17180010.040000] ueagle_atm: Unknown symbol usbatm_usb_probe

I can load the ueagle-atm module by hand with (-f = force)
```
sudo modprobe -f ueagle-atm
```

and than restarting my own init script for sagem fast 800 will start the connection, so I'm temporarily online, but I would love to have fixed it completely.

How can I make the boot process to "force" loading of ueagle-atm module?
And why in the first place I have to do this?

---

### Post by sideshowb0b on 2006-12-15
Ditto the above.

I dont supose you can un-update the kernel?

When trying to re-compile the ueagle-atm module i noticed there's a file called ueagle-atm4.tar.gz (i've been using ueagle-atm-1.3.tar.gz). Is this a new version of the drivers - would ths help?

Found this forum message about fc5 [http://www.mail-archive.com/ueagleatm-dev@gna.org/msg00564.html](http://www.mail-archive.com/ueagleatm-dev@gna.org/msg00564.html)

Looks like the 2.6.18 kernel has the ueagle-atm drive built in - is there any way of getting this kernel for edgy?

---

### Post by ped on 2006-12-15
fixed to some extend:

basicaly one of the first steps during modem intall
(according to [http://www.ubuntuforums.org/showthread.php?t=144468](http://www.ubuntuforums.org/showthread.php?t=144468) )
was to delete built-in kernel ueagle-atm.ko and usbatm.ko files.

Their location in first post in incorrect maybe, I had them in:
/lib/modules/2.6.17-10-generic/kernel/drivers/usb/atm

after kernel update those two files appeared again, that was the cause of my boot script to stop working correctly.

So after kernel update I suggest:
1) remove those two files

2) get back to your ueagle-atm-1.3 directory from where you did install the fresh drivers and I suggest to recompile with upgraded kernel headers. (This step may be not required, I did it just to make sure everything is ok, so I don't know if it can be ommited.)

```
cd ....where you extracted the ueagle-atm sources...
sudo make clean
make
sudo make install

```

After these 2 steps everything else works ok (i.e. you don't need to follow the rest of configuration of the modem, all those config files are still in place and should be functional, if you had it already working before kernel update).

Restart, and there I'm, online right after boot again automagically.

(in case somebody is interested into my init.d scripts, let me know, I'm using PPPoE LLC mode for the SAGEM fast 800 modem ... warning, the original thread is dealing with PPPoA type of connection, so if you need PPPoE like me, you should follow only the first steps till the modem is "operational", since there you need to follow some other how-to... czech one: [http://forum.ubuntu.cz/viewtopic.php?id=1658](http://forum.ubuntu.cz/viewtopic.php?id=1658) and the message #36 )

---

### Post by sideshowb0b on 2006-12-16
Thanks ped!!

I thought i'd already tried this - but your instructions worked! I didn't run make clean last time so maybe this was the problem.

---

### Post by ped on 2006-12-18
> **sideshowb0b said:**
> Thanks ped!!

I thought i'd already tried this - but your instructions worked! I didn't run make clean last time so maybe this was the problem.

It should be not needed, as by upgrading kernel headers the makefile should have detected the recompile is needed.

Than again, the updated kernel headers do have probably last-modified date/time stamp set from the package creator and those may be older than your last try of compilation with old kernel headers, in such case the make will not detect the compilation is needed...
Hmmm hard to tell afterwards why it didn't work without clean, but doing a clean ahead of build is always the safest way with properly written applications and extremely dangerous with those written badly. :D

Probably the safest path how to minimize chance of whole system reinstall is to untar the sources into new directory, compile there (it will have to compile, because old object/binary are in the old directory from previous compilation) and try to install the freshly compiled files. If it does not work, doing make clean in any of those two directories should either make the disaster grow bigger or prepare the ground for another make + make install round (the latter is much more likely, but at this point your backup disc should be already prepared to jump into the process of rescue).

Luckily the ueagle-atm-1.3 package has correctly written make clean, so it didn't do anything bad to my system.

Keep in mind that running clean process with "sudo" allows it to be quite harmful to the system (as running ***anything*** else with sudo (root privileges), Maybe running "make clean" without sudo firstly is also very good idea.. in such case you will very likely see error messages about low rights whenever the script tries to remove anything from system itself, and you can afterwards judge from the error messages whether you really want those changes to happen, and re-run the clean this time with sudo to allow it do everything it wanted to to the system itself.

This post is not related to SAGEM problem, it's just general remark about safety of running unknown scripts on your box ... always backup, and whenever you are asked to run any console commands, try to learn which things should ring your bell to be cautious (sudo, su, kdesu & family, rm, any tool for creating partitions, mv, /dev/null, etc...) and even if you are not programmer, try to learn some basics, what is run, when it's run, what is input/output redirection, etc...
If in doubt, ask somebody you trust who can understand command line on linux and predict result of such line.

Of course, **never** ever run "sudo rm -rf /" (there are better/more correct ways how to format all your discs). :) pity this one can be so much obfuscated that even seasoned programmer may not see it in the proposed command line, nor ordinary user may have idea that there's somewhere "sudo" or "rm" on that weird line he's copying from web. And yeah, some geeks love to make such "fun". That's why I'm really suggesting to learn a thing or two about command line even to ordinary users, it may not help you to fix your problems, but it may help you to know when it's right time to give up, and ask somebody trustworthy.

---

