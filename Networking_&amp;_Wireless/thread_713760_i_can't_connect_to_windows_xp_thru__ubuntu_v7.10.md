---
title: "i can't connect to windows xp thru  ubuntu v7.10"
date: 2008-03-03
forum: Networking &amp; Wireless
---

### Post by aeon19 on 2008-03-03
Good day mate i have a problem i tried to share a folder from Ubuntu and i want it to access  from windows xp  once i click the icon network on windows it prompt user name and password i try to enter the user and password of Ubuntu but i cannot access it..can you help me out guys thanks in advance:confused:


br,

---

### Post by PreviousN on 2008-03-03
hmm..

do you have samba? If you know for sure, then good. If you don't, then search for it in the forums/community docs to read about it. 

Here's how to troubleshoot your problem if you already have it and know what it is:

sudo -i
gedit /etc/samba/smb.conf

Scroll to the bottom and then find your share name. Make sure theres' a "users = yourusername

Then, save the file and go back to the terminal. 
Type 

"smbpass -a yourusername"

Then, enter a password. Finally, "/etc/init.d/samba restart"

and then...

sudo -k

and close your terminal. I think your problem is that there isn't any usersadded to samba. Samba doesn't necessarily link with the system users, and you can have a different samba password than the one to log into your computer. 

Cheers.

---

### Post by aeon19 on 2008-03-03
> **PreviousN said:**
> hmm..

do you have samba? If you know for sure, then good. If you don't, then search for it in the forums/community docs to read about it. 

Here's how to troubleshoot your problem if you already have it and know what it is:

sudo -i
gedit /etc/samba/smb.conf

Scroll to the bottom and then find your share name. Make sure theres' a "users = yourusername

Then, save the file and go back to the terminal. 
Type 

"smbpass -a yourusername"

Then, enter a password. Finally, "/etc/init.d/samba restart"

and then...

sudo -k

and close your terminal. I think your problem is that there isn't any usersadded to samba. Samba doesn't necessarily link with the system users, and you can have a different samba password than the one to log into your computer. 

Cheers.

thanks mate ill  try this and post the result

br,

---

### Post by jc1cell on 2008-03-05
> **PreviousN said:**
> 


... I think your problem is that there isn't any usersadded to samba. Samba doesn't necessarily link with the system users, and you can have a different samba password than the one to log into your computer. 

Cheers.

Sorry to jump in here...I'm having the exact same problem.  My machines ping each other back and forth  (Xp running Virtual Ubuntu Server and Virtual Ubuntu Desktop).  I can access XP shared folder from Udesktop but can't access shared Udesktop from xp...password issue. Can't access my server from xp....password issue.

I do have samba on both ubuntu installs (and nfs on udesktop for connectivity to userver but that's another story) and created two different usernames and passwords thinking that the first one didn't apply properly.  But it simply doesn't accept either the password or the username.

I will go ahead and follow any instructions you give to the originator of the thread without going into too many details of my situation so as to no hijack this thread and then have everybody get confused..I have a different thread going about this and anything i get over there I will post a link here so you guys can check it...

jc

ps...  I couldn't find the users=yourusername in the smb.conf. I will try creating another username and see if it applies it.

Tried adding using your command and noticed it didn't work, so i found this : smbpasswd -a and ran it....It accepted the command but no matter what username I put it returned "Failed to modify password entry for USERNAME".

---

### Post by Iowan on 2008-03-05
> **PreviousN said:**
> 
"smbpass -a yourusername"
**smbpasswd -a yourusername** ??

> **jc1cell said:**
> It accepted the command but no matter what username I put it returned "Failed to modify password entry for USERNAME".
Maybe **sudo smbpasswd -a yourusername**

---

### Post by WildeBeest on 2008-03-05
I had the same problem.

As long as you're samba is set up correctly. From the windows side when it asks you for the user name and password, enter only the name(same one as in samba)  leave the password blank.

It worked for me.

---

### Post by jonandrews on 2008-03-06
I've put a step bu  step guide to networking between XP & Ubuntu on a website:

[www.europe.eclipse.co.uk/Ubuntu](www.europe.eclipse.co.uk/Ubuntu)

See if that helps.

---

