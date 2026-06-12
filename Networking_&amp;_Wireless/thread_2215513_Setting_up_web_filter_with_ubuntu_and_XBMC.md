---
title: "Setting up web filter with ubuntu and XBMC"
date: 2014-04-07
forum: Networking &amp; Wireless
---

### Post by DarkRanger on 2014-04-07
I am new to Ubuntu and Linux in general. I have worked on a CentOS server before, but just the basic web server stuff.

I am in the process of setting up an HTPC running Ubuntu with XBMC. However, I also want the HTPC to serve as a web stats machine (for 2 users and whatever wireless devices might join the network). Basically, I want logs on which device is pulling data. It doesn't have to show session times and whatever, it just needs to show device x accessed this site, and pulled this amount of data. Or it used this protocol (HTTP, FTP, Torrent) and pulled this amount of data.

There are a few questions I have regarding this, and I would like if someone can help me out, or just kick me in the right direction.

1. What would be the best network monitor to run on ubuntu? I want something that can pull logs, and send them via email to me automatically.
2. How would I set this up on the HTPC?
3. Will it hamper performance on the HTPC? Logic dictates and suggests no, but I don't really know what kind of resource hog this might be. It's a Core2Duo machine with 3 or 4 Gigs ram.

I am sure there will be more questions as I receive answers, but I feel this is a good place to start.

Thanks!

---

### Post by TheFu on 2014-04-07
If this machine is NOT your router too, then how will it get the data? Does your router have remote logging facilities?

Any added processing will affect performance to some level.
Any added disk I/O will affect performance to some level.
With 3 other machines on the network, I wouldn't worry, but with 200 then I would.

Do not let the XBMC machine use wifi - it needs to be wired ethernet for many reasons.

---

### Post by DarkRanger on 2014-04-07
Yeah it will be wired ethernet as it is located right next to the router.

Can't I set it up to be the DHCP server? so that internet traffic passes through it to the internet? I don't know much about this, so I need to know if this is possible and viable, and how I can do it?

---

### Post by TheFu on 2014-04-07
Being a DHCP server doesn't make traffic go through it.

You need for the router to report any traffic somewhere that understands those reports and can generate reports and graphs.
There are routers that can do this or you can load an aftermarker firmware onto many of them - tomato, dd-wrt, openwrt which might do enough of what you want - it all depends on your specific router model.

Or you can use pfsense - like many universities do - it can do almost anything the huge routers do for $50K-$2M+.

Be careful going with any all-in-one solution like Ebox/Zentyal or ipcop or ... there must be 50 of them. Just because you can put all that stuff onto a single box, doesn't mean it is a good idea or secure.  Routers really, really, need to be single purpose machines, IMHO.  I've deployed a tiny pfSense router for clients using low power Alix hardware. After configuration, we don't need to touch it for years. Something like 4W of power used.  A dual-core Atom (or AMD close) can be had for $100 that uses a little more power (16W) and has much greater processing/capability. The only concern is whether pfSense will like any specific hardware - I tried to put it onto a Via C7 CPU machine here (12W) that was a media center in 2004, but after install the BSD didn't want to boot, didn't recognize the SATA controller.

OTOH, my requirements are probably greater than yours having a /29 network and needing to forward multiple public IPs internally.
**[Tomato]("http://www.polarcloud.com/tomato")** is the most user friendly of those choices.  

For all the aftermarket firmwares, **carefully** check that your specific model, version, release, is compatible with any specific firmware before moving forward. **You've been warned.**

This [article]("http://lifehacker.com/344765/turn-your-60-router-into-a-user-friendly-super-router-with-tomato") is a little dated, but the features are a good list.  Aftermarket firmwares tend to be much more secure than the commercial ones which almost every vendor has either inserted back doors or failed to properly secure.

---

### Post by SeijiSensei on 2014-04-07
Are all the devices connecting from behind your firewall, or will some be using the public Internet?  If the latter, things get complicated, but if they're all on your own network, there are a variety of solutions you can try.

I'd start by running **[ntop]("http://www.ntop.org/")** on the server.  It will produce nice traffic reports, though you'll need to use a browser to see them rather than email.  It's in the Ubuntu repositories.

By the way, as a "term of art," the phrase "web filter" usually means some system for controlling the browsing behavior of web users via something like the Squid proxy.  I wondered how you were intending to use XBMC for this when I read the subject line.

---

