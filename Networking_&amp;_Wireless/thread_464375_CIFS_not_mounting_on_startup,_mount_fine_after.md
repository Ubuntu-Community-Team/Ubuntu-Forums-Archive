---
title: "CIFS not mounting on startup, mount fine after"
date: 2007-06-04
forum: Networking &amp; Wireless
---

### Post by UrbanSlayer on 2007-06-04
I've just built a new MythTV box with Feisty (used to run Breezy), did a clean install.

Everything works, except for mounting my CIFS shares on startup.

I have the following line in my fstab -

//lumiere/60GB /media/60GB cifs auto,credentials=/home/.smbpasswd,user,dir_mode=0777,file_mode=0777 0 0

I have tried it with auto, noauto or neither.  I have also tried using the IP address and the machine name is in /etc/hosts with the correct IP.  The current permissions on the credentials file is 700, but it was 600, owned by root etc, but neither worked.

I can mount all the drives listed like the above once the machine has finished booting by running sudo mount -a, all drives mount.  I have checked dmesg, messages, syslog, auth.log, both samba logs and I have no events relating to my cifs shares mounting, or not mounting.

I have Samba and smbfs installed.  The above example line works perfectly in my Debian Sarge and Etch servers, on startup, and did work fine on Breezy.  I have seen the HALD bug, but I am not effected by it, it just seems like it isnt even trying to mount the shares.

What is wrong?  Can anyone help?

Thanks

---

### Post by dmizer on 2007-06-04
are you using a wireless connection which requires a password to activate after you've logged in?

another thing that can cause this to happen is if you've configured your desktop to log you in automatically.

you can overcome this problem but it's a bit of a pain, and i'm not sure i can be much help with that.  here's a thread of someone who did manage to get it working: [http://ubuntuforums.org/showthread.php?p=2028558#post2028558](http://ubuntuforums.org/showthread.php?p=2028558#post2028558)

---

### Post by UrbanSlayer on 2007-06-05
I dont use wireless, its a wired connection.

I do have a user login on startup, but this was never an issue on Breezy.  I shall look into using autofs, but for now (this is a terrible hack), I have written a very simple script that just contains -

mount -a (plus the bin/sh stuff etc)

And put it in /etc/init.d and got it to start on runlevel2, so all items in my fstab get mounted.  It seems to work ok, although I think I will modify it to be -

mount -a -t cifs just to deal with my windows mounts.  Still dirty, but it seems to work.

Cheers!

---

### Post by dmizer on 2007-06-05
it'd probably be safer to add this line:
```
mount /media/60GB
```
to /etc/rc.local

also, do you have the same problem if you replace "lumiere" with lumiere's actual ip address?  it could be that the network is just timing out on trying to resolve the host name.

---

### Post by UrbanSlayer on 2007-06-05
Have tried the IP address as well, I get the same result.  I have 6 of those lines (for different shares), that one is just an example, the rest are the same (except for sharename and mount point, obviously..heh).

I will try adding that, and see what happens, but wont the sudo part as for a password?

---

### Post by dmizer on 2007-06-05
rc.local will run things as though from a root prompt, so no need for a "sudo" or a password.

edit:
lol ... i added "sudo" to the command out of sheer habit.  i edited the post and removed "sudo" from the command, it is not necessary.

---

