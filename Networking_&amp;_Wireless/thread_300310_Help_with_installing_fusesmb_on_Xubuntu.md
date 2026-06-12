---
title: "Help with installing fusesmb on Xubuntu?"
date: 2006-11-15
forum: Networking &amp; Wireless
---

### Post by Tazix on 2006-11-15
Anybody have some tips or a link to a guide on how to properly install fusesmb on Xubuntu Edgy?

When I look in Synaptic, and search for the fusesmb package... the details area says:

"It is based on FUSE (userspace filesystem framework for Linux), thus you will have to prepare fuse kernel module to be able to use it"

Not exactly sure what "preparing the fuse kernel module" entails.

Basically... what I'm trying to do is get Thunar to see / mount my Windows Network shares, without resorting to installing Nautilus or XFFM.

So, a step by step guide to accomplish that, would be most appreciated.

-Taz

---

### Post by Tazix on 2006-11-15
Got it working myself.  Real slick too.

~Create a folder and share it with XFCE's Applications -> System -> Shared Folders. (This should trigger a Samba install if you don't already have a share, and it should allow you to define the proper workgroup)
~ Install fusesmb in Synaptic (from Universe repository)
~ Edit (sudo mousepad /etc/modules) /etc/modules and add the word 'fuse' to the modules to be loaded (without quotes)
~ Reboot, so the fuse module loads, and the proper workgroup is read for samba.
~ In XFCE Applications -> System -> Users and Groups... Properties of your username... User Priveleges Tab... check "Allow use of fuse file systems..."
~ Create a directory (for non command-line peeps... gksudo thunar) that you are going to mount your network browse to... I used /media/network.  Change permissions to read / write for group and others (777).
~ In XFCE Applications -> Settings -> Autostarted Applications... Add an application... name and describe as you wish... for command line, put: fusesmb /media/network (Or whatever mountoint you created).
~ Open Thunar, and navigate to the parent folder of your mountpoint... then drag the 'mounpoint folder' to the places (shortcut) pane of thunar.
~logout and log back in (So the user privilege and fusesmb autostart will take affect)

Ta-da!... network browsing like Nautilus, in Thunar. (assuming your samba was set up right, with the correct workgroup, etc.)

Hope that helps some Xubuntu folks, since Thunar lacks network browsing fucntionality.

-Taz

---

### Post by compuguy1088 on 2006-11-19
Works like a charm in Xubuntu. Actually, it works better than nautilus at the moment, because of network refresh issues that are in it right now (as of edgy).

---

### Post by foxy123 on 2006-11-23
> **Tazix said:**
> Got it working myself.  Real slick too.

~Create a folder and share it with XFCE's Applications -> System -> Shared Folders. (This should trigger a Samba install if you don't already have a share, and it should allow you to define the proper workgroup)
~ Install fusesmb in Synaptic (from Universe repository)
~ Edit (sudo mousepad /etc/modules) /etc/modules and add the word 'fuse' to the modules to be loaded (without quotes)
~ Reboot, so the fuse module loads, and the proper workgroup is read for samba.
~ In XFCE Applications -> System -> Users and Groups... Properties of your username... User Priveleges Tab... check "Allow use of fuse file systems..."
~ Create a directory (for non command-line peeps... gksudo thunar) that you are going to mount your network browse to... I used /media/network.  Change permissions to read / write for group and others (777).
~ In XFCE Applications -> Settings -> Autostarted Applications... Add an application... name and describe as you wish... for command line, put: fusesmb /media/network (Or whatever mountoint you created).
~ Open Thunar, and navigate to the parent folder of your mountpoint... then drag the 'mounpoint folder' to the places (shortcut) pane of thunar.
~logout and log back in (So the user privilege and fusesmb autostart will take affect)

Ta-da!... network browsing like Nautilus, in Thunar. (assuming your samba was set up right, with the correct workgroup, etc.)

Hope that helps some Xubuntu folks, since Thunar lacks network browsing fucntionality.

-Taz

I do not have 

> "Allow use of fuse file systems..."

in my User Privileges :( I am on Dapper and I backported fusesmb from Feisty.

---

### Post by foxy123 on 2006-11-24
> **foxy123 said:**
> I do not have 



in my User Privileges :( I am on Dapper and I backported fusesmb from Feisty.

OK, I've just added myself in the fuse group and everything works fine. Thanks a lot for this fantastic idea, I have been dreaming about something like this for ages.

---

### Post by Tazix on 2006-11-29
> **foxy123 said:**
> OK, I've just added myself in the fuse group and everything works fine. Thanks a lot for this fantastic idea, I have been dreaming about something like this for ages.

Glad you found a solution.

None of this was my idea...  I just kept looking at the comments / suggestions on the Thunar site, because I was wondering when it was going to support Network browsing.  The author of Thunar recommends fusesmb as the best solution.

Whether he ever builds a front-end or plugin for Thunar to fusesmb, I don't know.  He states he rather have something like fusesmb handling the network browsing because it works in everything... not just Thunar.  So you basically can save a word processor file directly to a network share, just like you can in Winblows. ;)

-Taz

---

### Post by mcleaver on 2006-12-19
I'm not very nerdy so "install fusesmb" doesn't really mean much to me... certainly as it doesn't seem to be anywhere in 6.06.
My problem is that 6.10 doesn't support my wireless and 6.06 doesn't seem to support samba. Catch 22 :(
Rgds
Martin

---

### Post by bgochnauer on 2007-03-17
I use Konqueror - it's a great filemanager with smb support on Xfce (xubuntu)

I used Synaptic to load **kubuntu-desktop** then just added it with menu editor
and command: "kfmclient openProfile webbrowsing" or just "konqueror"

:)

---

### Post by jerrylamos on 2007-04-04
O.K., just loaded Konqueror and it does access shared folders!  Amazing!  (any clue how many MB that took??  I'll have to do a df -h before and after next time.....)

Now how do I add Konqueror to a menu?  How do I start a menu editor?  Where are the menu's?

Thanks much!  Cheers, Jerry:)

---

### Post by mawebb on 2007-06-09
Just tried the Fusesmb trick on Xubuntu 7.04 and it worked first time. Great!. Many thanks.

Mike

---

### Post by boterbram on 2008-01-21
I can't get it to work on 7.10, I will have to be root to use fusesmb and then access my mountpoint, so it's pretty much useless like this, anybody any ideas?

gr

EDIT:

It pretty much works now, but not really yet. I can finally see some folders in my mountpoint, but I can't acces them, it says "not enough memory". What should I do?

---

### Post by drsox1899 on 2008-04-27
> **jerrylamos said:**
> O.K., just loaded Konqueror and it does access shared folders!  Amazing!  (any clue how many MB that took??  I'll have to do a df -h before and after next time.....)

Now how do I add Konqueror to a menu?  How do I start a menu editor?  Where are the menu's?

Thanks much!  Cheers, Jerry:)

Just for info, as I'm about to try this also, 829MB of extra space & 263MB of downloads.

What it doesn't tell you is what the effect is on system overhead and response time !

Here's just as good an alternative - Dolphin

---

