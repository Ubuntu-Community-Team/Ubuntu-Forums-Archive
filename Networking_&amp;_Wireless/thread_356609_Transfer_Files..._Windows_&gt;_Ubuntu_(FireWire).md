---
title: "Transfer Files... Windows &gt; Ubuntu (FireWire?)"
date: 2007-02-08
forum: Networking &amp; Wireless
---

### Post by delta99 on 2007-02-08
Hi 

How does one transfer files from the windows machine to a ubuntu machine?

Both PC's are connected to a router. I have a spare PCI network adaptor that I could use. 

I need to transfer 1GB+ files from the windows machine to the Ubuntu machine, i just don't know about this firewire and how to set it up. 

can someone please spoon feed me ? I am absolute noob with linux networking, I have used windows networking in the past, but that's easy! 

Or are there other ways? Better ways?

---

### Post by Mr Nick on 2007-02-08
Via email....Send yourself an email from windows, and receive it on the Linux OS.

---

### Post by bionnaki on 2007-02-08
gaim file transfer.

---

### Post by spd106 on 2007-02-08
It might be more efficient to use samba. 

If both PCs are connected to the same network (windows workgroup) then you should be able to see the windows PC by opening Places -> Network Servers then click through to the windows network.

Just make sure that you've shared the folder on the windows PC first.

This only works one way, if you want to access files from Ubuntu on the windows PC then you will have to install the samba server. See [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by GMachine_24 on 2007-02-08
First, yes, Samba is the way to go. It is relatively easy to configure. The Ubuntu how to is ... convoluted. I used this article 

[http://www.linuxjournal.com/article/8590](http://www.linuxjournal.com/article/8590)

as a guide and it worked on the FC4 machine and also on my Ubuntu boxes. It also tells you how to set up automatic backups - although you can do this using your Windosx 'backup' utility.

Anyway, **what I think this person really needs to know - and it's something I'm trying to figure out - is how or if an external firewire drive can be set up as a network drive on an Ubuntu box**. I have drives connected via PCI/IDE cards networked successfully but cannot figure out if it's possible to use Samba to connect an external firewire drive on an Ubuntu machine as a network share. 

DOES ANYONE KNOW IF IT IS POSSIBLE AND IF SO HOW TO DO IT? I have searched quite a bit and found nothing.

Thank you.

gmachine

---

### Post by bukwirm on 2007-02-08
GMachine_24: 

Can you get the firewire drive mounted?

If the drive is detected and mounted, you should be able to share it with Samba just like any other drive.

---

### Post by GMachine_24 on 2007-02-10
bukwirm:

you are so right. i mounted the sda1 drive after creating a mount point and created an entry in my smb.conf file for the mount point and, voila, it works (after mounting the drive via command line prompt).

actually, it took a little playing around with the smb.conf file and i think i have to mount the firewire drive via command line prompt after every reboot (adding a line to /etc/fstab definitely does NOT work) but that's cool. perhaps there is some other way to get it mounted automatically with each boot - but i do not know what that is.

so.... i thank you for your assistance.

gmachine

---

### Post by copilot on 2007-04-03
What model number/manufacturer is your firewire card? I'm working on a project where I'll need to use a couple firewire cards to dump data to new drives and I'm hoping you're using a common card that I can get quickly. =) Thanks!

---

