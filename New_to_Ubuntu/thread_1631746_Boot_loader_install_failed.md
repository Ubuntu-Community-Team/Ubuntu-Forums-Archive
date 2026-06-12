---
title: "Boot loader install failed"
date: 2010-11-27
forum: New to Ubuntu
---

### Post by Strange Wolfy on 2010-11-27
Ok sorry i'm back. I'm Trying to install 10.10 but it failed to install the grub help! Oh and it gives me 3 options choose a different device to install the boot loader on continue without boot loader or cancel installation but it wont let me continue no matter how many time i click ok.

---

### Post by lmarmisa on 2010-11-27
Normally, you should select /dev/sda for installing grub.

---

### Post by sikander3786 on 2010-11-27
It will only show that option if you have more than one HDDs.

And if so, you should install Grub to the MBR of the drive you are installing Ubuntu to (if your Bios has the option to boot from that HDD).

It would be better to know how many HDDs and which OS is previously installed there and on which drive?

---

### Post by Strange Wolfy on 2010-11-27
I do but it does not let me click ok.

---

### Post by wilee-nilee on 2010-11-27
Lets make this fairly easy, hopefully. Run the bootscript in my signature. Post the text generated to code tags as described also in my signature.

---

### Post by Strange Wolfy on 2010-11-27
> **sikander3786 said:**
> It will only show that option if you have more than one HDDs.

And if so, you should install Grub to the MBR of the drive you are installing Ubuntu to (if your Bios has the option to boot from that HDD).

It would be better to know how many HDDs and which OS is previously installed there and on which drive?
I only have one hdd in it but it also reads the usb im installing it from and no previous os on it and how do I go as for installing grub.

---

### Post by lmarmisa on 2010-11-27
> **Strange Wolfy said:**
> I do but it does not let me click ok.

If you are unsure about your selection or you get problems selecting /dev/sda, try to continue without boot loader. In this case, a GRUB install procedure will be needed later.

---

### Post by Strange Wolfy on 2010-11-27
> **lmarmisa said:**
> If you are unsure about your selection or you get problems selecting /dev/sda, try to continue without boot loader. In this case, a GRUB install procedure will be needed later.

I choose the option but when i click ok it dosnt do anything.

---

### Post by Strange Wolfy on 2010-11-27
See

---

### Post by lmarmisa on 2010-11-27
What kind of installation are you trying to do?. Install alongside other operating systems?. Erase and use the entire disk?. Specify partitions manually?.

---

### Post by Strange Wolfy on 2010-11-27
> **lmarmisa said:**
> What kind of installation are you trying to do?. Install alongside other operating systems?. Erase and use the entire disk?. Specify partitions manually?.

 Erase and use the entire disk

---

### Post by wilee-nilee on 2010-11-27
Look at my post and post the bootscript. To be honest without the information in it we are flailing in the dark.

Use the code tags as described in my signature and the bootscript link is there as well.

---

### Post by lmarmisa on 2010-11-27
Please, open a terminal, type this command and post its output:

```

sudo fdisk -l

```

---

### Post by Strange Wolfy on 2010-11-27
> **lmarmisa said:**
> Please, open a terminal, type this command and post its output:

```

sudo fdisk -l

```
Disk /dev/sda: 966 MB, 966787072 bytes
255 heads, 63 sectors/track, 117 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6e594b12

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         118      944096+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(116, 254, 63) logical=(117, 137, 20)

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000dbd55

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19076   153219072   83  Linux
/dev/sdb2           19076       19458     3068929    5  Extended
/dev/sdb5           19076       19458     3068928   82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by wilee-nilee on 2010-11-27
See yah PM me if you can't get it fixed and have posted the script and code tagged it.

---

### Post by lmarmisa on 2010-11-27
Is your hard drive external (USB)?.

---

### Post by Strange Wolfy on 2010-11-27
> **lmarmisa said:**
> Is your hard drive external (USB)?.
No

---

### Post by lmarmisa on 2010-11-27
> **Strange Wolfy said:**
> No

What kind of device is /dev/sda?. A pendrive?.

---

### Post by sikander3786 on 2010-11-27
You need to provide the info **wilee-nilee** has been asking for over and over.

Hope you can fix it yourself. Or please provide the output of bootinfoscript in order to let us advise on that.

Good Luck!

---

### Post by wilee-nilee on 2010-11-27
> **sikander3786 said:**
> You need to provide the info **wilee-nilee** has been asking for over and over.

Hope you can fix it yourself. Or please provide the output of bootinfoscript in order to let us advise on that.

Good Luck!

Thanks man you or I could have **probably** had this fixed a hour ago if the script was just posted. And the mod who wrote all the great grub tutorials is online.

---

