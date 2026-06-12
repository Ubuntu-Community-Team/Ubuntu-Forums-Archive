---
title: "FYI: 2wire, AT&amp;T Uverse, old Dell Dimension...work!"
date: 2007-09-11
forum: Networking &amp; Wireless
---

### Post by kelly777 on 2007-09-11
I felt like I'd share my experience with Ubuntu in the hopes it will help someone else.  I'm new to this OS and decided to install it on an old Dell Dimension 8100 with a [2wire wireless USB card]("http://www.2wire.com/?p=117").  My internet provider is AT&T Uverse and they have their own gateway/router device installed.

It took about 10 days of on and off trying, but I finally have the pc networked to my laptops and the internetz works!

Here is how it ultimately went down...

To get the 2wire card set up, I had to use ndiswrapper and the WLanUIG.inf file from the install CD.  It worked just fine.

I initially tried WPA (because that's how the tech set up the gateway/router).  I tried wpasupplicant, editing the conf file, messing with the /etc/network/interfaces file...nothing worked (well, I got it to work once, but after re-boot it never worked again).

I switched the gateway/router to WEP and hid the SSID.  I then used the WICD tool to connect.  BINGO!  Works for static IP as well as DHCP.

I can now network with my other PCs, and even share the printer attached to the Ubuntu box.

Hopefully this helps someone out there.

---

### Post by w4d on 2007-09-24
I have no idea what you said and how to do it. Perhaps a more in-depth description / tutorial?

Thanks.

---

### Post by lamarcheb on 2007-10-24
Thanks for the information. I just booted from the Live 7.10 AMD64 disc and as many users have reported the 2WIRE USB 802.1G adapter is not recognized.  To know that it works using NDISWRAPPER is a relief.

For those readers not familiar with NDISWRAPPER: it is a software that allows the use of Windows network drivers to be used under Linux. There are many posts in ubuntuforums that explains how to configure it, but the easiest for me was to read the instructions written by the author of the software. Once configured, it works very well.

Doing a Google on NDISWRAPPER, the first hit will be its home page at sourceforge.net.

Good luck.

---

### Post by coldguy on 2007-12-07
Awesome for you, but not working for me yet. The driver seems to have been installed using NDISWRAPPER, but I still get no option for wireless in the network manager. Help?!

---

### Post by lamarcheb on 2008-02-07
I have the exact same problem as the previous post. 64-bit ubuntu 7.10. Driver is installed but is not recognized.:confused:

---

