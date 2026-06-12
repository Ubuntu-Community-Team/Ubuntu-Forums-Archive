---
title: "fresh install, update, laptop freezes.....getting very discouraged"
date: 2011-02-19
forum: New to Ubuntu
---

### Post by adduds on 2011-02-19
fresh install of ubuntu 10.10 works fine absolutely great until i do the main update (304mb)

install updates (required system reboot) and now it will not load the os.....all i hear is the install music then freezes 

i even tried (or rather had to) re-install then installed the 304mb of updates same thing happen and i don't know what to do I can't just sit there and install one update at a time until i figure out which one is

anyone know why this is happening?

laptop is an acer aspire 5742-7784 

specs

> - Intel Core i5-460 @ 2.53GHz
- 4GB DDR3 RAM
- 320GB Hard Drive
- DVDRW
- 15.6" HD Widescreen
- VGA & HDMI Output
- 2-in-1 Card Reader
- Acer Nplify 802.11b/g/n/ Wireless
- Windows 7 Home Premium 64-bit


---

### Post by Dutch70 on 2011-02-19
It's likely a kernel update causing it to freeze. You may be able to reboot & log into the old kernel after the update. Until you find out how to fix it.

Edit: Now I see that you probably know that.

---

### Post by waynefoutz on 2011-02-19
+1 on the kernel. Mine did this as well. Boot into the old kernel. then  use this guide to lock your kernel to keep it from upgrading again.

[http://www.ubuntugeek.com/how-to-lock-package-versions-from-synaptic-package-manager.html]("http://www.ubuntugeek.com/how-to-lock-package-versions-from-synaptic-package-manager.html")


the files you'll want to lock in synaptic  are the linux-headers-2.6.xx.xx, linux-headers-2.6.xx.xx-generic, and linux-image-2.6.xx.xx the x's are the version you booted into. mark the ones that upgraded earlier for removal, and hit apply.

---

### Post by adduds on 2011-02-19
the files you'll want to lock in synaptic are the linux-headers-2.6.xx.xx, linux-headers-2.6.xx.xx-generic, and linux-image-2.6.xx.xx the x's are the version you booted into. mark the ones that upgraded earlier for removal, and hit apply. 

will this effect anything in the future for updates and compiling code and stuff??

all i did was re-install the os (for the 3rd time) followed ur instructions on locking the kernal

how persay can you log into an old kernal?

---

### Post by Dutch70 on 2011-02-19
> **will this effect anything in the future for updates and compiling code and stuff??**

all i did was re-install the os (for the 3rd time) followed ur instructions on locking the kernal

how persay can you log into an old kernal?

Sorry, I can't answer the part of your question that's in **bold**.

as for the rest...
You would have to have an old kernel to log into. New kernels come out fairly often. Sometimes  when you download & install Ubuntu, 
there has already been a new kernel since your download site was updated, so, when you update you may get a new kernel version. It will show up on your boot menu...

eg... 
Ubuntu, with Linux 2.6.35-25 generic
Ubuntu, with Linux 2.6.35-25 generic (recovery mode)

when you get a kernel update, your boot menu would then look something like this...

Ubuntu, with Linux 2.6.35-**26** generic
Ubuntu, with Linux 2.6.35-**26** generic (recovery mode)
Ubuntu, with Linux 2.6.35-**25** generic
Ubuntu, with Linux 2.6.35-**25** generic (recovery mode)

If you're getting kernel updates, you always want to keep 2 (like above)
so that if there is a problem, you can log into the old kernel, which would be 2.6.35-25 (not recovery mode)

At least that's my understanding, but I've never had a problem that I know of from a kernel update... until maybe now...lol. not sure yet.
but that may be b/c I have Ubuntu heavily modified  & Kubuntu installed in  it.

Best Regards

---

### Post by waynefoutz on 2011-02-19
I have my kernel locked, several new ones have come out since the one that I'm using in 10.04. Like you, updating caused my system to freeze, so I stick with the one that works. I still get all the security updates and application updates as i always did, it just skips any kernel updates. No harm what soever, and I've been running like this for months now.

---

### Post by adduds on 2011-02-19
> **Dutch70 said:**
> 
when you get a kernel update, your boot menu would then look something like this...

Ubuntu, with Linux 2.6.35-**26** generic
Ubuntu, with Linux 2.6.35-**26** generic (recovery mode)
Ubuntu, with Linux 2.6.35-**25** generic
Ubuntu, with Linux 2.6.35-**25** generic (recovery mode)

If you're getting kernel updates, you always want to keep 2 (like above)
so that if there is a problem, you can log into the old kernel, which would be 2.6.35-25 (not recovery mode)

At least that's my understanding, but I've never had a problem that I know of from a kernel update... until maybe now...lol. not sure yet.
but that may be b/c I have Ubuntu heavily modified  & Kubuntu installed in  it.

Best Regards

First: omg ty very much for the help

Not sure why but after i did my system update i did not get a boot option menu it just autobooted into the os as usual?....

I have seen then menu before i know what you're talking about but only on my dual boot system just wonderin' after my update i didn't get a boot menu so i just re-installed how would i get the menu if it happened again?

---

### Post by Dutch70 on 2011-02-19
> **adduds said:**
> First: omg ty very much for the help

Not sure why but after i did my system update i did not get a boot option menu it just autobooted into the os as usual?....

I have seen then menu before i know what you're talking about but only on my dual boot system just wonderin' after my update i didn't get a boot menu so i just re-installed how would i get the menu if it happened again?

I've never ran anything but dual boot, but at some point during the boot loading process, you should get a menu to choose from. How else would you choose recovery mode?

---

### Post by adduds on 2011-02-21
> **Dutch70 said:**
> I've never ran anything but dual boot, but at some point during the boot loading process, you should get a menu to choose from. How else would you choose recovery mode?

Just so ya know :)

