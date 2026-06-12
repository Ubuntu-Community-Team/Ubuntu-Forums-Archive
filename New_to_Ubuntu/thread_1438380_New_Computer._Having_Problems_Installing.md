---
title: "New Computer. Having Problems Installing"
date: 2010-03-24
forum: New to Ubuntu
---

### Post by Hastor on 2010-03-24
Okay, first off, hello. I'm quite new to this forum.
On to other business. I just acquired a dell studio computer. For some reason or another I cannot seem to get Ubuntu to work properly. I can install it easily by using the direct install option, and the process works out pretty well. The problem occurs when, after rebooting, I click on ubuntu when deciding which operating system to use. At this point, my computer screen goes blank and it seems that no matter how long I wait Ubuntu doesn't start up. Any help?

---

### Post by Hastor on 2010-03-24
Okay, first off, hello. I'm quite new to this forum.
On to other business. I just acquired a dell studio computer. For some reason or another I cannot seem to get Ubuntu to work properly. I can install it easily by using the direct install option, and the process works out pretty well. The problem occurs when, after rebooting, I click on ubuntu when deciding which operating system to use. At this point, my computer screen goes blank and it seems that no matter how long I wait Ubuntu doesn't start up. Any help would be much appreciated. Thank you.

---

### Post by k3lt01 on 2010-03-25
Ok, some questions. Just trying to get an idea of what you have done and how you have done it and what type of system you have.

What did you use to install Ubuntu with? the Ubuntu from Ubuntu or Ubuntu from Dell? Yes Dell have their own version for their own machines.
What are your computers specs?
What version of Ubuntu did you use? 8.04, 8.10, 9.04, 9.10?
Have you read the [Dell section of this forum]("http://ubuntuforums.org/forumdisplay.php?f=342")?

If you can give some more information it would help us to help you better.

---

### Post by QIII on 2010-03-25
Could you give us some more specifics, such as...

The version of Ubuntu you have installed and as much detail as you can give us about the specifications of the machine?

---

### Post by kooia on 2010-03-25
So the GRUB section? The part where you can choose between Windows or Linux?

Well, you need to make sure your computer is totally off, not in sleep mode or anything.  I think Ubuntu has a bug... Sleep doesn't work.  When you get to the GRUB, press ENTER.  Try that... I think it might work better.

Maybe the problem you're having is that your BIOS settings are still set to boot from the CD.  Change the BIOS settings back to the HDD (hard drive) as the primary drive.  I had this problem, too.  It becomes extra problematic if there's no CD in there.

So make sure that your BIOS settings has your Hard Drive as the Primary boot device.

P.S.  I'm really new, too.  Ubuntu, you'll find out, is a very fast (but complicated) operating system.

---

### Post by Hastor on 2010-03-25
> **k3lt01 said:**
> Ok, some questions. Just trying to get an idea of what you have done and how you have done it and what type of system you have.
 
What did you use to install Ubuntu with? the Ubuntu from Ubuntu or Ubuntu from Dell? Yes Dell have their own version for their own machines.
What are your computers specs?
What version of Ubuntu did you use? 8.04, 8.10, 9.04, 9.10?
Have you read the [Dell section of this forum]("http://ubuntuforums.org/forumdisplay.php?f=342")?
 
If you can give some more information it would help us to help you better.
 
 
1) I installed Ubuntu from the Ubuntu site. I used the direct download option.
2) All I have is a huge list of stuff that went on my computer. What specific specs are necessery?
3) I'm 99% sure I downloaded 9.10
4) I'm currently looking over the Dell section.
 
Thank you very much for giving a helping hand. I will assist you to the best of my ability.

---

### Post by Hastor on 2010-03-25
> **kooia said:**
> So the GRUB section? The part where you can choose between Windows or Linux?
 
Well, you need to make sure your computer is totally off, not in sleep mode or anything. I think Ubuntu has a bug... Sleep doesn't work. When you get to the GRUB, press ENTER. Try that... I think it might work better.
 
Maybe the problem you're having is that your BIOS settings are still set to boot from the CD. Change the BIOS settings back to the HDD (hard drive) as the primary drive. I had this problem, too. It becomes extra problematic if there's no CD in there.
 
So make sure that your BIOS settings has your Hard Drive as the Primary boot device.
 
P.S. I'm really new, too. Ubuntu, you'll find out, is a very fast (but complicated) operating system.
 
Thank you very much, but how would I find the BIOS settings? Thank you.

---

### Post by coffeecat on 2010-03-25
You don't need to change the BIOS settings. If the BIOS is set to boot from the optical drive first and there is no bootable CD or DVD in it, it will simply boot from the hard drive. In fact that is what is happening already if you are getting the menu to choose between Windows or Ubuntu.

Also, I doubt whether this is a sleep problem. Ubuntu does not have a bug affecting sleep. Some implementations of ACPI cause issues with sleep in Ubuntu but this is probably only in a minority of machines. I have two laptops and two desktops - all different - and sleep works just fine in Ubuntu in all of them.

Questions:

Did you install a wubi install or a side-by-side dual-boot with Ubuntu on its own partition? If you're not sure what wubi is, have a look here:

[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

If that looks familiar - then you are using Wubi.

Have you tried running Ubuntu from a live CD? For this you do need the BIOS set to boot from the optical drive first. :wink: If it is a wubi install, but your machine will boot to an Ubuntu desktop from a live CD, that would be useful to know.

I'm not familiar with the Dell range, so please post details of the hardware, particularly graphics. That might give us a clue.

---

### Post by overdrank on 2010-03-25
Hi and welcome, please do not create multiple threads on the same issue. Threads merged :)

