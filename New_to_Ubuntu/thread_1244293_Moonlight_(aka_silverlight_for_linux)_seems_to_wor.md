---
title: "Moonlight (aka silverlight for linux) seems to work much better now."
date: 2009-08-19
forum: New to Ubuntu
---

### Post by philinux on 2009-08-19
Just got the addon updated to 1.99.1.1

---

### Post by Bartender on 2009-08-19
Can you share a few more details?  Some friends have cable broadband, a Netflix subscription, and a Linux PC I built for their two boys.  

Right now the kids commandeer the parents' Windows PC when they want to watch Netflix stuff.  I told them I'd let them know ASAP if anything changed.

Thanks!

---

### Post by philinux on 2009-08-19
You get the moonlight plugin here.

[http://go-mono.com/moonlight-preview/](http://go-mono.com/moonlight-preview/)

I use it to watch itv.com catchup now.

---

### Post by Peterfc on 2009-08-19
Thanks Philinux

Peter

---

### Post by directhex on 2009-08-19
> **philinux said:**
> You get the moonlight plugin here.

[http://go-mono.com/moonlight-preview/](http://go-mono.com/moonlight-preview/)

I use it to watch itv.com catchup now.

[http://go-mono.com/moonlight-beta/](http://go-mono.com/moonlight-beta/) - your URL is for the pre-beta test builds

And you're welcome for ITV Catchup. Whilst someone else did all the work for it (Rolf Kvinge), it's IP-locked to UK-only people, so I helped Rolf get a proxy into the UK to work on it - see [http://www2.apebox.org/wordpress/rants/156/](http://www2.apebox.org/wordpress/rants/156/)

Sadly 1.99.1 regressed ITV support, so I poked upstream viciously into the ribs, which is why 1.99.1.1 exists (it has a newer version of System.ServiceModel.dll than 1.99.1 did, explicitly to fix ITV)

---

### Post by philinux on 2009-08-19
Nice one.

---

### Post by Bartender on 2009-08-20
I found that link the other day, but was worried about the "supported" link.  It only mentions Ubuntu 8.04.  You're saying it appears to be working on Jaunty as well?

---

### Post by philinux on 2009-08-20
Not appears, is.

Full screen is awful but with compiz zoom it's fine.

---

### Post by AprilWriter on 2009-08-24
Does it allow you to use the instant browse feature on Netflix? 

April

---

### Post by LowSky on 2009-08-24
All of the media is in WMV with DRM encoding, in otherwords, no it wont work regarless of which version of Moonlight you have. It's like trying to listen to old itunes DRM enable music. It simply a DRM issue

---

### Post by amandaandsteve on 2009-09-01
im new to ubuntu and have jaunty but even though i have loaded the latest moonlight i still cant view itv. it says i need silverlight but when i try to load it i am told i am running the latest moonlight.
any ideas
thanks

---

### Post by directhex on 2009-09-02
> **amandaandsteve said:**
> im new to ubuntu and have jaunty but even though i have loaded the latest moonlight i still cant view itv. it says i need silverlight but when i try to load it i am told i am running the latest moonlight.
any ideas
thanks

You need to use a 2.0 beta, not the package.

[http://go-mono.com/moonlight-beta](http://go-mono.com/moonlight-beta) definitely works - but you need to remove any 1.0 you have installed first, otherwise your browser will crash

---

### Post by philinux on 2009-09-02
My plugin auto upgraded itself to 1.99.2 according to a right click on itv.

---

