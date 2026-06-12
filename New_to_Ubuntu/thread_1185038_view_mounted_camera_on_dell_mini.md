---
title: "view mounted camera on dell mini"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by ifs_ands_or_buts on 2009-06-11
Hi,

I just got a dell mini 9 with the pre-installed dell ubuntu 8.02.

I want to be able to import pictures from my canon rebel XTi. If I plug it in with a USB cable, I know it connects because I can import photos with F-Stop. However I don't see the camera listed in the "Computer" section and I want to be able to browse. I looked at the Ubuntu help and it makes it seem like if I plug the camera in it should automatically show up there.

Does anyone have any advice? Thanks

---

### Post by unutbu on 2009-06-11
Look in the ~/.gvfs directory.

---

### Post by ifs_ands_or_buts on 2009-06-11
> **unutbu said:**
> Look in the ~/.gvfs directory.

thanks, although that didn't seem to work.

---

### Post by unutbu on 2009-06-12
When you turn on the camera, does a window pop up asking if you wish to open F-spot?
If so, click Cancel. For some reason the files are not mounted in ~/.gvfs unless you do so. 

If you do not see a window pop up, perhaps it is because you've set it to always open F-spot automatically. If this is the case, then you might have to disable that. Unfortunately, I don't know how that's done...

---

### Post by ifs_ands_or_buts on 2009-06-12
> **unutbu said:**
> When you turn on the camera, does a window pop up asking if you wish to open F-spot?
If so, click Cancel. For some reason the files are not mounted in ~/.gvfs unless you do so. 

If you do not see a window pop up, perhaps it is because you've set it to always open F-spot automatically. If this is the case, then you might have to disable that. Unfortunately, I don't know how that's done...

Nothing pops up when I plug the camera in, neither F-Stop nor an ubuntu pop-up. F-stop does recognize the camera but I want to be able to browse the camera in nautilus.

Is there a way to mount the camera? Could this possibly be a permission issue? I ask becuase I installed gphoto2 and was only able to have it show the camera when I used sudo.

---

### Post by unutbu on 2009-06-12
> Is there a way to mount the camera? 

I don't have experience with USB card readers -- so I may be wrong about this -- but I believe if you pop out your Compact Flash card and put it in a USB card reader, and plug the USB card reader into your machine, your machine will/should recognize the USB card reader as an external drive and you can mount the card using the "mount" command. Ubuntu may even mount it automatically for you.

If you plug the camera directly into the machine using the USB cable, then I believe the method described below will mount the camera's CF card's files in ~/.gvfs.
I don't know of a command-line way to force the mounting of the camera in this scenario.

> Could this possibly be a permission issue? I ask becuase I installed gphoto2 and was only able to have it show the camera when I used sudo.

Now this is interesting. I can use this command
```

/usr/bin/gphoto2 --port usb: --force-overwrite --get-all-files 
```

to download the pictures, and I don't have to sudo to use it.
If this is the source of the problem, I'm not sure how to fix it.

Would you try the following experiment?

Turn off the camera.
Turn off the computer.
Turn the computer on, boot Ubuntu.
Log in tho Ubuntu.
Plug the USB cable into the camera.
Plug the USB cable into the computer.
Turn on the camera.
A window should appear. (See attachment below)
Click Cancel
Open nautilus (Places>Home folder)
Type in ~/.gvfs in the Location field.
The files in the camera are located here: ~/.gvfs/gphoto2 mount on usb%3A008,007/DCIM/100CANON/

This part of the path, "usb%3A008,007", may change each time the above ritual is performed.

If this does not work, how about open a terminal (Applications>Accessories>Terminal) and type these commands:
```

lsb_release -a                      # Find out what release of Ubuntu you are using (8.02 is not valid)
lsusb                               # See if the computer detects the camera 
ls -l ~/.gvfs                       # List what's in ~/.gvfs
ps axuw | grep gvfs                 # See what gvfs processes are running
dpkg --get-selections | grep gvfs   # See what gvfs packages are installed
dpkg --get-selections | grep gphoto # See what gphoto2 packages are installed
gvfs-mount -l                       # Output will mention your camera if mounted successfully.
```

Please post the output to all the above commands.
I'm not sure if the above commands will uncover why it works for me and not for you, but that's all I can think of to do.

---

### Post by ifs_ands_or_buts on 2009-06-12
> **unutbu said:**
> Is there a way to mount the camera? 

I don't have experience with USB card readers -- so I may be wrong about this -- but I believe if you pop out your Compact Flash card and put it in a USB card reader, and plug the USB card reader into your machine, your machine will/should recognize the USB card reader as an external drive and you can mount the card using the "mount" command. Ubuntu may even mount it automatically for you.