---

### Post by Hastor on 2010-03-25
> **coffeecat said:**
> You don't need to change the BIOS settings. If the BIOS is set to boot from the optical drive first and there is no bootable CD or DVD in it, it will simply boot from the hard drive. In fact that is what is happening already if you are getting the menu to choose between Windows or Ubuntu.
 
Also, I doubt whether this is a sleep problem. Ubuntu does not have a bug affecting sleep. Some implementations of ACPI cause issues with sleep in Ubuntu but this is probably only in a minority of machines. I have two laptops and two desktops - all different - and sleep works just fine in Ubuntu in all of them.
 
Questions:
 
Did you install a wubi install or a side-by-side dual-boot with Ubuntu on its own partition? If you're not sure what wubi is, have a look here:
 
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)
 
If that looks familiar - then you are using Wubi.
 
Have you tried running Ubuntu from a live CD? For this you do need the BIOS set to boot from the optical drive first. :wink: If it is a wubi install, but your machine will boot to an Ubuntu desktop from a live CD, that would be useful to know.
 
I'm not familiar with the Dell range, so please post details of the hardware, particularly graphics. That might give us a clue.
 
I tried running Ubuntu through Daemon tools which I would assume is similar to running it off a CD. Now, I think there is something wrong with how my computer boots as opposed to there being something wrong with ubuntu. I decided to try to boot up ubuntu and leave it for as long as possible once the screen went black. I came back to notice that it had instead booted windows 7. This makes me think that my computer is entirely overlooking ubuntu or something. Other than that, I think my computer has the ability to run Ubuntu but there is just something wrong in the settings. I mean, this is a brand new, 2010 computer. I'm near certain it has the processing ability to run Ubuntu. Aside from that, I'm out of ideas.

---

### Post by k3lt01 on 2010-03-25
> **Hastor said:**
> 1) I installed Ubuntu from the Ubuntu site. I used the direct download option.
2) All I have is a huge list of stuff that went on my computer. What specific specs are necessery?
3) I'm 99% sure I downloaded 9.10
4) I'm currently looking over the Dell section.
 
Thank you very much for giving a helping hand. I will assist you to the best of my ability. Check my signature at the bottom of this post, it has my laptops general specs. If you can tell us what your general specs are, or better yet put it in a signature, we can possibly be more helpful.

> **Hastor said:**
>  I decided to try to boot up ubuntu and leave it for as long as possible once the screen went black. I came back to notice that it had instead booted windows 7.Did you boot and then leave your PC? So you weren't watching it am I correct? If I am try it again but stay and watch what happens.

---

### Post by coffeecat on 2010-03-26
> **Hastor said:**
> I tried running Ubuntu through Daemon tools which I would assume is similar to running it off a CD.

No, it isn't. As far as I can see Daemon Tools is a Windows app that allows you to run a CD virtually. Which means that Ubuntu would be running virtually, which is more or less what it is doing (or trying to do) in Wubi - except that you didn't answer my question about wubi. Virtualising Ubuntu is not the same as running Ubuntu **properly**.

For information about the live CD, see here:

[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

And we still haven't seen your system specs. Without relevant information it's impossible to be more helpful.

---

### Post by mastablasta on 2010-03-26
No wonder it's not working. Daemon tools is not the way to install an operating system. 
 
Read this book before using Linux:
[[COLOR=#444444]http://www.ubuntupocketguide.com/[/COLOR]]("http://www.ubuntupocketguide.com/")
 
It will give information on how to install Ubuntu (ver8.04, but it s the same with 9.10)
 
If you want virtual version of the system then the post above already answered it.
 
Also you will need to get Dell Ubuntu version i think to make everything work with more ease..
 
You can see more on this here: [http://ubuntuforums.org/showthread.php?t=1141757](http://ubuntuforums.org/showthread.php?t=1141757)
 
There is also a 9.10 version out there. Do some search.

---

### Post by Hastor on 2010-03-26
Thanky you. I have actually achieved installing an earlier version (9.04) and it is workign well. The only problem I am having now is that it is not connecting to a wireless network. I know that there is another forum for this type of problem, but I was wondering whether this might have arrisen out of a poor installation process. Thank you.

---

### Post by k3lt01 on 2010-03-26
If you had used the Dell version of Ubuntu you shouldn't have any difficulties at all now.

I'm assuming because you are having difficulties you didn't use the Dell version. So my recommendation is that you now ask your questions on the Dell section of this forum.

---

### Post by Hastor on 2010-03-27
Thank you very much for your time. I will look into this dell version and report back on its successfullness. Thanks again. ;)

---

### Post by sandyd on 2010-03-27
i currently have a studio 1737. just install the package "bcmwl-kernel-source" and you should be redy to go. (assuming 9.04) has that package. & that the card is a broadcom one.

---

### Post by b33tfr33kr on 2010-03-27
i see no reason that 9.10 would not run on your machine. it's new and common.  i also think that using the Dell version of 9.10 will solve your problem.  also, once your system is installed, run the update manager with a wired internet connection to see if that fixes your wifi.

---

### Post by Hastor on 2010-03-28
> **b33tfr33kr said:**
> i see no reason that 9.10 would not run on your machine. it's new and common.  i also think that using the Dell version of 9.10 will solve your problem.  also, once your system is installed, run the update manager with a wired internet connection to see if that fixes your wifi.

I tried doing this and I was able to procure the 9.10 version through a wired connection, but it is still not recognising my wireless network. From now one I will be posting in the Dell section so I will probably not be able to reply as readily to your replies as I would like. Thank you all for your help.

---