### Post by lmarmisa on 2010-11-27
I attach here the captures explaining step by step how to install Ubuntu 10.10 Desktop Edition in your case. I suppose the case of Ubuntu Remix will be very similar.

Pay attention in step 4 to select drive sdb.

If you are asked during the installation to define the device for the grub loader select **/dev/sdb**.

NOTE: I post here the 5 first captures.

---

### Post by lmarmisa on 2010-11-27
Other captures here.

---

### Post by sikander3786 on 2010-11-27
> **wilee-nilee said:**
> Thanks man you or I could have **probably** had this fixed a hour ago if the script was just posted. And the mod who wrote all the great grub tutorials is online.
We are open for help but nobody needs us :-)

I am still keeping an eye on the thread though ;-)

---

### Post by Strange Wolfy on 2010-11-27
Sorry Guys I feel asleep last night it was really late here when I was posting. Aww I think the installation is working now When I woke up a few minutes ago I tried again this time it is not giving me the same error. Weird? last night I must a tried like hundred of times and failed. Well i'm not sure yet cause it is downloading pages Ill post back when its done.:popcorn:

---

### Post by Strange Wolfy on 2010-11-27
Okay it says installing system

---

### Post by Strange Wolfy on 2010-11-27
Fail it said it installed but when I turned the netbook on the screen turns black and has 1 white line blinking.

---

### Post by Strange Wolfy on 2010-11-27
aww i plugged the usb in the rebooted and it booted up the installed netbook? What did I do?

---

### Post by lmarmisa on 2010-11-27
> **Strange Wolfy said:**
> Fail it said it installed but when I turned the netbook on the screen turns black and has 1 white line blinking.

You does not need to reinstall. The problem is related to the grub loader that is writen in the /dev/sda device.

You need to boot into a Live CD (or pendrive), open a terminal and type these commands:

```

sudo bash
mount /dev/sdb1 /mnt
mount --bind /dev /mnt/dev
chroot /mnt
grub-install /dev/sdb
exit
exit
exit

```I believe the problem will be fixed with this procedure.

---

### Post by lmarmisa on 2010-11-27
> **Strange Wolfy said:**
> aww i plugged the usb in the rebooted and it booted up the installed netbook? What did I do?

Yes. You are booting up the installed Ubuntu system.

In this case, it is easier to fix the boot loader. Simply type this command:

```

sudo install-grub /dev/sdb

```

---

### Post by Strange Wolfy on 2010-11-27
> **lmarmisa said:**
> Yes. You are booting up the installed Ubuntu system.

In this case, it is easier to fix the boot loader. Simply type this command:

```

sudo install-grub /dev/sdb

```
The ternimal is asking for my password but wont let me type?

---

### Post by lmarmisa on 2010-11-27
The chars of your password are hidden but this is normal. Type your password and press return.

---

### Post by lmarmisa on 2010-11-27
> **lmarmisa said:**
> The chars of your password are hidden but this is normal. Type your password and press return.

Sorry. This is not my best day. :(

I missed the command.

This is the CORRECT command:

```

sudo grub-install /dev/sdb

```

---

### Post by Strange Wolfy on 2010-11-27
> **lmarmisa said:**
> Sorry. This is not my best day. :(

I missed the command.

This is the CORRECT command:

```

sudo grub-install /dev/sdb

```

Haha no wonder it said command not found haha its okay.

---

### Post by Strange Wolfy on 2010-11-27
Thanks its working now. I love you! Your the best.:KS

---

### Post by lmarmisa on 2010-11-27
Finally done. :D

Your system is very odd. Normally, the internal hard drive is detected as device /dev/sda but in your case this device is the USB stick and your internal hard drive is /dev/sdb.

And this was also a problem for the Ubuntu installer. We needed to fix the boot loader for this reason.

Anyway, congratulations and enjoy your Ubuntu Remix system.

Please, mark the thread as SOLVED.

Best regards,

Luis

---

### Post by theozzlives on 2010-11-27
Just for the sake of conversation, my boot drive is sdb (SATA) and my IDE drive is sda on one of my machines. Was a little confusing when setting up my fstab, but it does happen.

---

### Post by jonathandines on 2011-03-04
Hi, Sorry to jack this thread. I too am having a similar problem on my other notebook.
I went to install Ubuntu using entire hdd. I get to the bootloader install failed. I can't use any other options. Could you please detail what I can do to rectify this asap

Thanks

---

### Post by jonathandines on 2011-03-04
I'd of cancelled the installation despite there message that it may leave my computer unable to boot if //i was able to click it.

:( anybody there?

---

### Post by Andrey0614 on 2011-03-24
any body here? trying to install ubuntu 10.10 and having "boot loader install failed" message. cant choose any options. keep pressing them, but no response.

---

