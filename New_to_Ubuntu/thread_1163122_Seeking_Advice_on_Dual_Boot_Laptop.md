---
title: "Seeking Advice on Dual Boot Laptop"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by VanEyck on 2009-05-18
Hi everybody,

I want to buy a dual-boot laptop with Jaunty and Windows XP pre-installed.  System 76 has affordable, sturdy looking laptops, but they don't offer XP.  Other sites that I've seen offer XP, but either don't offer Jaunty, or they are really expensive.

So, should I go with System 76, and try to install XP myself?  Somehow, that strikes me as a bad idea.  Or should I get a laptop with XP and Hardy, then install Jaunty?  This sounds like the better idea to me, except that these sites have had difficulty getting Jaunty to work on their equipment, and that's why thy offer Hardy in the first place!

I'd also be willing to just buy a windows laptop and install Jaunty over it, but I worry about hardware compatibility in that case as well.

Anyone have any suggestions?

---

### Post by ptn107 on 2009-05-18
If you can't find one with Windows/Ubuntu already on it, I'd get one with just Windows so you can install Ubuntu onto it yourself (installing Ubuntu is a breeze).  Ubuntu should be installed *after* Windows in any case.  Avoid one with just Ubuntu on it especially if your not comfortable installing Windows yourself and/or are not prepared to fix the bootloader after windows takes it over.  Do you really even need Windows in the first place?, if not just get a straight Ubuntu machine from System 76.

---

### Post by VanEyck on 2009-05-18
I've successfully lived (very happily) without windows or wine for the last 2.5 years.  I actually hate windows.

But my circumstances are changing and I will need Windows starting in September.  And, although I hate windows, I will be really happy to play civ again.

---

### Post by mikewhatever on 2009-05-18
> **VanEyck said:**
> 
So, should I go with System 76, and try to install XP myself?  Somehow, that strikes me as a bad idea.  Or should I get a laptop with XP and Hardy, then install Jaunty?  This sounds like the better idea to me, except that these sites have had difficulty getting Jaunty to work on their equipment, and that's why thy offer Hardy in the first place!


Do they really say there are problems with Jaunty? I'd rather suggest they don't want having to support two versions of Ubuntu, so they stay with Hardy, which is a long term support version.

---

### Post by VanEyck on 2009-05-18
> **mikewhatever said:**
> Do they really say there are problems with Jaunty? I'd rather suggest they don't want having to support two versions of Ubuntu, so they stay with Hardy, which is a long term support version.

One of the sites specifically said that.  I'm guessing it has to do with one or two pieces of hardware.  I'm taking their word for it but I don't really see why something would work in Hardy, but not in Jaunty.

---

### Post by A55h4t on 2009-05-18
As ptn107 said installing Ubuntu is a breeze.  The office I work in is a Dell shop and I have a Latitude D630 laptop that came with XP Pro on it.  Installing Ubuntu on this laptop in a dualboot configuration was very easy and Ubuntu was able to pickup all the hardware, even the wireless card.  I have put quite a few different Linux distros on this laptop and I can tell you that Jaunty runs great on it.  I don't think it would be hard for you to find a laptop that you can dualboot XP and Ubuntu on at all.  I like what system76 is doing as far as promoting Ubuntu and all but I think they are a little expensive.  Seems to me you can get a similar system with Windows on it for the same price, point being that they should be cheaper because Ubuntu is free and Windows is not.

---

### Post by VanEyck on 2009-05-18
Ok,

New question.  I've never dealt with Windows Vista before.  If I buy a laptop with Vista pre-installed, will I have any issues if I install Jaunty (and dramatically reduce the space alloted to Windows).  I wouldn't want Windows to occupy more than 25GB of a 300GB hard drive.  Would I have problems trying to confine Vista so much?

---

### Post by robertron76 on 2009-05-18
> **VanEyck said:**
> Ok,

New question.  I've never dealt with Windows Vista before.  If I buy a laptop with Vista pre-installed, will I have any issues if I install Jaunty (and dramatically reduce the space alloted to Windows).  I wouldn't want Windows to occupy more than 25GB of a 300GB hard drive.  Would I have problems trying to confine Vista so much?

me, neither.I bought a laptop month ago with Vista Ultimate and 250GB HDD in it.

With Vista, I was able to make partitions and with a separate partition, I installed Ubuntu 8.04 HH LTS Desktop as dual-boot mode and happy with it.

But, there are some caveats : 


[LIST=1]
[*]If you're buying anew laptop, make sure you buy  Windows Vista separately. Vista pre-installed is OEM from the hardware manufacturer such as SONY,DELL,HP etc and does not have all features of Vista.SONY SUPPORT actually told me to buy a retail vesion of Windows Vista, after paying 1300$ for the laptop.They also told me to buy a separate 3rd party partition software to partition the HDD, as OEM version can't do this.I used trial version of Partition softare from google and was able to make partitions for Ubuntu.Or buy a basic  version of Vista with laptop and purchase a separate retail version of Vista.There are rumors that for retail users of Vista, you may get a Windows 7 freely, am not sure and no guarantee on this....
[*]Look for the processor,Grpahics Card details and make sure they support VT and the graphics card is comaptible with Ubuntu or not. Ubuntu 8.04 supports my ATI Graphics card, but Ubuntu 9.04 has known issues with ATI.My laptop processor T6400 does not support VT (I realized after buying this), hence I did dual-boot.Otherwise, I would have made my laptop with Ubuntu only and use VMware-Windows.
[*]When making new partitions or playing with partitions such as delete,recover etc, make sure you know what you're doing.I randomly created a separate partition for data archival one day, and my GRUB reported Error 17.I could not boot neither Ubuntu nor Vista.I did not use recovery dics or boot discs (didn't had one at that time), panicked and reinstalled Ubunut from the scratch.Then everything was fine.Not trying to scare you, but be aware of.
[/LIST]
HTH,

R

---

