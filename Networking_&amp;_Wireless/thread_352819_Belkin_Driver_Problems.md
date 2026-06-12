---
title: "Belkin Driver Problems"
date: 2007-02-03
forum: Networking &amp; Wireless
---

### Post by liambre on 2007-02-03
Hey everyone,
i'm new to linux, and this is my first day of using it properly. 

I've recently bought a Belkin F5D7000 PCI card for wireless in this computer. I'm having great difficulties installing a driver though. I'm using ndiswrapper to use windows drivers, but im having no luck so far.

When i try the code:
```
sudo ndiswrapper -i /home/drivers/bcmw15a.inf
```

I get asked for the password, and then receive the output:
```
Installing bcmw15a
couldn't copy /home/drivers/bcmw15a.inf at /usr/sbin/ndiswrapper line 135
```

It's getting really frustrating, and I just can't figure what's wrong.

Thanks for any help provided,

Liambre.

---

### Post by seventynine on 2007-02-03
not sure if this helps, but i have the same card running via fwcutter method (the alternative method) with WPA working.........maybe u want to try it?

---

### Post by liambre on 2007-02-03
if it works, i'd love to try it :P

---

### Post by seventynine on 2007-02-03
here's the guide i used: [http://ubuntuforums.org/showthread.php?t=185174&highlight=fwcutter](http://ubuntuforums.org/showthread.php?t=185174&highlight=fwcutter)

---

### Post by jml on 2007-02-04
If you are still not successful, you may want to try blacklisting the Broadcom driver Ubuntu installs by default ( search this forum with terms blacklist and Broadcom) and then try again.

Joe

---

### Post by msimon1960 on 2007-02-04
Check out the thread by 'PiracyRocks' -- he's put together a simple guide for overcoming this.  I have the FD570001 Belkin cards on three workstations.

Matt

---

### Post by helliewm on 2007-02-04
I think you have the wrong file for ndiswrapper try the bcmwl5.inf. You also need to blacklist the bcmxx  files.

sudo gedit /etc/modprob.d/blacklist

Enter a line in the file 

Blacklist bcmxx.

You also need to active the driver

sudo modprob.d

I think I have remembered that correctly.

Helen

---

