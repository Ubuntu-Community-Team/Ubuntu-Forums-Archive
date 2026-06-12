---
title: "Gateway MX7118 Laptop problems"
date: 2006-10-31
forum: Networking &amp; Wireless
---

### Post by casperiv on 2006-10-31
I am totally confused.  Alright, I have spent forever trying to get my wireless working, and don't seem to be getting any closer.

After following the wireless guides, I used ndiswrapper to install a windows driver.  In the manager it says the hardware present: yes.  When I look at interfaces in console it comes up as eth1.  When I did all this I didn't blacklist the default wireless drivers, so I went back and did it.  Still nothing.  Right now I can see it come up in my devices, but doesn't work.  Also, in System -> Administration -> Networking all I can see is Wired Connection and Modem.  Why does System -> Administration -> Windows Wireless Drivers say that bcmwl5 and hardware present: yes, but I don't even see a wireless option in Networking?

Please, I got my audio working, my wired is working, but without wireless my laptop is kind of useless.  I need your help!

---

### Post by -Chi.0 on 2006-10-31
Check this link for help w/ NdisWrapper on Edgy](*,) 
[http://ubuntuforums.org/showthread.php?p=1692550#post1692550]("http://ubuntuforums.org/showthread.php?p=1692550#post1692550")
I hope this helps:-k

---

### Post by casperiv on 2006-10-31
I followed that information, and I followed the link inside.  It says it's working, but it never registers the wireless in ifconfig.  I have the newest wrapper, I blacklisted the default drivers, I have run all their checks, but nothing seems to work.

---

### Post by casperiv on 2006-10-31
I just did another run through with the "Problems w/ ubuntu wireless with broadcom" thread without success.  Ever since I did the "blacklist"of the old driver it has never shown back up in Networking.

Please, I really want to get this working.  All I need to do is get WIFI working and everything will be working on my laptop.

---

### Post by warkro on 2007-01-10
> **casperiv said:**
> I just did another run through with the "Problems w/ ubuntu wireless with broadcom" thread without success.  Ever since I did the "blacklist"of the old driver it has never shown back up in Networking.

Please, I really want to get this working.  All I need to do is get WIFI working and everything will be working on my laptop.

hey I got my wireless working with the exact same laptop.  
followed this howto
[http://www.ubuntuforums.org/showthread.php?t=285809](http://www.ubuntuforums.org/showthread.php?t=285809)

but i didn't ever touch System > Admin > Networking > wireless settings

I just plugged my ethernet... downloaded automatix...used it to install network manager and after that it worked fine.   Make sure your /etc/network/interfaces file only contains the lines with the word LO in it.

---

