---
title: "Tried to move /home to another drive.....oops!"
date: 2009-12-26
forum: New to Ubuntu
---

### Post by charlier653 on 2009-12-26
I did something wrong, I think.

I was following [this]("http://ubuntuforums.org/showthread.php?t=46866")tutorial, and have come up with this error message on relog:

nautilus could not create the following folders: /home/charlie/Desktop, /home/charlie/.nautilus


Have tried creating those files, now I get:

Mount of rood filesystem failed.5-da72-43e9-948d-a919cef4a140
A maintenance shell will now be started.
CONTROL-D will terminate this shell and reboot the system.
Give root password for maintenance
(or type Control-D to continue.)

---

### Post by Barriehie on 2009-12-26
> **charlier653 said:**
> I did something wrong, I think.

I was following [this]("http://ubuntuforums.org/showthread.php?t=46866")tutorial, and have come up with this error message on relog:

nautilus could not create the following folders: /home/charlie/Desktop, /home/charlie/.nautilus


Have tried creating those files, now I get:

Mount of rood filesystem failed.5-da72-43e9-948d-a919cef4a140
A maintenance shell will now be started.
CONTROL-D will terminate this shell and reboot the system.
Give root password for maintenance
(or type Control-D to continue.)

Did you make any backups before trying this???

Barrie

---

### Post by taurus on 2009-12-26
Did you modify /etc/fstab and somehow screw up some entries in there?  

```
df -h
sudo blkid
cat /etc/fstab
```

If the UUID for / is wrong, then you cannot boot your machine until you've fixed that.

---

### Post by halitech on 2009-12-26
maybe the info here will help (its a little more up to date then a 2 year old thread)

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by charlier653 on 2009-12-26
Hmmm

I apologize for bothering you all.

I thought about what my options were, and have decided to just reinstall, with the changes I need.

I had just installed this distro a few days ago so there really wasn't anything irreplacable on it yet.

Thank you for your replies and help!

---

### Post by Barriehie on 2009-12-26
Backups are a good thing!

Barrie

---

### Post by charlier653 on 2009-12-26
I will remember that, and i have set up a partition just for that, for when I do something wrong again. You KNOW it will happen!

Thanks!

---

### Post by Barriehie on 2009-12-26
And then copy that onto a thumb drive... :)

B.

---

### Post by charlier653 on 2009-12-26
Something else I learned from this experience.......Use the UUID to identify the partition that you are reassigning! Is no doubt then where you are going etc.

I think that was the problem, I specified the wrong partition, using /dev/sd**, trying to take a shortcut I shouldn't have.

---

