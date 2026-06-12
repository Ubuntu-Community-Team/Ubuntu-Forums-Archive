---
title: "INFO @wl_cfg80211_attach : Registered CFG80211 phy"
date: 2013-11-20
forum: Networking &amp; Wireless
---

### Post by adam17 on 2013-11-20
Hi,

I am having a few problems with my Dell Latitude running Ubuntu 12.04 LTS. The battery was not clipped in properly and as a result caused a power failure during boot and seemed to corrupt the ubuntu install. After a fresh install i figured this would all be fine. However now I am having problems with wifi drivers and bios which I did not have previously. On the Dell website there are new bios versions available but of course only for windows. How do I update the bios? 

Thanks

Adam

---

### Post by mörgæs on 2013-11-20
Why do you think that the BIOS is failing?

---

### Post by adam17 on 2013-11-20
To be honest I am not sure what is going on I am just trying to eliminate possible causes. The BIOS is rev A07 and the latest is A09 the real problem is on boot up with the wifi drivers it displays an error message saying the files cannot be found and when installing the drivers in the additional drivers utility it starts and then crashes to a black screen. But I would guess that is a different thread for that.

---

### Post by adam17 on 2013-11-20
I keep trying to install the Wifi Drivers on m,y Dell Latitude D430 running Ubuntu 12.04 LTS but whenever I try It gets about 3/4 of the way and goes to a black screen with loads of numbers similar to blue screen on windows.  can anyone tell me why it is doing this and how I can stop it?

---

### Post by adam17 on 2013-11-20
Hi all,

I am getting this message pop up when booting:

[   14.107965] INFO @wl_cfg80211_attach : Registered CFG80211 phy


Does anyone know how to stop / fix this?

I am running Ubuntu 12.04 LTS on a Dell Latitude D430

Adam

---

### Post by mörgæs on 2013-11-20
No, let's keep this in one thread. If needed I can move /rename it.

You said this was a fresh install. Did you install and apply all updates using wired internet access?

---

### Post by adam17 on 2013-11-21
Hi, 

I re-installed Ubuntu 12.04 and installed all the updates and the Wifi now works. However I am still having the this message appear on boot.


[   14.107965] INFO @wl_cfg80211_attach : Registered CFG80211 phy

What does this mean? and how do I stop it?

Adam

---

### Post by mörgæs on 2013-11-22
I wouldn't worry about it, but let's see what the guys in Networking say.
Thread moved.

---

### Post by Cagrihan on 2014-02-09
Hi,

When booting; I am getting this message, too:

[   14.107965] INFO @wl_cfg80211_attach : Registered CFG80211 phy


  Could you stop this?

I am running Ubuntu 13.10 LTS on a Sony Vaio

---

### Post by mörgæs on 2014-02-10
I don't know how to stop it. 
There's a [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1160322"). Feel free to add yourself to 'affects me' and change the status to 'confirmed'.

---

