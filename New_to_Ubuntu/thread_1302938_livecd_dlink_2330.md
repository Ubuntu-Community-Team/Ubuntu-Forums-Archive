---
title: "livecd dlink 2330"
date: 2009-10-27
forum: New to Ubuntu
---

### Post by Sonnyh on 2009-10-27
Hi,

I'm using a liveCD with Ubuntu 9 and my dlink wireless 2330 doesn't work.  Can I get it to work if I just run the livecd or do I have to install the program on the HD?  If I can, how do I go about it?  IBM laptop with winXP.

Thanks,

---

### Post by LunaticHiatus on 2009-10-27
Are you using Karmic or Jaunty? It might be best just to wait a couple days for karmic to come out. The upgrade will be covering compatibility issues with a lot of things like wireless drivers.

Worst comes to worst, you can always install windows wireless drivers, but someone else can probably help you with that better then i can.

---

### Post by Sonnyh on 2009-10-27
I'm using 9.04 version.

Thanks,

---

### Post by LunaticHiatus on 2009-10-27
Yeah, might want to wait for karmic and upgrade. Generally, windows drivers tend to be kinda poop so you dont want to use them if you don't have to. If you do have to, you have to use Ndiswrapper the last time I checked. 

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

but Im not really up and up on the situation with Ndiswrapper and windows wireless drivers. so, like I said, someone else would probably be more helpful.

---

### Post by matthewbpt on 2009-10-27
Before we can figure out why your card doesn't work we need to know exactly what wireless card you have. If you boot the live cd and go to Applications > Accesories > Terminal and type in,

```
lspci
```

and paste the output here we can find out (or if you already know what wireless card it uses...)

---

### Post by Sonnyh on 2009-10-28
Thanks for your help.  Got it going by installing Ndiswrapper, etc. although to be honest I'm not sure how it worked.  I think that the files where already available on the live cd disk but I didn't know how to get them.

Sonny

---

