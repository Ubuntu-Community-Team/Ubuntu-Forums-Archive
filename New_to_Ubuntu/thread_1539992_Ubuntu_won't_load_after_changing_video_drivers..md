---
title: "Ubuntu won't load after changing video drivers."
date: 2010-07-27
forum: New to Ubuntu
---

### Post by danc666 on 2010-07-27
Hey guys, I'm new to Ubuntu and am liking it very much so far apart from this little problem.

Problem:- I installed the open source ati video driver to see if i could get some 3d gaming going, it worked after the initial restart but since then Ubuntu won't load. i see the grub screen and can also use safe mode and the default drivers (failsafe?) and it loads. 3d games don't work tho. (this is not a problem as i don't play much on the computer, have a ps3 for that). 

Full screen video works fine (even with mp3s and the video playing) with the Failsafe driver. so thats all i need. 
The computer gets used for websurfing, mild video production and music playback.

The Video card is a ati card (r300?)
cpu is Intel pentum 4 2.8ghz
ram 1015mb

I suppose my question is can someone help me get this back to the default drivers again? I don't need 3d to work It was way to slow to run Torcs anyway. (the reason i wanted 3d, and i can play that on the windows comp anyway)

I'm new to Ubuntu but should be able to follow and directions from you guys no probs.  
I really like Ubuntu and it will be my main OS when i fix this. 

Thanks for any help.

---

### Post by fatality_uk on 2010-07-27
How did you install the ATI drivers?

---

### Post by Krabby.Linux on 2010-07-27
Boot using the Failsafe first, than uninstall the drivers and try to reinstall them, sometimes this works. Sounds like something went wrong with the installation. Update your system first (Update Manager)

---

### Post by 3rdalbum on 2010-07-27
> **danc666 said:**
> Problem:- I installed the open source ati video driver

I guess this is the disturbing part, because Ubuntu already ships with the open-source ATI video driver, so I'm wondering what you actually installed. What method did you use to install this driver? If you followed a HOWTO, then please give us a link to it.

---

### Post by danc666 on 2010-07-27
The system is up to date. 
I followed this [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) 

The reason i did try to change it was because torcs was tearing when i played it. When i first rebooted torcs had no tearing but only had 0.5fps.

How do i uninstall?

---

### Post by danc666 on 2010-07-28
Well after doing some more searching today. I found a thread on how to uninstall the drivers and reinstall them. It has worked and i can now even play some tracks in torcs (with graphics turned down tho) with a better card it may run better. 

Thanks for taking the time to reply. 

Now i can enjoy Ubuntu :D (til i stuff it up again)

---

### Post by Musifeli on 2012-01-07
After updating video driver for Oneiric 11.10 & rebooted gave me a black screen
followed instructions tried removing driver & reinstalling xorg driver but did not work,

fianlly gave up, I had previously created a bootable usb with 11.10 & reinstalled
and kept doc & music files without deleting my Windows partitions.

That did the trick, then had to do some reinstalling of some extra programs, 
Thanks to that I did not have t reinstall my Thunderbird email programs.
          Jesus is coming soon.

---

