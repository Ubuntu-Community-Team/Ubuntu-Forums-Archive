---
title: "How good is virtualisation?"
date: 2011-03-06
forum: New to Ubuntu
---

### Post by RogerGT on 2011-03-06
As a prospective Linux user I'd be glad to have an opinion or two on my questions below.  I run XP on a my home PC but am keen to explore a switch to Ubuntu or a similar quality distro (I'm currently dual booting on a trial basis but it's obviously pretty slow).   The only problem is that I'm fairly dependent on some proprietary software which simply won't function under a Linux environment even using Wine.  I've read that by using virtualisation software with a Linux host it's possible to instal XP as a guest and then to instal and run proprietary software within XP.  Is it really that simple?  Will this software run properly in that situation?  I'm literate but not a techie, so is virtualisation a reasonably straightforward process?  Are there any disadvantages or pitfalls to be aware of?

Any views, opinions or references to other sources of information would be greatly appreciated.

Many thanks.

---

### Post by mikewhatever on 2011-03-06
Virtualisation is indeed rather easy these days, thanks to Virtual Box. You'll need a relatively powerful computer to run it, and the only disadvantage I can think of is in the area of 3d games and heavy graphics.

---

### Post by RogerGT on 2011-03-06
Thanks for that  -  it's a 3.0ghz dual core with 2gb RAM and 250gb HD so hopefully that will do the job?  I'm not a gamer, so 3D graphics shouldn't be an issue?

---

### Post by thane1 on 2011-03-06
I've been using Virtualbox for a couple of months now and I'm more than just pleased.  I had been having trouble getting workout data from a heartrate monitor transferred into linux for analysis, as everything was windows oriented.  The same for a Computrainer bike program.  There were other programs, which also caused problems.  Dual booting was inconvenient and didn't let me work in Ubuntu as desired with these programs.  Wine wasn't an option for these programs either.

     With Virtualbox set up using Ubuntu as the host machine and XP as the guest machine, I now have access to _all[U] _[/U] of my programs without dual booting.  Ubuntu works normally and if I shut down my client XP to a saved state, the startup time for XP to have a working desktop is negligible.  The XP runs a little slower, than it would in a dual boot system.  There is definitely a learning curve involved and a few procedures to sort out if for instance you are trying to get the client to access real hardware for some programs instead of the virtualized hardware (ie: a dvd burner, serial or com ports, usb ).  But the documentation is excellent and if you cannot find, what you're looking for, the forum assistance is phenomenal.

     Virtualization won't run on just any old box though.  The cpu and mobo need to support virtualization.  So I needed to update to a new cpu, mobo and ram. Lots of ram helps as you'll be running more than one operating sytem at once and they both still need their quota.  However after getting the new parts and mixing and matching parts from the new system and the 3 other  systems in the house, I'm now down to 2 computers in the house, thanks to what Virtualbox has let me do.    Cheers

---

### Post by ikt on 2011-03-06
> **RogerGT said:**
> Thanks for that  -  it's a 3.0ghz dual core with 2gb RAM and 250gb HD so hopefully that will do the job?  I'm not a gamer, so 3D graphics shouldn't be an issue?

what applications to you need to run in xp?

---

### Post by Anuovis on 2011-03-06
I am using VirtualBox myself and it really handles the virtual Windows XP well. Once you set it up, it's almost the same as using the regular Windows.

Just be sure that you have enough resources (especially RAM) to run Ubuntu and virtual Windows and whatever software you want to use.

Also, all the hardware is emulated by the host so you can't use Windows drivers and such. Not that you'd need to do so though, the software takes care of that.

I also advice you to install Guest Addons if you use VirtualBox, it makes file sharing between host and guest possible. You can do that from the menu once you launch the Windows for the first time.

As far as I am aware, the main concern should be resources since you are essentially running to OSes at the same time. Also, 3D graphics might be a problem, like someone mentioned already.

---

### Post by blueridgedog on 2011-03-06
> **RogerGT said:**
> Thanks for that  -  it's a 3.0ghz dual core with 2gb RAM and 250gb HD so hopefully that will do the job?  I'm not a gamer, so 3D graphics shouldn't be an issue?

You won't have any issues running Virtual Box, but if you end up doing it full time, you may want a bit more memory.  With only two gig of RAM, you will not be able to allocate much to a virtual machine without "swapping" onto your hard drive.

