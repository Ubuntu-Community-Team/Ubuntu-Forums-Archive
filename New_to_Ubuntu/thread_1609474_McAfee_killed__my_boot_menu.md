---
title: "McAfee killed  my boot menu"
date: 2010-10-30
forum: New to Ubuntu
---

### Post by Buntu Bunny on 2010-10-30
I am running Lucid on a duel boot with Windows 7. I got the bright idea to try Windows Security Essentials free antivirus, for the rare occasion when I might need to go online with Windows. I had to download and install it from Win.

During the download/installation, I was informed that other AV programs could interfere with Security Essentials, and was advised to uninstall them. In my case it was McAfee, which came preloaded on my Dell Inspiron 570. 

After Windows uninstalled McAfee, I needed to reboot, which I did. When the computer rebooted, I got the following:

[I]No module name found
Aborted. Press any key to exit.[/I]

I pressed any key and got the following:

[I]No boot device available
Strike the F1 key to retry boot
SATA0: Installed
SATA1: Installed
SATA2: None
SATA3: None[/I]

F1 started repeated the above.

My next step was to try the Windows recovery disk I made before installing Ubuntu.  From that, I got an error: 0X4001100200001012

The only option it gave me was to click OK, which I did, which  started the the whole thing all over.

Next I went into boot options via F12. Here's what happened when I tried the various options:

SATA ST3320418AS - repeated the problem sequence
CD/DVD - described above with Win recovery disk
Boot to Utility partition - repeats the above
Esc to boot to defaults - ditto

Then I ran the diagnostics option, and memory passed

I went to set up and copied down the following:

System: Inspiron 540
Bios: A01, 01/25/10
ADM Sempron 140 Processor
L2 Cache: 1024 kb
Installed memory 2048 MB
Mem speed 1066 MHz

Main:
SATA - 0 Hard Disk vendor ST 3320418AS size 320 GB
SARA - 1 ATAPI CDROM
SATA - 2 not detected
SATA - 3 not detected

Before I installed Ubuntu, I resized C to 151.45 GB, which gave me 136.72 GB to install Lucid. Unfortunately I did not <kicking self profusely> create a recovery disk in Ubuntu.

I don't have a very good feeling about this. Is there any hope? 

Please note that I'm at a computer at the county library. That means I have a time limit plus, I dont' live very close. What I'm trying to say is that if you respond and I don't get back to you right away, it's not because I'm ignoring you. Library is closed Sunday, so I'm here for the next 35 mins before I'm cut off, then I'll be back on Monday.

---

### Post by janpol on 2010-10-30
Have you tried to boot from a Ubuntu live cd?

Over there, you can try to recover grub2, here are the instructions on how to do it:

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

5. Recover the boot loader:

```
sudo grub-install /dev/sda
```

If you get any errors, run:

```
grub-install --recheck /dev/sda
```

6. Exit the chroot, umount the system and reboot your system (and try to boot from your Hard Drive):

```
exit
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt
sudo reboot
```

7.If you can get now into Ubuntu, but grub doesn't show Windows 7, run from a terminal (inside your Ubuntu installation, you don't need the livecd anymore ;)):

```
sudo update-grub
```

Hope it helps!

Source: [http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html]("http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html")

---

### Post by Buntu Bunny on 2010-10-30
Janpol, thank you so much. I have copied it all down and will go home to try it. Will report back immediately if it works. If not, I'll sign in again from the library.

---

### Post by Buntu Bunny on 2010-10-30
It worked!!! Janpol thank you so much. What a relief. I'd nearly given up hope, and am so thankful for this forum. Thank you especially for your prompt reply and for spelling it all so well for me. I'm very grateful.

---

### Post by theozzlives on 2010-10-30
> **Buntu Bunny said:**
> It worked!!! Janpol thank you so much. What a relief. I'd nearly given up hope, and am so thankful for this forum. Thank you especially for your prompt reply and for spelling it all so well for me. I'm very grateful.

