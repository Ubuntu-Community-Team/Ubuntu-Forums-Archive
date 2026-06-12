---
title: "compiling kernel for intel 4965"
date: 2008-02-18
forum: Networking &amp; Wireless
---

### Post by goodrench on 2008-02-18
I have been trying to compile the latest kernel for my laptop but I am getting errors during the compilation.
I had it working acouple of times but had no sound.
now when I try it I can get the sound working but not the wireless card.
Does anyone have any ideas?


this is the error
```

make[6]: *** [drivers/net/wireless/iwlwifi/iwl3945-base.o] Error 1
make[5]: *** [drivers/net/wireless/iwlwifi] Error 2
make[4]: *** [drivers/net/wireless] Error 2
make[3]: *** [drivers/net] Error 2
make[2]: *** [drivers] Error 2
make[2]: Leaving directory `/usr/src/linux-2.6.24'
make[1]: *** [debian/stamp-build-kernel] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.24'
make: *** [stamp-buildpackage] Error 2
drew@laptop:/usr/src/linux$ 

```

---

### Post by glug101 on 2008-02-19
Sorry I don't have time for a more in depth response, but I thought I could at least cover the obvious/most missed.  

If you haven't already, try running this command:
```
sudo apt-get build-dep linux-kernel-devel
```

Worked for me.  Good luck!

P.S. If that doesn't work, post your config file here and somebody else with more time might be able to help.

---

### Post by goodrench on 2008-02-19
Thank you.
I will try it tonight.

---

### Post by goodrench on 2008-02-19
Well, I tried it and it did not work.
I have the box checked for the intel 4965 support in the xconfig page.
I don't know what I am doing wrong.
Are the checked boxes in the xconfig page the ones that are currently enabled?
If they are then maybe I should not be checking that box.
I do not get the error that I had in my first post now.
I can't remember how I got it to work the first time.
Should I uncheck the box for the 3945 chipset?

---

### Post by goodrench on 2008-02-22
I still can't seem to make it work.
Still trying.

---

### Post by davidb_ on 2008-02-23
[http://jkyamog.blogspot.com/2007/12/linux-install-on-hp-6910p-using-ubuntu.html](http://jkyamog.blogspot.com/2007/12/linux-install-on-hp-6910p-using-ubuntu.html)

You might read through that. He mentions making a package for that wireless card.

---

### Post by goodrench on 2008-02-23
I was able to figure it out tonight.
I had to copy firmware files from 2.6.22-14 to 2.6.24.2


```
sudo cp -r /lib/firmware/2.6.22.14-generic /lib/firmware/2.6.24.2

```

After that I recompiled the kernel again and upon reboot wireless worked flawlessly.
Although my webcam does not work and neither does virtualbox.

---