---

### Post by RogerGT on 2011-03-06
> **ikt said:**
> what applications to you need to run in xp?

Microsoft Money, Sibelius (music notation software), Sharpeye (music scanning program), possibly Netobjects Fusion, a website design program.  Skype, too, I think is better set up under Windows.  That's about it, I think.

---

### Post by RogerGT on 2011-03-06
> **Anuovis said:**
> I am using VirtualBox myself and it really handles the virtual Windows XP well. Once you set it up, it's almost the same as using the regular Windows.

Just be sure that you have enough resources (especially RAM) to run Ubuntu and virtual Windows and whatever software you want to use.

Also, all the hardware is emulated by the host so you can't use Windows drivers and such. Not that you'd need to do so though, the software takes care of that.

I also advice you to install Guest Addons if you use VirtualBox, it makes file sharing between host and guest possible. You can do that from the menu once you launch the Windows for the first time.

As far as I am aware, the main concern should be resources since you are essentially running to OSes at the same time. Also, 3D graphics might be a problem, like someone mentioned already.

Is 2gb likely to be enough?

---

### Post by RogerGT on 2011-03-06
Thanks for all your comments folks, you've definitely encouraged me, particularly since people seem to be having a lot of success using VirtualBox.  Maybe time for a RAM upgrade though.  I'm having to log off now, I'm afraid.  It's late here 'down under' and an early morning awaits tomorrow!  I would naturally still welcome other comments but will have to wait until morning.  

Many thanks again.

---

### Post by spillage2 on 2011-03-10
Would just like to say I'm running vbox with 3gb of ram and can quite easly run ubi 10.04 and have xp ubi backtrack fedora all running at the same time in vbox without any issues.

---

### Post by JKyleOKC on 2011-03-10
I have seven VMs installed on this machine, which has approximately the same specs as yours, but usually only one of them active at a time. Some of them run XP and others run Win2K; all of them are set up with minimum RAM and moderately small virtual drives, but my approach is to have each of them handle only specialized tasks. One is for program development with Delphi, another for development with Visual Basic (which is necessary to support a utility I wrote many years ago), a third for doing data conversion, and so on. All of them are in "saved" state when not running so they take only a few seconds to activate.

You do need to be especially careful about backing up any critical data that you have stored on virtual drives, because accidental file corruption can make such a drive totally unreadable (unlike real drives, where software exists to recover from such damage). I recently lost the past six months worth of Email messages to just such a disaster that happened on another machine here. That's the only problem I've encountered, though, in some two years of virtualization via VirtualBox...

---

### Post by boron on 2011-03-13
> **RogerGT said:**
> As a prospective Linux user I'd be glad to have an opinion or two on my questions below.  I run XP on a my home PC but am keen to explore a switch to Ubuntu or a similar quality distro (I'm currently dual booting on a trial basis but it's obviously pretty slow).   The only problem is that I'm fairly dependent on some proprietary software which simply won't function under a Linux environment even using Wine.  I've read that by using virtualisation software with a Linux host it's possible to instal XP as a guest and then to instal and run proprietary software within XP.  Is it really that simple?  Will this software run properly in that situation?  I'm literate but not a techie, so is virtualisation a reasonably straightforward process?  Are there any disadvantages or pitfalls to be aware of?

Any views, opinions or references to other sources of information would be greatly appreciated.

