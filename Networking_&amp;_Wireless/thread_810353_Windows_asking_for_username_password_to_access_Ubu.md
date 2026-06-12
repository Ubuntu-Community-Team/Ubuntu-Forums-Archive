---
title: "Windows asking for username password to access Ubuntu shared files"
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by RobHK on 2008-05-28
My laptop Ubuntu setup can see and access my Windows network which includes my desktop PC running XP Home. 

I wanted the XP setup on the desktop PC to access the Ubuntu setup on the laptop. On the laptop (Ubuntu)I set up a shared folder in my /home/[myname] folder and installed the packages that were offered. 

I could then see my Ubuntu laptop and the shared folder in "Windows Network" on the Ubuntu laptop. But if I try to access the Ubuntu laptop from the desktop with XP, I am asked (on the desktop XP)for a username and password. It doesn't accept the Ubuntu username and password or "root" and the Ubuntu root password.

In XP, I see the workgroup and the two computers inside it. The password request comes when I click on the icon for the laptop.

Any ideas anyone? TIA.

---

### Post by Iowan on 2008-05-28
Sometimes I miss what the system does automagically, and what must be done manually... Did you add your username to "the Samba club" with **smbpasswd -a username**?

---

### Post by RobHK on 2008-05-30
> **Iowan said:**
> Sometimes I miss what the system does automagically, and what must be done manually... Did you add your username to "the Samba club" with **smbpasswd -a username**?

No I didn't. I'll try it tonight and report back.

Love "automagically"! Great neologism ;) Typo or intentional?

---

### Post by eldragon on 2008-05-30
in your /etc/samba/smb.conf file you need to allow guest logins

in the global section, find the line
guest account = 

if its commented, uncomment it. and then add your username (or whoever you wish to pose as guest. remember to add this user to samba with smbpasswd. this user must exist in the systems user list.


then on the shared section you wish to allow guest logins (aka, no password)

add 

public = yes


one thing to take into account. the guest user, MUST have read access in the ext3 folder you are sharing if you wish for him to be able to read/write.

so, if samba allows read/write, but the filesystem doesnt, the user wont be able to read/write. that is done with the chmod command.


and remember, any change done to smb.conf, needs a daemon restart. so run sudo /etc/init.d/samba restart after saving that file.

hope im clear enough.

---

### Post by RobHK on 2008-06-03
> **eldragon said:**
> in your /etc/samba/smb.conf file you need to allow guest logins

in the global section, find the line
guest account = 

if its commented, uncomment it. and then add your username (or whoever you wish to pose as guest. remember to add this user to samba with smbpasswd. this user must exist in the systems user list.


then on the shared section you wish to allow guest logins (aka, no password)

add 

public = yes


one thing to take into account. the guest user, MUST have read access in the ext3 folder you are sharing if you wish for him to be able to read/write.

so, if samba allows read/write, but the filesystem doesnt, the user wont be able to read/write. that is done with the chmod command.


and remember, any change done to smb.conf, needs a daemon restart. so run sudo /etc/init.d/samba restart after saving that file.

hope im clear enough.

I really appreciate your help, but I haven't in fact got round to dealing with this. I can't, for that reason, say whether it worked, but I wouldn't want to appear ungrateful by not replying. I will come back here  when I do get round to addressing it. It's not something I really need to do, but if I have a system I like it to work properly :).

I wish Ubuntu and Linux generally well, but it's been hell on earth getting my laptop to function (wireless and display). Pity, because the desktop was just install'n'play.

---

### Post by Iowan on 2008-06-03
> **RobHK said:**
> Love "automagically"! Great neologism ;) Typo or intentional?Intentional.  Sometimes the system must be configured to work automatically.  Sometimes it handles things by itself - by magic.  Sometimes it's hard to tell where the "auto" stops and the "magic" starts.

---

