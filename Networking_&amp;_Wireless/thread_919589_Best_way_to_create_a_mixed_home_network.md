---
title: "Best way to create a mixed home network?"
date: 2008-09-14
forum: Networking &amp; Wireless
---

### Post by GepettoBR on 2008-09-14
I'm tired of making Hardy's broken SAMBA/Nautilus mix work well, so I decided to turn things the other way around. In my house there are four computers, as follows:

0)Dual-booting Windows XP and Ubuntu Hardy
1)Running Hardy
2)Running XP
3)Running Vista (yikes - this one isn't mine, don't lynch me)

Since making a Windows network doesn't work at all for me (not even sharing my printer - connected to the XP-only machine - with the Ubuntu machines works) what are my alternatives? How do Linux computers normally connect in a LAN and can I throw my Windows machines into the mix? I've read a bit about SSH but I have no idea how it works.

Thanks in advance,
Paulo.

---

### Post by GepettoBR on 2008-09-14
I linked here in the BUMP thread, a parallel discussion is taking place:

> **pp. said:**
> Bump

A bit more information would be useful. In what way does your Samba/Windows/Nautilus setup not work? What kind of printer is it that you want to share from your Windows XP box, and how, exactly, does it not work? Why don't you connect the printer to the network instead of to the PC?

> **GepettoBR said:**
> Nautilus simply won't display anything when I go to Places>Network>Windows Network>Workgroup>[computer name], and sometimes it doesn't even display the computers on the network (not even the one I'm accessing from). All pings work and I can connect to shares via Places>Connect to server... but even though I managed to install the remote printer via CUPS, it won't print anything I send it via Ubuntu - not even a test page. On the other hand, the Windows computers have no trouble accessing the shares on my Ubuntu computers, which means that at the very least, the samba server is configured correctly.

The printer is a Hewlett-Packard DeskJet 640C, connected to the XP-only machine. The dual-boot machine has no trouble using it via Windows, and as far as I know, no one has tried accessing it from the Vista laptop. I haven't connected it to the network because I lack the hardware to do so- I don't have a print server and my router won't accept USB clients (I don't even now if just plugging the printer into the router wold work, really, but the router only has ports for ethernet cables). Currently, if I want to print a file from a Ubuntu client, I have to access the shared folder from the XP machine and print locally.

Looking around for an answer, I found that many people have the same or similar problems in Hardy, and this apparently wasn't an issue in Gutsy. Oddly enough, when my friend's computer powered down during a Windows re-install and screwed the MBR, I was able to safely use a Hardy LiveCD to force-mount the disk and transfer the files to his dad's Mac via Samba and Nautilus. Still, most anecdotal evidence points to this being a general issue with Ubuntu 8.04.

Being that none of the proposed solutions have worked for me so far, I decided to look at this from another angle: if Ubuntu won't play nice in a Windows environment, can Windows play nice in a Linux environment? Sadly, I don't know how to set one up, which is why I started that thread.

Please tell me if there is anything else I should have said.

*Edit: Holy cow I forgot to BUMP! Now I must BUMP in double! BUMPBUMP!*


> **pp. said:**
> BUMP

My suggestions:

[LIST]
[*]Put your narrative above into the thread where you ask for support.
[*]Try accessing the printer from another Windows client. If that works, you know at least that the XP box is sharing it properly.
[*]Try and check if all the Windows and Linux boxes are in the same work group. Also, change the name of the work group from 'Workgroup' to some other value (on all boxes).
[*]I'm not sure if CUPS is what you need for using the printer on the Windows box.
[/LIST]

BTW, I can not see the names of the other computers in my LAN, either. I also can not usually see the names of the shares. That seems to be some kind of shortcoming of the Hardy Heron.

---

### Post by GepettoBR on 2008-09-14
Oops, double-post.

> **pp. said:**
> BUMP

My suggestions:

[LIST]
[*]Put your narrative above into the thread where you ask for support.
[*]Try accessing the printer from another Windows client. If that works, you know at least that the XP box is sharing it properly.
[*]Try and check if all the Windows and Linux boxes are in the same work group. Also, change the name of the work group from 'Workgroup' to some other value (on all boxes).
[*]I'm not sure if CUPS is what you need for using the printer on the Windows box.
[/LIST]

