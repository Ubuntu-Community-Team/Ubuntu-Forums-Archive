---
title: "[SOLVED] Yet more broadcom issues.  Please help."
date: 2008-12-14
forum: New to Ubuntu
---

### Post by BeastMode on 2008-12-14
OK.  If this isn't my first post, it's darn close, but here goes.

Typically, I just search the forums and come up with my answers, but this one is leading me in different directions.

I, of course, have a broadcom chip that isn't working...but it used to.

I have an HP DV9920US.  It has the Broadcom 4321 AG (shows as a 4328 in Ubuntu).  I used to have Ubuntu 8.04 and had my wireless working via NDISWrapper.  Then, for a spell, I didn't use Ubuntu at all...totally deleted it off my computer.  Decided that I loved the SSH uses for linux, so I decided to put it back on.  I originally went back to Ubuntu 8.10 and the restricted broadcom chip wouldn't work.  It would show my networks, but kept bringing up the network key screen and would never connect.  So, I figured that since I used to have it in Hardy, I'd just install Hardy again...and no dice.  I have the same issues.  It will show the wireless, but keep bringing up the network key and not connecting.

Was I working off of a different kernel before?  I imagine I was...but anyway.  I have read around and tried many of the things I have seen as solutions, including blacklisting the b43xx, doing the wirelessfix thing, but I get nothing.  

I loved Linux before when I got my wireless working, but this is getting pretty frustrating.  I now have a need to work in both a Windows and Linux environment, so dual booting is an absolute must.

If anyone needs me to post outputs of anything, feel free to ask and I will.

Thanks in advance.

---

### Post by BeastMode on 2008-12-15
bump...

anyone, please?

---

### Post by linuxford on 2008-12-15
I could have sworn I was able to connect without broadcasting my ssid, but after while, it was freaking out, and acting strange, asking me to keep on typing in the password, and would not connect. I changed my router back again to broadcasting the ssid, and then it would connect no problem.

---

### Post by Her Ghost on 2008-12-15
hi - I had similar problems with my Broadcom wireless continually bringing up the network key prompt (this was installed through the restricted hardware drivers in 8.10, not ndiswrapper).

I checked that wireless worked by removing security from my router and connecting - this worked fine.

So I re-applied the security - no luck.

I changed the security from WPA2 to WEP and it worked fine.



So if you can ascertain that your device actually works then you might want to give WEP a try and see if that sorts your problem.

---

### Post by iponeverything on 2008-12-15
related issue?

[http://ubuntuforums.org/showthread.php?t=1010650](http://ubuntuforums.org/showthread.php?t=1010650)

---

### Post by BeastMode on 2008-12-15
> **Her Ghost said:**
> hi - I had similar problems with my Broadcom wireless continually bringing up the network key prompt (this was installed through the restricted hardware drivers in 8.10, not ndiswrapper).

I checked that wireless worked by removing security from my router and connecting - this worked fine.

So I re-applied the security - no luck.

I changed the security from WPA2 to WEP and it worked fine.



So if you can ascertain that your device actually works then you might want to give WEP a try and see if that sorts your problem.


This thread can be marked as solved....I don't know how to do it if it's even possible for me to.


You were correct, sir.  Thanks for your response, and I have duly thanked you.  I'd be concerned that I wouldn't be able to connect to someone else's network when I'm out and about, but I only really connect to open wifi spots then, so this will work just fine.

---

### Post by d3vnu11 on 2010-01-21
> **BeastMode said:**
> This thread can be marked as solved....I don't know how to do it if it's even possible for me to.


You were correct, sir.  Thanks for your response, and I have duly thanked you.  I'd be concerned that I wouldn't be able to connect to someone else's network when I'm out and about, but I only really connect to open wifi spots then, so this will work just fine.

I have that same exact laptop just curious what driver you are using with ndiswrapper. And maybe a place to get it. I've been trying to get it to work thinking it was a BCM4328 I'm hoping you have just turned on a light to a solution for myself :) 
Regards,
Kevin

---

