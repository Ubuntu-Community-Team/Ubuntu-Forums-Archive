---
title: "Save to network drive"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by cbanakis on 2009-05-18
ok, in the last few weeks I've figured out tons of Ubuntu.

I know its a pretty dumb question, but how do I save files to a network drive??

I have full read and write access to the drive, but in every applications "Save As" option, the network drive is not listed as an option.

Does anyone know how to make a network drive visible in the "Places" Column in the save as dialog???

---

### Post by AndyCee on 2009-05-18
You know I never noticed that. How interesting.

I can think of a few ways to work around it, but if I try to save this web page, and type into the filename:

network:///

then press tab, I'm told "only local files may be selected". Is this a limitation of nautilus, firefox, or am i doing it wrong?

---

### Post by cbanakis on 2009-05-19
Right?

I spent so many hours figuring all this crazy stuff out so I can ditch windows and make the switch, and now I'm caught on this stupid insignificant snag

---

### Post by GMachine_24 on 2009-05-19
I think what you want to do is mount the network drive on your computer ... you can do this using Samba....

Click this link for a basic "how to"

[http://www.automaticable.com/2008-01-18/how-to-mount-a-network-drive-in-ubuntu/](http://www.automaticable.com/2008-01-18/how-to-mount-a-network-drive-in-ubuntu/)

The Ubuntu "how to" is here:

[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

---

### Post by cbanakis on 2009-05-19
> **GMachine_24 said:**
> I think what you want to do is mount the network drive on your computer ... you can do this using Samba....

Click this link for a basic "how to"

[http://www.automaticable.com/2008-01-18/how-to-mount-a-network-drive-in-ubuntu/](http://www.automaticable.com/2008-01-18/how-to-mount-a-network-drive-in-ubuntu/)

The Ubuntu "how to" is here:

[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)
I'm not sure...

I think it is mounted already, but the "Save As" dialog in applications does not see it.

If I click on places in the gnome panel on top of my screen, the network drive is listed there.

It is also on my desktop, and if I right click on the desktop icon, it lists "un-mount" as an option, leading me to believe it is mounted already

---

### Post by HermanAB on 2009-05-19
Howdy,

In general, Linux (or Windows!) applications are not 'network aware'.  The exception being programs that deal exclusively with networks: File browsers, web browsers, FTP clients and the like.

In order to save a file to a networked device from a common application such as a word processor, you have to use a 'network file system' to 'mount' the distant share and graft it onto the local file system.  In a Windows XP system, a network share is 'mapped' to a local 'drive letter'.  In a Windows Server system, a distant share can be grafted anywhere in the local file system.  Linux is similar to a Windows server and grafts distant shares anywhere - there are no 'drive letters'.

In Linux, there are two ways to mount distant shares: Temporarily (ad hoc) or permanently (mounted at boot).  You can do a temporary mount using Nautilus:
CLick File, Connect to Server.
Select the service type, add your user name and click OK.

The share will be temporarily mounted in /media and you office applications can then access it there.  I use this feature on my laptop computer.

The other way, is to add mount commands to /etc/fstab.  Permanent mounts are more suitable for use with stationary desktop machines and servers.

---

### Post by cbanakis on 2009-05-19
> **HermanAB said:**
> Howdy,

In general, Linux (or Windows!) applications are not 'network aware'.  The exception being programs that deal exclusively with networks: File browsers, web browsers, FTP clients and the like.

In order to save a file to a networked device from a common application such as a word processor, you have to use a 'network file system' to 'mount' the distant share and graft it onto the local file system.  In a Windows XP system, a network share is 'mapped' to a local 'drive letter'.  In a Windows Server system, a distant share can be grafted anywhere in the local file system.  Linux is similar to a Windows server and grafts distant shares anywhere - there are no 'drive letters'.

In Linux, there are two ways to mount distant shares: Temporarily (ad hoc) or permanently (mounted at boot).  You can do a temporary mount using Nautilus:
CLick File, Connect to Server.
Select the service type, add your user name and click OK.

The share will be temporarily mounted in /media and you office applications can then access it there.  I use this feature on my laptop computer.

The other way, is to add mount commands to /etc/fstab.  Permanent mounts are more suitable for use with stationary desktop machines and servers.
ok, It sounds like HermanAB knows what I need.
I have a 26TB Windows Vista file server, and I'm trying to get my ubuntu desktop to be able to save directly to the server.

I assume the permanent mount is the way for me, but it sounds a bit out of my league.

Can you or someone else try to walk me through it?

Also, when you say the share will be mounted in "/media"

your saying the path to the network drive will be {File System/Media} ???

Right now if I go to that directory it lists "cdrom" "cdrom0" and "cdrom1"

And it looks like 1 of them is my DVD drive, and the other 2 are my local hard drive

Is that right?

And I assume whenever I figure this out, my network drive will be "cdrom3" then?


Thanks

---

### Post by cbanakis on 2009-05-19
OK, I figured out how to do it the "Temporary Way" As described by HermanAB...
All it did was add the same drive a second time.
And still no way to save to that drive.

I'm not sure if the permanent way will be any different.

---

### Post by HermanAB on 2009-05-19
Well, once you mounted it, how exactly do you go about trying to save to it?

You can open a Nautilus file browser and go to /media and look for it, or you can doublke click the icon on the desktop (which does the same thing), then you can click drag ddrop files, or you can open a word processer, click File, Save As, and go to /media/whatever and save something.

If it is difficult then you are doing something wrong.

---

### Post by cbanakis on 2009-05-19
> **HermanAB said:**
> Well, once you mounted it, how exactly do you go about trying to save to it?

You can open a Nautilus file browser and go to /media and look for it, or you can doublke click the icon on the desktop (which does the same thing), then you can click drag ddrop files, or you can open a word processer, click File, Save As, and go to /media/whatever and save something.

If it is difficult then you are doing something wrong.
it is not listed in /media

No matter how I mount it, I can read and right to it in "explorer" for lack of a better word... but the "save as" dialog in applications does not list the network drive, and it is not visible in /media.

I must be doing something wrong as you said, but I cant imagine what it could be.

---

### Post by GMachine_24 on 2009-05-19
Hi:

Why don't you post the contents of your etc/fstab file here.

Since your network drive is being mounted when your computer boots, it should be listed in the fstab file - and if you want it to mount to /media then you can change the line in fstab that mounts your network drive so that it mounts to /media instead of wherever it is mounting now (perhaps /mnt).

==gm

---

### Post by cbanakis on 2009-05-19
It doesnt look like its listed in fstab.

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=0dc634de-1f15-4134-a5e9-7c44d230f814 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1d4d39eb-657a-4d58-9b26-9ff3a6dae882 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by cbanakis on 2009-05-19
ok, anyone with a network drive, in your web browser, click on (file) (save page as)

And unless I'm a moron, you wont be able to save to your network drive.

I'm probably a moron anyways, but there has to be someone out there who can save to a network drive

---

### Post by uidb4056 on 2009-05-19
> **cbanakis said:**
> ok, anyone with a network drive, in your web browser, click on (file) (save page as)

And unless I'm a moron, you wont be able to save to your network drive.

I'm probably a moron anyways, but there has to be someone out there who can save to a network drive

I'm running 9.04 and I've found that when I mount a network drive from nautilus it appears as a folder under /home/username/.gvfs please note that in order you can found it on Nautilus you need to show hidden files (you can do it pressing ctrl-H in Nautilus).

The best way however is to create a folder in your /home/username and use it as a mount point at boot in your /etc/fstab.

---

### Post by cbanakis on 2009-05-19
> **uidb4056 said:**
> I'm running 9.04 and I've found that when I mount a network drive from nautilus it appears as a folder under /home/username/.gvfs please note that in order you can found it on Nautilus you need to show hidden files (you can do it pressing ctrl-H in Nautilus).

The best way however is to create a folder in your /home/username and use it as a mount point at boot in your /etc/fstab.
WOW!!!
And so its that easy.

I dont understand how to "The best way however is to create a folder in your /home/username and use it as a mount point at boot in your /etc/fstab."

but sure enough, I can save to my network drive now.

Thank you very very much uidb4056
If your ever in Chicago, I'd like to buy you a beer.

I just saved this web-page to my file server :)

I guess all I needed was the path, and how to show the hidden files.

You said its better to use a folder and create a mount point?

You have already done so much, but can you walk me through that process?

Thank you again very much.

---

### Post by uidb4056 on 2009-05-19
> **cbanakis said:**
> WOW!!!
And so its that easy.

I dont understand how to "The best way however is to create a folder in your /home/username and use it as a mount point at boot in your /etc/fstab."

but sure enough, I can save to my network drive now.

Thank you very very much uidb4056
If your ever in Chicago, I'd like to buy you a beer.

I just saved this web-page to my file server :)

I guess all I needed was the path, and how to show the hidden files.

You said its better to use a folder and create a mount point?

You have already done so much, but can you walk me through that process?

Thank you again very much.

You have to edit /etc/fstab as root

```
sudo gedit /etc/fstab
```and add this line:

```
//computername/sharename /home/username/foldertomountname smbfs credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

You need also create if not exists or edit the file .smbcredentials

```
sudo gedit /root/.smbcredentials
```and add two lines as:

username=yourusername
password=yourpassword

Save it and then test you can mount using from terminal

```
sudo mount -a 
```If it works then you will have mounted every time you boot. For sure there can be another ways but this is running for me.

---

### Post by cbanakis on 2009-05-20
ok, so I skipped this step...

--------------------------------------------------------------------------------

 	Code:
 	sudo gedit /root/.smbcredentials 
and add two lines as:

username=yourusername
password=yourpassword

--------------------------------------------------------------------------------

I skipped it because my share is setup to not require a user name or password, If thats a problem, please let me know.

But it does not appear to be working.

this is what I get from - sudo mount -a

--------------------------------------------------------------------------------

chris@The-Machine:~$ sudo mount -a
[sudo] password for chris: 
mount: wrong fs type, bad option, bad superblock on //File-Server/******-Terabytes,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

--------------------------------------------------------------------------------

And here is a copy of my fstab

--------------------------------------------------------------------------------

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=0dc634de-1f15-4134-a5e9-7c44d230f814 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1d4d39eb-657a-4d58-9b26-9ff3a6dae882 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
//File-Server/******-Terabytes /home/chris/******-Terabytes smbfs credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

--------------------------------------------------------------------------------

Did I do something wrong?

The name of the computer with the network drive is "File-Server" And the name of the drive is "******-Terabytes"

I appologize for the language if it offends anyone, but if you had a 26TB RAID array in your house, what would you call it?

Thanks as always

Ubuntu has better peer support than you can buy from Microsoft...

You all rock and so does Ubuntu, at least now that I kinda know how to use it.

---

### Post by uidb4056 on 2009-05-20
[quote=cbanakis]Did I do something wrong?

The name of the computer with the network drive is "File-Server" And the name of the drive is "******-Terabytes"

I appologize for the language if it offends anyone, but if you had a 26TB RAID array in your house, what would you call it?

Thanks as always

Ubuntu has better peer support than you can buy from Microsoft...

You all rock and so does Ubuntu, at least now that I kinda know how to use it.[/quote]

I'm not sure but have you installed smbfs?

If not install it from synaptic or run in terminal:

sudo apt-get install smbfs

Also if you don't need username to the share you can replace:

credentials=/root/.smbcredentials

by

user

---

### Post by cbanakis on 2009-05-21
Thank you very much, Looks like I got it all working now.

the only thing left in my setup that still has issues is my ATI 3870 HD.

and from what I read, the only solution is for me to play the waiting game

I wish I would have started with linux back in the day instead of windows, If I did I would know everything by now.  :)

---

### Post by OriTheEep on 2009-05-22
I have lots of problems to fix with my Ubuntu 9.04 setup.

So I was very relieved to find somebody else who couldn't preload his Windows shares.

I agree with "I wish I would have started with linux back in the day instead of [W]indows, If I did I would know everything by now." but, at the time when I started playing with PCs, Windows 3.0 was similarly the great white hope of those fed up with the proprietory nature of the computer industry. A lesson of some sort?

Getting the problems solved is the priority. I'd like to be able to understand what's going on but that might have to wait for more experience and more time to browse these threads.

So, problem:

I've entered the following lines in fstab for the four shares being connected to

//av/xchange /safe/xchange smbfs user,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//AV/applications /safe/applications smbfs user,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//AV/setup progs /safe/setup_progs smbfs user,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//AV/documents /safe/documents smbfs user,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

and installed smbfs as suggested.

on "sudo mount -a" I get

tom@server:~$ sudo mount -a
[sudo] password for tom: 
[mntent]: line 21 in /etc/fstab is bad
mount error: could not resolve address for av: No address associated with hostname
No ip address specified and hostname not found
mount error: could not resolve address for AV: No address associated with hostname
No ip address specified and hostname not found
mount error: could not resolve address for AV: No address associated with hostname
No ip address specified and hostname not found
tom@server:~$ 

I changed "AV" to "av" in one instance suspecting case sensitivity. Note that the error message only appears three times.

I assume that there is another definition file that needs to be fed with information?

Thanks :)

---

### Post by uidb4056 on 2009-05-22
> **OriTheEep said:**
> //av/xchange /safe/xchange smbfs user,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//AV/applications /safe/applications smbfs user,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//AV/setup progs /safe/setup_progs smbfs user,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//AV/documents /safe/documents smbfs user,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

and installed smbfs as suggested.

on "sudo mount -a" I get

tom@server:~$ sudo mount -a
[sudo] password for tom: 
[mntent]: line 21 in /etc/fstab is bad
mount error: could not resolve address for av: No address associated with hostname
No ip address specified and hostname not found
mount error: could not resolve address for AV: No address associated with hostname
No ip address specified and hostname not found
mount error: could not resolve address for AV: No address associated with hostname
No ip address specified and hostname not found
tom@server:~$ 

I changed "AV" to "av" in one instance suspecting case sensitivity. Note that the error message only appears three times.

I assume that there is another definition file that needs to be fed with information?

It seems that you don't have name resolution to your windows machine, you can test from terminal:

ping av

to see if there are answer, if not you have to check tha you get answer to ping if you use the IP address instead of machine name. If you get answer using IP addrees you can replace 'av' in /etc/fstab with the IP address and it should work.

In addition I assume that the folders you want to use as a mount points are already created?

---

### Post by OriTheEep on 2009-05-22
> **uidb4056 said:**
> It seems that you don't have name resolution to your windows machine, you can test from terminal:

ping av

to see if there are answer, if not you have to check tha you get answer to ping if you use the IP address instead of machine name. If you get answer using IP addrees you can replace 'av' in /etc/fstab with the IP address and it should work.

In addition I assume that the folders you want to use as a mount points are already created?

Hello uidb4056,

Thanks for the quick reply.

You are quite correct in your first suspicion. Now you say it I do recall that there isn't a DNS server on the network. If that a simple thing to set up (i.e. a simple thing to help me with :) ) then it might be an idea to set that up on this machine. Although I am quite happy to configure this small network by hand, I would prefer not to have to remember every place where the information needs to be modified should something change.

The shares on the Windows machine do exist, are in use by other machines on the network and indeed this one when accessed via Nautilus.

 In fstab, I replaced the computer name in the first line only with the IP address:[INDENT]//192.168.1.3/xchange /safe/xchange smbfs user,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
[/INDENT]but when I tried "sudo mount -a", I read[INDENT]tom@server:~$ sudo mount -a
[sudo] password for tom: 
[COLOR=Red][mntent]: line 21 in /etc/fstab is bad
Password: 
mount error(112): Host is down
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)[/COLOR]
mount error: could not resolve address for AV: No address associated with hostname
No ip address specified and hostname not found
mount error: could not resolve address for AV: No address associated with hostname
No ip address specified and hostname not found
[/INDENT]I was a little puzzled by the second password prompt. Still only three error messages. I tried this twice in case AV had been asleep on the first attempt.

Despite the "Host is Down" message, an immediately subsequent PING gave:[INDENT]tom@server:~$ ping 192.168.1.3
PING 192.168.1.3 (192.168.1.3) 56(84) bytes of data.
64 bytes from 192.168.1.3: icmp_seq=1 ttl=128 time=0.476 ms
64 bytes from 192.168.1.3: icmp_seq=2 ttl=128 time=0.448 ms
64 bytes from 192.168.1.3: icmp_seq=3 ttl=128 time=0.471 ms
64 bytes from 192.168.1.3: icmp_seq=4 ttl=128 time=0.464 ms
64 bytes from 192.168.1.3: icmp_seq=5 ttl=128 time=0.442 ms
64 bytes from 192.168.1.3: icmp_seq=6 ttl=128 time=0.474 ms
^C
--- 192.168.1.3 ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 4998ms
rtt min/avg/max/mdev = 0.442/0.462/0.476/0.025 ms
[/INDENT]man mount.cifs didn't seem to be relevant but I'm afraid I did get lost amongst all the unfamiliar abbreviations.

:confused:

---

### Post by uidb4056 on 2009-05-23
> The shares on the Windows machine do exist, are in use by other machines on the network and indeed this one when accessed via Nautilus.

 In fstab, I replaced the computer name in the first line only with the IP address:[INDENT]//192.168.1.3/xchange /safe/xchange smbfs user,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
[/INDENT]but when I tried "sudo mount -a", I read[INDENT]tom@server:~$ sudo mount -a
[sudo] password for tom: 
[COLOR=Red][mntent]: line 21 in /etc/fstab is bad
Password: 
mount error(112): Host is down
Refer to the mount.cifs(:cool: manual page (e.g.man mount.cifs)[/COLOR]
mount error: could not resolve address for AV: No address associated with hostname
No ip address specified and hostname not found
mount error: could not resolve address for AV: No address associated with hostname
No ip address specified and hostname not found

First, can you post your complete fstab

Second, instead to use /safe/xchange as a mount point I suggest you create a mount point inside your home dir (this way you can avoid permissions trouble) by ex.:

tom@server:~$mkdir test

then your mount point should look as:

/home/tom/test

Third, the password prompt you get seems to come from permissions on windows share, you can fix it doing:

tom@server:~$echo username=*mywindowsusername* > .smbpasswd
tom@server:~$echo password=*mywindowspassword* >> .smbpasswd[COLOR=#ff0000][FONT=monospace]
[/FONT][/COLOR]tom@server:~$[COLOR=#ff0000][COLOR=Black]chmod 600 .smbpasswd

you have to replace italics by your username and password on windows machine

then you can use in your fstab

[/COLOR][/COLOR]```
//192.168.1.3/xchange /home/tom/test smbfs [COLOR=Black]credentials=/home/*tom*/.smbpasswd,uid=*tom*,gid=*users*[/COLOR],iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```
[/INDENT]

---

### Post by OriTheEep on 2009-05-23
> **uidb4056 said:**
> First, can you post your complete fstab


Of course:[INDENT]# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=9b4440e8-40f2-429a-a61f-bcaf806c6731 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=7517d5c2-9adb-4a47-9469-49fa7e38bdc9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


#Existing Windows shares

//192.168.1.3/xchange /safe/xchange smbfs user,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//192.168.1.3/applications /safe/applications smbfs user,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//192.168.1.3/setup progs /safe/setup_progs smbfs user,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//192.168.1.3/documents /safe/documents smbfs user,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0


# Server shares

# /dev/mapper/pdc_heiedeai    /safe/xchange    ext3    defaults    0    0
# /dev/mapper/pdc_heiedeai    /safe/applications    ext3    defaults    0    0
# /dev/mapper/pdc_heiedeai    /safe/setup_progs    ext3    defaults    0    0
# /dev/mapper/pdc_heiedeai    /safe/documents    ext3    defaults    0    0
[/INDENT]The four principal network shares currently on AV will be moved to this machine where a RAID 1 array is awaiting set up. I am, like many other Win->Linux migrants, stalled by deciding on whether to use one or many partitions. GParted is asking questions I don't understand and I am troubled by the fact that it can see not just the array but the component drives which I would have thought should be hidden by the RAID controller. Worry about all that later, I suppose.


> **uidb4056 said:**
> Second, instead to use /safe/xchange as a mount point I suggest you create a mount point inside your home dir (this way you can avoid permissions trouble)



Well, yes, OK as a test but as a final solution is does lack a certain elegance. If doing that does show that there is a problem with permissions that will also have to be overcome (sigh).

> **uidb4056 said:**
>  Third, the password prompt you get seems to come from permissions on windows share.


The Windows machines use share level access control; AV is actually running Win98SE. There is supposed to be a mechanism that password-protects write privilege but it doesn't work so I don't try to use it. Would I still need to use the .smbpasswd file? There are currently no passwords to put in it!

I'll try moving the mount points now and await your ideas on passwords. Unless you want to hear how moving the mount points went first?

---

### Post by OriTheEep on 2009-05-23
Having moved the mount points and re-edited the relevant lines in fstab to:[INDENT]#Existing Windows shares with mount poionts moved

//192.168.1.3/xchange /home/tom/test/xchange smbfs user,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//192.168.1.3/applications /home/tom/test/applications smbfs user,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//192.168.1.3/setup progs /home/tom/test/setup_progs smbfs user,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//192.168.1.3/documents /home/tom/test/documents smbfs user,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
[/INDENT]The error messages are:[INDENT]tom@server:~$ sudo mount -a
[mntent]: line 29 in /etc/fstab is bad
Password: 
mount error(2): No such file or directory
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
Password: 
mount error(112): Host is down
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
Password: 
mount error(112): Host is down
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
tom@server:~$ 
[/INDENT]Unfortunately, apart from the first, it isn't possible to definitively associate the error messages with even just the line causing them. The mount points were empty so none of the lines actually worked.

I think I understand " line 29 in /etc/fstab is bad" now if it refers to the share "SETUP PROGS". Windows shares can have spaces in the names. I presume from its appearance before the execution errors that the file is parsed as a whole first.

Nautilus allows access without asking for a password so is this perhaps a "feature" of Mount? It wouldn't be so bad if Nautilus mounts appeared in file dialogue boxes.

Is the change from "No such file or directory" to "Host is down" caused in some way by the lack of response when Mount tries to pass a password with the connection request?

Is it possible to put a null password in .smbpasswd, should that file be required? What will Win98SE do with such a password anyway. I think I'll go and have a lie down for a bit.

I'll restore the mount points to what they were.

---

### Post by uidb4056 on 2009-05-24
> **OriTheEep said:**
> Having moved the mount points and re-edited the relevant lines in fstab to:[INDENT]#Existing Windows shares with mount poionts moved

//192.168.1.3/xchange /home/tom/test/xchange smbfs user,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//192.168.1.3/applications /home/tom/test/applications smbfs user,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//192.168.1.3/setup progs /home/tom/test/setup_progs smbfs user,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//192.168.1.3/documents /home/tom/test/documents smbfs user,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
[/INDENT]The error messages are:[INDENT]tom@server:~$ sudo mount -a
[mntent]: line 29 in /etc/fstab is bad
Password: 
mount error(2): No such file or directory
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
Password: 
mount error(112): Host is down
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
Password: 
mount error(112): Host is down
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
tom@server:~$ 
[/INDENT]Unfortunately, apart from the first, it isn't possible to definitively associate the error messages with even just the line causing them. The mount points were empty so none of the lines actually worked.

I think I understand " line 29 in /etc/fstab is bad" now if it refers to the share "SETUP PROGS". Windows shares can have spaces in the names. I presume from its appearance before the execution errors that the file is parsed as a whole first.

Nautilus allows access without asking for a password so is this perhaps a "feature" of Mount? It wouldn't be so bad if Nautilus mounts appeared in file dialogue boxes.

Is the change from "No such file or directory" to "Host is down" caused in some way by the lack of response when Mount tries to pass a password with the connection request?

Is it possible to put a null password in .smbpasswd, should that file be required? What will Win98SE do with such a password anyway. I think I'll go and have a lie down for a bit.

I'll restore the mount points to what they were.

Well, first we go to fix the problem of space in your share name, you can avoid it writing:

//192.168.1.3/setup\040progs /home/tom/test/setup_progs smbfs user,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

Second I've read on google that there are problems to mount Win98 shares but I'm not able to found a suggested solution for this, any way the options I'we offered you will run with XP or W2K I can suggest some checks and changes:[INDENT]Do you have smbclient installed?, you can try running it from terminal ans if shows 'command not found' you can install it using 'sudo apt-get install smbclient'

You can try to replace in fstab smbfs by cifs and placing the line as:
```

//192.168.1.3/xchange /home/tom/test/xchange        cifs    guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

[/INDENT]Third, if nothing of this working you have the possibility to access your shares after being manually mounted on Nautilus, when a share is mounted manually on Nautilus there is a hidden folder in your /home/tom named .gvfs (at least in 9.04 I'm running), in order to unhide it in Nautilus to let you browse it you can press ctrl-H key the you can see what is showed up in this folder. Then you can access your shares from Nautilus and from terminal using:

/home/tom/.gvfs/xchange

I know this is not elegant solution but can be a workaround until you move your data to your new RAID 1

---

### Post by OriTheEep on 2009-05-24
> **uidb4056 said:**
> Well, first we go to fix the problem of space in your share name, you can avoid it writing:

//192.168.1.3/setup\040progs /home/tom/test/setup_progs smbfs user,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0



I'd already tried the intuitive alternative of putting quotes around the share name. Not intuitive to the writers of Linux, it would seem. Thanks for telling me how I should do it!

> **uidb4056 said:**
> Second I've read on google that there are problems to mount Win98 shares but I'm not able to found a suggested solution for this,


Delicious! Just my luck.

> **uidb4056 said:**
>  any way the options I'we offered you will run with XP or W2K


The Win98SE machines will all be upgraded in spec and Ubuntued in the course of however long it takes me to get round to them, leaving just one machine running XP, but each will still need to be able to run Windows applications. Presumably there are emulators about but will I need a valid Windows licence to use them? If these licences are only for Win98, do I have more problems ahead?

> **uidb4056 said:**
>  I can suggest some checks and changes:[INDENT]Do you have smbclient installed?, you can try running it from terminal ans if shows 'command not found' you can install it using 'sudo apt-get install smbclient'

You can try to replace in fstab smbfs by cifs and placing the line as:
```

//192.168.1.3/xchange /home/tom/test/xchange        cifs    guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```[/INDENT]

Didn't work, I'm afraid. Does this exhaust the options?

> **uidb4056 said:**
> Third, if nothing of this working you have the possibility to access your shares after being manually mounted on Nautilus, when a share is mounted manually on Nautilus there is a hidden folder in your /home/tom named .gvfs (at least in 9.04 I'm running), in order to unhide it in Nautilus to let you browse it you can press ctrl-H key the you can see what is showed up in this folder. Then you can access your shares from Nautilus and from terminal using:

/home/tom/.gvfs/xchange

I know this is not elegant solution but can be a workaround until you move your data to your new RAID 1


Far from elegant but am I right in thinking that I can cause the /safe/ folders intended as mount points to point to these folders making this mess invisible to the user?

Will Nautilus run macros of any kind? If so I could ensure that these /home/tom/.gvfs/ folders are mounted at boot time. Currently I hibernate the PC rather than switch it off but even so the network mounts are not always readily available. Nautilus occasionally pops up an error dialogue when I try to look at them, even if it is sometimes showing the contents underneath. :-s

Apropos the RAID array: I still remained unconvinced about using several partitions. I note that the Ubuntu installer only made two partitions, one for swapping purposes, of the system disc. I'm inclined to stick to using just the one partition but if you or anyone else feels strongly to the contrary, I will listen most carefully to the arguments. :)

---

### Post by uidb4056 on 2009-05-24
> Didn't work, I'm afraid. Does this exhaust the options?

Not yet, googling a little bit I've found that someone with similar problems had fixed it writing the sharenames in upper case even if the sharenames in Win98 were in lower case. Nothing to loose testing it.

---

### Post by OriTheEep on 2009-05-24
> **uidb4056 said:**
> Not yet, googling a little bit I've found that someone with similar problems had fixed it writing the sharenames in upper case even if the sharenames in Win98 were in lower case. Nothing to loose testing it.

Yes, that is good thinking. Share names are always shown in upper case in Win98.

(five minutes later)

Errr... no. it didn't work :'(

Looking at the address bar in Nautilus inspired me to try the following line in fstab[INDENT]smb://192.168.1.3/XCHANGE /safe/xchange smbfs    guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
[/INDENT]which gave[INDENT]tom@server:~$ sudo mount -a
Warning: mapping 'guest' to 'guest,sec=none'

Mounting cifs URL not implemented yet. Attempt to mount smb://192.168.1.3/XCHANGE
No ip address specified and hostname not found
tom@server:~$ 
[/INDENT]At least I've verified that the IP address/share exists, at least as far as Nautilus is concerned. Why does Mount (or does the complaint come from Samba?) still think that it hasn't been given an IP address?

Then there is the dreaded "not implemented yet"!

---

### Post by uidb4056 on 2009-05-25
> **OriTheEep said:**
> Yes, that is good thinking. Share names are always shown in upper case in Win98.

(five minutes later)

Errr... no. it didn't work :'(

Looking at the address bar in Nautilus inspired me to try the following line in fstab[INDENT]smb://192.168.1.3/XCHANGE /safe/xchange smbfs    guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
[/INDENT]which gave[INDENT]tom@server:~$ sudo mount -a
Warning: mapping 'guest' to 'guest,sec=none'

Mounting cifs URL not implemented yet. Attempt to mount smb://192.168.1.3/XCHANGE
No ip address specified and hostname not found
tom@server:~$ 
[/INDENT]At least I've verified that the IP address/share exists, at least as far as Nautilus is concerned. Why does Mount (or does the complaint come from Samba?) still think that it hasn't been given an IP address?

Then there is the dreaded "not implemented yet"!

Well I think I've exhausted all what can imagine, the real problem is W98, at least you can mount shares in nautilus and if needed you can browse to them through /home/tom/.gvfs. Is not too much but at least you can read,copy,move and delete files.

---

### Post by OriTheEep on 2009-05-25
> **uidb4056 said:**
> Well I think I've exhausted all what can imagine, the real problem is W98, at least you can mount shares in nautilus and if needed you can browse to them through /home/tom/.gvfs. Is not too much but at least you can read,copy,move and delete files.

Agreed, I am considerably better off now thanks to your help :) !

So thanks for bearing with me. It is a shame that Ubuntu doesn't support Win98 shares but hopefully that won't be a problem to me for long.

---

### Post by Pudibund on 2009-06-01
I had a similar problem, which eventually I managed to solve by adding

[FONT=Courier New]servern=FILESERVER[/FONT] into the options. WIN98 doesn't support a default server name and so needs to have it specified explicitly (according to[FONT=Courier New] 'man samba.cifs'[/FONT])

So your fstab line might be

[FONT=Courier New][SIZE=1]
smb://192.168.1.3/XCHANGE /safe/xchange smbfs    servern=AV,guest,rw,iocharset=utf8,file_mode=0777,dir_mode=07  77 0 0[/SIZE][/FONT]

Whilst it worked for me, I don't know for sure if this will solve your problem, but it might lead in the right direction.

---

### Post by cbanakis on 2009-06-20
WOW!, 
Who would have thought a noob like me would have started such a popular thread

---

### Post by daveinlaguna on 2009-07-08
Here's an easy way to open and save files to your network drives from Firefox.

1. Mount the drives that you want to access. (If you want to mount them permanently, see the Ubuntu documentation for that)

2. Using your file  browser, go to your home folder. Under "view" select "show hidden files."

3. Scroll down to the folder .gvfs, and right click on it. Select "make link."

4. Drag and drop the folder "link to .gvfs" to your desktop.

5. When saving a file to a network drive in Firefox, navigate to the .gvfs link folder on your desktop.

The .gvfs link folder will show your network drives. The Firefox "open" and "save as" boxes can see this folder and access the drives through it. You only have to put this link on your desktop once. It will stay there when you reboot.

---

### Post by sDaddy on 2009-10-24
I have been looking for some method of getting many of the programs I'm using to even See the networked drive..  Been trying to edit tags for MP3's, which are on a MyBook wayyyy over there...   and could not figure it out, along with trying other programs for other things..  I was getting ready to quit Ubuntu just for that reason..   If I couldn't manipulate my files the way I wanted to...  why use it?  

Lucky for me, seeing that the networked drive should be in /home/username/.gvfs  saved the day...   

Now, I have no problems saving files, or even finding the drive it's self over the network! Another Noob saved!

Thanks!!!

---

### Post by kmchirki on 2010-07-23
> **Pudibund said:**
> I had a similar problem, which eventually I managed to solve by adding

[FONT=Courier New]servern=FILESERVER[/FONT] into the options. WIN98 doesn't support a default server name and so needs to have it specified explicitly (according to[FONT=Courier New] 'man samba.cifs'[/FONT])

So your fstab line might be

[FONT=Courier New][SIZE=1]
smb://192.168.1.3/XCHANGE /safe/xchange smbfs    servern=AV,guest,rw,iocharset=utf8,file_mode=0777,dir_mode=07  77 0 0[/SIZE][/FONT]

Whilst it worked for me, I don't know for sure if this will solve your problem, but it might lead in the right direction.

Try to use this line in your /etc/fstab file instead of the previous one, it worked perfectly for me:
[FONT=Courier New][SIZE=1]
//192.168.1.3/XCHANGE  /safe/xchange smbfs  guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0[/SIZE][/FONT]

have a nice day :D

---

### Post by zralok on 2010-09-23
> **daveinlaguna said:**
> Here's an easy way to open and save files to your network drives from Firefox.
 
1. Mount the drives that you want to access. (If you want to mount them permanently, see the Ubuntu documentation for that)
 
2. Using your file browser, go to your home folder. Under "view" select "show hidden files."
 
3. Scroll down to the folder .gvfs, and right click on it. Select "make link."
 
4. Drag and drop the folder "link to .gvfs" to your desktop.
 
5. When saving a file to a network drive in Firefox, navigate to the .gvfs link folder on your desktop.
 
The .gvfs link folder will show your network drives. The Firefox "open" and "save as" boxes can see this folder and access the drives through it. You only have to put this link on your desktop once. It will stay there when you reboot.
Thank you "daveinlaguna"
This works perfectly for me.:)

---

