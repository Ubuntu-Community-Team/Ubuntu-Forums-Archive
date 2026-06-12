---
title: "Big Uh-oh!"
date: 2009-10-24
forum: New to Ubuntu
---

### Post by donaldshelton on 2009-10-24
I found out I needed to download and install Java in order to play Pogo.com games.

I went to synaptic and found the packages I needed.  I downloaded them, but as the installation process started, the computer inexplicably turned off.

Now when I try to redownload and install, I get E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Could someone please reply and give me the EXACT words I need to type into the terminal?????

Thanks

Don

---

### Post by Arlanthir on 2009-10-24
> **donaldshelton said:**
> I found out I needed to download and install Java in order to play Pogo.com games.

I went to synaptic and found the packages I needed.  I downloaded them, but as the installation process started, the computer inexplicably turned off.

Now when I try to redownload and install, I get E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Could someone please reply and give me the EXACT words I need to type into the terminal?????

Thanks

Don

Have you tried

sudo dpkg --configure -a

?

---

### Post by donaldshelton on 2009-10-24
Big thanks to you!!!

Don

---

### Post by RJARRRPCGP on 2009-10-24
> **donaldshelton said:**
> I found out I needed to download and install Java in order to play Pogo.com games.

I went to synaptic and found the packages I needed.  I downloaded them, but as the installation process started, the computer inexplicably turned off.


Sounds like you need to check the heatsink. Sounds like your processor hit TJMax. (thermal junction max, an Intel spec for the critical temp point.)

---

