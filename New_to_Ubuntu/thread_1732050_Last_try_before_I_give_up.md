---
title: "Last try before I give up"
date: 2011-04-17
forum: New to Ubuntu
---

### Post by indusarts on 2011-04-17
I have spent weeks trying to get a simple Linux NAS setup on my home system.  I decided to use Ubuntu w/GUI (after trying Xubuntu; I did not want to use the command line as my main inferface) on an old computer as a NAS drive.  I was then planning on letting it backup/sync files to my raid server (actually unRaid) and installing FTP or VPN and Apache for remote access of files.

Samba took a while to get straight,  I can now access the drive/computer from my WinXP Pro desktop machine.  I can also see the unRaid shares from the Ubuntu machine, as well as any other Win machines shares that are available.  I have mapped the NAS folder on the Ubuntu machine as a drive on my WinXP machine.

The problem I am stuck at now is with mounting remote folders for the backup programs I am evaluating to backup/sync to the unRaid server.  I have tried to follow an uncountable number of tutorials as well as advice from this forum on how to mount a remote folder.  So far, none have been successful.

I can see the remote folder in Nautilus.  I have mounted it via Nautilus.  It is available and bookmarked in Gigolo.  (Plus, I have just discovered any time I open a remote folder with Nautilus, it gets mounted to the desktop as well as being bookmarked in Gigolo  - wt*???)  And I can  access them in the .gvfs file, but I was told that is not a good method to access network folders (by someone in the forum)

The unRaid server is called Tower, it's IP address is 192.117.17.202, there is no username or password.  The main folder for backup is called 100g.  My Ubuntu machine is call xbntusrvr. I have created a folder for the mount point in /media called 100g

Here is my fstab file:
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=c6518c3c-90c7-4cfe-a919-9422afdc95fd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c5f65c31-5f1f-419d-9e80-4e6cde06f224 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Here are the attempts I have made to edit the fstab folder to mount the folder: (I commented out each unsuccessful attempt)
#//192.117.17.202/100g /media/100g smbfs credentials=/etc/samba/user,rw,uid=<myusername> 0 0
#sudo mount //192.117.17.202/100g /media/100g smbfs username=<myusername>,password=<mysmbpassword> 0       0
#//Tower/100g /media/100g smbfs credentials=/etc/samba/user,rw,uid=mspringer 0 0
#//Tower/100g /media/100g smbfs username=<myusername>,password=<mysmbpassword> 0       0
#//192.117.17.202/100g /media/100g smbfs username=<myusername>,password=<mysmbpassword> 0       0
#mount.cifs //Tower/100g /media/100g -o user=mspringer,pass=mspringer
#//19.117.17.202/100g /media/100g cifs credentials=/etc/samba/user,rw,uid=mspringer,gid=users,iocharset=utf8 0 0
#//Tower/100g /media/100g smbfs credentials=/etc/samba/user,rw,uid=1000 0 0
#//192.117.17.202/100g /media/100g smbfs credentials username=<myusername>,password=<mysmbpassword> 0       0
#//192.117.17.202/100g /media/100g smbfs credentials=/etc/samba/user,rw,uid=<myusername> 0 0

And each time tried $ sudo mount /media/100g - none worked I received the errors 
mount: can't find /mnt/100g in /etc/fstab or /etc/mtab
error -1 (Unknown error 4294967295) opening credential file /etc/samba/user


I did create a file called /etc/samba/user after I understood what the credential file error was looking for. I guess I don't understand in the least the idea of mounting a remote folder, though I have read dozens of tutorials telling me how.  I'm not sure why this seems so complicated, the entire job of external drive, networking, backup and remote access took me only a few hours in Windows.  I wanted to use Linux because I thought it would be more secure and I would have more control over remote access and backup/sync, as well as learning something about Linux.  So far this is not the case - except for the learning part and that hasn't been great.


At this point I am extemely frustrated, if I don't figure this out soon I think I will just purchase one of the DLink NAS boxes.  They don't have great reviews, but I don't have great demands.  If anyone is available to help/ walk me thru, I would appreciate it.

Thanks 
Mark Springer
industrial arts

---

### Post by mörgæs on 2011-04-18
I guess that this forum will help you better:
[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

---

### Post by HermanAB on 2011-04-18
Howdy,

First of all, you should not use smbfs.  It is deprecated. Use CIFS.

Secondly, it looks like you are tripped up by outdated guides.. There are good guides on the Samba web site.

---

