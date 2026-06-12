---
title: "Ubuntu, Mac OSX, Windows workgroup"
date: 2007-07-28
forum: Networking &amp; Wireless
---

### Post by Angel700 on 2007-07-28
I have created a workgroup that has an xp machine, an ibook, and my Ubuntu.  Using samba I am able to access all shares through the Mac and the XP.  My problem is that I am able to get the shares from XP on my Ubuntu, but I cannot access the Mac.  When I access the Mac through my XP i am prompted for the username and password after that i can access the share.  When I try it through Ubuntu (using: smb://xxx.xxx.xxx.xxx) i am not prompted for a username and password, it just opens a blank directory.  Where can I enter the username and password?  Is there any settings I can adjust on the Mac that allows me access without entering a username and password?  Any help would be much appreciated.

---

### Post by Frem on 2007-07-28
You can enter a user name and password by going to the "places" menu, then "connect to server" and changing the service type to "Windows share".

I don't have any OS X shares to connect to, and I don't use a Mac, so I'm not sure how to turn the Samba authentication off. :-(

---

### Post by Angel700 on 2007-07-28
i selected windows share, but it only asks for a username and not a password, and even when I enter it, it still doesn't connect.  Is there any other way you can think of?

---

### Post by nicholaspaul on 2007-07-28
I have a similar network (OSX x3, OS9, Win XP x2, Ubuntu Feisty) and I just have to make sure that the same user exists on all machines, and add each user to the smbusers list in ubuntu (using smbpasswd in the command line). Does that help any?

From Ubuntu, windows and OSX show up in the Places/Network menu or window. In Windows, the OSX machines show up in Network Places, and in OSX they show up under Network in the Finder (Macs are in 'My Network' and Win/Ubuntu are in 'Home', the name of my network). 
Hope that helps.

---

### Post by Angel700 on 2007-07-29
thanks for the help everyone, but it just started working by itself for some reason.  I think i just needed to restart or something.  Thanks again

---

