---
title: "reinstall windows xp?"
date: 2010-07-07
forum: New to Ubuntu
---

### Post by nh5y on 2010-07-07
i've been using ubuntu for about a year or a year and a half, but i am taking the bar exam this month and i need a laptop with windows on it.  my computer did not come with an installation cd, but had windows xp already installed and i'm pretty sure that in the past, i've reinstalled windows by pressing f2 or f11 or something like that at bootup.

i'm wondering if there's any possibility that this option is still available -- is there a way for me to reinstall windows with a button?  is windows still in there somewhere?

i bet some people will say "no way to know but try" but i don't want to do anything to my computer until i have good reason b/c i just don't want to risk any messups with my computer.


i use a sony vaio VGN-TXN17P; got it late 2006.

thanks

natasha

---

### Post by donkyhotay on 2010-07-07
Those buttons won't work, they require that you have the original partitions and boot path your computer shipped with, these would have been changed when you installed ubuntu. You'll probably have to get in touch with your computer manufacturer for a set of recovery discs but these generally put the system back to the original factory condition, wiping out linux entirely. Sometimes you can't get them anymore (especially if you're system is old) at which point you either don't use windows or you pay for a retail copy of windows.

---

### Post by Mr Nemo on 2010-07-07
If you install ubuntu onto your system you will be able to select between windows and ubuntu through GRUB (ubuntu's bootloader). Just installing ubuntu will give you this option.

**Re-read your post and i misread it. Unless you used the whole hard drive for ubuntu windows should still be in there somewhere. I'm sure there is a way to check.

---

### Post by Matt__ on 2010-07-07
depends if you chose to manually partition your hard drive or use entire disk when you installed Ubuntu.
if the latter then no you cant restore windows and will need to get another disk/borrow one (assuming you have a license key printed on bottom of laptop) or a whole new license and disk if not.

nemo ubuntu is already installed....I would assume that grub would be seen with its windows option if there was one :)

---

### Post by donkyhotay on 2010-07-07
> **Mr Nemo said:**
> If you install ubuntu onto your system you will be able to select between windows and ubuntu through GRUB (ubuntu's bootloader). Just installing ubuntu will give you this option.

This only works if you have windows already installed and set up a dual-boot with linux. My understanding of OP is that windows is gone completely and only ubuntu remains.

---

### Post by Mr Nemo on 2010-07-07
Ya I have a habit of not reading the whole post sometimes. Sorry OP.

---

### Post by nh5y on 2010-07-07
> **Matt__ said:**
> depends if you chose to manually partition your hard drive or use entire disk when you installed Ubuntu.
if the latter then no you cant restore windows and will need to get another disk/borrow one (assuming you have a license key printed on bottom of laptop) or a whole new license and disk if not.

nemo ubuntu is already installed....I would assume that grub would be seen with its windows option if there was one :)
I'm not sure, but I *bet* I used the entire disk the first time I installed ubuntu.

I do still have the license key printed on the bottom of my computer.  do you think my boyfriend's Dell XP reinstallation cd would work for this (or is it that b/c it's a "reinstallation" cd it won't work)?

this is a huge pain in my *** -- thank you for all your help.

---

### Post by yeats on 2010-07-07
> I do still have the license key printed on the bottom of my computer. do you think my boyfriend's Dell XP reinstallation cd would work for this (or is it that b/c it's a "reinstallation" cd it won't work)?


Yes, this should work.  You can always call Microsoft at the verification step and explain the situation.  Since you paid for Windows with the machine, it will work.

I'll also mention that if the laptop has enough resources, you can run Windows in VirtualBox and keep Ubuntu as your main OS - this is what I did.

---

### Post by nh5y on 2010-07-07
> **chrissharp123 said:**
> Yes, this should work.  You can always call Microsoft at the verification step and explain the situation.  Since you paid for Windows with the machine, it will work.

I'll also mention that if the laptop has enough resources, you can run Windows in VirtualBox and keep Ubuntu as your main OS - this is what I did.
So the Dell cd should work on my Vaio?!  That is exciting news!  I hope that is true!

I'd like to clean up my system anyway, so I think I'll just do windows for the bar and ubuntu from scratch after that.

