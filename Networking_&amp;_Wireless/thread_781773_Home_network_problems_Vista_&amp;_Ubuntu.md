---
title: "Home network problems Vista &amp; Ubuntu"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by PintoZ on 2008-05-04
Hi guys, I've started using ubuntu few days ago, I did it because I need to start using linux for work, I really like it, i have the 8.04  version.

Right now I'm having a problem with files sharing, my laptop has ubuntu, while my pc has vista, the problem is:

Ubuntu can see vista, but doesn't see any shared folder, while there are many.

Vista can't see ubuntu, I can anyway connect directly to ubuntu typing the IP address, but then it asks to login, and I put my ubuntu's user name and password, and it gets error.

I tried to share a folder in ubuntu, but it gives that error:
'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.

Well, I'm not that good with linux, and I don't know what to do, if anyone could help me I'd be really thankful =)

EDIT: using this guide: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605) now i can share folders with ubuntu, and vista can use them, I still don't see any vista folder from ubuntu

---

### Post by PintoZ on 2008-05-07
No one does have any idea to help me?

---

### Post by subzero316 on 2008-05-07
```
sudo mkdir /usr/local/samba/lib/usershares
sudo chgrp yourusername /usr/local/samba/lib/usershares
sudo chmod 1770 /usr/local/samba/lib/usershares
```
Then add these parametersusershare 

```
sudo gedit smb.conf
```
Add these lines

path = /usr/local/samba/lib/usershares
usershare max shares = 10 # (or the desired number of shares)

---

### Post by PintoZ on 2008-05-07
Thanks for the reply!

```
mkdir: cannot create directory `/usr/local/samba/lib/usershares': No such file or directory
```
Di you maybe mean /var/lib/samba/usershares ??

---

### Post by kixome on 2008-05-07
I am new to ubuntu and had the same problem. After searching forever to no avail i decided to try a few things.

first i went to System>Administration>users and groups
 I unlocked it and clicked manage groups> I then made sure i was on the list for sambashare.

Next I:

sudo cp /etc/samba/smb.conf /etc/samba/smb.bak
sudo gedit /etc/samba/smb.conf 
 
and edited it to enable wins and changed the workgroup to (your workgroup)

BE FOREWARNED: I am new so i don't know if something could happen later by enabling these permissions, so I recommend creating your shares and putting the permissions back via "sudo chmod -rwx (directories listed below)"
Next:

sudo chmod +rwx /var
sudo chmod +rwx /var/lib
sudo chmod +rwx /var/lib/samba/
sudo chmod +rwx /var/lib/samba/usershares

The chmod's were the commands that allowed me to create the shares using the sharing tab. After you enable the shares and restart they, for some reason will not show that they are enabled under their own sharing tabs but if you go to network servers, they will be accessible. I also installed firestarter and i reccommend using a firewall if you know how to use one. It took a few tries but my shares and my vnc and pretty much everything else works fine.

---

### Post by subzero316 on 2008-05-07
> **PintoZ said:**
> Thanks for the reply!

```
mkdir: cannot create directory `/usr/local/samba/lib/usershares': No such file or directory
```
Di you maybe mean /var/lib/samba/usershares ??


Yea the one u say...
__________________________

Btw u dont have 2 say thanks jus click the medal on right thatz 'thank u' .:)

---

### Post by PintoZ on 2008-05-07
Thank you, I checked if I was on the samba group, I was there, I'm also in the same workgroup of my second PC with Vista.

The problem is:
Vista can see and use shared folders on ubuntu.
Ubuntu can see vista's PC but can't see any shared folder there.
I tried now with another pc with XP and i can see Xp's shared folders :S
Wtf, I'm getting confused, I should try if with another windows pc I can see VIsta's folders

---

### Post by subzero316 on 2008-05-07
> **PintoZ said:**
> Thank you, I checked if I was on the samba group, I was there, I'm also in the same workgroup of my second PC with Vista.

The problem is:
Vista can see and use shared folders on ubuntu.
Ubuntu can see vista's PC but can't see any shared folder there.
I tried now with another pc with XP and i can see Xp's shared folders :S
Wtf, I'm getting confused, I should try if with another windows pc I can see VIsta's folders


ubuntu cant access your vista share folder eh....

First there is an option to allow users that can access n read in vista chk that out. may be itz on for that xp user.

also see

[http://ubuntuforums.org/showthread.php?t=394412]("http://ubuntuforums.org/showthread.php?t=394412")

---

### Post by PintoZ on 2008-05-09
I tried to follow that topic, but I still have the problem, ubuntu can see vista's PC, but can't see or access shared folders :S while another vista pc can see them.

---

