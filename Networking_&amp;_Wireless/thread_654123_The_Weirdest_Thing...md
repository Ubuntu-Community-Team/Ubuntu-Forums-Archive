---
title: "The Weirdest Thing.."
date: 2007-12-30
forum: Networking &amp; Wireless
---

### Post by DariusJD on 2007-12-30
Okay. I am running Ubuntu 7.10.
I have a cable modem that allows both Ethernet and USB connections. I often the USB connection and it works perfectly. 

However, when I use my USB Ethernet Adapter (I don't have a Ethernet port) to hook up my router, Ubuntu acts strange. It recognizes the connection. It allows me to ping websites, I can access Google.com; perform searches, I can access Belkin.com (router manufacturer), I can even access my network (e.g. 192.168.2.2). I can also access my router's settings. This tells me that Ubuntu IS getting a connection and is allowing me to access Google, Belkin and my LOCALHOST, but is restricting access...The little icon at the top also says I am connected..

People can connect to the router and access the internet just fine, but for some reason my wired, ethernet connection won't work.

This is really strange and I hope I worded it correctly so that it isn't too confusing.
Someone help me out!

---

### Post by DariusJD on 2007-12-30
Also, I recently migrated to Linux and everything worked fine on Windows...
Could WINE solve this? ...

---

### Post by Furat on 2007-12-30
May be the problem with firefox not Ubuntu, when u pig websites did u usde there names or IP , can u install programs using synaptic ? if u can try to install opera

---

### Post by jken146 on 2007-12-30
What exactly doesn't work?  If you can connect to your router and to the internet then what do you mean by "but is restricting access..."?

---

### Post by DariusJD on 2007-12-30
> **jken146 said:**
> What exactly doesn't work?  If you can connect to your router and to the internet then what do you mean by "but is restricting access..."?

You see, it's strange..

I can ping websites. (I haven't tried IPs.)
I cannot download from Synaptic
I can access Google.com, Belkin.com (My router's manufacturer) and I can access [http://localhost/](http://localhost/)  However, other websites will not load.
I can perform searches in Google also, but when I try to click on a link, I get a 404.
However, when I disconnect the router and use USB, I can access any website.

..understand now?

---

### Post by tdrusk on 2007-12-30
go to system>administration>software sources and enable the ubuntu repositories. See if after you reload that you can get updates and such.

---

### Post by DariusJD on 2007-12-31
That didn't work...

---

### Post by arsenic23 on 2007-12-31
What ISP do you use?
Do you know how they authenticate?

Some cable companies will block you from visiting almost anything untill your authenticating with them properly.  This would cause the same behavior your describing, where you can ping everything but not receive anything else.

I'm not 100% on how this works, but I've seen it several times now.

---

### Post by DariusJD on 2007-12-31
I have Comcast.
But before I used Ubuntu, I was using Windows and it works fine. Like now, I am using USB and it works fine.

---

