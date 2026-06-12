---
title: "User rights"
date: 2010-08-08
forum: New to Ubuntu
---

### Post by EgoGratis on 2010-08-08
I don't understand something. First user on Ubuntu is so called super-user (has option Administer the system permission checked). But if i look at default settings for this users. This is what i don't understand:

[IMG]http://www.techotopia.com/images/0/03/Ubuntu_linux_user_privileges2.jpg[/IMG]

For default (super) user options like Configure printers, Connect to internet using a modem, Connect to wireless and ethernet networks, Use audio devices, Use CD-ROM drives. This all is default (off) unchecked.

So how come i can listen to the music, print files, connect to internet and use CD-ROM device. And without password or nothing else? Can somebody explain this to me? Articles on the internet are all the same. Like all was written by the same person. And that person doesn't quite know what he or she is writing or talkin abaut.

---

### Post by ikt on 2010-08-08
> **EgoGratis said:**
> First user on Ubuntu is so called super-user

Is it?

I thought all users are required to type in their password when they do things that require elevated privileges.

---

### Post by mike555 on 2010-08-08
if you are the only user those boxes should be checked, if you are not the original first user they shouldn't be checked (by default).

---

### Post by da burger on 2010-08-08
> **ikt said:**
> Is it?

I thought all users are required to type in their password when they do things that require elevated privileges.

I don't know the answer to the OPs question but I can help a bit here. The "first" user (as the in the one numbered 0) is called root and can do anything without a password. The user created when you install ubuntu is able to temporarily pretend to be root after entering a password.

---

### Post by QLee on 2010-08-08
[QUOTE=EgoGratis]
...
For default (super) user options like Configure printers, Connect to internet using a modem, Connect to wireless and ethernet networks, Use audio devices, Use CD-ROM drives. This all is default (off) unchecked.

So how come i can listen to the music, print files, connect to internet and use CD-ROM device. And without password or nothing else? Can somebody explain this to me? Articles on the internet are all the same. Like all was written by the same person. And that person doesn't quite know what he or she is writing or talkin abaut.[/QUOTE]

The picture you showed was of the default options for creating a new user, to see your options you have to look at the properties of your username.

By the way, the first user created is not the SU, just an admin user that can use sudo to do required tasks with the permissions of SU.

---

### Post by uRock on 2010-08-08
Accounts without the Administer system checked will not be able to use sudo to get anything done.

---

### Post by EgoGratis on 2010-08-08
This are the default User Privileges i get in 10.04 for first user. I didn't make it clear in first post that the picture is just for better understanding of what i would like to know. I didn't make screenshot of my system because is not in english language. And no where on Google i can find picture of default settings in 10.04 for first user. So i manually edited the first one in the post. All privileges with green square are the default settings for first user in 10.04.

[IMG]http://i34.tinypic.com/2yy1frc.jpg[/IMG]

So why am i able to listen to the music use wired and wireless network, mount file system... If this GUI tool says i don't have "User Privileges" to do that?

---

### Post by marshmallow1304 on 2010-08-08
The User Privileges you see there correspond to groups.  For example, if the 'Administer the system' box is checked, the user is added to the 'admin' group, which is, by default, the only non-root group that can use sudo.  The thing that is confusing you is that many of those groups are not necessary in Ubuntu.  I suspect that adding a user to them would allow that user to access the system on a lower level than is necessary to use the system normally, like accessing a network on the command line instead of using network manager.

---

### Post by cannonballsimp on 2010-08-08
Hi

I´m also having trouble with user privileges in Lucid Lynx. I am the only user, but I still can´t write to the /usr folder. Would making me a member of the ´root´ user group remove the prohibition, do you think?


thanks

---

### Post by marshmallow1304 on 2010-08-08
> **cannonballsimp said:**
> 
I´m also having trouble with user privileges in Lucid Lynx. I am the only user, but I still can´t write to the /usr folder. Would making me a member of the ´root´ user group remove the prohibition, do you think?

/usr is owned by root.  Use [sudo]("https://wiki.ubuntu.com/RootSudo") to gain write access.

---

### Post by uRock on 2010-08-08
> **cannonballsimp said:**
> Hi

I´m also having trouble with user privileges in Lucid Lynx. I am the only user, but I still can´t write to the /usr folder. Would making me a member of the ´root´ user group remove the prohibition, do you think?


thanks
To add to the advice that Marshmallow1304 has given, this inablilty to alter the root directories is what helps protect against malware being easily written in Linux.

---

### Post by astrognome on 2010-08-08
Like what marshmallow1304 has said, the permissions listed only correspond to the group that is your username, i.e. your default group.  The user that is created upon install of Ubuntu has many groups associated with it.  For a listing go to Applications -> Accessories -> Terminal and type:

$ groups

Unix file system permissions are organized into three classes: "user", "group", and "others". The use of groups allows additional abilities to be delegated in an organized manner. The use of groups allows user access to disks, printers, as well as other other peripherals. Groups also allows the superuser to delegate some administrative tasks to normal users.

It is not strictly correct that accounts without "administer system" checked will not be able to use sudo.  Any user can be added to the sudoers list by the sysadmin.

Hope this helps.

---

### Post by EgoGratis on 2010-08-11
> Like what  marshmallow1304 has said, the permissions listed only correspond to the  group that is your username, i.e. your default group.

I see. So **User Privileges** from GUI "front end" are set for the "users defoult group".

And automatically new user in Ubuntu is associated to some other groups to. And for those groups. Command:

$ groups

Lists groups user is associated to. What about groups. How to see an understand what can some user in some group do?

---

### Post by Piccy on 2010-11-02
I understand EgoGratis. I am trying to get my head around the created groups in Ubuntu.

Is there a way to find the permissions for a group say "adm" ie what does this group grant me and what am I missing from not being in another group say "bin"

doing a groups command gives me this (login name andrew)
andrew adm dialout cdrom floppy audio dip video plugdev fuse lpadmin admin netdev

---

