---
title: "can't upgrade to 8.10"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by concerto on 2009-01-09
I start up the update manager and everything starts off fine and then an error pops up and it displays the message below.  I did try the sudo apt-get clean from the terminal and after I enter my password and press enter nothing happens.  I have a 300 GIG hard Drive and it's not even half way full and i'm getting a memory error message.  What should I do guys?



Not enough free disk space

The upgrade aborts now. The upgrade needs a total of 113M free space on disk '/boot'. Please free at least an additional 75.5M of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.




thanks everyone

---

### Post by Crafty Kisses on 2009-01-09
Sounds like you might have too many kernel images stored within your **/boot** partition. I'd also like to know what are the results of this command?
```
df -h
```

---

### Post by concerto on 2009-01-09
concerto@concerto:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             290G  9.1G  267G   4% /
varrun                1.5G   96K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G   68K  1.5G   1% /dev
devshm                1.5G   12K  1.5G   1% /dev/shm
/dev/sda3             193M  148M   36M  81% /boot
tmpfs                 1.5G   39M  1.5G   3% /lib/modules/2.6.24-23-generic/volatile
concerto@concerto:~$

thank you codename.  I hope this helps

---

### Post by concerto on 2009-01-10
?

---

### Post by jrusso2 on 2009-01-10
If you have too many kernels in /boot there is probably not enough room left so delete them making sure you don't delete the one your booting from.

---

### Post by concerto on 2009-01-10
jrusso2,
     Do you know how to delete these Kernels?

---

### Post by SunnyRabbiera on 2009-01-10
truth be told Ubuntu 8.10 doesnt offer much over 8.04, you can just stick to what you have without any real drawbacks.

---

### Post by concerto on 2009-01-10
Well,...  I guess that solves everything then.  :(

---

