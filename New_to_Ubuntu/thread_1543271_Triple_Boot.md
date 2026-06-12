---
title: "Triple Boot?"
date: 2010-07-31
forum: New to Ubuntu
---

### Post by Kirkland14 on 2010-07-31
So on my laptop I have ubuntu and win7 dual booted all ready.  For one of my classes I have to use XP(I don't know why so old) .  I want to be able to also work on my homework on the go(I run XP and ubuntu on my desktop).  When I tried to install XP on my LT I got the dreaded blue screen, so I didn't try again.  I was just wondering if its even possible to do a triple boot and have it run smoothly? Thanks

Kevin

---

### Post by jtarin on 2010-07-31
Recommend you install XP,Win7, Ubuntu...in that order. Not possible? Have you a seperate partition for XP?
You could always install in Virtual Box.

---

### Post by Kirkland14 on 2010-07-31
> **jtarin said:**
> Recommend you install XP,Win7, Ubuntu...in that order. Not possible? Have you a seperate partition for XP?
You could always install in Virtual Box.


I guess I figured I would repartition the disk after the xp disk booted.  Doesn't work like that though huh? I'm kinda new to all this but learn pretty quick.  Thanks

Kevin

ps  the other thing is that I don't really want to uninstall and then reinstall the other 2(Win7 and ubuntu)

---

### Post by louieb on 2010-07-31
Just my 2 cents -  [Virtualization]("http://ubuntuforums.org/forumdisplay.php?f=308") is the way to go. VirtualBox OSE is in the repositories. But I would use the PUEL version of [VirtualBox]("http://www.virtualbox.org/").    If you have a couple of gig of memory its pretty easy to set up. - easier that trying to triple boot.

---

### Post by Kirkland14 on 2010-07-31
> **louieb said:**
> Just my 2 cents -  [Virtualization]("http://ubuntuforums.org/forumdisplay.php?f=308") is the way to go. VirtualBox OSE is in the repositories. But I would use the PUEL version of [VirtualBox]("http://www.virtualbox.org/").    If you have a couple of gig of memory it pretty easy to set up. - easier that trying to triple boot.

Sounds interesting!  I'll give it a try and let ya know.  Thanks

Kevin

---

### Post by Windows Nerd on 2010-07-31
> **louieb said:**
> Just my 2 cents -  [Virtualization]("http://ubuntuforums.org/forumdisplay.php?f=308") is the way to go. VirtualBox OSE is in the repositories. But I would use the PUEL version of [VirtualBox]("http://www.virtualbox.org/").    If you have a couple of gig of memory its pretty easy to set up. - easier that trying to triple boot.

And the other advantage is that you can boot into your XP virtual machine without having to stop what you are currently doing and reboot.

Doesn't Windows 7 have it's own sort of "XP emulator" for support for XP applications?

---

### Post by andrew.46 on 2010-08-01
Hi Kevin,

Another vote here for virtualisation. I attach a screenshot showing Slackware host with Windows 7 and Lucid Lynx guests on Virtualbox OSE.

Andrew

---

### Post by ottosykora on 2010-08-01
I made expereince that virtualization is something only for new and rather powerful computers.
On my not so new toshiba it is not of any practical use, since all goes so slow then, the boot of XP takes alone over 15 minutes.

I have w7, XP, ubuntu10, Debian lenny, Fedora12 on same drive booted by grub legacy. The grub legacy for convenience I have placed into its own separate partition at the and of the drive. This seems more simple to be edited then maintenance of all the grubs accumulated in the various linux versions.

Often people use for such setup the bootmanager provided by w7 too, which can do the same job apparently.

---

### Post by Kirkland14 on 2010-08-01
So win7 has it built in?  interesting.  I'm just waiting to get back to my house so I can get the xp disk.  I've been at my GF's house for the last day so haven't had a chance to try any of this out.  Thanks all for the info.  I'll post which one I found worked best for me. 

Kevin

---

### Post by Windows Nerd on 2010-08-01
> **Kirkland14 said:**
> So win7 has it built in?  interesting.  I'm just waiting to get back to my house so I can get the xp disk.  I've been at my GF's house for the last day so haven't had a chance to try any of this out.  Thanks all for the info.  I'll post which one I found worked best for me. 

Kevin

I'm not 100% sure that it has it built in, but I remember reading it somewhere across the internet.

With a quick Google search, I found this (Which confirms my remembering). It's called XP mode, which you apparently have to download:

[http://www.microsoft.com/windows/virtual-pc/download.aspx](http://www.microsoft.com/windows/virtual-pc/download.aspx)

Hope any of our suggestions work for you.

---

### Post by Kirkland14 on 2010-08-01
computers are so frustrating sometimes.  1st I got VB but when it comes to license code it says its not valid(but I know it is) and then when I tried the microsoft download for win7 apparently you have to have home premium or better( I only have the normal home edition 64bit(FU MS).  any Ideas?  Thanks

Kevin

---

### Post by Kirkland14 on 2010-08-01
So apparently win XP H.E. is okay to run on VB and the code I thought I had for my Pro is actually the H.E. code.  But it all works now.  Thanks for everybodys info.

Kevin

---

### Post by Windows Nerd on 2010-08-26
> **ottosykora said:**
> I made expereince that virtualization is something only for new and rather powerful computers.
On my not so new toshiba it is not of any practical use, since all goes so slow then, the boot of XP takes alone over 15 minutes.

I have w7, XP, ubuntu10, Debian lenny, Fedora12 on same drive booted by grub legacy. The grub legacy for convenience I have placed into its own separate partition at the and of the drive. This seems more simple to be edited then maintenance of all the grubs accumulated in the various linux versions.

Often people use for such setup the bootmanager provided by w7 too, which can do the same job apparently.

Though I know this thread is solved, I feel that I need to respond to this post, as it may benefit others reading this thread when searching the forum for this issue.

I virtualize on a P4 computer from 2003. XP still runs like a champ in a Virtual Machine (and better than when it was installed and actually run with the real machine.

I should also note that I run a Arch Linux environment with openbox, which is pretty lightweight. I am not sure how XP would run with Ubuntu installed with several applications running. XP uses about 1-1.5GB of RAM, so your virtualbox experience with XP _will_ depend on how much RAM you have installed on your machine.

Scott

---

