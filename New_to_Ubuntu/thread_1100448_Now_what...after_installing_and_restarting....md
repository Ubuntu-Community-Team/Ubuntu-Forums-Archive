---
title: "Now what?...after installing and restarting..."
date: 2009-03-19
forum: New to Ubuntu
---

### Post by ckh1 on 2009-03-19
So,
 I downloaded ubuntu 8.10 successfully
I burned ubuntu 8.10 to a cd successfully...finally.
 I installed ubuntu 8.10 on my dell insipron 2650 successfully
I reboot and choose the ubuntu option successfully
then i get a grub prompt and nothing else...NOW WHAT?
Coming from XP, so far not impressed.
Looking at the forum threads, it looks like there are tons and tons and tons of issues. But I will hang in there for a little bit longer.
Please someone change my mind about ubuntu/linux successfully!

---

### Post by philinux on 2009-03-19
Ok lets see what you did as it obviously has not gone well.

Boot the live cd. Download this boot info script to the live cd Desktop.
[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Open a terminal, Applications>accessories >terminal and use this command. Copy and paste it.
sudo bash ~/Desktop/boot_info_script*.sh

This creates a results.txt file.

Attach it to a post. you can use the live cd for all of this.

---

### Post by LowSky on 2009-03-19
> **ckh1 said:**
> 
Coming from XP, so far not impressed.
Looking at the forum threads, it looks like there are tons and tons and tons of issues. But I will hang in there for a little bit longer.
Please someone change my mind about ubuntu/linux successfully!

Ever try to install Windows XP on a computer with SATA drives and No floppy drive... yeah you can't, and tell me who even buys a floppy drive anymore.

All those issues you see, is nothing but people with minor issues. But then again the web is full of Windows Forums of people with problems too. Besides people are here to post issues not to post success, thats another part of this forum.

You say you got some grub prompt, could you be more specific, did the screen say some error?

if it is just a prompt, just enter your name then password, then type startx, it will boot into the Os you saw during the LiveCD

---

### Post by lovinglinux on 2009-03-19
> **ckh1 said:**
> Please someone change my mind about ubuntu/linux successfully!

Okay

> **ckh1 said:**
>  I downloaded ubuntu 8.10 successfully

This first step is already impressive, because you were able to download the OS for free and legally, probably at a good speed.

Ubuntu 1 x 0 Windows

> **ckh1 said:**
> I burned ubuntu 8.10 to a cd successfully...finally

I don't think Miscrosoft would allow you to burn as many copies you want of Windows and share these copies with your friends. You probably would have to order each copy and pay a lot of cash for each of them. But doing this with Ubuntu is trivial and legal.

Ubuntu 2 x 0 Windows

> **ckh1 said:**
> I installed ubuntu 8.10 on my dell insipron 2650 successfully

How long it would take to install if it was a Windows copy?

Ubuntu 3 x 0 Windows

> **ckh1 said:**
> I reboot and choose the ubuntu option successfully
then i get a grub prompt and nothing else...NOW WHAT?

Now you can get support for free from a HUGE community of people which, in average, is more tech savvy than Windows users and won't tell you to turn UAC or to proceed with another kind of insecure action.

> **ckh1 said:**
> Coming from XP, so far not impressed.

Did you tried to run Ubuntu from the Live CD first to test the OS with your machine before installing it? 

Wait, I don't think Windows has an official Live CD for testing and you have to buy the software before testing it anyway. I remember that hundreds of people in my country were very pissed off when Vista was released. They rushed to the stores in the first day the OS was available, due to massive advertising, to buy a expensive copy. But then they realized that most hardware were not supported and they weren't able to get the most of the OS features or even run it, even after passing the upgrade advisor test.

Ubuntu 4 x 0 Windows

> **ckh1 said:**
> Looking at the forum threads, it looks like there are tons and tons and tons of issues.

Yes they are, like any other OS. The difference is that there is a huge and experienced community that gives you support for free at a centralized place, where you can also find tutorials, wiki and other forms of support. For instance, your question was replied just one hour after being posted here. If you think this is not fast enough, you could access the [IRC channel]("http://www.ubuntu.com/support/community/chatirc") for free live support.

Ubuntu 5 x 0 Windows

I'm sure you will solve your problem with the help of this community and will change your mind once the OS running properly.

I had a similar problem with a notebook, but in my case I wasn't able to install Ubuntu. The notebook was purchased with another Linux distribution, not currently maintained. After days trying to install I discovered that the problem was due to a tampered motherboard. The manufacturer change some settings in the motherboard to get the Windows Vista compatibility logo and this modification was preventing any modern Linux distribution to be installed. After reading some posts here, I was able to bypass this issue and install Ubuntu, which I'm using on all machines here very happily. 

So, before making up your mind, you should realize that most of the problems with Ubuntu are not due to lack of quality, but due to greedy corporations that do not provide hardware support for it and sometimes they screw the ones that are supported.

---

### Post by mvalviar on 2009-03-19
Any messages at the GRUB prompt we should know about?

---

### Post by ckh1 on 2009-03-19
no error messages at the grub prompt.
I will try the suggestions.
Thanks for the score keeping explanation, definately made me smile!
I am willing to try anything, to be set free from Microsoft!
thanks I will let you all know if the suggestions worked!

---

### Post by linuxisevolution on 2009-03-19
> **LowSky said:**
> Ever try to install Windows XP on a computer with SATA drives and No floppy drive... yeah you can't, and tell me who even buys a floppy drive anymore.

All those issues you see, is nothing but people with minor issues. But then again the web is full of Windows Forums of people with problems too. Besides people are here to post issues not to post success, thats another part of this forum.

You say you got some grub prompt, could you be more specific, did the screen say some error?

if it is just a prompt, just enter your name then password, then type startx, it will boot into the Os you saw during the LiveCD

I installed Windows Xp with 2 sata drives, and did not have to use a floppy for drivers. The drivers were included...

---

### Post by ckh1 on 2009-03-19
enter name and then password at the grub prompt?...what name and password would that be?

whatever I type and hit enter for I get Error 27: Unrecognized command

not sure if this means anything, before the grub prompt at the top of the screen:
GRUB4DOS 0.4.4 2008-10-27, Memory: 636K / 509M, CodeEnd: 0x42910  [ Minimal BASH- like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists the possible completions of a device/filename. ]

---

### Post by Paqman on 2009-03-19
So did the LiveCD actually run alright? If so i'd say something went awry with your install attempt (which is probably not your fault). If that's the case i'd try reinstalling and hoping for better luck.

One thing to watch out for: how fast did you burn the CD? For software you should always burn at the slowest speed possible. Media files like music and movies has lots of error-checking built in to deal with the errors in disk burning you get if you burn quickly, but with software those errors mean it just won't work. Try to burn at x4 or under, and check the disk integrity before starting an install.

---

### Post by ckh1 on 2009-03-19
I got it to work. I just uninstalled it and the re-installed it.
Now for other issues....
Thanks guys.

---

### Post by Paqman on 2009-03-19
No problem. If you need help with anything you'll find most of the questions people have post-install have been asked a million times. Just use the search feature and you'll probably get an answer straight away. Otherwise feel free to post your problems in a new thread.

---

