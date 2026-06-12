---
title: "can't open /root/dev/console: no such file"
date: 2011-03-08
forum: New to Ubuntu
---

### Post by marisflowers on 2011-03-08
Hello to all -
I have been using Linux (Ubuntu 10.04) on my Acer Aspire One since Nov. I am very new to this, but I have not had any problems so far...well, until today!

I can't boot up - plain and simple.
Here's what I get:

....... (a lot of stuff that scrolls and I can't get to it).......

"BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(intramfs) [COLOR=Red]exit[/COLOR]
[COLOR=Black]/init: line271: can't open /root/dev/console: no such file
[ 407.680477] kernel panic - not syncing: Attempted to kill init!
[ 407.680551] Pid: 1, comm: init Tainted: G         D     2.3.32-29-generic #58-Ubuntu
[ 407.608639] Call Trace:
[ 407.680707]   [<c058c1a0>] ? printk+0x1d/0x25
[ 407.680773]   [<c058c0d6>] panic+0x48/0xf5
[ 407.680840]   [<c014f15d>] forget_original_parent+0x2bd/0x2c0
[ 407.680910]   [<c014f173>] exit_notify+0x13/0x170
[ 407.680976]   [<c0150a89>] do_exit+0x189/0x310
[ 407.681050]   [<c0150c4e>] do_group_exit+0x3e/0xa0
[ 407.681128]   [<c0150cc8>] sys_exit-group+0x18/0x20
[ 407.681200]   [<c01033ec>] syscall_call+0x7/xb"

And then a blinking cursor and I can't type & the computer is 'frozen'. I have been looking around to see what the problem might be and it seems it's either hardware or a weird 'Grub' installation. My hard drive is a brand new seagate 500gb. Grub? Sounds like chow to me! I have no idea what to do and I am a total newb. I did boot from my Ubuntu ISO file & was able to boot off of my USB drive - but it's not MY Ubuntu. I really don't want to re-install because I had a little trouble getting sound the first time - a great person on this forum helped me out & they got it fixed for me, so I'm a turning to you again, Oh Great Ubuntu Forum, Mass Collective of Brilliant Minds...

I humbly await any help someone can throw my way and am happy to provide further information per your request...Thank you in advance for your time & I hope that you have a great day!!!
Mari


[/COLOR]

---

### Post by bodhi.zazen on 2011-03-08
Hard to tell from that information.

Basically your kernel is not being found on the hard drive.

Could be anything from faulty hardware to a bad kernel or initramfs.

What messages do you get right before dropping to busybox ?

Busybox is a simple "shell" included in the initramfs and is used as a fall back if your system does not boot.

There should be an error message right before dropping into busybox.

Try  booting an older kernel.

Alternately you can try booting a live CD (usb in your case) and investigating your hardware from there.

---

### Post by marisflowers on 2011-03-08
Than you for your time!
I just re-booted & the terminal says:

"Killed
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg"

Does that information help at all? 
(I use Linux because I like the philosophy - but I am VERY limited as to the "how" behind it)

I appreciate you trying to help me - I have the original Ubuntu ISO file that I used, so I can always reinstall, but I am trying to avoid that...

Have a great day and I hope wherever you are the weather is wonderful! 

Mari

P.S. the prompt does start with (initramfs)
AND
I will try to check my hardware with the ISO file
Thanks so much!
M

---

### Post by bodhi.zazen on 2011-03-08
> **marisflowers said:**
> Than you for your time!
I just re-booted & the terminal says:

"Killed
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg"

Does that information help at all? 
(I use Linux because I like the philosophy - but I am VERY limited as to the "how" behind it)

I appreciate you trying to help me - I have the original Ubuntu ISO file that I used, so I can always reinstall, but I am trying to avoid that...

Have a great day and I hope wherever you are the weather is wonderful! 

Mari

P.S. the prompt does start with (initramfs)
AND
I will try to check my hardware with the ISO file
Thanks so much!
M

Basically when you boot ..

first grub starts, then the boot process is passed to the initramfs, and finally your kernel.

grub and initramfs are working, but the boot process is not finding the kernel.

Can you give an even earlier error message (those are all saying the same thing, the initramfs can not pass off the boot process to the kernel).

My guess is you have a hardware problem, but that is speculation.

Booting a live CD or USB can help as well. You can then look at your hard drive and / or mount your Ubuntu partition for repairs.

Does an earlier kernel work ?

---

### Post by marisflowers on 2011-03-08
Sorry I took so long to reply - I am having trouble calling up my grub menu to boot another kernel.
When I re-start w/in 3 seconds I hit the ESC key & get a flash of screen, but then it continues to boot - I am looking like crazy over forums for a fix - but I can't find what I am doing wrong.

Thanks again for your time and I am trying my best!!!

In the meantime I will boot from my USB and try to look @ my hardware. I'm just not sure what I am looking at :^).

Thanks again and have a wonderful day.

Mari

Okey-doke...it will not boot with an earlier kernel. Hmm...I wish it would have been that awesomely easy!
Will check hardware now...thanks you thank you!
M

---

### Post by bodhi.zazen on 2011-03-08
> **marisflowers said:**
> Sorry I took so long to reply - I am having trouble calling up my grub menu to boot another kernel.
When I re-start w/in 3 seconds I hit the ESC key & get a flash of screen, but then it continues to boot - I am looking like crazy over forums for a fix - but I can't find what I am doing wrong.

Thanks again for your time and I am trying my best!!!

In the meantime I will boot from my USB and try to look @ my hardware. I'm just not sure what I am looking at :^).

Thanks again and have a wonderful day.

Mari

Okey-doke...it will not boot with an earlier kernel. Hmm...I wish it would have been that awesomely easy!
Will check hardware now...thanks you thank you!
M

My guess is you have a problem with your hard drive. Hopefully it is simply a loose cable.

Once you get a live CD running, check your partitions with gparted.

Post back if you need further assistance.

---

### Post by belize1334 on 2011-04-17
I thought I'd chime in because I just had this issue and got it resolved but I don't know how permanent the fix will be...

Same initial issue... I'd get an error message on boot-up that \dev could not be found on \root\dev... 
I searched around a bit and found somebody suggesting that the partition had not been properly unmounted, possibly due to a power failure. I loaded my live cd, and then ran fdisk on my HD (\dev\sda). This showed nothing abnormal so I mounted the boot partition (\dev\sda1 in my case) and then restarted the computer. Everything booted normally after that. But, I'm still skeptical that it could be a hard-ware issue and if the problem occurs again I'll be replacing the HD. 

system is:
Inspiron 6000
10.04
Seagate 160 GB w/ 25GB OS partition

---

