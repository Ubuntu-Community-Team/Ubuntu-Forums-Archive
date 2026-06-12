---
title: "Help With Boot Procedures"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by foy1der on 2009-01-21
Hi,
Let me start by saying that I love Ubuntu. I have it set up on a computer that I do not frequently use and I get to play with and learn at my own pace.
With that said, I thought that I might be ready to make the step up to putting Ubuntu on my notebook (Toshiba Satellite M40). I wanted to keep Windows on the computer so I could dual boot, so I used acronis to chop off a hunk of my HD and I used that for Ubuntu. I installed it and a few things did not work out as I had planned. I couldn't find any drivers for my BT mouse and a whole slew of other problems later I think that I made a bad choice for putting Ubuntu on my notebook. I thought that I could fix this by just deleting the partition that had Ubuntu on it and using acronis to put it back on my HD. Long story short, Ubuntu still wants to boot. It tries to start and gives me an error 22. Then it just sits there and does nothing. Are there boot files that I also have to change? Should I have removed Ubuntu in a different manner to avoid this problem? Any help would be greatly appreciated.

Thanks,
foy1der

I also forgot to mention that I don't get a choice of which OS I would like to boot. It just assumes Ubuntu and loading it fails.

---

### Post by gn2 on 2009-01-21
You need to reinstate the Windows bootloader by running fixmbr.

There are various ways of doing so, [here's a how-to]("http://www.users.bigpond.net.au/hermanzone/p18.htm#STEP_ONE") from the excellent Hermanzone website.

---

### Post by foy1der on 2009-01-21
thanks for the reply gn2. I followed the step in [this](http://www.users.bigpond.net.au/hermanzone/p18.htm#Replace_GRUB_in_MBR_with_ms-sys) how to and when I try to install ms-sys, my terminal screen shows this

```

ubuntu@ubuntu:~$ sudo apt-get install ms-sys
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ms-sys
ubuntu@ubuntu:~$

```

I also tried referring to ms-sys as "ms-sys-2.1.3" as that is the latest version on sourceforge.net and "ms-sys*" I am looking in all of the available repositories and I couldn't find ms-sys in the Add/Remove Applications area either. The website I referred to says I should be able to do this from a live cd, so I don't think it's that either.

---

### Post by foy1der on 2009-01-21
I gave up. I tried to get ms-sys on my other ubuntu box and I couldn't get it to work on that one either. I threw the notebook hard drive in an enclosure, backed up and started over. Lesson learned, you can't just delete Ubuntu. Or any OS for that matter.

---

### Post by mjheagle8 on 2009-01-21
you need to run fixmbr in windows!

---

### Post by foy1der on 2009-01-21
That would have worked if I was able to get into Windows. I had no choice when the computer started it went right into Ubuntu and when Ubuntu wasn't there, it gave me Error 22.

---

### Post by mjheagle8 on 2009-01-21
you cant select windows from grub?

---

### Post by foy1der on 2009-01-21
I did at one point, but early today I was trying to get my notebook back to the way it was before I put Ubuntu on it and I screwed something up. Then I had nothing.

---

### Post by boof1988 on 2009-01-21
> **foy1der said:**
> That would have worked if I was able to get into Windows. I had no choice when the computer started it went right into Ubuntu and when Ubuntu wasn't there, it gave me Error 22.

One handy utility to have is a SuperGrubDisk.  It can't fix every problem... but it can sometimes fix a Windoze or Linux boot problem.  Sometimes even automatically.

If you are able, make a SuperGrubDisk (CD, USB-Flash or floppy) and it just might save you some troubles/frustrations in the future.  It's helped me out more than once.

HTH...

---

