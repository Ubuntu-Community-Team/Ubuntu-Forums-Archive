---
title: "Networking - Wired Ethernet Problems"
date: 2006-10-19
forum: Networking &amp; Wireless
---

### Post by whatever123 on 2006-10-19
I have Ubuntu 6.06 LTS... I have installed it, and plugged in my ethernet, and Firefox won't connect!  Where do I start troubleshooting?  I despartely need help on this, b/c I want to switch from Windows...

Thanks in advance!

---

### Post by TheWizzard on 2006-10-19
was your pc plugged in your ethernet when you installed ubuntu?

---

### Post by whatever123 on 2006-10-19
Yes, the ethernet was plugged in.  The light for the ethernet card comes on indicating a connection on my desktop.  But Firefox won't show the websites.  Tonight, I'll post my ifconfig file.  I'm confused with ipv6, but have read that it should not affect my networking status.

---

### Post by Iowan on 2006-10-19
> **whatever123 said:**
> ...  Tonight, I'll post my ifconfig file.
Also post the **/etc/network/interfaces** file.

---

### Post by CatKiller on 2006-10-19
> **whatever123 said:**
> I have Ubuntu 6.06 LTS... I have installed it, and plugged in my ethernet, and Firefox won't connect!  Where do I start troubleshooting?  I despartely need help on this, b/c I want to switch from Windows...

Thanks in advance!

Did you do System -> Administration -> Networking to say whether you're using a Static IP or DHCP, or whatever?

---

### Post by whatever123 on 2006-10-19
I was using a Linksys WET54G (wireless ethernet bridge), after I couldn't connect using Linksys WUSB54GC.  It was a painful experience.  Last night, the WET54G didn't work, but I think that it must need to be rebooted after being used by Windows XP on my dual-boot machine.  Ideally, it acts as a wired ethernet link.  Hopefully, that was the problem, and it doesn't flake out again.  

In the meantime, if anyone can figure out how to connect a WUSB54GC, please let me know.  I tried using ndiswrapper (3 different methods, 2 different installs) and various drivers from rt2x00.serialmonkey.com.  Nothing worked!  It's usb id is 13b1:0026.  I found that was different and, probably, updated from the original with usb id 13b1:0020.  

Once linux gets wireless right, I'll be a big fan!

---

### Post by cna2008 on 2006-10-31
Install a software of analysis. 
[http://www.colasoft.com](http://www.colasoft.com)

---

