---
title: "home sharing not working"
date: 2010-12-20
forum: New to Ubuntu
---

### Post by degarb on 2010-12-20
I have two linux machines on a router network (windows samba).   The desktop (park group) cannot load file list of the (gerber group) laptop.  And the laptop must enter some password browse desktop shares, which I have no idea how to hack into and guess this password, which I never setup.

---

### Post by cariboo on 2010-12-20
The two systems should be in the same workgroup. When asked for a user name and password, it usually is the username and password for the computer you're connecting to.

I'd suggest if both systems are running a Linux variant, you use NFS, it is much easier to setup and maintain. For an NFS how to have a look [here]("https://help.ubuntu.com/community/SettingUpNFSHowTo").

---

### Post by degarb on 2010-12-20
> **cariboo907 said:**
> The two systems should be in the same workgroup. When asked for a user name and password, it usually is the username and password for the computer you're connecting to.

I'd suggest if both systems are running a Linux variant, you use NFS, it is much easier to setup and maintain. For an NFS how to have a look [here]("https://help.ubuntu.com/community/SettingUpNFSHowTo").


I listen all night to book mp3s from xp.   

I did [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605) 

I got the workgroup changed by editing the config.   I added a user.  However. Neither computer can mount the other's shares.

---

### Post by jazzerit on 2010-12-20
if they're both linux, then I tend to use sftp- but my individual computers don't have external IP addresses assigned, so people outside of my LAN can't connect.

---

### Post by t0p on 2010-12-20
If you haven't set up a username and password yourself, they will probably be the default username and password.  Something stupid like username: "admin" and password: "admin" is often the case.

Fire up google and do a search for default password and the make/model of your router.  There are sites that have lists of default username/password combos for various routers and other devices.  But remember: you should use this mighty power for good only, *never* for evil!  ;)

If you got the router second-hand and the previous owner changed the username/password, there should be a "reset" button on the router, probably in a little hole in the back of the router, you'll need to use a pen or something to press it.  When you reset the router, all configurations will revert to defaults, including the username/password.  Then you can use my first suggestion.

---

### Post by degarb on 2010-12-20
> **jazzerit said:**
> if they're both linux, then I tend to use sftp- but my individual computers don't have external IP addresses assigned, so people outside of my LAN can't connect.


I cannot use linux if it cannot network with windows xp.    

I won't be able to listen to books upstairs, access documents, listen to prerecorded streams , my music, books or watch movies.   

All I am getting is unable to mount

On 9 trying to browse 10 I see folders, but on opening folders I get, Unble to mount: I get failed to retrieve share list from server. 

On 10 browsing garbers I am getting this error message.   No files.


Can't I just wipe out samba and start over.  One package if designed with user in mind should fix this.  I also tried installing smbfs.

---

### Post by presence1960 on 2010-12-20
> **cariboo907 said:**
> The two systems should be in the same workgroup. When asked for a user name and password, it usually is the username and password for the computer you're connecting to.

I'd suggest if both systems are running a Linux variant, you use NFS, it is much easier to setup and maintain. For an NFS how to have a look [here]("https://help.ubuntu.com/community/SettingUpNFSHowTo").

Very kool avatar cariboo!

---

