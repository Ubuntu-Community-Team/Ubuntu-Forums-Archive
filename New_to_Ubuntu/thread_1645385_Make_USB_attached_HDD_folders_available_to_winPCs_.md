---
title: "Make USB attached HDD folders available to winPCs on network"
date: 2010-12-14
forum: New to Ubuntu
---

### Post by learnin on 2010-12-14
Hello,
I am trying to share, with Windows users, some folders on a USB attached HDD on my Ubuntu 10.04 LTS system. The first time I invoked the "shares-admin" command in Terminal the system said it needed to install software that was not currently installed which i assumed was Samba and ??? All seems to have installed OK. When I run "shares-admin" and, after logging as root, I try to set up a share the drop down selector for "Share through" only shows "Unix networks (NFS)" and not a "*Windows networks (SMB)"* choice. I think this is what is preventing me from sharing folders to the windows pc's. I can share folders in my Home directory using "Nautilus", right mouse clicking and choosing "Sharing Options". That works OK. I've read about modifying my fstab file, smb.conf file etc. but... not sure I am doing things quite right. Also, I don't get how to navigate to this USB attached HDD in Terminal to look at the contents that way. I assume because the drive is viewable in the GUI that it is mounted but...? Thanks for your help.
Vic

---

### Post by pricetech on 2010-12-14
As far as installing Samba:

[http://ubuntuforums.org/showthread.php?t=1644585](http://ubuntuforums.org/showthread.php?t=1644585)

and yes, if you can see it in Nautilus, it's mounted.

---

### Post by learnin on 2010-12-15
Hello,
Thanks for the response. Your tip seems like it would have been helpful if I started there but... I may have overworked the problem at this point. I have tried to share via Nautilus and created some glitch with a folder in my Home directory. I tried to un-install/re-install various SAMBA and Nautilus packages? but as I said, may have messed things up a bit.

I still can't access the USB HDD on a WinPC or MacPC on our network (I can see an icon but a WinPC/MacPC error message says it "can't find" the resource). Is there fundamentally a big difference trying to share a USB plugged-in storage device versus an internal IDE-ATA or SATA attached storage device? It is possible I haven't addressed some Mount, Mount-Point? issue. I am going to clean re-install Ubuntu and try your solution and see if things sort out. Thanks for the advice. I will provide updates as I muddle through this. Ain't learnin stuff great!
Vic

---

