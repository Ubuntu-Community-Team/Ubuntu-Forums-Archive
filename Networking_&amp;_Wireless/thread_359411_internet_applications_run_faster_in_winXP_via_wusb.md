---
title: "internet applications run faster in winXP via wusb4g"
date: 2007-02-11
forum: Networking &amp; Wireless
---

### Post by wickstopher on 2007-02-11
I have both an Edgy Eft and a Windows XP pro partition on my PC.  My linksys wusb4g works well in Ubuntu, but I have noticed that internet applications (most noticeably firefox) download significantly faster in Windows XP.  I never had to install any drivers or use ndiswrapper for the device in Edgy.  Does anyone know of a way to get my speeds up?  Perhaps the USB2.0 drivers in Edgy are not quite up to par with the XP drivers?  Or, perhaps I need to install a more suitable driver for the device in Edgy?  If anybody has any ideas, let me know!  Everything else in Edgy runs so much better than in Windows, and I would like to get my transfer speeds up to snuff!  It would be one more step towards deleting the XP partition off of my machine entirely.

---

### Post by Floppyjoe on 2007-02-12
[http://www.ubuntuforums.org/showthread.php?t=166562&highlight=faster+firefox](http://www.ubuntuforums.org/showthread.php?t=166562&highlight=faster+firefox)

[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4]("https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4")

---

### Post by wickstopher on 2007-02-12
I followed the instructions and ended up with this:

```
ip a | grep inet6
    inet6 ::1/128 scope host 
    inet6 fe80::218:39ff:fe04:d97e/64 scope link 

```

So, apparently I am getting output and inet6 is not disabled.  The link you gave didn't give any instructions for what to do if you were getting output on entering this command.  Any ideas?

Besides this, after disabling inet6 in firefox, things seem to be running a lot quicker.  It could be the placebo effect, but it at least seems to be faster.

---

### Post by Floppyjoe on 2007-02-12
Try:
```
sudo gedit /etc/modprobe.d/blacklist-ipv6
```
add the line:
```
blacklist ipv6
```
Then save file and restart.

---

### Post by wickstopher on 2007-02-12
Thanks, that worked!  Although, if anybody is reading this, for future reference, the code I used was:

```
gksudo gedit /etc/modprobe.d/blacklist
```

and then I added the line:

```
blacklist ipv6
```

---

