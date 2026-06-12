---
title: "need networking help! - can't access network machine"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by ghostofzuul on 2009-01-21
hi. 

i can't access my mac through my network... most of the time i can see the mac on the network from my linux box however there are times (especially after re-start) when the mac doesn't appear on the network. When it does appear on the network and i click on it, it doesn't give me the password dialog to sign-in. The wheel spins and then nothing. 

Sharing on the mac is set up properly as I have other computers on the network that can access the mac tower and don't don't have this issue however they are also macs.

Going the other way... I can access the files and read and write to the drives on my linux box from my mac just fine, every single time so i know the network and sharing is set up properly....

Funny that even when I can move files across the network from the mac to the linux box the linux box still doesn't always show the mac in the network.

I don't want to ftp into the mac or have to do a lot of messing around in the command line... so if anyone has an obvious fix that i'm overlooking.... let me know... if it's more complicated i'm a command line novice so be nice!

thanks!

---

### Post by mjheagle8 on 2009-01-21
how do you try to connect to the mac? via ssh? samba?
and what do you want to do? see the screen? browse shared folder(s)?

---

### Post by ghostofzuul on 2009-01-21
> **mjheagle8 said:**
> how do you try to connect to the mac? via ssh? samba?
and what do you want to do? see the screen? browse shared folder(s)?

Hi, I've got samba installed in ubuntu and have all the folders set up for sharing... as mentioned the mac can access all the shared folders on both drives of the ubuntu box....

don't want to see the screen or vpn or anything, just want access to the folders and desktop.... 

thanks!

---

### Post by mjheagle8 on 2009-01-21
ok what are you using to share the folders on the mac?

---

### Post by ghostofzuul on 2009-01-21
> **mjheagle8 said:**
> ok what are you using to share the folders on the mac?

on the mac, in preferences>sharing both "personal file sharing" and "windows sharing" are selected and active. my user is set up to log-in to the shared folders... but as i mentioned... click on the machine in ubuntu and nothing happens... it just gives me a blank window. if i click on the unbuntu machine itself in the network... i can see all the shared folders as i would expect to when i clicked on the icon for the mac machine...

thanks again for all your help.

---

### Post by mjheagle8 on 2009-01-21
do you have all the necessary samba packages installed on your ubuntu system?

---

### Post by ghostofzuul on 2009-02-06
bump.

still having this issues and haven't found any help pages or info that explains the problem.... 

thinking it's got to be something obvious but can't put my finger on it.

if anyone with fresh eyes has any ideas i'd appreciate it!

thanks!

---

### Post by Kellemora on 2009-02-06
Hi Ghost

I'll start by saying that there is a BUG in Nautilus, been there for about 3 years now if not longer...........

That being said:
Have you installed smbclient and smbtree?  I'll show you why you need tree in a minute.  IF you see smbfs is installed, uncheck it so it gets turned OFF, it prevents many shares from showing.

In smb.conf did you change WORKGROUP =  WORKGROUP so it reads WORKGROUP = TheNameOfYourWorkgroup?

In System/Admin did you add your name and group in Users & Groups?

OK, about smbtree.  In terminal, if you type smbtree and all of your shares show up, then your network and samba are working correctly.
If you see them in smbtree but not in Places/Network, it's the Bug in Nautilus causing this.  Tomorrow it might be working just fine, then a couple of days later not working again.

The way around this is to go up to the top of the nautilus page and select Go/Location and type in the IP address of the machine you are trying to reach, then all the shares will show for you.
When typing the IP address, the form to use for Samba is
smb://xxx.xxx.xxx.xxx EG: smb://192.168.1.101 then hit enter.
Naturally the numbers will be the address on your system for that computer.

I could have saved nearly two full weeks of burning the midnight oil had someone, anyone, would have told me about this BUG in nautilus and how to get around it.  I had to figure this out on my own the hard way!  Among many other things too!

Good Luck

TTUL
Gary

---

### Post by jwatrous on 2009-02-06
I just installed 8.0.4 on a t41 thinkpad and can't see any wireless devices.

---

