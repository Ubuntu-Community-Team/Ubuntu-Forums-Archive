---
title: "Ubuntu 10.04 &amp; WUSB600N configuration issues"
date: 2011-01-29
forum: New to Ubuntu
---

### Post by tesseract1 on 2011-01-29
Hello, I'm new to Ubuntu.

How do I configure my Wireless USB device?  I've searched many topics regarding this and they all use different methods to achieve configuration.  I've tried many of the methods (no success), but now I don't know if I've permanently broke something.  I've tried so many methods I cannot recall all the ones I've tried.

I currently have my Ubuntu 10.04 dual booting with Windows7 on one hard drive.

At the moment, I cannot connect to any wireless networks on my Ubuntu setup.  It is a Linksys WUSB600N v1.

I appreciate any assistance.

---

### Post by DOSIX on 2011-01-29
I had so many wireless problems with 10.04 that after I configured my wireless drivers to work (WUSB100N or somethign along those lines) the internet still wouldn't totally work so I ended up upgrading to 10.10. Amazing wireless driver support compared to 10.04.

---

### Post by tesseract1 on 2011-01-31
I have solved my issues it seems with this device.  I used the NDIS resolution.

Connected by wire, downloaded NDIS from software center, downloaded driver from Linksys website, and applied the rt2870.inf driver.

Worked after a reboot.

---

### Post by tesseract1 on 2011-02-06
Reopening thread:

Ok I guess I haven't solved my issue.

It seems as though the wireless will connect to the network for a session.  I'll turn my computer back on and boot Ubuntu a few days later, and the wireless will not connect.  It will keep trying, never attain an IP and constantly ask me for my router's password.

What gives?  It is starting to really frustrate me.

I tinkered with NDIS.  I removed the driver, and installed it again.  NDIS froze and I had to do a hard-reboot.  Now I can't even boot into Ubuntu.  I log in and the next screen freezes.

---

### Post by tesseract1 on 2011-02-06
Update:[INDENT]So I have determined that each time I start up Ubuntu, I run into 1 of three situations with my wireless connection.


[LIST=1]
[*]Wireless connects, authenticates, and I can effectively browse the internet for at least 5 minutes.  The wireless drops the SSID and continually asks me for a passphrase.
[*]Wireless connects, authenticates, and the connection is stable for the entire duration of the session.
[*]Wireless does not connect whatsoever and it keeps asking me for a passphrase after a duration of trying to connect.
[/LIST]
More often than not it is either option 1 or 3 that occurs.

NDIS is giving me issues with stalling my entire system and making it very difficult to boot back into Ubuntu.

I'm not really sure what to do. I really want to give Ubuntu a try but this wireless issue is making it very difficult to.

Any help is appreciated.
[/INDENT]

---

### Post by tesseract1 on 2011-02-20
All is well.  Reinstalled Ubuntu 10.04.  Went the route of blacklisting a few of those drivers.  Works fine.

Thanks.

---

