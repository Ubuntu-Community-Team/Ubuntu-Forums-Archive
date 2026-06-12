---
title: "File sharing with OS X"
date: 2008-01-09
forum: Networking &amp; Wireless
---

### Post by Danyl on 2008-01-09
Hi again

I'm trying to establish a connect with my OS X machine so I can share files between them. I'm running both machines through a Belkin router/modem, will that still work?

I've followed this guide: [http://www.linuxquestions.org/linux/answers/Networking/File_sharing_with_OS_X_using_Ubuntu_5_04]("http://www.linuxquestions.org/linux/answers/Networking/File_sharing_with_OS_X_using_Ubuntu_5_04") but I've had no luck (I'm running Gutsy not 5.04).

I have no experience with Samba whatsoever and have found similar threads fairly  unhelpful.

Is my hostname the name that appears when I first fire up the terminal? Ie: **dan@dan-ubuntu** or is the hostname just **dan-ubuntu**? I'm confused!

Has anyone successfully achieved what I'm attempting to do?

---

### Post by tgalati4 on 2008-01-10
Samba can be finicky to set up.

Make sure your /etc/samba/smb.conf file contains stuff like:

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam guest

   obey pam restrictions = yes

   guest account = tgalati4
   invalid users = 

.
.
.

[tubuntu2_music_share]
path = /home/tgalati4/mp3
comment = Useful for sharing tracks
available = yes
browseable = yes
public = yes
writable = no

[windoze]
path = /mnt/windows
comment = useful for win98 files
available = yes
browseable = yes
public = yes
writable = no


---------------------

Make sure that you have the same username and password on the Mac side otherwise it will not authenticate properly.  Depending on what version of Mac OS X, you may have a bug in Finder for connecting to the server.  If so, then use the "Go-->Connect to Server"

smb://TUBUNTU2/tubuntu2_music_share

Log in with your samba username and password (which should be the same as your mac username and password).

You may have to restart samba after modifying your smb.conf:

>sudo /etc/init.d/samba restart

---

