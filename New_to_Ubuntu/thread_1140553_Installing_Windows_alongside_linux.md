---
title: "Installing Windows alongside linux"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by ayastona on 2009-04-27
hey i wanna use windows to use some programs that are windows-exclusive... i have wine and virtualbox should i just run windows through one of those? or should i install windows on a different partition on my drive? i want windows as a secondary thing on my machine.. is it possible?

---

### Post by miwaypet on 2009-04-27
Depends on your specs. VBox will take up some ram. If you have a good 2GHz dual core processor and 2 or more Gigs of ram, then go VB.

Dual booting is good. But I don't like giving up ground to Windows, unless I have to.

Wine works for some things. You need to ask in the forums about that specifically. We have a wine forum here, ya know.

---

### Post by JediJazz on 2009-04-27
As Ayastona say a decent powerful computer would be required for VB.

Dual booting is another option a simple way to achieve it would be. (Example on a 60 gb Hard Drive)

a. install Windows on your computer but specify the windows partition to be only to take up 20gb. (a partition)
Once windows is installed stick in an ubuntu disc and install that.
The ubuntu disc should show your partitions  the 20gb with Windows and 40gb to install Ubuntu in.
The installer in Ubuntu should pick up the Presence of the Windows OS you installed earlier and create a Menu (A Grub Menu) which the user can select what OS you want to use when you boot up the machine. 

They are far better indepth explanations out there but if you want to go down this route look for Tutorials on Dual Booting  Windows and Ubuntu.

Cheers

Jazz

---

### Post by Locke_99GS on 2009-04-27
OP: What apps do you require Windows for? 

Some apps require a Windows install, some work great in WINE, some are OK in a VM.

I would first look for linux alternatives to, or linux versions of, the Windows apps in question. If that's a no-go, try the Windows' app in WINE. Then try it in a VM. If you cannot get the app to function by these means, then you will require a Windows install.

---

### Post by bennachie on 2009-04-27
A lot of people choose to dual-boot for various reasons. The only problem in adding Windows to a Linux machine (apart from taking up disk space that could be used for something more productive) is that, as implied by an earlier post, the Windows installer expects to be able to barrel in and take over the show. You will therefore need to shrink and move your Linux partition, and create a new primary partition formatted as NTFS within which you can let the Windows installer do its thing. Afterwards, you will have to adjust things so that you can, once again, boot into Linux as well. You could use something like SuperGrubDisk for that purpose.

I'm not personally keen on Wine or VirtualBox. Wine works OK, but by no means all Windows programs work smoothly in that environment, while VirtualBox can be a major resource hog.

However, before putting in all that effort, why not have a look at the following, reasonably comprehensive, list of Linux packages which are equivalent to Windows packages? You may find what you want there.

[http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software](http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software)

---

