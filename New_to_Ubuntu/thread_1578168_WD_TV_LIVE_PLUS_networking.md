---
title: "WD TV LIVE PLUS networking"
date: 2010-09-20
forum: New to Ubuntu
---

### Post by completeidiot on 2010-09-20
I'm trying to set up networking with my new media player....and as the name says, I'm an Ubuntu idiot.
How do I find my:
Subnet mask 
Gateway 
Dns

Thanks

---

### Post by NoBugs! on 2010-09-20
Right click the network icon, click "Connection information".

---

### Post by completeidiot on 2010-09-20
Wow.
This marks a new low in captain obvious.
Thanks
One shot one kill

---

### Post by completeidiot on 2010-09-20
Actually.... I thought that had it all, but it doesn't seem to show my "Gateway"... ?

---

### Post by k33bz on 2010-09-20
open up your terminal

```
ifconfig
```

---

### Post by completeidiot on 2010-09-20
So i'm working in Samba trying to get this going...I've selected the folder that I want to share. But I'm not sure what to put for authentication mode etc

---

### Post by completeidiot on 2010-09-20
thus far the media player has not recognized a network at all

---

### Post by colin.p on 2010-09-20
It is tricky, at least that is what I found. I managed to get the WDTV to see the shared folders on my 10.04 desktop, but not my 10.04 laptop.
Everything is the same, but obviously the Live doesn't like something.
Networking on the Live is problematic at best, just check out their forums.
It seemed to work ok connecting to my wifes Vista laptop, at least the couple of times I tried, but not to another win 7 laptop (you think it's hard in ubuntu, wait till you try 7).
I said screw it and just use the Live as a media server and connect my drives to it. Then I can access the files from any computer and access it from any computer as well.

---

### Post by completeidiot on 2010-09-20
That sucks...hopefully someone will figure it out soon.

I can't even stream netflix at this point, because it can't locate my wifi. even though my phone, ubuntu netbook and macbook don't have any problems. don't get it.

---

### Post by colin.p on 2010-09-21
Mine is hooked up wired to my router and connects to the internet just fine.
I have the live version, not the plus, so I don't have netflix, but it connects just fine to youtube.
You can get it to network to shares, it's just a lot of hoops you have to jump through. It may be better for you to check the WD forums or the WTDV forums.
There are alot smarter people than me there that could give you a heads up on networking the live or plus.

---

### Post by nosebreaker on 2012-02-02
In case anyone else comes across this, the fix for me was to start nmbd and enable "Samba Client" in the firewall.
/sbin/service nmb start

I'm not 100% sure if I needed to enable Samba Client in the firewall or not but it works so I'm leaving it on.

---

### Post by 3rdalbum on 2012-02-03
> **nosebreaker said:**
> In case anyone else comes across this, the fix for me was to start nmbd and enable "Samba Client" in the firewall.
/sbin/service nmb start

I'm not 100% sure if I needed to enable Samba Client in the firewall or not but it works so I'm leaving it on.

Well yeah, your WD TV won't be able to communicate with the Samba server if all its communication is getting dropped by the firewall...

If you're behind a modem/router you probably don't even need a personal firewall on the computer, as you'd already be protected by the one in the router.

---

