---
title: "Samba. Mapped drives. Win2k Pro. XP SP2. Vista."
date: 2007-12-21
forum: Networking &amp; Wireless
---

### Post by Roasted on 2007-12-21
I just got Samba up and running. I have 5 computers in the household. I have my Ubuntu desktop, Vista laptop, brother's Win2kPro desktop, other brother's Win2kPro desktop, and my mother's Dell XP SP2 desktop.

I mapped the drives out across the network to locate my spare hard drive in my desktop which contains the samba share I want to distribute out. I set up username's and passwords for them, however, when they reboot they are prompted with having to put the password in to reconnect the mapped drive.

How can I set it to automatically connect without having to put the password in, as if the password is saved?

---

### Post by glasswalkerny on 2007-12-22
If you are talking about all the Windows systems you need to select **Connect as _[COLOR="RoyalBlue"]different user name[/COLOR]_ **in the map drive window. In there you can put in the username and password for the share and it should remember it. Otherwise when windows tries to re-establish the shares it tries using the username/password that windows was logged in under.

---

### Post by Roasted on 2007-12-22
How about this...

Seeing as though I actively dual boot on my desktop, where the samba server is, I'm thinking it may not be in my best interest to have the drives prompt the users for passwords upon logon. 

I wonder... is it possible to prevent the drivers from reconnecting upon logon, however say my brother wanted to back something up, go to my computer, see the disconnected drive, right click - connect, type in username and password, BAM, he's in? 

That'd be nice, because I'm not always in linux with the share running, sometimes I'm gaming in windows. I'll see if I can get it working like this.

---

