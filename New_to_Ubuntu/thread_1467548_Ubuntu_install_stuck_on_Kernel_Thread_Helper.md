---
title: "Ubuntu install stuck on Kernel_Thread_Helper"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by oso_te_great on 2010-04-30
There are some numbers after that, and I can get them if they are necessary.  Here is what I did.

I am running Win7 on a Toshiba Satellite E205, I am trying to install the version released today.

I downloaded the ISO, burned using the Win7 Disk Image Burner.  Then I booted off of the CD, where this purple screen loaded.  Then it started running code (Which for purposes of this post, we will call "Screen Alpha"), then stopped with the Kernal_Thread_Helper

I waited a while, thinking that something would happen, but alas, after an hour, it was still on the same screen.

Then I restarted to windows 7, popped in the CD, and Wubui popped up.  With Wubui I tried the live installation, and the installation through windows, all starting with the countdown to install screen, then going to Screen Alpha, and ending in that Kernal Thread Helper line

After that, when I restarted, the dual-boot screen came up, and when I chose Ubuntu again, it sent me to Screen Alpha, again with the same result

I really want to install Linux, and have on older machines with no problems.  Please help me.

If a mod sees the need to move this elsewhere, no problem, I just thought that my noobness trumped with this question.  Thank you to all who help, in any way, even if it is to tell me I am a noob

---

### Post by Sealbhach on 2010-04-30
Sounds like it's borked. Can you get into Windows? 

How did you close down the installation when it got stuck? 

.

---

### Post by oso_te_great on 2010-04-30
I held down the power button for a few seconds to turn it off, and I booted into windows just fine

---

### Post by Sealbhach on 2010-04-30
> **oso_te_great said:**
> I held down the power button for a few seconds to turn it off, and I booted into windows just fine

Right, your Ubuntu is definitely borked then. Sometimes, Ubuntu won't install on some machines, due to some problems with hardware. In the past I have found that on some machines, the installer would stop and give some error messages and wouldn't continue, so I assumed that the hardware just doesn't fit, if you know what I mean.

When you boot up from the Ubuntu CD, do you get to a Live CD session, with full desktop?

.

---

### Post by oso_te_great on 2010-04-30
No

My roommate told me that since I am running on an intel I5, I probably downloaded the 64bit, I am currently DLing the x86

Could this be the case?

When i booted off of the cd, I thought that was the live cd

---

### Post by Sealbhach on 2010-04-30
> **oso_te_great said:**
> No

My roommate told me that since I am running on an intel I5, I probably downloaded the 64bit, I am currently DLing the x86

Could this be the case?

When i booted off of the cd, I thought that was the live cd

No, the LiveCD brings you up a live working desktop, you can surf the net, write documents, watch movies and all that in a Live CD session.

.

---

### Post by oso_te_great on 2010-04-30
> **Sealbhach said:**
> No, the LiveCD brings you up a live working desktop, you can surf the net, write documents, watch movies and all that in a Live CD session.

.

I know that, but I thought when I booted from the CD, that was *supposed* to happen, not the KTH thing

[IMG]http://mail.google.com/mail/?ui=2&ik=814b59ad84&view=att&th=12852667e6efa2a6&attid=0.1&disp=inline&zw[/IMG]

---

### Post by sebastian.ricaldoni on 2010-05-02
Same thing happened to me. I have a Toshiba Satellite L505. I wanted to install Ubuntu 10 but with some bumps in the middle. After reading some other posts I ran the installation process using 'acpi=off' which at least allowed me to install it. After the installation process was done I restarted my notebook and when I try to load Ubuntu I get a list of (errors?) and the last row contains a kernel_thread_helper message. 
Any idea why this could be happening? This isn't the first time I install Ubuntu but certainly the first time I ran into this issue.
I would appreciate any help.

Thanks,
Sebastian

---

### Post by computerwiz908 on 2010-05-08
> **sebastian.ricaldoni said:**
> Same thing happened to me. I have a Toshiba Satellite L505. I wanted to install Ubuntu 10 but with some bumps in the middle. After reading some other posts I ran the installation process using 'acpi=off' which at least allowed me to install it. After the installation process was done I restarted my notebook and when I try to load Ubuntu I get a list of (errors?) and the last row contains a kernel_thread_helper message. 
Any idea why this could be happening? This isn't the first time I install Ubuntu but certainly the first time I ran into this issue.
I would appreciate any help.

Thanks,
Sebastian

I have the same issue with my Satellite E205.  I used Wubi to install Ubuntu, and when it first did not work, I used "ACPI Workarounds," which at least installed it.  However, I can't boot the OS.  Is my hardware simply not compatible with Ubuntu, or any other Linux distro for that matter?

---

### Post by frillybob on 2010-05-08
Press f6 when it's loading then press f6 again and say acpi=off I had the same problem with the same OS and and same pc and am now a happy dual-booter!

---

### Post by wdaim on 2010-05-11
> **oso_te_great said:**
> There are some numbers after that, and I can get them if they are necessary.  Here is what I did.

I am running Win7 on a Toshiba Satellite E205, I am trying to install the version released today.

I downloaded the ISO, burned using the Win7 Disk Image Burner.  Then I booted off of the CD, where this purple screen loaded.  Then it started running code (Which for purposes of this post, we will call "Screen Alpha"), then stopped with the Kernal_Thread_Helper

I waited a while, thinking that something would happen, but alas, after an hour, it was still on the same screen.

Then I restarted to windows 7, popped in the CD, and Wubui popped up.  With Wubui I tried the live installation, and the installation through windows, all starting with the countdown to install screen, then going to Screen Alpha, and ending in that Kernal Thread Helper line

After that, when I restarted, the dual-boot screen came up, and when I chose Ubuntu again, it sent me to Screen Alpha, again with the same result

I really want to install Linux, and have on older machines with no problems.  Please help me.

If a mod sees the need to move this elsewhere, no problem, I just thought that my noobness trumped with this question.  Thank you to all who help, in any way, even if it is to tell me I am a noob

you should have used the 32 bit installation for that system, also you should use a better tool such as PowerISO to burn the image to a disc and set teh speed to something slower such as 1x or 4x, this will ensure the image burns correctly. also i would click "Try Ubuntu without making chnaged to my system" and have a lay around first as linux is very different to any other OS.

---

### Post by linuxlovinwarren on 2010-06-10
it took me awhile to figure it out for my E205, installing with acpi=off doesn't put acpi=off into the boot options, so once grub loads hit e to edit the boot options and add it in manually, after your in ubuntu there are instructions if you search for them to turn it off in grub 2 so you don't have to mess with it any more. GL!

---

### Post by danerben on 2011-02-23
Booting with acpi=off isnt a good way around, because you wont have advanced power control then. It is only a temporary workaround to make the system install and run it for the first time.

The real solution is upgrading to a newer kernel. That should do the trick without disabling acpi..

---