If you plug the camera directly into the machine using the USB cable, then I believe the method described below will mount the camera's CF card's files in ~/.gvfs.
I don't know of a command-line way to force the mounting of the camera in this scenario.



Now this is interesting. I can use this command
```

/usr/bin/gphoto2 --port usb: --force-overwrite --get-all-files 
```

to download the pictures, and I don't have to sudo to use it.
If this is the source of the problem, I'm not sure how to fix it.

Would you try the following experiment?

Turn off the camera.
Turn off the computer.
Turn the computer on, boot Ubuntu.
Log in tho Ubuntu.
Plug the USB cable into the camera.
Plug the USB cable into the computer.
Turn on the camera.
A window should appear. (See attachment below)
Click Cancel
Open nautilus (Places>Home folder)
Type in ~/.gvfs in the Location field.
The files in the camera are located here: ~/.gvfs/gphoto2 mount on usb%3A008,007/DCIM/100CANON/

This part of the path, "usb%3A008,007", may change each time the above ritual is performed.

If this does not work, how about open a terminal (Applications>Accessories>Terminal) and type these commands:
```

lsb_release -a                      # Find out what release of Ubuntu you are using (8.02 is not valid)
lsusb                               # See if the computer detects the camera 
ls -l ~/.gvfs                       # List what's in ~/.gvfs
ps axuw | grep gvfs                 # See what gvfs processes are running
dpkg --get-selections | grep gvfs   # See what gvfs packages are installed
dpkg --get-selections | grep gphoto # See what gphoto2 packages are installed
gvfs-mount -l                       # Output will mention your camera if mounted successfully.
```

Please post the output to all the above commands.
I'm not sure if the above commands will uncover why it works for me and not for you, but that's all I can think of to do.


Thanks, I will try this when I get home and post the output. 

