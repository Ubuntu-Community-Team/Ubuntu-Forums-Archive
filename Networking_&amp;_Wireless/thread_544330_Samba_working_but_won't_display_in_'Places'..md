---
title: "Samba working but won't display in 'Places'."
date: 2007-09-06
forum: Networking &amp; Wireless
---

### Post by alaekiefer on 2007-09-06
I've browsed through the forums and I've gone through most, if not all, posts related to Samba Shares (and the bugs evident in the newest version, etc.) and I feel that they don't relate to my present problem.

In brief:

1) I had just reinstalled Ubuntu Feisty on my laptop.
2) My folder-sharing, using Samba, was working in the first place.
3) It stopped working, I think, once I ran the auto-update application.
4) The problem: 

a) I can connect fine to my home PC (running on XP) using 'smbclient' in the terminal. (And using smbclient -l lists down my folders just fine.) The command 'smbtree' puts down all my folders nicely the way they should be. 
b) The 'MSHOME' network appears in my Places folder, and so do all the shared folders in that domain.
c) The problem being this:  I can't access my folder in the XP computer.

5) The funny part: I use Windows XP in Ubuntu through Virtualbox. And I CAN LOGIN into both my Ubuntu and XP (the folder on the home PC) through it.
6)I've edited my smb.conf file already, and for ease of use I've set security to 'share'.

I'm at my wit's end now. I've been toying around for the whole day, gone to a bunch of forums, and so on and so forth. (And for the record, I don't think I'm a victim of that 'msdfs proxy' bug too.)

I'm becoming very frustrated, but I can't rest unless this problem's settled, so any help would be VERY much appreciated. (Please do ask questions! If anything other people who have the same problem as me will have something to refer to in the near future.)

---

### Post by alaekiefer on 2007-09-06
*bump*

---

### Post by A$h X on 2007-09-06
I had this exact same problem on my machine, and unfortunately there is no concrete solution. I'm dual-booting, and have setup a home network on XP consisting of 3 machines. Everything was working fine, logged into Ubuntu and I could even see the other machines no problems. Then I tried to access the shared folder on the remote machines and the fun began. It took around 30 secs to get to the other machines on the network, but after that it was working normally. 
However, after a reboot into XP, the mshome network no longer accessible. :( It took multiple reboots and creating a new network to get the machines seeing each other again. and it only worked for one machine- the others I had to create a manual shortcut to each one. It now works, but not as it was indented. 
Samba leaves a lot to be desired when it comes to home networking. I hope your machine pops up after waiting for a while, that's all I can really recommend. :confused:

---

### Post by alaekiefer on 2007-09-07
> **A$h X said:**
> I had this exact same problem on my machine, and unfortunately there is no concrete solution. I'm dual-booting, and have setup a home network on XP consisting of 3 machines. Everything was working fine, logged into Ubuntu and I could even see the other machines no problems. Then I tried to access the shared folder on the remote machines and the fun began. It took around 30 secs to get to the other machines on the network, but after that it was working normally. 
However, after a reboot into XP, the mshome network no longer accessible. :( It took multiple reboots and creating a new network to get the machines seeing each other again. and it only worked for one machine- the others I had to create a manual shortcut to each one. It now works, but not as it was indented. 
Samba leaves a lot to be desired when it comes to home networking. I hope your machine pops up after waiting for a while, that's all I can really recommend. :confused:

Thank you for replying! 

I see now that there really isn't any concrete solution to this problem, is there? I'm not very happy, but I guess I can't do anything but wait for the next Ubuntu update. *sigh*

By the way, did creating a new network on the XP machine immediately allow you access to its shared folder your Ubuntu machine?

---

### Post by A$h X on 2007-09-08
> **alaekiefer said:**
> Thank you for replying! 

I see now that there really isn't any concrete solution to this problem, is there? I'm not very happy, but I guess I can't do anything but wait for the next Ubuntu update. *sigh*

By the way, did creating a new network on the XP machine immediately allow you access to its shared folder your Ubuntu machine?

No need to thank me, I had ALOT of problems with connecting to windows networks, and I read countless threads here, the majority of which suggested editing samba.cfg - I tried that and not sure if it solved my problem. Anyway I decided to check up on the state of my network, found some interesting results, have a look at the attached screenshots. 

The left shows my network in ubuntu, and the right in XP. My machine (alpha2) is a dual boot, while the others are XP only. My machine in both ubuntu and XP can read/write to the others with no problem. Whilst alpha2 is in XP, the others can read/write to it normally. However, if alpha2 is in ubuntu, then the others can only read/copy files from the shared folder!  No delete/write access whatsoever. :confused:

Now i know this isn't ideal, but TBH i've had so many problems with samba i'm content just to boot into XP to move files from the network into my machine (mostly move files from alpha2 to the others). Pity the permissions are somewhat confusing to implement in samba, otherwise it would be an almost flawless networking tool.

---

### Post by A$h X on 2007-09-09
Hey did you sort out your problem? I want to help anyone having trouble with samba as personally speaking it was the only part of ubuntu that caused me any problems. If anyone wants i'll post up my smb.conf and then it can be edited to suit your needs.

---

### Post by strange_cathect on 2007-09-09
I seem to have the opposite problem.  I can see my Samba shares in my two laptops which run XP and connect wirelessly to the network.  However, my desktop (which runs Ubuntu) doesn't see the Samba shares.  

The weird thing is that it recently worked fine (right after I set up the samba shares) but then it suddenly stopped working.  I can't figure it out.  Any ideas or help will be appreciated!

---

