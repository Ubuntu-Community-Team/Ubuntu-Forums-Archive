---
title: "Kinda a Newb to Ubuntu, But Need help, installed Windows 7 after ubuntu"
date: 2011-02-16
forum: New to Ubuntu
---

### Post by throwback1718 on 2011-02-16
Whats up guys, I have a laptop, which I had windows XP on it. But that OS was kind of giving me some problems. 

So eventually I had installed ubuntu. Loved it. But some of the things that I needed to do, weren't possible in Ubuntu. 

So I finally got a copy of windows 7 and installed it on the partition that contained my original windows XP. Now the only issue is that when booting the computer, the option list to choose the OS you want to use doesn't appear. The only thing that happens is that it loads up straight into Windows. 

Is there any way that I can possibly get back that OS option screen? I really would like to load into ubuntu.

Thanks in advance.

---

### Post by jwcalla on 2011-02-16
I can't believe Windows still does this.  Even with Win 7?  Yeash.

Have a look at this:  [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by coffeecat on 2011-02-16
> **throwback1718 said:**
> Is there any way that I can possibly get back that OS option screen?

It's fairly straightforward.

First - did you install one of Ubuntu Karmic/9.10, Lucid/10.04 or Maverick/10.10? If so you have grub 2 for the Ubuntu bootloader - it's the grub menu you want back - and the link below will help. If you had Ubuntu Jaunty/9.04 or earlier or if you upgraded from Jaunty or earlier, then the link won't help because Jaunty came with legacy grub.

Have a look here:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Just follow it from the heading "Re-installing grub 2" down to instruction 8 of method 1. If you don't understand anything, post back, and if you need help interpreting the output of 'sudo fdisk -l', then post the output of that command. That's:

```
sudo fdisk -l
```Note the '-l' is a lower-case L, not a number 1. It's not clear from the typeface in that link.

---

### Post by throwback1718 on 2011-02-16
okay guys I will try these out and give you all some feedback thanks

---

### Post by oracle2b on 2011-02-16
You could also install [EasyBCD ]("http://neosmart.net/dl.php?id=1")to get your boot back, I think it'll chain load the boot menu.

---

### Post by hansolo4949 on 2011-02-16
Ouch, when you installed Windows 7 after Ubuntu, you axed Grub (the boot loader) so now Ubuntu will nit boot. This is actually rather easy to fix, since all you need to do is reinstall Grub. I myself do not know (yet) how to do so, but a quick google search should find the answer you want. This tutorial should be helpful:[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Good luck!

---

### Post by throwback1718 on 2011-02-17
thanks guys, the link that coffeecat provided was exactly what solved the problem

---