A card reader is always an option (I've plugged USB sticks in with no problem) but I want to avoid that because I had a bent CF pin once, and want to minimize the amount of times I remove it from my camera.

---

### Post by ifs_ands_or_buts on 2009-06-12
> **unutbu said:**
> I don't have experience with USB card readers -- so I may be wrong about this -- but I believe if you pop out your Compact Flash card and put it in a USB card reader, and plug the USB card reader into your machine, your machine will/should recognize the USB card reader as an external drive and you can mount the card using the "mount" command. Ubuntu may even mount it automatically for you.

If you plug the camera directly into the machine using the USB cable, then I believe the method described below will mount the camera's CF card's files in ~/.gvfs.
I don't know of a command-line way to force the mounting of the camera in this scenario.



Now this is interesting. I can use this command
```

/usr/bin/gphoto2 --port usb: --force-overwrite --get-all-files 
```

to download the pictures, and I don't have to sudo to use it.
If this is the source of the problem, I'm not sure how to fix it.

Would you try the following experiment?

Turn off the camera.
Turn off the computer.
Turn the computer on, boot Ubuntu.
Log in tho Ubuntu.
Plug the USB cable into the camera.
Plug the USB cable into the computer.
Turn on the camera.
A window should appear. (See attachment below)
Click Cancel
Open nautilus (Places>Home folder)
Type in ~/.gvfs in the Location field.
The files in the camera are located here: ~/.gvfs/gphoto2 mount on usb%3A008,007/DCIM/100CANON/

This part of the path, "usb%3A008,007", may change each time the above ritual is performed.

If this does not work, how about open a terminal (Applications>Accessories>Terminal) and type these commands:
```

lsb_release -a                      # Find out what release of Ubuntu you are using (8.02 is not valid)
lsusb                               # See if the computer detects the camera 
ls -l ~/.gvfs                       # List what's in ~/.gvfs
ps axuw | grep gvfs                 # See what gvfs processes are running
dpkg --get-selections | grep gvfs   # See what gvfs packages are installed
dpkg --get-selections | grep gphoto # See what gphoto2 packages are installed
gvfs-mount -l                       # Output will mention your camera if mounted successfully.
```

Please post the output to all the above commands.
I'm not sure if the above commands will uncover why it works for me and not for you, but that's all I can think of to do.


Yeah, I definitely don't get the popup you attached. Here is my output (Sorry I meant Ubuntu 8.04.2, not 8.02). I notice the last command was not found which could be a problem?

rachel@rachel:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.2
Release:	8.04
Codename:	hardy
rachel@rachel:~$ lsusb
Bus 004 Device 002: ID 413c:02b0 Dell Computer Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 004: ID 04a9:3110 Canon, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 064e:a102 Suyin Corp. 
rachel@rachel:~$ ls -l ~/.gvfs
total 0
rachel@rachel:~$ ps axuw | grep gvfs
rachel    4917  0.0  0.2   5276  2072 ?        S    18:37   0:00 /usr/lib/gvfs/gvfsd
rachel    4928  0.0  0.1  28956  1984 ?        Ssl  18:37   0:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/rachel/.gvfs
rachel    5021  0.0  0.2   5276  2124 ?        S    18:37   0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
rachel    5023  0.0  0.2  13728  2552 ?        S    18:37   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
rachel    5682  0.0  0.0   2988   772 pts/0    S+   19:03   0:00 grep gvfs
rachel@rachel:~$ dpkg --get-selections | grep gvfs
gvfs						install
gvfs-backends					install
gvfs-fuse					install
libgvfscommon0					install
rachel@rachel:~$ dpkg --get-selections | grep gphoto
gphoto2						install
gphotofs					install
libgphoto2-2					install
libgphoto2-port0				install
rachel@rachel:~$ gvfs-mount -l
bash: gvfs-mount: command not found
he rachel@rachel:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.2
Release:	8.04
Codename:	hardy
rachel@rachel:~$ lsusb
Bus 004 Device 002: ID 413c:02b0 Dell Computer Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 004: ID 04a9:3110 Canon, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 064e:a102 Suyin Corp. 
rachel@rachel:~$ ls -l ~/.gvfs
total 0
rachel@rachel:~$ ps axuw | grep gvfs
rachel    4917  0.0  0.2   5276  2072 ?        S    18:37   0:00 /usr/lib/gvfs/gvfsd
rachel    4928  0.0  0.1  28956  1984 ?        Ssl  18:37   0:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/rachel/.gvfs
rachel    5021  0.0  0.2   5276  2124 ?        S    18:37   0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
rachel    5023  0.0  0.2  13728  2552 ?        S    18:37   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
rachel    5682  0.0  0.0   2988   772 pts/0    S+   19:03   0:00 grep gvfs
rachel@rachel:~$ dpkg --get-selections | grep gvfs
gvfs						install
gvfs-backends					install
gvfs-fuse					install
libgvfscommon0					install
rachel@rachel:~$ dpkg --get-selections | grep gphoto
gphoto2						install
gphotofs					install
libgphoto2-2					install
libgphoto2-port0				install
rachel@rachel:~$ gvfs-mount -l
bash: gvfs-mount: command not found

Thanks again!

---

### Post by ifs_ands_or_buts on 2009-06-12
(sorry didn't mean to post the above terminal outputs twice - still not used to this tiny keyboard)

---

### Post by unutbu on 2009-06-12
Try installing the gvfs-bin package. This is the package that provides the gvfs-mount command, and many others.
Then try again.

---

### Post by ifs_ands_or_buts on 2009-06-13
> **unutbu said:**
> Try installing the gvfs-bin package. This is the package that provides the gvfs-mount command, and many others.
Then try again.

Just installed and restarted but still no luck. The output looks the same as before except gvfs-bin is listed as installed, and the output to gvfs-mount -l is empty.

---

### Post by unutbu on 2009-06-13
Aha. I think I may have found the problem:
Hardy ships with a package called gvfs-backends version 0.2.3-0ubuntu4. 
The description of this package (apt-cache show gvfs-backends) reads

> gvfs is a userspace virtual filesystem where mount runs as a separate processes which you talk to via dbus. It also contains a gio module that seamlessly adds gvfs support to all applications using the gio API. It also supports exposing the gvfs mounts to non-gio applications using fuse.

This package contains the archive, burn, cdda, computer, dav, dnssd, ftp, http, localtest, network, obexftp, sftp, smb, smb-browse and trash backends. 

Intrepid ships with gvfs-backends version 1.0.2-0ubuntu3, and its description reads

> 
gvfs is a userspace virtual filesystem where mount runs as a separate processes which you talk to via dbus. It also contains a gio module that seamlessly adds gvfs support to all applications using the gio API. It also supports exposing the gvfs mounts to non-gio applications using fuse.

This package contains the archive, burn, cdda, computer, dav, dnssd, ftp, **gphoto2**, http, localtest, network, obexftp, sftp, smb, smb-browse and trash backends.

Notice that Intrepid's gvfs-backends includes a backend for gphoto2 while Hardy's does not.

---

### Post by ifs_ands_or_buts on 2009-06-14
Thanks for you all your help. I actually just upgraded to 9.04 and my camera works out of the box, but this information will still be useful if I need to revert to the factory installed version at any point.

---

