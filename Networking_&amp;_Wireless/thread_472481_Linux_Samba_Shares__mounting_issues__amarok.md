---
title: "Linux Samba Shares / mounting issues / amarok"
date: 2007-06-13
forum: Networking &amp; Wireless
---

### Post by katiad on 2007-06-13
I have a small network of two linux (k/ubuntu edgy) boxes and one xp box. 

Comp #1 (Kubuntu) - holds two shares:  /data/dublin  and /data/paris that I've set up as free-access, all connections allowed, samba shares (they hold my music and random need-to-be-shared documents. Connecting to them from the XP box is fine, can map the drives, etc. Connecting to them through the "network connections" screen in Comp #2 (ubuntu, no kde), works fine - files and documents are easily accessible, and an icon is easily placed on its desktop.

However... I'd like to simply mount Comp #1's /data/dublin on Comp #2 the same way I've mounted windows shares, by editing /etc/fstab and mounting it into /media/dublin - because evidently, just connecting to a remote share via the graphical link-on-the-desktop route means I cannot make Amarok use that share as its media library.

So what do I need to do? I used kde's samba graphical screen to set up the shares as public, browseable, and available, specified no users, allowed all connections, made it writable, and it works perfectly in XP and through the network servers screen in ubuntu. I'm just unable to mount it on the local filesystem at a specific mount point.

Please help! The following line /does not work/. Ends up with "mount point cannot be resolved" errors. Yes, there is a /media/dublin folder, chmod 777. I did not put in a username/password or credentials because... I'm not sure what I would put there, being as none needs to be supplied to access it (or perhaps I'm wrong?) Everything else is identical to the way I've mounted my windows shares. (Except in that case, I use cifs instead of smbfs due to freeze-at-startup issues.)  What can I do to mount this properly?

//192.168.X.XXX/dublin /media/dublin smbfs auto,gid=users,guest,file_mode=0777,dir_mode=0777 0 0

Sorry for any blatant idiocy. I'm feeling like I've made a small, silly error and I'm being too dense to realize what it is.

---

### Post by katiad on 2007-06-13
Let me also add that:

sudo smbmount //192.168.X.XXX/dublin /media/music mounts the share without a problem - however, this sets all permissions to root only, and Amarok refuses to build a collection from it. 

I am not sure, but may be looking at two separate issues here?

---

### Post by dmizer on 2007-06-13
try this:
```
sudo aptitude install smbfs
```
the line you have in place has cifs options rather thans smbfs options.  you're better off with cifs anyway because you can handle larger file transfers.  try simply changing "smbfs" to "cifs" and it should work.  also, there's no need for the "auto" option as auto is assumed unless specified otherwise.

if you're having problems with your system freezing because of cifs, you should enable wins support.  follow the second link in my sig for how to do that.

if you're dead set on using smbfs, your fstab line should look like this:
```
/192.168.X.XXX/dublin /media/dublin smbfs[COLOR="Red"] gid=user[/COLOR],guest,rw,fmask=777,dmask=777 0 0
```
if even that does not work, post the output of the following:
```
smbtree
```

---

### Post by katiad on 2007-06-13
Thanks. Got it now!

---

### Post by DugieHowsa on 2007-06-25
Hey folks.  I am still having trouble with my cifs/smbfs mounts  Using smbfs, nautilus and other applications freeze up.  Using cifs, users only have read access, even though rw is defined in the fstab.  I do not experience any freeze ups though.

Here are t he relevant lines in my fstab.  I only use 1 at a time to test various configurations:

#  Mounting NAS FileShare01
# //Fileserver01/Netshare /media/Fileserver01 /media/Fileserver01 smbfs guest,rw,file_mode=0777,dir_mode=0777 0 0
# //192.168.2.10/Netshare /media/Fileserver01 cifs username=anonymous,password=letmein,rw,file_mode=0777,dir_mode=0777 0 0
# //Fileserver01/Netshare /media/Fileserver01 cifs auto,user,rw,gid=smbusers 0 0
# //Fileserver01/NetShare /media/Fileserver01 cifs guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

There are no permisisions on this server.  When I mount via smbfs, I get the permissions I want.

Here are the results of smbtree:

25OAKTERRACE
         \\FILESERVER01                  FileServer01
                \\FILESERVER01\ADMIN$           IPC Service ("FileServer01")
                \\FILESERVER01\IPC$             IPC Service ("FileServer01")
                \\FILESERVER01\NetShare       
                \\FILESERVER01\config         

Any help would be greatly appreciated.

---

