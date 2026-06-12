---
title: "XBMC Linux to Windows Shares"
date: 2008-01-30
forum: Networking &amp; Wireless
---

### Post by mikebeecham on 2008-01-30
Hi guys, 

Please bear with me, as this might be complicated:

I run an xbox media center, which initially ran SMB Windows Shares.  Since migrating over to linux, I have taken those shares and created Linux SMB's which the xbox utilises for streaming media.

For example, as long as the linux machine is on, I can stream media from the PC to the xbox downstairs through my router.  If I boot into Windows, then the XBOX cannot access those shared folders because it has been set up to view the linux SMB.

So, my question is this:

Is there any way to set up the XBMC, so that I can stream media from the linux shares, even when I am logged into Windows?

I hope that makes sense.

Thanks

---

### Post by Yhetti on 2008-01-30
If I'm understanding you right, what you'd have to do is create identically named shares and make sure that both Windows and Samba are broadcasting using the same computer name on the network.  You can then point the identical shares to the same locations on the PC's hard drive, and the XBox should be able to see them. 

When you do Windows networking, it basically only uses the computer name and the share name.  As long as the computer and share name are the same (and the username and password are also the same) then you should "see" the same fileshares when the PC is booted to Linux or Windows...

Is that the direction you're going in?

---

### Post by mikebeecham on 2008-01-31
I think so, yes.

I'm a little confused about the 'creating identical shares' bit...I'm assuming you're not talking about duplicating the actual folders?

On that basis, I did try to right-click and 'share' each folder through Linux, but it would not let me for some reason.

---

### Post by Yhetti on 2008-01-31
It's different in Linux.  More hands on, but more precise.  What you should do is get the name of the computer and all the shares you want to export in Windows and write them down.  

Make sure the directories you're sharing out in Windows are visable in Linux (mount them, wherever you want).
Then, as root, you edit /etc/samba/smb.conf and duplicate the Windows settings.  Most noticeably:

Under [Global]. make sure the WORKGROUP= and NETBIOS NAME= are correct (the workgroup, and the computer name respectively.)

Then, at the bottom, add shares to match.  So, if you have a Windows share called "ISOs" at d:\downloads\isos, you would do something like

[ISOs]
browseable = yes
public = yes
path = /media/sda2/downloads/isos

(assuming that your D: is at /media/sda2)

Then save the file and restart samba

/etc/init.d/samba restart


And your Linux machine should appear on the LAN roughly the same as your Windows machine.  Create as many shares as you need.

(if you don't have an /etc/samba/smb.conf, you'll need to install the actual Samba package:  sudo (or su) apt-get install samba )

---

