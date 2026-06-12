---
title: "Mount samba shares more like Linspire..."
date: 2006-09-27
forum: Networking &amp; Wireless
---

### Post by djRobbieF on 2006-09-27
One of the things I don’t like about nautilus (the “my computer” style feature of Ubuntu) is that when you mount your network shares, they’re not REALLY mounted; you still have to “buffer”, or download the content from your network prior to using it. This is a pain for me because I store all my MP3 files on a network drive; so when I want to listen to music in Ubuntu, I have to first copy the MP3 files to my computer, then I can listen. That’s no good for me.

So…

Bring up your linux terminal and do this:

```
sudo apt-get update
sudo apt-get install smbfs
modprobe smbfs
sudo mkdir /mnt/directory
sudo mount -t smbfs -o password= //servername/sharename /mnt/directory

```

Replace “directory” with the name you want to use as your mount-point.

Replace “servername” and “sharename” with the appropriate samba share values.

The above command uses an anonymous login. If your samba share requires a password, simply add it to password= (example: password=potato)

Now, browse to /mnt/directory in nautilus, and you’ll see that you can access your files without having to download them first ;) - Yes, now when I double-click my MP3 file, it plays instantly, as if it were on my local hard drive.

To make this mount automatically at startup, ```
sudo gedit /etc/fstab
``` and add this line:
```
//servername/sharename /mnt/directory smbfs o 0 0
```
Then, reboot your computer to test, and that mount point will now work forever and ever ;)

Cheers

---

### Post by dmizer on 2006-09-28
samba mount sure is a pain sometimes.  nice howto.  like to add a few things.

first of all, i think (not positive) but i think, if you mount the folder to /media instead of /mnt that a folder will automatically appear on your desktop when mounted.

but if you're sharing files from linux to linux, ssh and fuse are more secure and faster than samba.  also much easier to set up ssh on a linux box.

also, you have the option of setting up an internal streaming media server like so:
[http://easylinux.info/wiki/Ubuntu_dapper#Streaming_Media_Server](http://easylinux.info/wiki/Ubuntu_dapper#Streaming_Media_Server)

that way it will work on any system, any os, any computer that has access to your network with no extra configuration to the listening system.

---

### Post by djRobbieF on 2006-09-28
Thanks for the additions.  Yes; if it were just for MP3, those are good ideas.  I really meant for the MP3 thing to be more of an "example" - but the practical use of this howto spans much more than just MP3s.  I also prefer to keep all my documents on my network, and by mounting the folders in this way, I can open the documents, edit them, save them, etc. and they never really "touch" my local system.  In otherwords, when I reformat upon Edgy's release, I don't have to bother backing up all my stuff, because it's all stored on a network drive  ;)

Besides, my server has over a terribyte of storage space... so I'm lovin' it  ;)

BTW - I went with samba here for "ease of use" for cross-platform networks (for those networking their Ubuntu boxes with Windows systems, for example).  It's a simple solution.  In most home networks, security is not as much a concern as ease-of-use.  But I would certainly use alternative methods if setting this up at, for example, an office.

Cheers!

---