Thanks everyone!

Natasha

---

### Post by rwthelegend on 2010-07-07
> **nh5y said:**
> i've been using ubuntu for about a year or a year and a half, but i am taking the bar exam this month and i need a laptop with windows on it.  my computer did not come with an installation cd, but had windows xp already installed and i'm pretty sure that in the past, i've reinstalled windows by pressing f2 or f11 or something like that at bootup.

i'm wondering if there's any possibility that this option is still available -- is there a way for me to reinstall windows with a button?  is windows still in there somewhere?

i bet some people will say "no way to know but try" but i don't want to do anything to my computer until i have good reason b/c i just don't want to risk any messups with my computer.


i use a sony vaio VGN-TXN17P; got it late 2006.

thanks

natasha

If you can install Window with a button from the bios boot up screen, that means there is a partition somewhere with a Windows restore install on there. Unless you removed it, it should still be there. I never tried that on my laptop but just give it a try, it might work.

If not, well, you will need to purchase a copy of Windows or maybe Wine (let's you run some Windows application in Linux) can help you.

---

### Post by spydeyrch on 2010-07-07
Something you need to be aware of is that even if you use your boyfriend's XP install disc with your license key, which is perfectly legal and fine and will work, if you re-install XP to your HDD, you run the risk of either writing over your Ubuntu install, or, if you re-partition your HDD so that there is a second partition, you will overwrite GRUB and therefore won't be able to boot into ubuntu without some not-so-fun live cd & terminal work.

If your system can handle running a VM, I would recommend doing it that way. :p

-Spydey :D

---

### Post by QIII on 2010-07-07
Be careful about the VM idea, folks.

With an OEM disk (which is what you get with your spankin' new computer in most cases), the license agreement forbids the use of the disk to install Windows in a virtual machine.

Another problem with OEM disks is that they are often tailored to an OEM's machine and check for same on install -- which means that the OS may not install, it may be unstable or you might get lucky.

---

### Post by spydeyrch on 2010-07-07
> **QIII said:**
> Be careful about the VM idea, folks.

With an OEM disk (which is what you get with your spankin' new computer in most cases), the license agreement forbids the use of the disk to install Windows in a virtual machine.

Another problem with OEM disks is that they are often tailored to an OEM's machine and check for same on install -- which means that the OS may not install, it may be unstable or you might get lucky.

While the license agreement thing is true regarding VMs ....... you need to be aware of it ...... I have used many OEM discs to install on a computer that the disc didn't come with. BUT the computer did have a valid license key on its side or bottom. The thing with the OEM disc is that when it checks to see if the computer maker and OEM match, it will notice that they don't then it will ask for a CD key/license. This is when you would put in your CD key found on your computer/laptop.

If the hardware and OEM cd match up, all it really does is fill in the cd key for you and activate it without the need of an interent connection.

I have called MS personally and asked if by using an OEM that didn't come with my computer but using the license/CD key that did come with it, if I was breaking any agreement or anything. I was told (mind you this was back in 2001), that no, it didn't and that as long as I was using a valid license key found on the computer to which I was installing, that I was fine. The only thing, and it doesn't apply to your situation (at least I assume that it doesn't) is that the license key MUST stay on the computer with which it came. The sticker can not be removed and "transferred" to a different computer.

Hope that all makes sense. :D

-Spydey :)

---

### Post by QIII on 2010-07-07
As I said...  "you might get lucky".

---

### Post by Mark Phelps on 2010-07-07
> **nh5y said:**
> So the Dell cd should work on my Vaio?!  That is exciting news!  I hope that is true!

Depends on what you mean by "work"... and by what's actually on the CD.

If it's a full-blown restore image, then it's likely to be able to boot your machine and reinstall the OS.  It probably will have Dell drivers instead of Sony, so you may have to struggle with that.  But if you can get an internet connection after install, Windows Update should take care of finding and installing the proper drivers.

As to post-install activation, my guess is that, since Sony uses different certificates from Dell, that is likely to fail.  But then, since you have a product key for your Dell, you might "get lucky" in that entering it will then reactivate your machine.

You also might get "luckier" in that activation will NOT fail and you will be OK.

---

