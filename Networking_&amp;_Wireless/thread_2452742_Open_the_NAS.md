---
title: "Open the NAS"
date: 2020-10-27
forum: Networking &amp; Wireless
---

### Post by Phil Binner on 2020-10-27
I just did a clean install of XUbuntu 20.04.  All was well and the problems I was starting to get with the old system cleared up nicely.  One new problem arose though.  When I browse the network I can see my NAS, but It won't open.  It just says Failed to open "D-Link-NAS-5".  I don't have any special security on it.  When I first connect on a couple of old computers I have it brings up a password window but I just click connect and it connects anyway.  This computer was connecting fine this morning before the rebuild.  Any suggeations would be welcome.

---

### Post by TheFu on 2020-10-27
NFS or CIFS connection?
Have you tried manually mounting it from the terminal? When you do that, what are the errors shown?

---

### Post by Phil Binner on 2020-10-27
I have not done anything specific to set up a network connection, so I do not know how it is trying to connect.  What I have done is install XUbuntu and open Thunar. The bottom entry on Thunar (left pane) is Browse Network.  When I click that it shows 2 entries on the right hand side. The first is D-Link-NAS-5 and the other is Windows Network.  If I double click Windows Network it opens that, but it is empty.  That is probably because I haven't set up file sharing on the windows machine.  I could probably do that but I don't particularly want to.  What i want is the 2 desktop machines and the 2 laptops to all have access to the NAS.

When I double click D-Link-NAS-5 I get the message 'Failed to open "D-Link-NAS-5"', and below that 'Failed to retrieve share list from server: Software caused connection abort.'

On the Windows system the path to the NAS is \\D-LINK-NAS . I have tried to connect to it using Gigolo in as many configurations as I can think of, i.e FTP, SSH, and WebDAV.  Usually the name cannot be resolved.  I'm afraid my terminal skills are lamentable.  I have gone onto Ubuntu help to look for the correct commands, but what I got was software ad's aimed at a much higher level of network administration.  

I think it's important that I had access to the NAS this morning, and the XUbuntu computer that runs my TV has access, so the problem seems to have been caused by the new installation.

I would be very grateful for help, particularly in what terminal commands to use to resolve this.

---

### Post by Phil Binner on 2020-10-27
I tried various versions of the following command - sudo -t ftp mount D-Link-NAS-5 .  

ie. I tried it with D-LINK-NAS and \\D-LINK-NAS
I always got hhe reply "can't find in /etc/fstab."

I know this is just lack of knowledge. Please help.

---

### Post by TheFu on 2020-10-27
[https://ubuntuforums.org/showthread.php?t=2156134&p=12701873#post12701873](https://ubuntuforums.org/showthread.php?t=2156134&p=12701873#post12701873)  ?

That's my best guess.  Install the package it says. That might be enough. There have been changes to defaults for samba. I've read in these forums that only the cifs mounts work reliably now. That link has an example. These forums are full of threads for similar issues that you can try.

---

### Post by Morbius1 on 2020-10-28
> 'Failed to retrieve share list from server: Software caused connection abort.'
Your NAS can only speak the smb1 dialect of samba. The version of samba in 20.04 disables it.

You can re-enable it if you want.

Edit /etc/samba/smb.conf and right under the **workgroup = WORKGROUP** line add this one:
```
client min protocol = NT1
```
Then reboot your Xubuntu box.

Notes:

*** If you have no smb.conf file and you have no intention of sharing anything on your Xubuntu box to others install the samba client:
```
sudo apt install smbclient
```
Then you will have a smb.conf file to edit.

*** If the version of samba on your NAS is really really old you may need to add another option in Xubuntu under the first one you added:
```
client lanman auth = yes
```

---

### Post by Phil Binner on 2020-10-28
I'm struggling
First I installed cifs-utils
Then I added a user to the NAS. Previously I had always logged on as guest.
Then I edited /etc/fstab by adding the line 
# to mount the NAS
//92.168.1.73/D-Link-NAS /D-Link-NAS-5/volume_1 cifs auto,users,credentials=/etc/cred,uid=1000,gid=1000,file_mode=0660,dir_mode=0 770 0 0
I created a file called /etc/cred
Then I changed the last line to 
//D-Link-NAS-5/volume_1 /media/windowsshare  cifs  guest,uid=1000,iocharset=utf8  0  0

None of this worked.  The message is always as shown earlier

I think I am missing something at the conceptual level

---

### Post by Phil Binner on 2020-10-28
Sorry Morbius 1, I had missed your post.  Thanks.  I'll get to that now.

---

### Post by slickymaster on 2020-10-28
*Thread moved to **Networking & Wireless**.*

---

### Post by Morbius1 on 2020-10-28
>  //92.168.1.73/D-Link-NAS /D-Link-NAS-5/volume_1 cifs  auto,users,credentials=/etc/cred,uid=1000,gid=1000,file_mode=0660,dir_mode=0  770 0 0

If you are doing a cifs mount you have the same problem but the rules change because CIFS is Linux kernel based and does not look at smb.conf. THe equivalent to the changes in smb.conf in a cifs mount is to add two more options to your list:

**vers=1.0** and maybe **sec=ntlm**

So your cifs mount becomes:
```
 //92.168.1.73/D-Link-NAS /D-Link-NAS-5/volume_1 cifs  auto,users,credentials=/etc/cred,uid=1000,gid=1000,file_mode=0660,dir_mode=0770,vers=1.0,sec=ntlm 0 0
```

OR:
```
 //D-Link-NAS-5/volume_1 /media/windowsshare  cifs  guest,uid=1000,iocharset=utf8,vers=1.0,sec=ntlm  0  0
```

---

### Post by Phil Binner on 2020-10-28
I've been struggling with this the whole day but I'd never refreshed the thread.  This is all sorted now.  The way I have this set up the machines only communicate through the NAS, so there is no problem cutting off other communication.  I'm interested though.  Does Samba prevent linux machines talking to each other.

---

### Post by Phil Binner on 2020-10-28
Thanks. OK now.

---

### Post by Phil Binner on 2020-10-28
Thanks for the help.  How do I mark this as solved.

---

### Post by TheFu on 2020-10-28
> **Phil Binner said:**
> I've been struggling with this the whole day but I'd never refreshed the thread.  This is all sorted now.  The way I have this set up the machines only communicate through the NAS, so there is no problem cutting off other communication.  I'm interested though.  Does Samba prevent linux machines talking to each other.

No.  Samba is just 1 protocol of thousands.  I don't use samba between Unix systems. There are many easier, more secure, and simple to use protocols available.  I almost always use:
[LIST]
[*]ssh/scp/sftp/rsync
or
[*]nfs
[/LIST]

For example, in most Linux file managers, we can enter sftp:// URLs to convect securely from any client to any server.  Only ssh needs to be installed on both sides.  If ssh-keys are setup, then this is secure enough for use over the internet.
ssh is how Unix systems securely connect.

---

### Post by him610 on 2021-01-21
@moribus1 Thanks, your advice on #6 worked for me.

I had gone through this drill last spring when 20.04 was released; however, after recently rebuilding one of my systems, I could not find my notes.

Have a good day.

---

