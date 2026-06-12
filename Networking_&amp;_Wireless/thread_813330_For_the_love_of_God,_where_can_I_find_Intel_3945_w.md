---
title: "For the love of God, where can I find Intel 3945 windows drivers for ndiswrapper???"
date: 2008-05-30
forum: Networking &amp; Wireless
---

### Post by espartano on 2008-05-30
Please, for the love of god, I've been trying and trying but I just can't find where those drivers can be downloaded. I'm using Vista, so my drivers won't work with ndiswrapper, and the downloads that I have found so far are all .MSI files, and they won't execute in my notebook because they're for XP (an error message appears!) So I can't install them and I can't use them with ndiswrapper!!!

Im going crazy because of this wireless in Ubuntu, that connects but has no throughput AT ALL...it just won't send or receive any data...

Ndiswrapper is my last option, or I'll be stuck with this damn vista =(

Thanks guys!

---

### Post by travislucas on 2008-05-30
> **espartano said:**
> Im going crazy because of this wireless in Ubuntu,

I did a quick search at Intel's website and it seems like i've found what you need, I unzip the file, so it would seem like once downloaded it going to be one of two .exe files you going to need to extract to find the bcml5.inf file for Ndiswrapper, but this should get you started!

[http://downloadcenter.intel.com/confirm.aspx?httpDown=http://downloadmirror.intel.com/15798/eng/11.5.1.2_VT_DRIVERS.zip&agr=N&ProductID=2259&DwnldId=15798&strOSs=151&OSFullName=Windows%20Vista*%20Starter,%2032-bit%20version&lang=eng](http://downloadcenter.intel.com/confirm.aspx?httpDown=http://downloadmirror.intel.com/15798/eng/11.5.1.2_VT_DRIVERS.zip&agr=N&ProductID=2259&DwnldId=15798&strOSs=151&OSFullName=Windows%20Vista*%20Starter,%2032-bit%20version&lang=eng)

---

### Post by Mach1US on 2008-05-30
There is no reason why XP drivers wouldn't work with ndiswrapper , additionally i thing there more than one variation of drivers for this card family available natively in Ubuntu , make sure the kernel assigned the specific  one for your card as that is often a cause of networking problem.

---

### Post by hardyn on 2008-05-30
is there no native driver for 3945?

---

### Post by chili555 on 2008-05-30
> you going to need to extract to find the bcml5.inf file for Ndiswrapper, but this should get you started!Not likely. I think you need NETw4v32.inf. A typo, perhaps?> is there not a native driver for 3945? Indeed. If espartano is having trouble, perhaps we can help.

---

