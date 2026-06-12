---
title: "Need help with auto mounting windows shares"
date: 2009-08-15
forum: New to Ubuntu
---

### Post by Kedster on 2009-08-15
I am following these [instructions]("https://help.ubuntu.com/community/MountWindowsSharesPermanently") but I do not really understand a lot of it. like the share's don't have passwords and I don't have usernames when I mount them manually and what should the mount point be, I'm sorry I'm really confused

---

### Post by oldfred on 2009-08-15
Your instructions are for mounting a windows share on another computer. Do you want that or to mount a local share in a dual boot machine?
This has instructions for both:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

You have to make a directory to mount to and then mount it. If you want permanent mount, you edit fstab. The mount of a windows partition gives the permissions.

For local mounting, if that is what you want:
the example the above site gives is:
# NTFS ~ Use ntfs-3g for write access (rw) 
# /dev/hda1
UUID=12102C02102CEB83  /media/windows  ntfs-3g  auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=1  37   0  0

one of mine is:
# before uuid  /dev/sda1 /media/cdrive ntfs-3g defaults,locale=en_US.UTF-8 0 0
UUID=04B05B70B05B6768 /media/cdrive ntfs-3g defaults,locale=en_US.UTF-8 0 0

Of course you have to use your UUIDs.

---

### Post by Kedster on 2009-08-15
Ok well see I have my laptop and then i have another computer down stairs with tones of media on it and I have lots of it shared. I can access it from my laptop but I would like to have it mounted on start up 

when I go to places and then "network" and open that then there is "windows network" and then there's our home network called "HOME" and then I think the next part is where each computer is and the one downstairs is named "FAMILY-VDVQ3QR6" and then once your in that folder then there are all of the shared folders and if I go into the one with music names music the full path is 
smb://family/music%20(j)/

how would i go about making that auto mount.

---

### Post by RedRat on 2009-08-15
May I suggest that you download and install smb4k from the respositories. It will be installed under Applications>Accessories. Run the program and have it look for your Windows computers on the network. Click on them and then merely click on the particular folder you want mounted and it will appear on your Desktop. Sorry it doesn't do this on startup since you must start smb4k after logging in. 

The nice thing about smb4k is that when it places the mounted network drives on the Desktop, they are now available to all programs, including programs run under Wine. If you mount windows folders from Nautilus' Network Places, some programs do not "see" those network folders.

---

### Post by Kedster on 2009-08-15
i remeber when i was playing with conky a few months ago there was a way to write a script to start conky 15 sec after log in. i think the way it worked was the script would just be executed wait 15 secs and then start conky. so then u could put that script in start up applications.  would that same method or another method work

---

### Post by Kedster on 2009-08-16
i started using smb4k and then as i was doing things i got this error message 

```
Application: Smb4K (smb4k), signal SIGSEGV

Thread 1 (Thread 0xb5fb3700 (LWP 4101)):
[KCrash Handler]
#5  0xb69a8f60 in QString::operator= () from /usr/lib/libQtCore.so.4
#6  0x080573ec in _start ()

```

---

