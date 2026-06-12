---
title: "I'm back beginner with Hardy Heron"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by richie3418 on 2010-01-05
I have finally decided to come back with Ubuntu. I had trouble the last time with the laptop I was using and had to quit. It took me a long time but I had to re-format this desktop I now have so I figured what the heck and installed the Ubuntu I had on hand the 8.04 LTS on the same hard drive as windows xp home a dual boot using the grub boot. 
The install went great and everything seems to be working. So far I only got it updated and trying to figure out where to go from here. Does anyone think it would be wise to do the upgrades, in order, to the 9.10 or stay with Hardy Heron, I know that the 8.04 still has about another year or so of support.  Either way I will still need to find some how to on setting up to make this a useful desktop. I was a die hard windows user and am very much in the dark with this Ubuntu. This isn't a new system, it is a Dell dimension 4700, 320 gb., hd 100 gb. for Ubuntu, also 4 gb. memory only 3gb. usable because being a 32 bit, an integrated media accelerator, I have a 8600 GTS video card but took it out because it runs too hot unless I open cover and turn fan into it.
Any input on the upgrades or in making a comfortable desktop would be appreciated.

---

### Post by J V on 2010-01-05
Upgrades increase bloat, and there are several features in 9.10 you dont get with upgrades...

I *do* in fact suggest going for a fresh install of 9.10... You will find a LOT of improvements (3 clicks for graphics drivers anyone?)

You might want to make a seperate /home to make upgrading easy (without bloat)

Just cruise the forums and you will find LOTS of information on how to make your ubuntu more awesome :)

First things first, get 9.10, then install _[ubuntu restricted extras]("apt://ubuntu-restricted-extras")_

Good luck

---

### Post by mvalviar on 2010-01-05
I'd advise you to stay with LTS. Lots of annoying glitches propped out in Ibex, Jaunty and Karmic.

---

### Post by Merk42 on 2010-01-05
It really depends on what you want.
"Stability" or "leading edge"
I put each in quotes because it's not to say 9.10 is unstable or 8.04 is all old programs.
Upgrading from 8.04 to 9.10 though is a lot of downloading since you have to go 8.04 -> 8.10 -> 9.04 - 9.10

Maybe for you, stick with 8.04 to get the feel of Ubuntu, then in April you can directly upgrade to the next LTS 10.04 Lucid Lynx

---

### Post by Methuselah on 2010-01-05
Since you are basically doing a clean installation, it would be preferable for you to install 9.10 directly using a CD than to install 8.04 then upgrade to 9.10 (possibly through other releases).

Another thing to keep in mind is that some time in April Ubuntu 10.04 (Lucid Lynx) will be available which is another LTS release.
You would only need to stck with 9.10 for a few months and 10.04 will probably be rather close technologically to 9.10 so upgrading shouldn't be too drastic.

I'm leaning towards recommending you at least downlooad the Ubuntu 9.10 CD and try the Live CD in your computer.

---

### Post by slakkie on 2010-01-05
> **J V said:**
> Upgrades increase bloat, and there are several features in 9.10 you dont get with upgrades...


Untrue.

The only feature you don't have is ext4 and you can still format disks to ext4 afterwards so.. Not true. The only thing which might warrant a fresh install is if you want your root partition in ext4 and have all the performance benefits and/or features ext4 has, which a converted filesystem (from ext3 to ext4 doesn't have - you will only have these features on new files, copying files does not replace the inode so it will still be ext3).. 
And the bloat you are referring too, where can I find it?

Grub2 can be easily installed to replace grub-legacy, which is a relatively trivial upgrade.

---

### Post by Sef on 2010-01-05
Since Lucid Lynx, 10.04, is the next Long Term Stable (LTS) release, I would wait till it is released then upgrade.

---

### Post by pricetech on 2010-01-05
I'd stick with Hardy.  Learning Linux / Ubuntu is going to be pretty much the same whatever version you use.

What you add to your basic install is a personal preference.  Since you're learning, I would suggest you add whatever apps you want to learn most, one or two at a time, until you are comfortable with them, then when you do upgrade you'll pretty much know what you want and how to make it work to suit you.

Most of all, have fun and welcome back.

---

### Post by richie3418 on 2010-01-05
Thanks guys I think I'll go with the wait until the next LTS then upgrade. Now I have to cruise around and find what to put into this Hardy Heron to make it nice.

---

