---
title: "Permission problems when mounting samba shares"
date: 2008-11-02
forum: Networking &amp; Wireless
---

### Post by lingenfr on 2008-11-02
I set up a new intrepid machine and upgraded my file server to intrepid. I mount two samba shares on the file server via smbfs. An example line from /etc/fstab is as follows:

//192.168.1.110/videos  /media/videos smbfs credentials=/root/.smbcredentials,dir_mode=0777,file_mode=0777 0 0

My .smbcredentials file has the login/password for the account on my file server. However, now I can't write to /media/videos. When I look at permissions it is owned by polkituser and group messagebus. If I navigate to the //192.168.1.110/videos samba share with dolphin I can write to it, but it is written with owner polkituser and group messagebus and I can't get into it.

What the heck is going on? Is there a guide that shows the correct way to setup/connect to samba shares with Intrepid. Obviously the procedures have changed. Thanks.

---

### Post by lingenfr on 2008-11-03
Bump

---

### Post by lingenfr on 2008-11-08
Bump. Still need help.

---

### Post by lingenfr on 2008-11-23
Still haven't fixed this and still haven't received any help. How about it? Seems no matter what I do, when I create a new folder in my samba music share it is owned by haldaemon and in a system owned group. No sudo, su or anything will allow me to change the permissions. How do I fix this so that I can create folders with my user as the owner and group.

---

### Post by Iowan on 2008-11-24
It's unfortunate that no one has offered suggestions - the forum is usually more responsive.  SMBFS is deprecated - CIFS is the new standard.  It won't necessarily solve the access problems, but [this]("http://ubuntuforums.org/showthread.php?t=288534") How-To is a good starting place.

---

### Post by lingenfr on 2008-11-24
Thanks. That is a great howto. I will start working through it this evening. I expect I will also follow your link on disabling IPv6 as that is awfully annoying. Iowan's helping Iowan's is always good. Go Hawks!

---

### Post by Iowan on 2008-11-24
Iowans helping anyone is good.  Be aware that the IPv6 link is several versions old.  I've updated my Samba link, my IPv6 link is next...

---

### Post by lingenfr on 2008-11-24
The howto does not make clear as to the proper method for creating the share. I followed the directions at:

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_share_public_folders_with_read_only_or_read.2Fwrite_permissions_.28Authentication.3DNo.29](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_share_public_folders_with_read_only_or_read.2Fwrite_permissions_.28Authentication.3DNo.29)

Is this still correct or is there an updated method that would be better? I will continue googling.

---

### Post by lingenfr on 2008-12-14
Iowan, thanks. The howto you pointed to works fine. I seem to be able to copy to and delete files from my samba shares. Three issues (including the original) remain:

1) When the shares mount, a shortcut is created on my desktop. That is great. What is not great is that the default shortcut says: Remote Share (//mythtv-backend/music) which wraps to only display Remote Share (//... so it is impossible to tell one from another. If I tried to rename them or use a different icon it fails with permission problems.

2) I am using KDE and when I copy a file, I get a Konqueror Information box that says 'Could not change permissions for <file I'm copying>. I am copying from an ext3 partition to an ext3 partition using shared with samba.

3) I still have a problem similar to my original. When I create a folder, rather than it being own by the user/group in my .smbcredentials file, it is owned by user hplip and group netdev. I have tried using sudo, su hplip, etc, but no joy. I can't even enter the folder. Help!

---

### Post by Iowan on 2008-12-16
Working from command line or GUI?  **sudo** should mount a halo over your head to do pretty much what you want (good, bad, or otherwise).  Can't say I've used the .smbcredentials file... my exposure to Samba is getting dated - my favorite reference book is for Samba 2.X.

---

### Post by lingenfr on 2008-12-21
> **Iowan said:**
> Working from command line or GUI?  **sudo** should mount a halo over your head to do pretty much what you want (good, bad, or otherwise).  Can't say I've used the .smbcredentials file... my exposure to Samba is getting dated - my favorite reference book is for Samba 2.X.

I you are talking about 3) above, either. Same results from command line or gui.

---

