---
title: "SpeedTouch 330 problems after upgrade"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by andytayloruk on 2007-04-20
Hi,

I just upgraded to 7.04, and my SpeedTouch 330 modem is playing up. It worked fine through 6.10, but in 7.04 pages take up to 30 seconds to load or don't load at all, IRC times out, and eventually it just sits and hangs. I don't really understand whats going wrong or how to fix it... What should I do?

Thanks
Andy

---

### Post by mariovega on 2007-04-20
Mine also hangs. But its weird, if im downloading something it keep doing it. But i cant see any new webpages.

---

### Post by andytayloruk on 2007-04-21
Anyone? Its forcing me to use windows now, which is really annoying...

---

### Post by paolo di canio on 2007-04-25
Can you explain how you managed to install the modem ?
I could'nt find any solution :(
It drives me nuts.
I really want to use only ubuntu, but I have this problem.

AGAIN PROBLEMS : this morning, it worked. Now....nothing. I haven't any idea what happend.
Any sugestions. I used the speedtouch_ng package.

---

### Post by tyler_roach on 2007-04-28
I did a fresh install of Feisty, and my speedtouch wouldn't work at all at first. I had to install the libatm package, and it worked like a charm! Maybe you should try installing that package. You can get it at: 
[http://mirrors.kernel.org/ubuntu/pool/main/l/linux-atm/libatm1_2.4.1-17_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux-atm/libatm1_2.4.1-17_i386.deb)
Hope that helps!

---

### Post by Neoranger on 2007-04-29
I'm new to the whole Linux thing, after getting fed up with Windows (ok, I'm lying; that happened a long, long time ago) and I'm having the exact same issue with the Internet. I have a Speedtouch 550, using it via Ethernet instead of USB and it's acting weird. 

At first, it connected fine and I started downloading, but then I couldn't open a single page or download updates. Oddly, though, that other file kept downloading just fine, even if the connection seemed to be down. Now it doesn't connect at all and when it does, it lasts for less than a minute, before hanging up again. 

I'd try that package, but the link above is for i386 architecture; I have x64. Any ideas for that?

---

### Post by StevenHarper on 2007-05-20
> **andytayloruk said:**
> Hi,

I just upgraded to 7.04, and my SpeedTouch 330 modem is playing up. It worked fine through 6.10, but in 7.04 pages take up to 30 seconds to load or don't load at all, IRC times out, and eventually it just sits and hangs. I don't really understand whats going wrong or how to fix it... What should I do?

Thanks
Andy

Hi I have made a DEB package and app that manages Speedtouch 330 modems (v0-4)

You can look at it here [ https://launchpad.net/usb-adsl-modem-manager]("https://launchpad.net/usb-adsl-modem-manager")

And download it here
[http://www.squeezedonkey.com/svn/linux/trunk/releas]("http://www.squeezedonkey.com/svn/linux/trunk/releas")


Hope it helps


Steve

---

### Post by Cortesio on 2007-06-16
Thanks Steve, this really helps. The download link is 404 for me, I assume the link on the viewing page works fine though. I'll try it now and post back. :D

---

### Post by Cortesio on 2007-06-16
Works perfectly. The download link is [http://www.squeezedonkey.com/svn/linux/trunk/releases/usbadslmodemmanager_0.5.2-0ubuntu1_i386.deb](http://www.squeezedonkey.com/svn/linux/trunk/releases/usbadslmodemmanager_0.5.2-0ubuntu1_i386.deb)

BIG thanks to Steve for this piece of software! :KS

---

### Post by StevenHarper on 2007-06-19
> **Cortesio said:**
> Works perfectly. The download link is [http://www.squeezedonkey.com/svn/linux/trunk/releases/usbadslmodemmanager_0.5.2-0ubuntu1_i386.deb](http://www.squeezedonkey.com/svn/linux/trunk/releases/usbadslmodemmanager_0.5.2-0ubuntu1_i386.deb)

BIG thanks to Steve for this piece of software! :KS

Hi , im glad you like it

By the way I have had a tidy up in the releases directory

Best to check here

[http://www.squeezedonkey.com/wiki/linux/index.php?title=Main_Page](http://www.squeezedonkey.com/wiki/linux/index.php?title=Main_Page)

and I will never move it from here

[http://www.squeezedonkey.com/svn/linux/trunk/releases/](http://www.squeezedonkey.com/svn/linux/trunk/releases/)

Steve

---

