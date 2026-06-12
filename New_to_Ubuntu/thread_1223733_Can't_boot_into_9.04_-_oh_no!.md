---
title: "Can't boot into 9.04 - oh no!"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by biggiemokey on 2009-07-26
Hey everyone, I have XP and Jaunty installed on my computer.  I installed Jaunty through the upgrade tool in 8.10 after doing a fresh 8.10 install.  I now can't boot into 9.04 - the splash screen with the loading bar stops about a quarter of the way for about 10 minutes, then the bar fills up quickly.  It goes into a screen with text, saying a bunch of stuff is starting, with [OK] next to each one.  However, it hangs on Starting Bluetooth...so, I found this, which SHOULD help:
```
sudo mv /etc/init.d/bluetooth /etc/init.d/bluetooth_old
sudo update-rc.d bluetooth remove
sudo reboot
```
BUT, I can't get to a terminal to type that in!  When I try booting to recovery mode, I get:
```
IRQ 17
[   12.731019] Installing spdif_bug patch: Audigy 2 ZS [SB0353]
[   14.164011] phy0: device does not respond!
```
Audigy 2 is probably Sound Blaster Audigy 2, my audio software - don't know if that's what the audio card is called as well.  Anyway, please help me out...I really want to use Ubuntu!

---

### Post by Anthon on 2009-07-26
Have you switched of the computer between reboots? I sometimes found (especially with audiocards) that Windows leaves some residues (probably uploaded firmware) which prevent the Ubuntu drivers from starting.

---

### Post by biggiemokey on 2009-07-28
No, that doesn't help, I still get the same error message...

---

### Post by Grifulkin on 2009-07-28
I had the same problem, unplug everything that is plugged in via usb, except your keyboard of course and boot into Ubuntu, this happend to me yesterday actually, and then get to the terminal and type what you just said.  You can also when it freezes hit Alt+F2 and type ```
gdm start
``` and then do what you want to do, personally unplugging everything but your keyboard is the easiest thing to do.

---

### Post by biggiemokey on 2009-08-11
Thanks so much Grifulkin, that worked wonderfully.  I guess I'll just have to keep plugging and unplugging my USB stuff, but I'm sure I'll find some way to leave it plugged in eventually.  Maybe acpi=off will work, it helped other people with the bluetooth problem, but I don't actually know what it does.  Sorry for taking so long to reply, I was out of the country and away from my computer.

Ubuntu 9.04 rocks!  [SIZE="1"](so far, knock on wood)[/SIZE]

---

### Post by Cato2 on 2009-08-11
Some other quick tips:

- hit ESC right after the BIOS finishes, while GRUB is saying it's active, then select the Recovery Mode option 

- (hard cases) in GRUB, hit e to edit the line, and append 'init=/bin/bash' - lots of things won't work but you will get a root shell

For really hard cases, boot the Ubuntu live CD, mount the disk and chroot - e.g. if your Ubuntu install is on /dev/sda2 you can "mount /dev/sda2 /media/sda2" and then "sudo chroot /media/sda2" and you can then run commands from within your root filesystem, but executing them on the booted Live CD Ubuntu (Best to google for Ubuntu chroot howto, it's a bit of a weird idea at first).  This lets you edit config files etc, and even install a kernel module - all the normal apt-get and update-rc.d stuff will work on your real root filesystem.

---

