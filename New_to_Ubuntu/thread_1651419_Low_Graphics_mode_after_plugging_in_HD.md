---
title: "Low Graphics mode after plugging in HD"
date: 2010-12-23
forum: New to Ubuntu
---

### Post by esoteric926 on 2010-12-23
Hello,

I recently installed 10.4 LTS. I had disconnected 2 other HDs to be sure they dont get messed with during installation (Dual booting Win7). Installed drivers for display, rebooted, etc. Then installed XBMC, and messed with a few themes. Nothing major. After powerdown, I plugged in my other two HDs, and turned on. Booting up Ubuntu screen seemed to flicker a bit more than normal (actually, before it never flickered) then I get the dialogue: Low-Graphics mode 

Then I go to command prompt. I am stuck here.

I tried looking through posts, and I have tried everything from dpkg to xserver (Which also, it says it cant find xserver). Is there a recovery something to download or a way to fix my display driver issue?

Any help would be greatly appreciated!

Thanks

---

### Post by theasprint on 2010-12-23
Hi,

You mentioned > Installed drivers for display

Perhaps there is a way you can fix it.

I assume that your "drivers for display" are obtained from Ubuntu under System>Administration>Hardware Drivers?

So depending on your graphics card, I suggest you boot from a LiveCD (that means Try Ubuntu without Changes) and download the driver from your graphics card's website. Put the driver file in your HDD.

Then after booting up, you just run this command:
```
sudo bash <your graphics driver's directory>
```

* To know what graphics card you use, execute:
```
lspci | grep VGA
```

Hope this helps.

---

