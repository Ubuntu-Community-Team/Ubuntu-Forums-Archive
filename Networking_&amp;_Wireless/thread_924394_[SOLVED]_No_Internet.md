---
title: "[SOLVED] No Internet"
date: 2008-09-19
forum: Networking &amp; Wireless
---

### Post by deanium on 2008-09-19
Hey,

I know this does sound a tad off, but once I originally got ubuntu to install and run, I had issues with my graphics driver, but that seemed to be it; I had sound and internet connectivity (via wired connection to router). I have now overcome the graphics issue, but seem to have no internet connection. When booting into Windows (Vista HP x86) I am connected, and Ubuntu even claims that I am connected, however FF wont load a page, and I am unable to download new applications.

Seeing as it was working, and now isn't, something surely must have triggered it, but I don't know what.

Does anyone know how to reset the internet connection options, or whatever it is you'd have to do to re-establish a successful connection to the network. Sorry if I sound a bit dumb, I am very new to Linux.

Cheers,
Dean

---

### Post by shanix on 2008-09-19
1. DNS issue
It might be just as simple as DNS issue. You can try to use the Network Manager and set ur DNS to 4.2.2.2 (Public DNS Server) to see if it works for you.

2. DHCP issue
Check the ifconfig command and see if you get the IP address.

3. Routing issue
Try to ping 4.2.2.2 and see if you get an respond from it.

---

### Post by deanium on 2008-09-20
Right, wasn't too sure about accessing Network Manager so haven't been able to try that out. As for the DHCP, I am being assigned an IP address by my router correctly, and am able to ping 4.2.2.2 successfully.

I've noticed some change to the issue. I am able to load small pages such as Google and Google search results, however when I attempt to load larger pages (such as these forums) it wont load. I also attempted to load my router's web interface, to which I was greeted by some of the frames and background images loaded, but no more.

Could the problem be FF? Perhaps an option or something? I don't usually use FF so I don't really know its options or settings.

---

### Post by noobuntu_86 on 2008-09-20
When the google results load is it at full connection speed? Or real slow? Perhaps look at this and see if it helps you:

[CLICK HERE]("http://ubuntuforums.org/showthread.php?t=826020&highlight=slow+upload")

It may be a long shot, but might be worth a go :)

---

### Post by Iowan on 2008-09-20
> **shanix said:**
> 2. DHCP issue
Check the ifconfig command and see if you get the IP address.
Also check if it is a "real" address - or if **avah**i has issued a 169.x.x.x zeroconf address.

---

### Post by deanium on 2008-09-20
The google results load at full speed, and the ping of 4.2.2.2 is as fast as any normal ping. The IP I've been assigned (as far as I can see) is a 192.168.x.x which would surely imply my router is doing its job as DHCP Server.

I do find it odd as I clearly have some level of connection, however as I said, it appears to be "loading" larger pages, but never gets there (I have waited up to 15mins and nothing). Also when trying to install software from the built in thingy (not sure if that is in fact the technical name, I'm a bit new at this) it never gets anywhere.

---

### Post by deanium on 2008-09-20
Just to add, I have checked the Network Options (or whatever it's called), and it was set as Wired (in roaming mode), which I tried changing to disabling roaming mode. Both have the same effect.

---

### Post by deanium on 2008-09-20
OK this is weird. I've booted into Ubuntu again, just to see how it's going, and it's working. I'm writing now from Ubuntu. I have no idea what's caused this problem nor what's solved it, but I'm happy. If I do come up with any evident reasons for this, I will post them, but otherwise thank you all for your help.

---