BTW, I can not see the names of the other computers in my LAN, either. I also can not usually see the names of the shares. That seems to be some kind of shortcoming of the Hardy Heron.

[LIST]
[*]0 Done
[*]1 The printer works from the Dual-Boot machine if it runs Windows (this was mentioned on my previous post)
[*]2 They are all in the "WORKGROUP" workgroup. I'll try changing the workgroup and I'll post back the results.
[*]3 I installed the printer in CUPS when I took my Ubuntu laptop to the same room as the printer and connected the computers directly with a crossover cable, long before I even had a router or a home network. It worked perfectly. CUPS has a specific option for printers connected to a Windows machine on the network.[/LIST]

---

### Post by Whiffle on 2008-09-14
Use something other than Nautilus for samba shares?   Dolphin has been working excellently for me in KDE.  

Printers should be able to work with CUPS, maybe try adding it through the cups html interface at [http://localhost:631](http://localhost:631)

---

### Post by GepettoBR on 2008-09-14
> **Whiffle said:**
> Use something other than Nautilus for samba shares?   Dolphin has been working excellently for me in KDE.  

Printers should be able to work with CUPS, maybe try adding it through the cups html interface at [http://localhost:631](http://localhost:631)

Dolphin shows the other computers on the network under "Samba Shares", but when I try to access any of them it diisplays a blank folder. The status bar reads "timeout on server (<server name>)". Konqueror doesn't work either.

The CUPS html interface is exactly what I used to install the network printer. It does not work.

---

### Post by Whiffle on 2008-09-14
Hmm.  What happens when you put in smb://nameofcomputer or smb://ipofcomputer into the address bar on konqueror?  

Not sure what to tell you on the printers, except to make sure you've got the right linux drivers for the printer in question.

---

### Post by GepettoBR on 2008-09-14
In both cases (hostname and IP) on all thee file managers (Konqueror, Nautilus and Dolphin) I get a blank folder. Dolphin still displays the timeout message. I also downloaded thunar, but it apparently lacks the ability to browse an SMB network.

---

### Post by bab1 on 2008-09-14
The Gnome/Nautilus gvfs interface is broken.  Samba does not work as expected.  See #5, 6, 6  in the following:
[http://ubuntuforums.org/showthread.php?t=916807&highlight=gregphil]("http://ubuntuforums.org/showthread.php?t=916807&highlight=gregphil")

The answer to your question at this point is a fresh install of Hardy Kubuntu .  I understand the KDE works correctly (as per GregPhil.

If you are a Gnome fan (as I am), my understanding is that Intrepid with Gnome 2.22 will solve most of these problems.  Gnome 2.22 uses the new gvfs libs instead of a hybrid of Gnome-gfs and gvfs.  In addition it looks like Samba has been updated from 3.0.xxx to 3.2.  All this is due in October with the 8.10 Intrepid release.

---

### Post by GepettoBR on 2008-09-14
> **bab1 said:**
> The Gnome/Nautilus gvfs interface is broken.  Samba does not work as expected.  See #5, 6, 6  in the following:
[http://ubuntuforums.org/showthread.php?t=916807&highlight=gregphil]("http://ubuntuforums.org/showthread.php?t=916807&highlight=gregphil")

The answer to your question at this point is a fresh install of Hardy Kubuntu .  I understand the KDE works correctly (as per GregPhil.

If you are a Gnome fan (as I am), my understanding is that Intrepid with Gnome 2.22 will solve most of these problems.  Gnome 2.22 uses the new gvfs libs instead of a hybrid of Gnome-gfs and gvfs.  In addition it looks like Samba has been updated from 3.0.xxx to 3.2.  All this is due in October with the 8.10 Intrepid release.

Wow, way to screw up an LTS version... Guess I'll wait for Intrepid then. I've been struggling with this since May, what's another two months? I won't mark the thread as solved, though, because waiting for the next release isn't actually a solution.

---

### Post by bab1 on 2008-09-14
It is indeed unfortunate that the LTS cycle has been screwed up.  Gnome releases are scheduled just before the Ubuntu releases are finalized.  It was a train wreck waiting to happen.

Look at the bottom right of:[https://bugs.launchpad.net/ubuntu]("http://https://bugs.launchpad.net/ubuntu")

You will see Hardy has almost 3 times the bugs as Gutsy.  There are 457 for Hardy and 161 for Gutsy.

---

