---
title: "Wireless r818x hard lock on Gutsy"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by mpmc on 2007-10-19
Hi everyone. 

I installed Gutsy today. ran the live CD everything running nice, So I decided to install it.

Once installed the first thing I did was attempt to setup my D-link DWL 510 wireless card. Ubuntu had already guessed that the module I needed was R818x. It asked me for a passphrase, Or in my case a hex to connect to the network.. I entered everything.. And BAM hard lock.

I rebooted & attempted to load up again.. Instead I was greeted a quick flash of white.  Kinda like a Neon light on it's last legs. Rebooted once more in recovery mode & from what I could see the kernel had, Had a Panic attack. :(

The first few lines it meantioned something about WEP.

I have no idea how to fix this without reinstalling & using ndiswrapper.

Help please!:shock:

---

### Post by MrShifty on 2007-11-26
Using ndiswrapper is the way to go. Just make sure to add r818x to 
```
/etc/modprobe.d/blacklist
```

---

### Post by mpmc on 2007-11-26
> **MrShifty said:**
> Using ndiswrapper is the way to go. Just make sure to add r818x to 
```
/etc/modprobe.d/blacklist
```

I manage to get it working with NDISWRAPPER, :)

---