Many thanks.  I am using Virtualbox on win7 running Ubuntu 10.10 (Maverick Meerkat) as a guest operating system, and this works very well, once guest additions is installed, so I am optimistic that VB would work for you, too.  Why not give it a try?  download virtualbox v4.04 from [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)
and install xp, then install guest additions - this allows better set up of your monitor resolution and also to share data between the host Os (Ubuntu I presume) and the guest (XP)
Good luck, it will cost nothing to try it.:P
had a problem installing guest additions, but found the solution on youtube at [http://www.youtube.com/watch?v=uVso11Ji7Bc](http://www.youtube.com/watch?v=uVso11Ji7Bc)

---

### Post by bk60544 on 2011-03-13
I have Win7 and Ubuntu 10.10 dual-booting on an Acer Laptop. Just started using Virutal Box to run XP.  The first "problem" I've encountered is that USB ports aren't working in XP - although they work in both Win7 and U10.10.  So check that ALL of your hardware is functional before you go through installing all of your programs.

---

### Post by JKyleOKC on 2011-03-13
If you're using vbox version 3, the "ose" that's in the repositories does not support USB. You have to use the "puel" edition that comes from Oracle's download site, and then install the "guest additions" in XP after installing XP itself.

If you're using vbox version 4, now in the repositories, you need to install its "extension pack" from the Oracle site in order to enable USB and guest additions.

Either way, it's free of cost for personal use but the PUEL and extension pack are "non-free" in the open-source sense of the word since their source code is not distributed due to proprietary concerns. It seems that USB itself may have some restrictions as to what can be made public...

The Oracle download site is at [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads) and it has DEB files that are fully compatible.

---

### Post by dbowlin17 on 2011-03-13
i love virtualization. When I initially tried it, I had a 2ghz pentium 4 with 1.5 gigs of ram. it was somewhat slow, but I got what i wanted to get done done. However, I have since built a new computer with an i3 550 (dual core but hyperthreading so ubuntu reads it as quad core) and 8gb of ddr3 (because it was 5 bucks more than 4 gigs) and i love it. I don't notice any speed issues when I have xp running. my best advice would be for you to try it. most all apps will work. the issues would be with the intense graphics or games. once again, you can always just install virtual box. i reccomend the real virtualbox [http://www.virtualbox.org/]("http://www.virtualbox.org/") because it supports usb devices and I feel is a more complete product when compared to virtual box OSE (what you find in ubuntu software center)

 hope this helps

---

### Post by blueridgedog on 2011-03-13
I have a quad core intel chip and 8 gig of ram running 64 bit Ubuntu.  I can run two virtual instances, each with ample resources and have no noticeable impact on the system (and no usage of swap).

---

### Post by Hedgehog1 on 2011-03-13
> **RogerGT said:**
> Thanks for that  -  it's a 3.0ghz dual core with 2gb RAM and 250gb HD so hopefully that will do the job?  I'm not a gamer, so 3D graphics shouldn't be an issue?

RogerGT,

For me, virtualzation allows me to have what ***would*** be a whole room full of PCs, but without all the extra hardware:

[IMG]http://img862.imageshack.us/img862/3982/vboxmanager.png[/IMG]

If you are not using 3D graphics in windows, then this is a great fit for you.

If you want to run more than one Virtual Machine at a time, you would want to add RAM.  But Ubuntu and XP in a VM will run very nicely on 2 gigs.

It really is awesome fun (as well as being useful).

***The Hedge***

:KS

---

### Post by bk60544 on 2011-03-14
Hi Jim, thanks for pointing me in the right direction, but it is a "dead end". Upgraded VB to 4.0.4, and the extension pack and guest additions [despite incomplete info from Oracle]. Now under "devices"> USB, the thumbdrive and drive APPEAR, but they are greyed/blacked out, so **not** accessible.  {Of course they are on functional on the Ubuntu desktop.}  Any clues, Oracle documentation is just horrible.

---

### Post by __Ryan__ on 2011-03-14
Shameless plug but I just wrote a guide to setup USB support in VirtualBox.

[setup-usb-support-in-oracle-virtualbox]("http://www.wiredrevolution.com/virtualbox/setup-usb-support-in-oracle-virtualbox")

Good Luck. VirtualBox is a great tool.

---

### Post by bk60544 on 2011-03-14
I also found this solution which worked for me. For those are having trouble  getting your virtual systems to read and write to USB devices, here's an  easy way to permanently fix that problem. This post is an addition to [http://ubuntuforums.org/showpost.php...45&postcount=4]("http://ubuntuforums.org/showpost.php?p=6122145&postcount=4") by bodhi.zazen and is Karmic-specific.

1. Go to System>Administration>Users and Groups
2. Click on your user name and unlock [COLOR=Red][i did not find "unlock".][/COLOR]
3. Click on "manage groups"
4. Scroll down until you see "vboxusers." Click on it and then on "Properties"
5. Click on any and all accounts you want to add to VirtualBox. This would generally be you. Don't click on root
6. Close everything
7. Reboot

TAH DAH! You are done! Now USB devices can be read and written to!

---

### Post by JKyleOKC on 2011-03-14
That was the solution I was about to suggest to you. The reboot isn't usually necessary, though; just logging out and then logging back in is adequate. Your group memberships are checked as part of the login process. And you should have found that your user id already had a check mark in vboxusers, if you installed it from your own login. However if you installed as "root" by using sudo in a terminal, it might not have been checked. The installation procedure creates the group, and adds the current user to it.

And this technique works at least through Lucid; it should continue to work indefinitely since it uses only normal system utilities!

EDIT 2: You don't have to unlock to change your own user info, but do in order to change the data for any other user.

---

### Post by bk60544 on 2011-03-14
JKyle, thanks for elaborating.  Now, any clues/tips on connecting a USB printer on a XP machine using SAMBA.  Using browse doesn't work, nor does manually entering [workgroup]/[machine]/[port]/[printer].  Printer is shared with other win pc's.

---

### Post by blueridgedog on 2011-03-14
> **bk60544 said:**
> JKyle, thanks for elaborating.  Now, any clues/tips on connecting a USB printer on a XP machine using SAMBA.  Using browse doesn't work, nor does manually entering [workgroup]/[machine]/[port]/[printer].  Printer is shared with other win pc's.

I assume that you are referring to an XP machine instance in a virtual box.  If so, try the IP address of the printer host in the windows explorer address bar (not internet explorer) formated as \\192.168.1.1 (for example)

---

### Post by JKyleOKC on 2011-03-14
> **bk60544 said:**
> JKyle, thanks for elaborating.  Now, any clues/tips on connecting a USB printer on a XP machine using SAMBA.  Using browse doesn't work, nor does manually entering [workgroup]/[machine]/[port]/[printer].  Printer is shared with other win pc's.First, how are your vbox network adapters configured? You have several choices available, and they will affect how you communicate with shared devices on the network. I use static IP address for all four boxes on my LAN, and have all my virtual machines set up with "bridged" network adapters. They are, in turn, assigned their own static IP addresses. I use the 192.168.0.0 subnet, and the real machines are assigned as 2, 3, 4, and 5 (that is, this box is 192.168.0.2 on the LAN). The virtual machines get 2-digit identities; my email VM running on 192.168.0.5 has the address 192.168.0.52. Doing it this way lets all the machines communicate with each other (of course when they are running) just as if they were all physical boxes connected to the LAN.

If you set the adapters up as "NAT" then they will get addresses from a different subnet range, and will not be able to communicate easily with each other but will be able to get to the outside world.

To connect a printer running on a real Windows box elsewhere on your network to an XP VM that has a bridged adapter, assuming that the printer is already shared with other boxes on your network, it's necessary to know the NetBIOS names of its host box and of the printer itself. One way to get this information, from Ubuntu, is to run the command "smbtree" in a terminal window. If it asks for a password just hit Enter. This is part of the Samba suite, but I believe it's installed automatically with Ubuntu. It will take a little while to poll the network, then display a tree view of all the devices it can find. These should include the printer, and the printer's host. Make note of both names. Then go into the XP VM and launch the Add Printer wizard. Tell it you want to add a network printer, and fill in the name with \\host\printer (replacing "host" with the host name you noted, and "printer" with the printer name). Note that these are backslashes rather than forward slashes. Then proceed through the wizard, and finally print a test page.

If your adapters are set for "NAT" I'm not sure how to do it, but the post from blueridgedog looks like a promising approach...

Connecting the printer to the Ubuntu host is a bit different but I found it to be simpler. If you need the procedure for that just let us know!

---

### Post by blueridgedog on 2011-03-14
> **JKyleOKC said:**
> 
If you set the adapters up as "NAT" then they will get addresses from a different subnet range, and will not be able to communicate easily with each other but will be able to get to the outside world.


Oddly, it ends up bing a subnet in a nat so to speak.  You can ping from the inside subnet used for the VM's to the outside, so I access my devices on the lan in nat mode, but would probably do bridging if I were to set it up again.

---

### Post by SeijiSensei on 2011-03-14
> **blueridgedog said:**
> I assume that you are referring to an XP machine instance in a virtual box.  If so, try the IP address of the printer host in the windows explorer address bar (not internet explorer) formated as \\192.168.1.1 (for example)

It's also useful to be able to map a Windows share over the network with \\ip.addr.of.server\share as a network drive, and mount the same share in Linux with smb://ip.addr.of.server/share.  That method works with both KDE Dolphin and GNOME Nautilus, I believe.  You can also share folders between the host and guest(s) with VirtualBox, but I find sharing over the network easier to set up.

---

