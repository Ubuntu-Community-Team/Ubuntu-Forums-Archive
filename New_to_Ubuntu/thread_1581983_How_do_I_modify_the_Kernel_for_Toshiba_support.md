---
title: "How do I modify the Kernel for Toshiba support?"
date: 2010-09-25
forum: New to Ubuntu
---

### Post by Dave Gravox on 2010-09-25
Hi. I have a Toshiba L510 (PSLGXA-002002) and after much difficulty have installed Ubuntu 10.04. I have no Fn key support, brightness, dual-core, battery, etc. 

Quoting from: [http://ubuntuforums.org/showthread.php?t=1437653&page=3](http://ubuntuforums.org/showthread.php?t=1437653&page=3)

"It ALL goes away if you compile a new kernel and set the config options which include the word TOSHIBA to yes, (especially CONFIG_TOSHIBA=y)."

Can someone please walk me through this? I've followed the instructions here:
[http://help.ubuntu.com/community/Kernel/Compile](http://help.ubuntu.com/community/Kernel/Compile)

I'm up to 5B and have downloaded the kernel package but not sure how to modify it from here.:confused:

---

### Post by mrhhug on 2010-09-25
this doesn't seem like a reason to compile from source. have you tried this approach?

[http://ubuntuforums.org/archive/index.php/t-9962.html](http://ubuntuforums.org/archive/index.php/t-9962.html)

---

### Post by Dave Gravox on 2010-09-26
FnFx is totally out of date and doesn't work for modern Toshibas. I ran into it when trying to get my previous Toshiba working for Ubuntu 8.10. It also only fixes the Fn key problem and none of the wider issues.

I have an Insyde BIOS which means FnFx is inappropriate anyway. Installed (I think) the Omnipage driver and that hasn't helped either.

A custom kernel is the only way I've heard so far that definitely works.

Does anyone know if 10.10 will solve any of this or why Toshibas seem to be so difficult to run with Linux?

---

### Post by spillin_dylan on 2010-09-26
I was having some similar issues with this as well.  Actually, I guess I still do, because my Fn+F# commands don't work either.  Regardless, is there a BIOS update for your model?  I updated my BIOS and my overheating problems went away.  Toshiba's website should have all the info you need for that.

Also, I might try a custom kernel, too, if that actually works.  It doesn't even seem that bad, after trying a Gentoo kernel last week.....  ;)

---

### Post by mrhhug on 2010-09-26
i tried downloading the source for hardy to see what your up against.

I remember updating source for something a few years ago... it wasn't ubuntu but the source was much different.

i noticed this is a new thread from this post, [http://ubuntuforums.org/showthread.php?t=1437653&page=3](http://ubuntuforums.org/showthread.php?t=1437653&page=3) 

> And have the kernel downloaded and ready for modification, but I'm not sure how to modify it. A search reveals 338 references to 'TOSHIBA' in the kernel directory. Could someone please tell me how and exactly what to modify in the config options?

kaosent recommended's > and set the config options which include the word TOSHIBA to yes, (especially CONFIG_TOSHIBA=y)

338 seems like ALOT to changing by hand, you COULD write a script but im thinking just give the CONFIG_TOSHIBA=y a try and go from there.

which source did you download?

im no mastermind to ubuntu but your not getting alot of other traffic in this thread so i don't want to leave you by yourself. a 3nd brain is exponential not just tripple.

---

### Post by spillin_dylan on 2010-09-27
Used this guide:

[http://blog.avirtualhome.com/2010/05/05/how-to-compile-a-ubuntu-lucid-kernel/]("http://blog.avirtualhome.com/2010/05/05/how-to-compile-a-ubuntu-lucid-kernel/")

And compiling as I type.  I will keep you posted!

The key to setting the Toshiba options this way is when you run ```
debian/rules editconfigs
```
to make sure you set the Toshiba Laptop flag, which if I remember was in the Processor category.  If you play around here, you should be able to find it too.

---

### Post by Dave Gravox on 2010-10-12
Modified the kernel as per the instructions and no dice. Everything is exactly the same.

Tried installing 10.10 and have run into the same problems I had with 10.04. Can't even boot the regular installer.

I'm over it. I've had two Toshibas and both have been nightmares trying to get Ubuntu to run properly. I wish Toshiba would at least try to achieve easy linux compatibility, but then again Canonical shouldn't be talking about 'just works' when that still seems to be exception rather than the rule.

For now I guess I'm stuck with Windows 7.

---

### Post by Blasphemist on 2010-10-12
I don't think my Toshiba Satellite hasn't had this problem with 10.04 nor 10.10. What exactly is it that doesn't work with those keys? I can't say that I use much other than F5 and F1.

---

### Post by Dave Gravox on 2010-10-12
Things not working:

Only recognizes a single Core of the i3
Installer Crashes. Needed to use the alternate installer
No Fn key support
No Battery/Power management support
No suspend/hibernate options

All of these work in Windows 7. BIOS is up to date.

Bluetooth and wireless DO work.

I suspect the Australia/New Zealand models are particularly problematic as people with other L510s seem to be having different, less severe issues.

---

### Post by Blasphemist on 2010-10-16
You may be right about the Aussie BIOS. I see there is quite a bit on the Toshiba support site about BIOS related keyboard issues. I didn't sort through it all but you may want to. So what is different about Aussie BIOS? Does it somehow have an accent? :)

---

### Post by Alver on 2010-10-16
> **Dave Gravox said:**
> Hi. I have a Toshiba L510 (PSLGXA-002002) and after much difficulty have installed Ubuntu 10.04. I have no Fn key support, brightness, dual-core, battery, etc. 

Quoting from: [http://ubuntuforums.org/showthread.php?t=1437653&page=3](http://ubuntuforums.org/showthread.php?t=1437653&page=3)

"It ALL goes away if you compile a new kernel and set the config options which include the word TOSHIBA to yes, (especially CONFIG_TOSHIBA=y)."

Can someone please walk me through this? I've followed the instructions here:
[http://help.ubuntu.com/community/Kernel/Compile](http://help.ubuntu.com/community/Kernel/Compile)

I'm up to 5B and have downloaded the kernel package but not sure how to modify it from here.:confused:
I cannot offer any recommandation since I have a different model (Satellite L505-10M, 6GB ram, dual boot W7/U 10.04.1). Please consider this only as a testimony. I hope some details of my experience may be of help:
1. Installation from U 10.04 iso dvd: not the slighthest problem
2. Wireless: I had to install wcid to get it working. After a few weeks I uninstalled wcid. My wireless is still working well after some 3 months. No explanation to offer.
3. Installed toshset, toshutils and fnfxd from synaptic. Now Fn/F5-6 is working in controlling screen brightness. Fn/F3 is also working. Must admit that I rarely use function keys.
4. Installed GkrellM which allows me to see what my battery is doing.
5. Installed Cairo dock recently, and to my pleasent surprise I noticed a fully functional brightness applet with a far greater range than the funcion keys.
6. I've set CPU "on demand".
7. Fan control is not possible on my laptop but then temperature has not been an issue sofar. Occasionally my fan takes off, depending on the job, but it dies down when a demanding job is finished. I've never ever seen the very high temperatures reported by some Toshiba owners.
8. I cannot report on hibernate and sleep modus since I never use these.

All in all, I'm rather pleased with U 10.04.1 sofar.

Hope this helps

Alver

---

### Post by Dave Gravox on 2010-10-25
My model (PSLGXA-002002)has an INSYDE H20 BIOS. I have the latest update (1.20). Other recent Toshiba models seem to have trouble with wi-fi but not much else. I don't have any trouble with wi-fi with my model. Other computers with an Insyde BIOS do seem to have major trouble, as shown in this thread:

[http://ubuntuforums.org/showthread.php?p=10025495](http://ubuntuforums.org/showthread.php?p=10025495)

Is it possible that this BIOS is simply not popular enough for it have been accommodated for in the kernel or modules?

---

