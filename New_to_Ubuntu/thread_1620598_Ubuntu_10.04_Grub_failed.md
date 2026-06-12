---
title: "Ubuntu 10.04 Grub failed"
date: 2010-11-13
forum: New to Ubuntu
---

### Post by tdapower on 2010-11-13
[SIZE=3]I created a customized ubuntu with using remastersys with my currently installed software packages(Distributable copy). But when i created a dvd and installing in to a partition of pc which windows xp installed, at the 93% of installation completed time a fatal error occurred.it Says

Unable to configure GRUB
Executing 'update-grub' failed
This is a fatal error

but I proceed the installation without installing the grub after retrying several times.

When installation completes and restarted the pc, the cli appeared with some text and prompt 
grub>

How do I solve this problem? pls:(
[/SIZE]

---

### Post by janpol on 2010-11-13
Try to reinstall grub2 using a liveCD:

1. Boot from the live cd

2. From a terminal, run:

```
sudo fdisk -l
```

That will show your partitions table, for example

```
/dev/sda1 29 8369 66999082+ 83 Linux
/dev/sda2 * 8370 13995 45190845 7 HPFS/NTFS
/dev/sda3 13996 14593 4803435 5 Extended
/dev/sda5 13996 14593 4803403+ 82 Linux swap / Solaris
```

3. Mount your linux partition (/dev/sda1 for this example):

```
sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
```

4. Chroot into it:

```
sudo chroot /mnt
```

5. Reinstall the boot loader:

```
sudo grub-install /dev/sda
```

If you get any errors, run:

```
grub-install --recheck /dev/sda
```

6. Reboot your system and try to boot from your Hard Drive:

7.If you can get now into Ubuntu, run from a terminal (inside your Ubuntu installation, you don't need the livecd anymore ;)):

```
sudo update-grub
```

Hope it helps!

Source: [http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html]("http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html")

---

### Post by tdapower on 2010-11-13
[SIZE=3]I followed your steps but [/SIZE][SIZE=3][COLOR=Red]failed[/COLOR][/SIZE][SIZE=3]. :confused:

When boot time the displaying text is 
[/SIZE][SIZE=3][COLOR=Red]
GNU GRUB version 1.98-1ubuntu7
minimal Bash-like line editing is supported....[/COLOR][/SIZE]

---

### Post by tk189 on 2010-11-13
Try following the great walkthrough here [how to purge and reinstall GRUB]("http://ubuntuforums.org/showthread.php?t=1581099") I use it daily :(

Sometimes I have the great pleasure of purging and reinstalling grub 3 or 4 times a day.

It's a massive problem affecting a lot of people and doesn't seem to be going away.

Hope it helps.

---

### Post by janpol on 2010-11-13
> **tdapower said:**
> [SIZE=3]I followed your steps but [/SIZE][SIZE=3][COLOR=Red]failed[/COLOR][/SIZE][SIZE=3]. :confused:

When boot time the displaying text is 
[/SIZE][SIZE=3][COLOR=Red]
GNU GRUB version 1.98-1ubuntu7
minimal Bash-like line editing is supported....[/COLOR][/SIZE]
I'm sorry to hear that :(, try to follow the walkthrough tk189 provided.

If that doesn't work, try to reinstall the system (or wait for someone to come with a better idea :p). If reinstalling fails, it's likely that there are some problems with that DVD you created.

---

### Post by tdapower on 2010-11-13
[SIZE=3]I tried reinstalling several times, but every time failed to install the GRUB, but when I install Ubuntu from original cd no problems occurred. Is it problem of my customized cd?[/SIZE]:(

---

### Post by drs305 on 2010-11-13
> **tdapower said:**
> [SIZE=3]I tried reinstalling several times, but every time failed to install the GRUB, but when I install Ubuntu from original cd no problems occurred. Is it problem of my customized cd?[/SIZE]:(

Initially I thought it could be a BIOS disk size limitation, but since the initial install of G2 failed during the installation (and not reboot) this is not as likely. 

If you use the 'chroot' method as described in the link previously mentioned as long as you can get to the Ubuntu desktop your CD/DVD shouldn't matter. 

By 'chrooting', checking for an Internet connection, then purging and reinstalling Grub2 it should provide you with a fresh, up-to-date version of Grub2 from online repositories. If you haven't tried this method, I would recommend do so.

---

### Post by tdapower on 2010-11-13
I also tried that several times but failed each time

---

### Post by drs305 on 2010-11-13
You could try booting into your Ubuntu installation from the grub prompt, using this guide, although it would seem the install is probably in worse shape than just a minor grub glitch:
[Grub Rescue Prompt Megathread]("http://ubuntuforums.org/showthread.php?t=1594052")

It's probably time to post the boot info script results. Boot the LiveCD, go to the following and download/run the script, then post the RESULTS.txt contents:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