### Post by pedro3005 on 2009-08-16
You could try the following:
[http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html](http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html)
or
[http://kim.biyn.com/Linux/how_to_mount_samba_windows_shares_at_boot_time_via_fstab](http://kim.biyn.com/Linux/how_to_mount_samba_windows_shares_at_boot_time_via_fstab)
or
[http://nerdnotes.wordpress.com/2007/03/02/windows-shares-in-etcfstab/](http://nerdnotes.wordpress.com/2007/03/02/windows-shares-in-etcfstab/)

They seem to suit your needs :)

---

### Post by Kedster on 2009-08-16
Ok so m usint the first set of instrucions from pedro and i just have a quick question, should the mount point be somethingthat is already created like would desktop work or is that the place u specify like Desktop/shared and then that would be the share

---

### Post by Kedster on 2009-08-16
And would my server name be "home" or "family"

---

### Post by pedro3005 on 2009-08-17
You should use for mount point something like /media/share , but be sure that directory already exists, or it will fail. I would not recommend mounting it to your desktop, though that would be possible. The server name it refers to is the name of the PC sharing. You can check that by going to Places > Network.

---

### Post by Kedster on 2009-08-17
is the "WORKGROUP" the same as the servername
and is the sharename have to have the computer name in it 
 and what is the "-0" 
does letter casing matter in any of this


right now my "WORKGROUP" is "HOME" and the computer name that im trying to connect to is "family"

here is the path that is nautilus when i mount from there
> smb://family/shared/

so this is the command iv been trying to run
```
ketterer@ketterer-laptop:~$ smbmount //home/family/shared /media/shared -o
```

and also tried
```
ketterer@ketterer-laptop:~$ smbmount //family/shared /media/shared -o 
```

any ideas why it isnt working

---

### Post by Kedster on 2009-08-17
i also just tried to add the user name and password part (there is none so i put defaults)

```
ketterer@ketterer-laptop:~$ smbmount //family/shared /media/shared -o username=defaults,password=defaults
mount error: could not resolve address for family: No address associated with hostname
No ip address specified and hostname not found
```

---

### Post by pedro3005 on 2009-08-18
Maybe try using the ip address? Like '//192.168.0.2/shared' . I don't know if it will work, but worth the try. Oh and i think on the password section you just replace the whole thing with defaults and not login=defaults etc.

---

### Post by Kedster on 2009-08-18
So using the ip address worked but could these commands ever mess up the the serving computer down stairs. like could the main server admin become my laptop by doing these commands

it seems when I mount using this method it takes the permissions and i think made me the admin because the main computer now can not see itslef in network places and can not see other windows computers on the network. also now ont he 2 linux laptops we can not see the main computer any more BUT if you know the path you can still access it.

---

### Post by Kedster on 2009-08-18
This is the bottom of my /etc/fstab 
```
//IPADDRESS/shared /media/Shared smbfs defaults 0 0
//IPADDRESS/music /media/Music smbfs defaults 0 0
//IPADDRESS/jordans /media/Backup smbfs defaults 0 0
//IPADDRESS/movies /media/Movies smbfs defaults 0 0
```

i took out the ip address just for safety

---

### Post by pedro3005 on 2009-08-18
First of all, no, it won't screw up your windows pc. Secondly, lol, the IP ADDRESS you took out wasn't really smart because that is the internal ip address, not the external one. About the computers not being visible on nautilus, you could try running nautilus as root, as i've read that it could help. ALT F2 then 'gksu nautilus'. If that doesn't work or if you have a problem with running nautilus as root, search google for 'browse windows share on ubuntu' as it comes up quite a lot.

---

### Post by zerhacke on 2009-08-18
Make sure you have the smbfs package installed.  You do NOT NEED SAMBA installed.

Ubuntu handles cifs and smbfs servers by ip address and not network name.  It doesn't matter what your server is named.

You will need to make sure that the directory you are mounting to exists.  If you don't have a /media/Shared folder it will not make it for you.

---

### Post by Kedster on 2009-08-18
But even the main server computer(running windows) cant see itself or any other windows computers that are there

---

### Post by Kedster on 2009-08-18
i am able to mount them now but now things on the main computer (running windows) are really weird

---

### Post by spadhawk on 2009-08-19
im on this network with kedster and when he mounts the shared network drives from the windows main machine on his laptop you can no longer browse the main windows machine from any other computer unless you already have the drive mounted or know the path to type in to map a drive. none of the windows machines are visible on the workgroup. though all mapped drives still work fine on the other machines. when you try to browse to map a drive it says that you dont have permissions. why does mounting the drives on his laptop change the permissions on the workgroup?

---

### Post by Kedster on 2009-08-19
If one of us also recently installed the packages used to share other stuff out off of the laptops could that do what is on

---

### Post by Kedster on 2009-08-23
does any one have any ideas

---

### Post by simonmcnair on 2009-08-30
this helped me ...

enable wins resolution
[http://ubuntuforums.org/showthread.php?t=88206](http://ubuntuforums.org/showthread.php?t=88206)

shouldn't be using smbfs, use cifs
[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

---

