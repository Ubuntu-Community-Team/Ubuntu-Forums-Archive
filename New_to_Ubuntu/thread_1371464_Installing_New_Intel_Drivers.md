---
title: "Installing New Intel Drivers"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by mmarton on 2010-01-03
I just installed 9.10 and am impressed overall.

The only real issue is graphics drivers.  I have an old Dell C400 with the Intel graphics chips.  I went to the Intel site but the automated system to detect my product and download updates wouldn't work.  Assuming that I can manually download the updated drivers, how do I install them?

My main issue is that Youtube videos in Firefox won't run very well.

Thanks.

---

### Post by dmaxel on 2010-01-03
Did you try checking if you can download and install any drivers via **System --> Administration --> Hardware Drivers**? You may be able to use proprietary drivers from Intel from that menu.

---

### Post by isaacj87 on 2010-01-03
> **mmarton said:**
> I just installed 9.10 and am impressed overall.

The only real issue is graphics drivers.  I have an old Dell C400 with the Intel graphics chips.  I went to the Intel site but the automated system to detect my product and download updates wouldn't work.  Assuming that I can manually download the updated drivers, how do I install them?

My main issue is that Youtube videos in Firefox won't run very well.

Thanks.

More likely than not, you have integrated graphics. But, let's first figure out what chipset you have. Run this command in terminal so we can have a peek inside:

```
lspci | grep -i intel
```

Copy and paste what you find back here. Personally, I have the i915 chipset that handles flash only moderately well. I tried updating to the beta (Flash 10.1) which is suppose to run better on lower end machines. So, that's an option you can try. If you're not satisfied with that, you can try updating the X.org drivers, which didn't return good results for me.

---

### Post by sandyd on 2010-01-03
> **mmarton said:**
> I just installed 9.10 and am impressed overall.

The only real issue is graphics drivers.  I have an old Dell C400 with the Intel graphics chips.  I went to the Intel site but the automated system to detect my product and download updates wouldn't work.  Assuming that I can manually download the updated drivers, how do I install them?

My main issue is that Youtube videos in Firefox won't run very well.

Thanks.
You have a 830M right?
The intel drivers for that card are installed by default since 2002, it might be a problem with the age of the video card.

what problems are you having?

---