That was the right course of action. Just so you know, I'll try to explain what happened. McAfee was watching your boot sector to insure you don't get a boot sector virus. Unfortunately many Windows AV programs don't count on GRUB being there, so it was wiped. Re-installing GRUB was the only answer.

---

### Post by wilee-nilee on 2010-10-30
Kind of a long way around just load grub to the mbr, it could have been done with two commands from a live cd.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by lisati on 2010-10-30
<smiles> Reminds me of the time I was looking at a laptop in the computer section of a local shop. On the screen was a security alert something like this: "McAfee: Your computer is at risk." This wasn't long after a [major disaster]("http://news.cnet.com/8301-1009_3-20003247-83.html") involving their AV updates that rendered many computers unusable.

---

### Post by Buntu Bunny on 2010-10-30
Theozzlives, ah, I figured it was something like that. Thanks for the explanation.

Wilee-nilee, I've bookmarked your link too. You're right, it does look simpler, but at least the fix I used did work and I'm relieved. Very relieved. 

Lisati, LOL. Honestly I never trusted McAfee. I got a virus once a long time ago while using it and tech support ignored my pleas for help.

One more question. Not sure that I want to but is it safe to boot to Windows now??? Can I assume McAfee actually uninstalled? Or will it highjack me again?

---

### Post by amateur_mav on 2010-10-30
If you have the Windows installation CD I suggest to boot that up because it has diagnostic utilities that will check your Windows installation for errors.
But my guess is you shouldn't have any problems. 
*
*
*
Guess I was wrong about her not having more problems - an hour has passed without a post from her.

---

### Post by janpol on 2010-10-31
> **Buntu Bunny said:**
> One more question. Not sure that I want to but is it safe to boot to Windows now??? Can I assume McAfee actually uninstalled? Or will it highjack me again?

Try to boot into Windows, it's most likely that your AV has been already uninstalled and this won't happen again. But, just to be safe, back up your data first (as you should always do ;)).

Regards!

---

### Post by Buntu Bunny on 2010-10-31
> **janpol said:**
> Try to boot into Windows, it's most likely that your AV has been already uninstalled and this won't happen again. But, just to be safe, back up your data first (as you should always do ;)).

Ah yes, I learned about that the hard way, didn't I. ;)  At least I know how to restore GRUB, just in case. 

Amateur_mav, no Windows installation CD; it was pre-installed. Still, if I can get into Windows with no mishap, running diagnostics would be a good idea. Of course, I may have to convince myself that I really want to go check it out. I've been awfully happy with Ubuntu for quite awhile.

---

### Post by theozzlives on 2010-10-31
> **Buntu Bunny said:**
> Ah yes, I learned about that the hard way, didn't I. ;)  At least I know how to restore GRUB, just in case. 

Amateur_mav, no Windows installation CD; it was pre-installed. Still, if I can get into Windows with no mishap, running diagnostics would be a good idea. Of course, I may have to convince myself that I really want to go check it out. I've been awfully happy with Ubuntu for quite awhile.

If it don't start, you can press F8 and choose to fix the startup.

---

### Post by Buntu Bunny on 2010-10-31
> **theozzlives said:**
> If it don't start, you can press F8 and choose to fix the startup.

Thanks, theozzlives. I didn't know that and will keep that info handy.

---

### Post by Buntu Bunny on 2011-08-15
For the record, I haven't booted windows since the episode here. After a major storm with loss of power and internet, I had to boot windows to facilitate my internet server's tech help. After exiting windows, GRUB was gone again! Had to go back to the library to copy down this solution *again*.

---

### Post by kansasnoob on 2011-08-16
> **Buntu Bunny said:**
> For the record, I haven't booted windows since the episode here. After a major storm with loss of power and internet, I had to boot windows to facilitate my internet server's tech help. After exiting windows, GRUB was gone again! Had to go back to the library to copy down this solution *again*.

I posted in your new thread:

[http://ubuntuforums.org/showpost.php?p=11156991&postcount=3](http://ubuntuforums.org/showpost.php?p=11156991&postcount=3)

---

