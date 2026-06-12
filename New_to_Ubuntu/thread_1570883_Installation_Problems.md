---
title: "Installation Problems"
date: 2010-09-08
forum: New to Ubuntu
---

### Post by Zachmarius on 2010-09-08
Hello all,

I am new to Ubuntu and was drawn to it for it's simplicity. I do know how to work some minor bootable things but I am not a tech wiz by any standard. I have installed Ubuntu's version 8 before and wanted to try out their latest. 10.04. THis unfortunately has not happened yet.

Computer specs
Compaq Presario SR1000V
Intel Pentium 4 2.6GHz
No Floppy
CD Lite on DVD+RW
HDD Seagate ST31202A 120GB
Mem - 512MB PC2100 (Two sticks of 256)
Running Phoenix BIOS

Now I've installed Windows 2000, Win XP, as well as Win7 on this computer. (All at different times) Each time the installation has gone through without a hitch. No problems whatsoever. However when I try to load the Ubuntu disc (4th burned disc I've tried) I get to the installation screen and press install. After a bit of text it stops loading at

...
[ 4.269953] [<c0208e82>] sys_write+0x42/0x70
[ 4.269953]  [<c01033ec>] syscall_call+0x7/0xb

If I run it after disabling all the boot parameters I get a bunch of text and it stops loading at

...
[ 4.430514] Call Trace:
[ 4.430599] [<c058a676>] ? printk+0x1d/0x1f
[ 4.430676] [<c058a5ae>] panic+0x48/0xf3
[ 4.430757] [<c014eccd>] forget_original_parent+0x2bd/0x2c0
[ 4.430836] [<c014ece3>] exit_notify+0x13/0x170
[ 4.430913] [<c01505f1>] do_exit+0x181/0310
[ 4.430991] [<c058dbe5>] oops_end+0x95/x50
[ 4.431071] [<c012b47c>] no_context+0xbc/0xe0
[ 4.431148] [<c012b447c>] __bad_area_nosemaphore+0x3c/x160
[ 4.431231] [<c01cf947>] ? get_page_from_freelist+x147/x360
[ 4.431312] [<c12b617>] bad_area_nosemaphore+0x17/0x20
...
[ 4.432021] [<c058db3>] error_code+0x73/0x80

I honestly don't know what to do with all these error codes and whatnot. I'm tempted to just give up after 4 cds burned, No option with USB (I've tried), and wait for a even more stable version. Or try a different OS.

---

### Post by sandyd on 2010-09-08
> **Zachmarius said:**
> Hello all,

I am new to Ubuntu and was drawn to it for it's simplicity. I do know how to work some minor bootable things but I am not a tech wiz by any standard. I have installed Ubuntu's version 8 before and wanted to try out their latest. 10.04. THis unfortunately has not happened yet.

Computer specs
Compaq Presario SR1000V
Intel Pentium 4 2.6GHz
No Floppy
CD Lite on DVD+RW
HDD Seagate ST31202A 120GB
Mem - 512MB PC2100 (Two sticks of 256)
Running Phoenix BIOS

Now I've installed Windows 2000, Win XP, as well as Win7 on this computer. (All at different times) Each time the installation has gone through without a hitch. No problems whatsoever. However when I try to load the Ubuntu disc (4th burned disc I've tried) I get to the installation screen and press install. After a bit of text it stops loading at

...
[ 4.269953] [<c0208e82>] sys_write+0x42/0x70
[ 4.269953]  [<c01033ec>] syscall_call+0x7/0xb

If I run it after disabling all the boot parameters I get a bunch of text and it stops loading at

...
[ 4.430514] Call Trace:
[ 4.430599] [<c058a676>] ? printk+0x1d/0x1f
[ 4.430676] [<c058a5ae>] panic+0x48/0xf3
[ 4.430757] [<c014eccd>] forget_original_parent+0x2bd/0x2c0
[ 4.430836] [<c014ece3>] exit_notify+0x13/0x170
[ 4.430913] [<c01505f1>] do_exit+0x181/0310
[ 4.430991] [<c058dbe5>] oops_end+0x95/x50
[ 4.431071] [<c012b47c>] no_context+0xbc/0xe0
[ 4.431148] [<c012b447c>] __bad_area_nosemaphore+0x3c/x160
[ 4.431231] [<c01cf947>] ? get_page_from_freelist+x147/x360
[ 4.431312] [<c12b617>] bad_area_nosemaphore+0x17/0x20
...
[ 4.432021] [<c058db3>] error_code+0x73/0x80