> 
GRUB 2's default menu will look familiar to GRUB users but there are a great number of differences beneath the surface.

    * On a new install of Ubuntu 9.10 or 10.04 with no other installed operating system, GRUB 2 will boot directly to the login prompt or Desktop. No menu will be displayed, even if multiple kernels are installed and later.

    * Hold down SHIFT to display the menu during boot (formerly ESC in GRUB legacy). 

for more info on configuring grub2 for the timer, default boot operation etc... check this out super gnarly documentation.... i did lots of tweaking to grub deuce after i read through this :) :)

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

cheers,
ad.

---

### Post by Dutch70 on 2011-02-21
> **adduds said:**
> Just so ya know :)

for more info on configuring grub2 for the timer, default boot operation etc... check this out super gnarly documentation.... i did lots of tweaking to grub deuce after i read through this :) :)

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

cheers,
ad.

Nice find adduds :)
So, does that mean you got everything worked out? 

and btw, what kind of graphics card do you have & did you have compiz running when it would freeze?

---

### Post by adduds on 2011-02-22
> Nice find adduds
So, does that mean you got everything worked out? 

everything is worked out, locked my kernal for updates :) and they should be fine now!!! :)


like on boot it wouldn't even show a login screen once it got to the point of loading the gdm it'd freeze like literally frozen out of my comp couldn't get into it at all! and i didn't know about that holding down shift to load grub boot options to boot into the old kernal so i ended up re-re-installing ubuntu lol followed waynefoutz on this thread to lock and keep my current kernal

> the files you'll want to lock in synaptic are the linux-headers-2.6.xx.xx, linux-headers-2.6.xx.xx-generic, and linux-image-2.6.xx.xx the x's are the version you booted into. mark the ones that upgraded earlier for removal, and hit apply. 

.....and no problems now!!! :)

onboard video card on an asus laptop (not sure not my computer :P) my parents, no compiz either...

although i do have an analog sound problem noticed only one speaker on the laptop plays???? if ya want i've threaded it....no responses yet though...i know they both work lol its brand new... so i dunno...  thanks again mate!

[http://ubuntuforums.org/showthread.php?t=1690873](http://ubuntuforums.org/showthread.php?t=1690873)

---

