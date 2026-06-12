---
title: "Ubuntu Messed Up My Windows Partition"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by RookieUbuntuUser58 on 2009-02-24
I decided to dual boot XP Pro and Ubuntu on my desktop. Well I decided to delete the recovery/drivers package (backup) that was in the first partition. So in my boot.ini I changed Windows Pro to 1 (as it was 2 before with the backup partition first). Anyway the install of Ubuntu went fine and I rebooted. I tried to enter Windows Pro through Grub but it takes me to a black screen where nothing happens at all (no errors or anything). In Ubuntu I made sure the Windows partition had the boot flag and it did but still luck. I tried to mount the drive to see the XP Pro files and I get this error (see attached image). Anyway I need my Windows partition as it has all my engineering software and etc. It would be appreciated if you guys could help me get it back (as it isn't deleted). Thanks.

---

### Post by Panzor on 2009-02-24
Ooooh, I think I know why that's happening. Windows stuff tends to complain when you have to hard boot it (hold down the button, I think other people have different names for that), and you really had no choice...hmm.

Does using the terminal to mount it work?

```
$sudo mkdir /mnt/windows
$sudo mount /dev/sda1 /mnt/windows
```
**replace /dev/sda1 with the correct device ("#fdisk -l" will tell you which) and the /mnt/windows directory should end up to be something akin to your C: drive**

If not, trying forcing it with the -f option and if THAT doesn't work...I think you'll have to get in to ntfs-3g stuff. I haven't needed to get into that, so I'm not your best resource, sorry :<.

---

### Post by Hobgoblin on 2009-02-24
> **boost3d23 said:**
> I decided to dual boot XP Pro and Ubuntu on my desktop. Well I decided to delete the recovery/drivers package (backup) that was in the first partition. So in my boot.ini I changed Windows Pro to 1 (as it was 2 before with the backup partition first). 

Can you explain in detail what you did.  Did you delete the recovery partition and install Ubuntu there?

Can you copy/paste the contents of the boot.ini and explain what you changed?

You could do as suggested in the screenshot you posted and force mount the ntfs partition but it would be better to mount it under Windows first.

---

### Post by RookieUbuntuUser58 on 2009-02-25
> **Panzor said:**
> Ooooh, I think I know why that's happening. Windows stuff tends to complain when you have to hard boot it (hold down the button, I think other people have different names for that), and you really had no choice...hmm.

Does using the terminal to mount it work?

```
$sudo mkdir /mnt/windows
$sudo mount /dev/sda1 /mnt/windows
```
**replace /dev/sda1 with the correct device ("#fdisk -l" will tell you which) and the /mnt/windows directory should end up to be something akin to your C: drive**

If not, trying forcing it with the -f option and if THAT doesn't work...I think you'll have to get in to ntfs-3g stuff. I haven't needed to get into that, so I'm not your best resource, sorry :<.

Okay I did that and it seems to have mounted it. I found all my Windows files under filesystem>mnt>windows. When I do fdisk -l though it says unable to read sda drive but I know the Windows partition so I was able to mount it. 

> **Hobgoblin said:**
> Can you explain in detail what you did.  Did you delete the recovery partition and install Ubuntu there?

Can you copy/paste the contents of the boot.ini and explain what you changed?

You could do as suggested in the screenshot you posted and force mount the ntfs partition but it would be better to mount it under Windows first.

I deleted the recovery partition and left that as free space. Then under my Windows partition I created the extended partition for the Ubuntu logical partitions. So essentially my Windows partition in the boot.ini was 2 before, since I removed the partition ahead of it; I changed the value to 1.

```
[boot loader]

timeout=5

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /noguiboot
```

Anyway I got it mounted. But Im cautious about trying to enter Windows XP Pro from the Grub bootloader, as this might happen again. Any other steps I have to take before trying to enter it?


Edit: NVM It seems to work now. I was able to boot into Windows from Grub. Thanks guys for the help.

---

### Post by Ravernomina on 2009-02-25
Try this command and let us know if it works.
Step 1. Pop in you windows XP DIsk and boot from it.
step 2. Enter the Recovery mode by selecting "R" when seeing the option at th ebottom of the screen.
step 3. Select You windows Partition.
step 4. Once in DOS type in these Codes....
**_bootcfg_**

Read about it more [http://pcsupport.about.com/od/termsb/p/bootcfg.htm]("http://pcsupport.about.com/od/termsb/p/bootcfg.htm")

---

### Post by billgoldberg on 2009-02-25
> **boost3d23 said:**
> I decided to dual boot XP Pro and Ubuntu on my desktop. Well I decided to delete the recovery/drivers package (backup) that was in the first partition. So in my boot.ini I changed Windows Pro to 1 (as it was 2 before with the backup partition first). Anyway the install of Ubuntu went fine and I rebooted. I tried to enter Windows Pro through Grub but it takes me to a black screen where nothing happens at all (no errors or anything). In Ubuntu I made sure the Windows partition had the boot flag and it did but still luck. I tried to mount the drive to see the XP Pro files and I get this error (see attached image). Anyway I need my Windows partition as it has all my engineering software and etc. It would be appreciated if you guys could help me get it back (as it isn't deleted). Thanks.

Excuse me but I have to say this:

Ubuntu did not mess up your Windows partition, you did.

--

The error you get is because you didn't close down Windows properly.

The NTFS partition is locked then and Ubuntu can't access it.

You could try to force mount it, but I've read that could be dangerous. Haven't done this myself.

---

### Post by mlentink on 2009-02-25
> **billgoldberg said:**
> Excuse me but I have to say this:

Ubuntu did not mess up your Windows partition, you did.

--

The error you get is because you didn't close down Windows properly.

The NTFS partition is locked then and Ubuntu can't access it.


+1 !

Bill beat me to it..

---

### Post by detroit/zero on 2009-02-25
> **mlentink said:**
> +1 !

Bill beat me to it..
+1 

It was the first thing that came to mind just seeing the title.

---

### Post by RookieUbuntuUser58 on 2009-02-25
> **billgoldberg said:**
> Excuse me but I have to say this:

Ubuntu did not mess up your Windows partition, you did.

--

The error you get is because you didn't close down Windows properly.

The NTFS partition is locked then and Ubuntu can't access it.

You could try to force mount it, but I've read that could be dangerous. Haven't done this myself.

> **mlentink said:**
> +1 !

Bill beat me to it..

> **detroit/zero said:**
> +1 

It was the first thing that came to mind just seeing the title.

Why didn't I close down windows correctly. Because when I rebooted after the ubuntu install and entered windows it sat at a black screen for 20 minutes doing nothing. So what was I suppose to do. I'm not a amateur here, I've installed Ubuntu on other PC's. So yes it was Ubuntu that caused the problem from the beginning not me. It forced the improper shutdown option. So before you guys judge, get more info first, Ubuntu isn't always perfect. 

And yes I solved the problem.

---

### Post by mlentink on 2009-02-25
> **boost3d23 said:**
> Why didn't I close down windows correctly. Because when I rebooted after the ubuntu install and entered windows it sat at a black screen for 20 minutes doing nothing. So what was I suppose to do....And yes I solved the problem.


Suit yourself.
But maybe you'd like to consider that error message had nothing to do with what happened ***after*** you installed Ubuntu, but everything with what happened ***before*** you did. I have seen that error message before, quite a few times. Every time it had something to do with the way the user had shut down his/her windows/vista. I have yet to find a case in which an Ubuntu install really did something to the ntfs filesystem, which basically is what that error message is about.

---

### Post by RookieUbuntuUser58 on 2009-02-25
> **mlentink said:**
> Suit yourself.
But maybe you'd like to consider that error message had nothing to do with what happened ***after*** you installed Ubuntu, but everything with what happened ***before*** you did. I have seen that error message before, quite a few times. Every time it had something to do with the way the user had shut down his/her windows/vista. I have yet to find a case in which an Ubuntu install really did something to the ntfs filesystem, which basically is what that error message is about.

Well I can tell you for a fact it happened after my Ubuntu install. Why, because I closed Windows properly before I booted from a USB (to install Ubuntu). I have never done a unclean shutdown ever unless it is forced upon me (only option). And this situation didn't occur right before the install. So yeah your judgements are completely false regarding the situation.

---

