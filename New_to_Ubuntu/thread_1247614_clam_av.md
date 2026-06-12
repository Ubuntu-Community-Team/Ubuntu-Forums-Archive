---
title: "clam av"
date: 2009-08-23
forum: New to Ubuntu
---

### Post by MelDJ on 2009-08-23
when i try to open clamav from terminal this comes

mel@mel-desktop:~$ clamd
ERROR: Can't open /var/log/clamav/clamav.log in append mode (check permissions!).
ERROR: Can't initialize the internal logger
mel@mel-desktop:~$ sudo clamd
ERROR: initgroups() failed.
mel@mel-desktop:~$ 

can someone help? i dont have the icon in either accerories or internet panel

---

### Post by HiImTye on 2009-08-23
try
```
gksu clamd
```

---

### Post by glenstewart on 2009-09-20
This worked for me:

In /etc/apparmor.d/usr.sbin.clamd

...add this line in bold, to the existing text shown:

/usr/sbin/clamd {
  #include <abstractions/base>
  #include <abstractions/nameservice>

**  capability dac_override,**


Then do:

sudo /etc/init.d/apparmor reload
sudo /etc/init.d/clamav-daemon start

---

### Post by 73ckn797 on 2009-09-20
Go to System/Administration/Synaptic Package Manager and install "clamtk". Is is the graphical application.

---

### Post by Paqman on 2009-09-21
> **HiImTye said:**
> try
```
gksu clamd
```

Definitely not!

gksu/gksudo should only be used for graphical apps, not for a daemon.

---

