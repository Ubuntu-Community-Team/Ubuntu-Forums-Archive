---
title: "[ubuntu] ASUS Zenbook ux303 - latest iwlwifi for 3.16?"
date: 2015-04-11
forum: Networking &amp; Wireless
---

### Post by c51 on 2015-04-11
> **Pilot6 said:**
> I do not know which wifi driver you have. You can make a topic in Networking and send me a link. I will look at it.
My false, sorry; I confused this topic with another more [specific one]("http://ubuntuforums.org/showthread.php?t=2243162&p=13226891#post13226891"). There (post #83), I read about the firmware. Current fw version with 3.16 kernel is v9.

I also found a newer version, v12 (iwlwifi-7260-12.ucode), which does not pass iwlwifi's API version check as of with kernel 3.16.x.

Maybe v10/v12 would be a nice improvement in terms of performance and stability? ("[We also release release a re-spin of iwlwifi-XXXX-10.ucode that includes a bug fix that has a major impact on users]("http://comments.gmane.org/gmane.linux.kernel.wireless.general/134116")").

Also fw v10 applies to 3.17 ([https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=769633](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=769633)), whereas v12 is targeted to 3.19+ (also see here [https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi](https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi)).

---

### Post by jeremy31 on 2015-04-11
If you want to use the iwlwifi-7260-10.ucode, the easiest way would be to install the 3.19 backports
```
[COLOR=#111111][FONT=Consolas]sudo apt-get install build-essential linux-headers-generic
[/FONT][/COLOR]wget -N -t 5 -T 10 [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.19-rc1/backports-3.19-rc1-1.tar.xz](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.19-rc1/backports-3.19-rc1-1.tar.xz)
tar -xf backports-3.19-rc1-1.tar.xz
cd ~/backports-3.19-rc1-1
make defconfig-iwlwifi
make
sudo make install
```

Reboot and if you have iwlwifi-7260-10.ucode in /lib/firmware it should load

---

### Post by c51 on 2015-04-11
> **jeremy31 said:**
> If you want to use the iwlwifi-7260-10.ucode, the easiest way would be to install the 3.19 backports
```
[COLOR=#111111][FONT=Consolas]sudo apt-get install build-essential linux-headers-generic
[/FONT][/COLOR]wget -N -t 5 -T 10 [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.19-rc1/backports-3.19-rc1-1.tar.xz](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.19-rc1/backports-3.19-rc1-1.tar.xz)
tar -xf backports-3.19-rc1-1.tar.xz
cd ~/backports-3.19-rc1-1
make defconfig-iwlwifi
make
sudo make install
```

Reboot and if you have iwlwifi-7260-10.ucode in /lib/firmware it should load
Mh, yes, thanks. Already considered that as an option but I don't want to give up focaltech support , which went into 4.0-rc kernel.

Pilot6 provided a custom kernel with touchscreen and focaltech touchpad supported, which I really appreciate very much. So my
question is if it would be possible to update iwlwifi driver as well for the 3.16 kernel (or maybe add focaltech for 3.19 if that would
be easier to accomplish).

Thanks for you help!
Regards,
c51

---

### Post by jeremy31 on 2015-04-11
What kernel are you using ```
uname -a
```

I know Pilot6 has a github site, so I might have to look at it to see what ucode support is in the iwlwifi

---

### Post by c51 on 2015-04-11
```
Linux z51 3.16.0-34-generic #45 SMP Tue Mar 24 09:40:38 MSK 2015 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by jeremy31 on 2015-04-11
I don't think the wifi backports will mess anything up with the rest of the kernel

---

### Post by c51 on 2015-04-11
Thanks jeremy31,

that was what I was afraid of at first. but I dont know ..  as an alternative maybe a 3.19.x kernel with focaltech AND fw v10 for iwlwifi might be the easier way to go?

Sadly I don't have the time to dive into the problems right now. I always used to have 2 machines to ensure my productivity; rather quickly this amount dropped to zero due some faulty hardware and got replaced by a zenbook which covered all my needs in term of hardware... but I did not take into account the possible lack of hardware support. 

I do have 14.10 and 15.04 on my "checkout-list". But for now I need like a stable and nicely working system :-(

---

### Post by jeremy31 on 2015-04-11
It would be possible to download the source code and make the change to allow it to load a newer firmware version, or you could possibly rename iwlwifi-7260-10.ucode(or even version 12) to iwlwifi-7260-9.ucode and see if the iwlwifi module even notices

---

### Post by c51 on 2015-04-11
That's what I already tried or... to be more specific - to "reproduce" what's to be expected: [have a look]("https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=769633#18") and you will see what the aforementioned API check was that I referred to. Also tried with v12 fw...

---

### Post by chili555 on 2015-04-11
Backports, that Jeremy recommends, is *only* the iwlwifi driver and it's associated suite; cfg80211, mac80211, et al. You can install it in three minutes and reboot to see if it loads the -12 firmware. If not, sudo make uninstall it. You have little to lose.

---

### Post by c51 on 2015-04-11
I'm pretty sure it will load; the point is that I would like to have both, wifi AND my touchpad working correctly; still the focus is on my touchpad - currently I have a 20m LAN cable attached to my laptop curling through my office and following me wherever I go if I can't use one of my 3 LAN cables around here... it's annoying as hell, as every cable is a possible killer for a laptop, as there are lways people around who are not that respectful... 

My 1st priority is a nicely working touchpad.

Stable (and fast) wifi would be the 2nd next thing I'd appreciate to see.

I have been using gentoo for severa yrs, but had to stick to OS X for the last 4 yrs and my customize skills got a bit rusty; I simply took ubuntu 14.04 for simplicity and expected to be in productivity mode again asap...

---

### Post by chili555 on 2015-04-11
I know nothing about touchpads. I do know that compiling a newer iwlwifi and associated suite won't affect your touchpad in any way. 

If you are struggling with your touchpad, I suggest a question on General Help.

---

### Post by c51 on 2015-04-11
The driver of the touchpad of my laptop is introduced in kernel 4.0-rcx (to be more specific: here).

I now found at least some related stuff on how to add/compile the focaltech into the driver [here]("https://bbs.archlinux.org/viewtopic.php?id=193593"). But currently I'm not sure how to compile a custom kernel for ubuntu or at least wont have the time to dive into that for next 2 or 3 weeks.

Therefore my 'request',works as expected for now and I donÄt want to got back to the preinstalled windows, as this would be one of my nightmare being come through.... 
 My request was dedicated to **pilot6** (as he advised me to do so).

The problem with the touchpad is that it by default it gets recognized as a mouse with no "touchpad features" enabled. Currently I'm reviewing a lot of stuff which implies a lot of falwless scrolling.
I cannot afford to buy another laptop that

---

### Post by jeremy31 on 2015-04-11
Why don't you run the wireless_script from the sticky post "before posting in networking and wireless" and we might find another option for you

---

### Post by c51 on 2015-04-13
> **chili555 said:**
> Backports, that Jeremy recommends, is *only* the iwlwifi driver and it's associated suite; cfg80211, mac80211, et al. You can install it in three minutes and reboot to see if it loads the -12 firmware. If not, sudo make uninstall it. You have little to lose.
Thanks you guys and sorry for being somehow ignorant on your suggestions. As I had limited time to do "experimental stuff" the last days I did not realize that it wasn't the whole 3.19 kernel but only really the wifi backports.

What jeremy31 suggested in post [#2]("http://ubuntuforums.org/showthread.php?t=2273231&p=13262729#post13262729") worked (for the 7260 fw v10), which already seems to have a positive impact on my wifi.

---

