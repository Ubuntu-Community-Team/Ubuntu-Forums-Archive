---
title: "Ubuntu 6.06 on Proliant ML370 G2 server"
date: 2007-02-19
forum: Networking &amp; Wireless
---

### Post by Dutchboy on 2007-02-19
Hi all,

I've recently installed Ubuntu 6.06 on a Compaq Proliant ML370 G2 server, and despite a few hiccups in the beginning, all seems to be working OK now.

We did notice a slow response on the web server when creating pages (we're using a Wiki on that machine). I first dismissed it as initial caching, but when I installed Veritas Backup Exec, I noticed the tremendous throughput of 2Mb/minute. Backing up the 2+Gb will take 16 hours???

I built a practically identical box, using different hardware, but the same software setup. This box reaches about 350Mb/minute easily, and is comparable to a previous Fedora Core 4 server I had running.

This leads me to believe there are some problems with the network driver, or the hard disk driver.

How can I determine which one is the problem, and how can I resolve it..?

---

### Post by Dutchboy on 2007-02-21
I just found [this thread]("http://www.ubuntuforums.org/showthread.php?t=30714") in the forums describing a problem with the Intel Ethernet Pro network card...

Since this would mean editing the GRUB configuration, I won't do it on the production system just yet. But I'll try it out and report back!

---

### Post by krisOlafsson on 2007-02-22
I'm am doing the Exact same setup with the same Computer too.  

and I'm having issues with networking.  the network connection was terribly slow and unresponsive.   here is something intresting, when I pinged the system from a windows pc on the same hub. the response time  veried greatly up to 3000ms to 6ms.  odd. I couldn't VNC into the system at all I would get a single frame and I would move the mouse once and it would lock up VNC.  to load the google start page took about a minute.
  ok so I tried to add "noapic" to grub. no help now it's worse. oddly I now have a black square in the top left hand side of the screen, also the network isn't any slower but it just works spraticaly. I ping it and I would lose 3 of 4.   at times it wouldn't respond at all. 
  
 Ubuntu loads from the CD fine and install nice and fast. boot times is quick too.

 Any Ideas.  a little background to this last week I tried to install openfiler on the system, it would hang on install, unless I added drivers manualy. then it would install fine, but when I would try to configure it through the weblogin the pages would timeout. probably something with that network driver or "NOAPIC"  

 I would love to get some ideas on where to go from here. I'm probably going to format and start all over, but this time I want to be armed with a a little more knowledge into this system.

thanks

---

### Post by Dutchboy on 2007-03-16
Hi kris,

> I would love to get some ideas on where to go from here. I'm probably going to format and start all over, but this time I want to be armed with a a little more knowledge into this system.

I got together last week with our systems engineer, since meddling around with drivers didn't get me anywhere. Replacing e100 by eepro100 (despite the warning in the modprobe.d/blacklist file) lowered throughput, so not an improvement.

I didn't see any options to lock the card as 100Mbps Full Duplex, so I was ready to compile a driver HP was listing on their website. When I checked the port on the hub, it had an orange instead of a green light associated with it. We plugged the network cable in another (better according to our systems engineer) hub, and everything has been working fine since then... I'm getting 50-60 times higher throughput.

We locked the port on the hub to 100Mbps/Full Duplex, which is what probably did the trick. If you look at the download page at HP, it shows some tools to lock the driver in the same mode, but since this worked, I didn't bother installing them...

If you're interested in the official HP drivers, drop me a line and I'll post the web page I found them on.

Good luck!

---

