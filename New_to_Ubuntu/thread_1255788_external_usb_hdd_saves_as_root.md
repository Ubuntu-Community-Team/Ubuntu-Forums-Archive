---
title: "external usb hdd saves as root"
date: 2009-09-01
forum: New to Ubuntu
---

### Post by cat2005 on 2009-09-01
I know this must have been covered somewhere because I could not be the first to have this problem.

If you know of other threads, resources, etc, then please point me there.

_Here it is:_

I have a secondary external usb hard drive in ext 3 format.  If I put something on it, it saves as "root".  That is to say, "root" is the owner and group.  

The only way I can change this is to switch accounts and sudo (gksudo nautilus); I only let one of my accounts have sudo power.  However, when I sudo and change the folder permissions, the permissions do not change for the folders and objects inside.  This is true even if I select the "apply permissions to objects inside" option - or whatever that option is called.

Any suggestions?  I can't use FAT because I except some large files (several GB).  NTFS throws a fuss.  That leaves me with ext3.

The sole purpose of this hard drive is storage.  It is not hosting an OS.

Thank you.

EDIT:  *I should clarify.  It saves things as "root" if I am doing something when everything is unmounted.  For example, I was running Clonezilla from my dvd drive.  The resulting Clonezilla images were saved as "root".  If I the computer is on and I am logged in as a user, then the data is saved under that user.  In both cases, I can not get permission changes to go into sub-folders (childs, or whatever they are called).*

---

### Post by SpinningAround on 2009-09-03
I guess it's chrown you are looking for 
[https://help.ubuntu.com/community/FilePermissions#Changing%20the%20File%20Owner%20and%20Group](https://help.ubuntu.com/community/FilePermissions#Changing%20the%20File%20Owner%20and%20Group)

[http://linux.about.com/od/commands/l/blcmdl1_chown.htm](http://linux.about.com/od/commands/l/blcmdl1_chown.htm)

Make sure to backup your files before you start editing :)

---

### Post by binbash on 2009-09-03
it is not chrown, it is chown.

You can get permissions of the files & folders by adding -R :

for example sudo chown asdasd /home/adadadasd/ -R

---

