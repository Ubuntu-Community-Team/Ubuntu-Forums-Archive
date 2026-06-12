---
title: "Mounting AFP shares from Mac OS X 10.8 to Ubuntu Server 13.10"
date: 2014-06-15
forum: Networking &amp; Wireless
---

### Post by jarrad2 on 2014-06-15
Hi guys

After an exhausting amount of time, I decided to write this HowTo seeing as it took me forever and I'm sure there might be others out there who want to know how to achieve this. 
I am suspecting as much purely because I found lots of half information out there that didn't work.
So here it is:

Start by installing some required libraries.
[COLOR=#000000][FONT=Helvetica]sudo apt-get install make libncurses-dev libreadline-dev libgcrypt-dev zlib1g-dev netatalk

Next, obtain Fuse directly from the source here:
[/FONT][/COLOR]http://sourceforge.net/projects/fuse/files/fuse-2.X/
I used wget

Unpack and install fuse

Edit /etc/fuse.conf to uncomment the line user_allow_other

Add your user to the Fuse group
sudo gpasswd -a user fuse

Obtain afpfs-ng 0.8.2 from here:
[https://github.com/simonvetter/afpfs-ng](https://github.com/simonvetter/afpfs-ng)
Note: I had some issues with the gzipped tarball that came down and ended up unzipping on another machine and then transferring via wget and http to my Ubuntu box

Unpack and install afpfs
sudo ldconfig (I found a reference to this, not sure if required)

Edit /etc/fstab
[COLOR=#000000][FONT=Helvetica]afpfs#afp://user:password@ip/share[/FONT][/COLOR][COLOR=#000000][FONT=Helvetica]    [/FONT][/COLOR][COLOR=#000000][FONT=Helvetica]/mnt/mountpoint[/FONT][/COLOR][COLOR=#000000][FONT=Helvetica]    no auto,[/FONT][/COLOR][COLOR=#000000][FONT=Helvetica]user=user,group=fuse[/FONT][/COLOR][COLOR=#000000][FONT=Helvetica]    [/FONT][/COLOR][COLOR=#000000][FONT=Helvetica]0[/FONT][/COLOR][COLOR=#000000][FONT=Helvetica]    [/FONT][/COLOR][COLOR=#000000][FONT=Helvetica]0

Yes passwords are unfortunately in the clear :\

The end result however, is that the AFP share will mount by using sudo [/FONT][/COLOR][COLOR=#000000][FONT=Helvetica]mount -a at /mnt/mountpoint and your user will be able to add/remove/manipulate files on this share point.[/FONT]

[FONT=Helvetica]Hopefully this helps someone else out there too.[/FONT][/COLOR]

---

### Post by mörgæs on 2014-06-15
Thanks, does it also work for a 14.04 server? 13.10 is soon out of support.

---

### Post by jarrad2 on 2014-06-15
I don't know as of yet. I will have to upgrade and try. I suspect it would still work.

Just a courtesy fyi - after 10 reboots all of a sudden the share is not mounting and holding up the boot process. I will get back to this when I resolve the problem.

I am suspecting this is an OS X issue rather than an Ubuntu one though. Something to do with AFP.

EDIT: It's a bit of a both issue and here's why:

It would appear that as long as session is being maintained for long enough between reboots, then that session will reconnect and the fstab entry will work and remain.
If the session is broken, then either netatalk, fuse or both have not initialised into the boot process before the fstab entry is called, resulting in a hung boot sequence.
A delightfully insecure method is to have the server terminal autologin and run a script via rc.local but this is definitely a very far cry from what I would like to see happen from a security perspective.

---

### Post by jarrad2 on 2014-06-18
Sigh, because it was insecure as hell due to the fact that:

a) the afpfs daemon doesn't run before fstab parses and
b) that afpfs daemon wants to run as the user mounting the share thus leading to me using an autologin and then scripting fstab parsing at user login, I ended up using CIFS to mount the share.

If you would like the full details of how to get it working using an autologin I will clearly adjust the first post to reflect this, but it would probably be a good idea to remove the HowTo from it now as I can't confidently say that this is a proper how to with security and so forth looking forward.

---

### Post by mörgæs on 2014-06-18
Ok, removed. 
Let me know if there is progress some day and you want it added again.

---