I honestly don't know what to do with all these error codes and whatnot. I'm tempted to just give up after 4 cds burned, No option with USB (I've tried), and wait for a even more stable version. Or try a different OS.
run memtest (press esc when the purple ubuntu screen first shows up)
[check md5 of iso]("https://help.ubuntu.com/community/HowToMD5SUM")

---

### Post by Jazzy_Jeff on 2010-09-08
Are you trying to use the Live CD? If so you may want to download the [alternate install cd.]("http://www.ubuntu.com/desktop/get-ubuntu/alternative-download")  It is text based but easy to follow. Make sure you burn it at the slowest speed available to make sure of a good burn.

---

### Post by Zachmarius on 2010-09-08
I cannot do a check md5. It says

Could not find kernal image: cd
Could not find kernal image: md5sum

I'll try the alternative cd right after this post.

---

### Post by Zachmarius on 2010-09-08
I just tried the alternative cd. Did a burn on the lowest setting I have and still came up with the error_code+0x73/x80

Any other ideas? I'd really like to get this working. Hey I'm stubborn. :)

---

### Post by Zachmarius on 2010-09-08
bump

---

### Post by sandyd on 2010-09-08
> **Zachmarius said:**
> bump
srry for late reply, was changing some stuff about myself on the net.

[http://www.memtest86.com/](http://www.memtest86.com/)
youll want to download the windows version and burn it to disc

---

### Post by Zachmarius on 2010-09-08
No problem at all. I know this is volunteer based so no worries. I downloaded it and it's running in my computer right now. The results are...

Pass Complete, no errors, press Esc to exit.

Pentium 4 (0.13) 2600Mhz
L1 Cache:     8K    18182 MB/s
L2 Cache: 512K    16456 MB/s
L3 Cache: None 
Memory    : 504M   778MB.s
Chipset     : Intel i845E/G/PE/GE   (ECC : Disabled) / FSB : 100Mhz

---

### Post by Zachmarius on 2010-09-08
bump

---

### Post by Miljet on 2010-09-09
Will the live CD boot without trying to install to disk? Will the live CD boot on another machine? What program are you using to burn the disk? And are you sure that you are burning it as an ISO image and not a data disk?

---

### Post by Zachmarius on 2010-09-09
I have determined that for some reason the problem is in my networking hardware. I took out the 56k modem that was built in but with no avail. The way I found this out was through the alternate cd of ubuntu.

I have tried kubuntu and even my old version of ubuntu 9.10 and it still hasn't worked. I have resigned myself to having Craprisoft on my computer for now. I don't know if ubuntu will have a fix for this at somepoint but as I don't know exactly what is wrong I can't exactly give them the point in which it won't work. Besides writing letter for letter the codes that came up on the screen I can't think of anything else.

Thanks for all who gave their help on this one. I really would like to get this running but it seems that there currently isnt' an OS besides Windows that works on this machine.

---

### Post by Zachmarius on 2010-09-09
> **Miljet said:**
> Will the live CD boot without trying to install to disk? Will the live CD boot on another machine? What program are you using to burn the disk? And are you sure that you are burning it as an ISO image and not a data disk?


The live cd will not boot either way. The live cd will run on another machine just fine. Both the kubuntu and the ubuntu version. I am using the exact directions that Ubuntu has on it's website for burning ISO's onto discs. Including the exact same program. I wasn't sure if my first disc (made through Nero) would do it so I installed InfraRecorder for the others.

---

### Post by Miljet on 2010-09-09
For what it is worth, it sounds like you are doing everything right. There is just some conflict with some hardware on this computer. And I am sorry that I have no idea what else to suggest.

I think that at this point I would explore some other distribution. Maybe Mandriva, or even Puppy Linux to see if it will boot.

---

### Post by Zachmarius on 2010-09-10
UPDATE: After I thought I couldn't load Ubuntu or Kubuntu on the machine I tried for a Hackintosh. I was able to get it loaded but not running. I slept on the problem then came back with a different solution. 

I got a USB drive actually working so now it can. I unplugged all non-essential components, (ie modem, video card, and dvd player) and tried to start up.

SUCCESS!!!! It worked. I figure that the 56K modem was something that Ubuntu hadn't bothered writing script for since no one actually uses it anymore. As I type Ubuntu is now being installed on the system.

Fact: I can change the hardware of that computer and boot up in less time than it takes to reheat rice with veggies. (1m 30s) I actually did that and that's how it worked. Sorry but that's pretty neat for me.

Thanks all for everyone's help. You all gave very good suggestions and helped my brain think of different ways to get around hardware issues.

---

