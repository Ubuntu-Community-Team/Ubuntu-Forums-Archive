---
title: "Help using Samba to connect to shares..."
date: 2005-11-12
forum: Networking &amp; Wireless
---

### Post by bencrouse on 2005-11-12
Hello, I've got some experience in linux, but I'm new to ubuntu and liking it very much so far. 
But I can't seem to get some shares mounted that I want to be able to read and write as a normal user.  I try this:

```
sudo smbmount //myfiles/home /media/myfiles/home -o credentials=/home/ben/.smbpasswd 
```

and the share mounts fine, but user "ben" doesn't have permissions to change.

so i try this as "ben":

```
smbmount //myfiles/home /media/myfiles/home -o credentials=/home/ben/.smbpasswd 
```

and it tells me that 

```
smbmnt must be installed suid root for direct user mounts (1000,1000)
```

so, now i try to change the /usr/bin/smbmnt as root like so (i got this idea from a google search):

```

chmod u+s smbmnt
chmod u+s smbmount
chmod u+s smbumount

```

and now finally i get this:

```
libsmb based programs must *NOT* be setuid root.
10028: Connection to myfiles failed
SMB connection failed

```

so im frustrated and now need some help.  i would rather not mount it in my fstab at boot because our network here (at college) sucks, and it takes a solid 10 seconds to mount.  and since i dont need it all the time, theres no point in making my boot time agonizingly long.
so id appreciate any help.
thanks!
peace
ben

---

### Post by mxyzptlk on 2005-11-12
all right here we go

first of all you need to know two simple things in ubuntu:

one

users:  you can add them from System>Administration>Users and groups.
from there you only have to make sure thet the name of the user you are adding, is the same name of the COMPUTER you want to set permissions and same PASSWORD.

two

you dont have to do all that command sequence you post here.
just need couple things

smbpasswd -a "user_name_just_added" ENTER

right after that it will ask you a password (important: check the terminal you are using TERMINAL or ROOT TERMINAL).

make sure the password matches with the added user
and then confirm password.


MOST IMPORTANTS THINGS HERE ARE: FIRST

ADD USER AND PASSWORD IN YOUR UBUNTU SYSTEM

THEN ADD SAME USERS TO SAMBA WITH smbpasswd -a

hope it helps

---

### Post by mxyzptlk on 2005-11-12
by the way

if you want to share something, just right click on the directory of the share you want and the system by default is going to share it in /home/your_personal_folder

in samba ubuntu you have by default that only the specific user you add has permissions to browse the shares you want but not the others users

if you want to change the permissions for a special directory or so you have to do it with chmod or chown commands.

i forgot something important check your /etc/samba/smb.conf and make changes as needed according to your necesities.

hope it helps

---

