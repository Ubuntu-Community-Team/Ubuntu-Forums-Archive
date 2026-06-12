---
title: "Mounting ext hdd messes up ssh"
date: 2014-08-21
forum: Networking &amp; Wireless
---

### Post by denywinarto on 2014-08-21
Ubuntu 12.04.4 LTS,
Everytime i mount my ext hdd, my ssh messes up... can't do putty or filezilla..
when i try to fix it via command line i get this message :

sudo: /usr/lib/sudo/sudoers.so must be only writable by owner

It seems to lost root access somehow which is very strange cause i logged in with root..

Upon restarting i'm getting this message :

the disk drive for /media/sdh1 is not ready

I think that's my external drive..

The problem seems to be gone if i skip mounting that disk on startup
But so far i'm not able to plug in any external storage..
I really like ubuntu but unstability issues like this makes me wonder if this is a good choice for long term use...

---

### Post by weatherman2 on 2014-08-21
This isn't an "unstability issue," this is a setup problem.

Please more specific about exactly what you are doing and how.

What do you mean exactly by "fix it via command line?"  What commands?

How did you try to mount the drive?  Did you add an entry to /etc/fstab?  If so, what is the content of your /etc/fstab file?

It seems you may have done something to cause the issue with the sudoers file - changed permissions on something?  Here's how you would fix that:

[http://askubuntu.com/questions/234603/how-do-i-deal-with-sudoers-so-must-be-only-be-writable-by-owner](http://askubuntu.com/questions/234603/how-do-i-deal-with-sudoers-so-must-be-only-be-writable-by-owner)

---

