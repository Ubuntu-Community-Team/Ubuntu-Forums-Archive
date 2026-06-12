---
title: "ndiswrapper and zd1211 in Edgy"
date: 2006-11-09
forum: Networking &amp; Wireless
---

### Post by somersetsimon on 2006-11-09
After my system collapsed ([http://www.ubuntuforums.org/showthread.php?t=293481)](http://www.ubuntuforums.org/showthread.php?t=293481)), I decided the only option was a complete reinstall. Previously, I had managed to get my zd1211b usb wireless adaptor working with Dapper, so I thought I'd give Edgy a try. For a change, I thought I'd take a look at KDE and Kubuntu, so I did an install from a Kubuntu Edgy Live CD. That's when I realised that I didn't know as much about KDE as I have learned about Gnome in my brief Linux experience!

Kubuntu seemed to have all the build-essential stuff already loaded, so I was ok to build the current version of ndiswrapper that I'd downloaded from sourceforge. Unfortunately, the build failed with a number of errors. They looked like the sort of errors I'd solved with Ubuntu by loading the correct linux-headers from the CD. I popped in the CD, but didn't know how to install stuff from it. In Ubuntu, Synaptic automatically starts up when an install CD is inserted. Kubuntu didn't seem to recognise anything from the CD...

Anyway, I had enough of this and installed Ubuntu Edgy instead. I followed exactly the same procedure that got my wireless working with Dapper - loaded all the headers and build-essential from the CD, built the latest version of ndiswrapper, installed the latest windows driver. Ndiswrapper reported that the driver and hardware was installed. However, ifconfig only identifed eth0 and lo, no sign of any wireless networks.

Are ndiswrapper and/or the zd1211b card handled differently in Edgy? :-k

---

### Post by FrodoB on 2006-11-09
I am using the zd1211b native drivers. You can see my build procedure here:

[http://www.ubuntuforums.org/showthread.php?t=295843](http://www.ubuntuforums.org/showthread.php?t=295843)

If you want to use ndiswrapper you may need to blacklist the zd1211rw module as described in my procedure as maybe the built-in may interfere with ndiswrapper as well.

Otherwise, the native driver works great in Edgy.

---

### Post by somersetsimon on 2006-11-10
Thanks,
I removed ndiswrapper, downloaded the latest native drivers and it worked!

Edgy on-line :-)

---

### Post by FrodoB on 2006-11-10
Excellent news!

---

### Post by somersetsimon on 2006-11-11
> **FrodoB said:**
> Excellent news!

I'm still not convinced about the wireless features in Ubuntu. After Ubuntu failed again, requiring yet another reinstall, I thought I'd try another variant, so I had a go at Kubuntu Edgy. I couldn't get wireless to work on that with the native drivers or ndiswrapper.

Ubuntu went down just after I got wireless working. I got it all sorted one night, booted up the next morning and it had lost all the settings, didn't even recognise wlan0. I shut down and came back to it after work. Tried to boot up then and nothing worked at all. Nobody seemed to be able to help either.

[http://www.ubuntuforums.org/showthread.php?t=293481](http://www.ubuntuforums.org/showthread.php?t=293481)

I think I'll go back to Dapper tomorrow. :-k 

My concern with Ubuntu is that, going by my Edgy experience, upgrading in the future could lose the functionality I have now. Hopefully someone will get wireless networking sorted out properly soon ](*,)

---

