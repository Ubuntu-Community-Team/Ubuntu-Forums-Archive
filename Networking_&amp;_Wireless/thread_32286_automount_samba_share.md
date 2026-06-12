---
title: "automount samba share"
date: 2005-05-06
forum: Networking &amp; Wireless
---

### Post by sue7504 on 2005-05-06
I'm trying to set up easy access to some folders on my Debian server. I can see the parent folder thru the Samba Windows share & would like to have it automatically loaded at start up & available thru a link (shortcut?) on the desktop.

The 'location' is showing as   smb://mail/data/Consultant


When I try 'make link'  to Consultant I get  ' error - unsupported operation. '   Do I have to 'mount' the share somehow. 

How do I change the start up config so that this happens automatically?

TIA from 1st time forum poster   

Sue

---

### Post by tkiesel on 2005-05-07
Hi Sue,

It's pretty easy to get these sorts of things to automount.  Make a folder where you'd like the mount to be.  I chose /mnt/tunes for the music on my wife's Windows XP computer. The location on her PC that I wanted to share showed up as smb://Pookie/tunes

So, after creating /mnt/tunes to hold the mount, I edited the file /etc/fstab by adding the line
```

//Pookie/tunes /mnt/tunes smbfs fmask=0777,dmask=0777 0 0
```

You'll have different entries for the share location and mount location, of course. If you need a user name and password to access the share, they can be added in the above line like so:

```

//Pookie/tunes /mnt/tunes smbfs username=tkiesel,password=passwd,fmask=0777,dmask=0777 0 0
```

using whatever username and password you have. :)

That'll automount the share and put it on your desktop. (after saving /etc/fstab, run 'sudo mount-a' so you don't have to wait for a reboot) If you want limited permissions to the share, you can use different codes for fmask and dmask, etc. There's lots of powerful potential in there, but this should at least get you up and running. :)

---

### Post by bobpaul on 2006-11-09
How about a way to have it mount when I try to access the folder rather than on bootup? That way if the samba share is down when I startup I can still access it without having to do a mount -a all the time...

---

### Post by kylevan on 2006-11-09
it might be possible to write a simple bash script that executes sudo mount -a and then opens nautilus or Konqueror (whatever you use) to the appropriate directory and place that on your desktop.

edit:  I tried it myself, and while it does work, it's a little inelegant (probably due to my lack of scripting knowledge,) since you have to run it in terminal to enter your password and execute the sudo.

```

!#/bin/bash

sudo mount -a
nautilus /mountpoint/here

```

---

### Post by jha0 on 2006-12-18
Hi kylevan, I have follow the steps you have describe but somehow I got this error when I try to auto mount it: **smbfs: mount_data version 1935764838 is not supported. **Wonder if you have ever come across this issue. Hope you can help.  Thanks in advance

---

### Post by Iowan on 2006-12-18
[http://www.ubuntuforums.org/showthread.php?p=1903303#post1903303]("http://www.ubuntuforums.org/showthread.php?p=1903303#post1903303")

---

