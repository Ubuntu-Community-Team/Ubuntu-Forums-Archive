---
title: "speed up xp in virtualbox !"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by MBG1987 on 2009-10-20
i didn't log on to the forum from loong time !! 
I just installed window$ xp on my ubuntu distro via virtualbox, but it's a bit slow I don't exactly y!! I thing the size of RAM and VGA specified for xp was little or large ,don't know! 
so what is the appropriate size of RAM and VGA for such OS.... My total RAM is 512 and VGA 256 
I hope to find the solution !! thnxxxxx

---

### Post by Marlonsm on 2009-10-20
I use 768 RAM and 128 VGA, so the VM will take about half of my 2Gb RAM, but it all depends on what you want to do with the VM.

---

### Post by howefield on 2009-10-20
> **MBG1987 said:**
> My total RAM is 512 and VGA 256

I'd say you need at least one gig to get decent performance running a virtualised system. You might get away with a little less, but 512 total ? Don't think so.

You might be better looking at dual booting or adding more memory..

---

### Post by HotShotDJ on 2009-10-20
> **MBG1987 said:**
> My total RAM is 512 and VGA 256 
I hope to find the solution !! thnxxxxxPlease clarify... when you say "total RAM is 512," do you mean the total RAM that is installed in your computer, or the total RAM that you have set up for your XP virtual machine to use.  If it is the former, then the only solution is to buy some more physical RAM.  My experience is that XP doesn't run very well with much less than 1G RAM, even when installed directly on the hardware.  You really need at least 2 Gig of physical RAM on your box in order to run Windows in a virtual machine.  The slowness that you are experiencing is probably due to some serious disk swapping, both by the host OS and the guest OS.

---

### Post by MBG1987 on 2009-10-20
[Marlonsm]("http://ubuntuforums.org/member.php?u=792604") [, howefield]("http://ubuntuforums.org/member.php?u=186490") , [HotShotDJ ]("http://ubuntuforums.org/member.php?u=196293")
thnx for replies ! I was think that the problem with the VB itself , but i will try to buy some memory to my  system that's nice solution 
thnxx agin !!

---

### Post by Mike_IronFist on 2009-10-20
> **MBG1987 said:**
> [Marlonsm]("http://ubuntuforums.org/member.php?u=792604") [, howefield]("http://ubuntuforums.org/member.php?u=186490") , [HotShotDJ ]("http://ubuntuforums.org/member.php?u=196293")
thnx for replies ! I was think that the problem with the VB itself , but i will try to buy some memory to my  system that's nice solution 
thnxx agin !!

My computer has 3 GB of RAM and I dedicate 512 MB to XP.

If you only have 512 MB total RAM, you don't really have enough RAM to run a virtual machine very well. So yeah, you'll want at minimum 1 GB of RAM before you try running virtual machines, and preferably 2 GB or more.

---

### Post by MBG1987 on 2009-10-21
> **Mike_IronFist said:**
> and preferably 2 GB or more.

I thing this's tooo much with my little budget !! lol

---

### Post by eriktheblu on 2009-10-21
With 512 MB total system memory, you're not going to get a whole lot of performance. XP technically requires 128, but in it's default configuration it will craw with less than 512.

If increasing system resources is not an option, and multi-boot doesn't meet your needs, the next thing to do is free up resources by eliminating unused processes. For Windows, [Black Viper](http://www.blackviper.com/) has excellent guides. In Ubuntu, all I can recommend is disabling compiz, or switching to a lighter desktop (XFCE, LXDE). I'm sure wiser men than I can come up with better means to slim down your Ubuntu if needed.

---

### Post by NightwishFan on 2009-10-21
You should check your bios for any settings on virtualization for intel/amd vt. There is also a checkbox to enable it in Vbox. My setting is under power settings in bios. It improves performance and reliability a good deal. Please note that you should disable the VT setting in bios after you are done with virtualization.

[http://en.wikipedia.org/wiki/X86_virtualization#Hardware_support](http://en.wikipedia.org/wiki/X86_virtualization#Hardware_support)

---

### Post by compiledkernel on 2009-10-21
[http://gwos.org/udsf/doku.php/software:virtualbox](http://gwos.org/udsf/doku.php/software:virtualbox) , should show some guidance.

---

