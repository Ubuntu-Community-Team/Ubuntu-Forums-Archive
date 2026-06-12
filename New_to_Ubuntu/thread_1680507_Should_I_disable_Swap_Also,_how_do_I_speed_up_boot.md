---
title: "Should I disable Swap? Also, how do I speed up boot?"
date: 2011-02-02
forum: New to Ubuntu
---

### Post by hansolo4949 on 2011-02-02
I'm a person who wants to get the most out of his computers, make them fast, decrease boot time, etc. and I have been wondering about disabling my swap file. I have 4 gigs of ram, so I think I would be good to go, though is there any real speed gain to this? Also, is there any way to speed up Ubuntu booting? mine boots between 1 minute, and 1 minute, 30 seconds, and I thought Ubuntu was much faster than that. I have tried profiling my boot, but I don't know whether I should remove "profile" from my grub file, or not. Thank you for your help!

---

### Post by Ocxic on 2011-02-02
if you don't want/need to hibernate or suspend, you can disable swap without worry.

---

### Post by wojox on 2011-02-02
< twelve parsecs, Han. :p

No really download BootChart:

```
sudo apt-get install bootchart
```

Then reboot and look in "/var/log/bootchart".

---

### Post by stmiller on 2011-02-02
Disabling swap won't really speed things up, per say.

Rather, change this value to prefer your ram vs. swap:

```

sudo nano /etc/sysctl.conf

```

Add this line at the bottom:

```

vm.swappiness=0

```

Reboot to see changes


Also, turn off these un-needed services from running in the background:

```

sudo apt-get install sysv-rc-conf

```
Then run
```

sudo sysv-rc-conf

```
Disable these things by clearing out ALL of the [x]'s across with space bar for each particular service:

saned &#8211; for scanners

pppd-dns &#8211; for dial up internet

dns-clean &#8211; for dial up internet

bluetooth &#8211; for bluetooth

cups - if you don't need to print


Also go to:

System > Preferences > Startup Items

And disable things such as:

bluetooth manager (if you don't need bluetooth)

evolution alarm notify (if you don't use evolution calendaring alarms)

---

### Post by ajgreeny on 2011-02-02
I think ```
sudo sysv-rc-conf
``` is now deprecated and does not work any more.

---

### Post by stmiller on 2011-02-02
> **ajgreeny said:**
> I think ```
sudo sysv-rc-conf
``` is now deprecated and does not work any more.

Works ok here. It's even in natty:

[http://packages.ubuntu.com/natty/sysv-rc-conf](http://packages.ubuntu.com/natty/sysv-rc-conf)



It just manages the /etc/rc.*/ symlinks. Cheers,

---

### Post by ajgreeny on 2011-02-03
Fair enough!

Perhaps it now does less than it used to, with so many things started using upstart, or whatever it is now.  I have to admit that I haven't looked at it for a long time now, though I did use it many times in previous ubuntu versions.

---

