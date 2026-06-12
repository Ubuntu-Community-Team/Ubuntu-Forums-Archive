---
title: "had to shut down improperly now wont restart"
date: 2010-03-23
forum: New to Ubuntu
---

### Post by misswham on 2010-03-23
i have linux mint helena and i started having problems a few days back where my ctrl buttons werent workiing.  I coulnt copy with ctrl-c and couldnt paste with ctrl-v also when i go into XP on VIRTUAL BOX I could't get to full screen by pressing right ctrl-F and i couldnt get the cursor back by pressing the right ctrl key,  It worked fine up until my ctrl buttons stopped working.  So today, I tried it again and still nothing and I had to exit by restarting at the tower.  When I would hit ctrl alt delete, it DID give me the option to log off properly but couldnt get to it because the cursor was stuck in VB.  I then restarted in Windows 7 (dual boot windows 7 and linux) and tested the control buttons there and they worked fine.  

Now when I restarted properly, my system wont restart.  It cuts on and the prduct logo shows and it goes dark like it is going to grub and it cuts off and starts again, over and over and over.  So I hit the bios settings and disabled quick start and it restarted now I am at the grub loading screen and it is stuck.  This is a new computer and I am at a loss.  

What does it seem like the problem is and can this be fixed without losing both my operating systems and my things on my harddrive?

---

### Post by Mykk on 2010-03-23
My first suggestion would be to use another keyboard for testing (if you have one). But to get stuck in at the grub seems completely unrelated.

When you say its stuck at the grub does that mean you cant select anything?

---

### Post by coffeecat on 2010-03-23
You could run 'fsck' from a live CD to see whether there are any filesystem inconsistencies and repair them. From a live CD (this can be Mint or Ubuntu - it doesn't matter which), open a terminal and:

```
sudo fsck /dev/sdax
```

... where x = your Mint root partition number, and assuming that Mint is on sda.

That might solve any problems caused by the unclean hard shutdown, but it sounds as though there were issues before that.

---

### Post by misswham on 2010-03-23
Yes i tried 3 keyboards and it worked the same.  i will go now and try the command.

---

### Post by misswham on 2010-03-23
and no it is stuck at 

GRUB loading.

---

### Post by Mykk on 2010-03-23
> **misswham said:**
> and no it is stuck at 

GRUB loading.

Do as [coffeecat]("http://ubuntuforums.org/member.php?u=129087") advises and use a live cd.

This is your best option.

---

### Post by conradin on 2010-03-23
What I would do is burn a live CD and attempt to repair the disk with the fsck utility.

---

### Post by misswham on 2010-03-23
this is the response i got from the terminal

sudo fsck /dev/sdax
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
fsck.ext2: No such file or directory while trying to open /dev/sdax

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

Guess what, the ctrl buttons work with the live cd.

---

### Post by coffeecat on 2010-03-23
> **misswham said:**
> sudo fsck /dev/sdax

Yes, I did say:

> **coffeecat said:**
> ```
sudo fsck /dev/sdax
```... where x = your Mint root partition number, and assuming that Mint is on sda.

If you don't know which is your Mint root partition, from the live CD run:

```
sudo fdisk -l
```.... where l = lower-case L. Post the output and someone will interpret it for you.

---

### Post by misswham on 2010-03-23
mint@mint ~ $ sudo fdisk -l

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb8a99397

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1828    14680064   27  Unknown
/dev/sda2   *        1828        1841      102400    7  HPFS/NTFS
/dev/sda3            1841       30046   226557612    7  HPFS/NTFS
/dev/sda4           30047       91201   491227537+   5  Extended
/dev/sda5           30047       90166   482913868+  83  Linux
/dev/sda6           90167       91201     8313606   82  Linux swap / Solaris
mint@mint ~ $

this is the outcome i got when i put in the last command

---

### Post by misswham on 2010-03-23
I am sorry.  I am sort of a novice and I guess I was supposed to replace the x in the command with a number.  I have posted the outcome and if I was supposed to replace the x with something, can someone tell me the new command please to fix it?

---

### Post by coffeecat on 2010-03-23
> **misswham said:**
> I am sorry.  I am sort of a novice and I guess I was supposed to replace the x in the command with a number.  I have posted the outcome and if I was supposed to replace the x with something, can someone tell me the new command please to fix it?

No problem. Your Linux root partition is /dev/sda5, so you need:

```
sudo fsck /dev/sda5
```Hopefully, that will autofix any problems it finds. However, if the filesystem is badly damaged, it may ask you questions that you won't understand. The only advice I can give is to go with the defaults, but you may find the filesystem is too badly damaged to be repaired by anyone but an expert (which I am not). Or maybe it isn't. Let's hope not.

If you find that Mint is unrecoverable, you may be able to rescue the XP virtual machine so that you don't have to reinstall it if you have to reinstall Mint.  But let's take one step at a time. The ctrl-combination issue may be a separate one - which is why it worked in the live session. But let's see what a 'sudo fsck' can achieve.

---

### Post by chaanakya_chiraag on 2010-03-23
I'm wondering what the "Unknown" partition is...

---

### Post by coffeecat on 2010-03-23
> **chaanakya_chiraag said:**
> I'm wondering what the "Unknown" partition is...

It's about 14GiB. It's probably a manufacturer's restore utility. It's usually on sda1 and sometimes shows up as unknown because the manufacturers do strange things to the partition table. The rest looks fairly standard Windows 7 stuff: a ~ 100MiB W7 separate boot partition on sda2 and Windows C:\ on sda3.

---

### Post by misswham on 2010-03-23
i just put in the new command in the terminal and this is what the outcome was

$ sudo fsck /dev/sda5
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
/dev/sda5: clean, 200097/30187520 files, 15594825/120728467 blocks
mint@mint ~ $ 


does this say anything?

also before this, i logged off and restarted and the same thing.  it starts, the emachines screen comes up and then it goes dark as if it is going to grub and then restarts over and over again, never making it to grub.

---

### Post by coffeecat on 2010-03-23
> **misswham said:**
> i just put in the new command in the terminal and this is what the outcome was

$ sudo fsck /dev/sda5
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
/dev/sda5: clean, 200097/30187520 files, 15594825/120728467 blocks
mint@mint ~ $ 


does this say anything?

also before this, i logged off and restarted and the same thing.  it starts, the emachines screen comes up and then it goes dark as if it is going to grub and then restarts over and over again, never making it to grub.

The good news is that your filesystem on sda5 is clean. The bad news is that I haven't a clue why you are having problems. This could be a BIOS issue or a grub issue. I'm groping in the dark here, but let's try re-installing grub. It won't do any harm, but it might not do any good if that's not the problem. Since Mint Helena is based on Ubuntu Karmic, you'll have grub 2, so we need to use grub 2 commands.

Boot up from the Mint Helena live CD (or Ubuntu Karmic - no other Linux CD will do) and from the terminal:

```
sudo mount /dev/sda5 /mnt
```and then...

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```And then reboot and tell us what happens. If you can get internet access from the live CD, you'd be best to copy and paste those commands to the terminal to avoid typos.

If anyone has any better ideas, please chip in.

---

### Post by misswham on 2010-03-23
ok i did the 2 commands and this is the outcome.  

mint@mint ~ $ sudo fsck /dev/sda5
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
/dev/sda5: clean, 200097/30187520 files, 15594825/120728467 blocks
mint@mint ~ $ sudo mount /dev/sda5 /mnt
mint@mint ~ $ sudo grub-install --root-directory=/mnt/ /dev/sda
Installation finished. No error reported.
This is the contents of the device map /mnt//boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)	/dev/sda


i am going to reboot now and see what happens

---

### Post by misswham on 2010-03-23
VOILA!  IT WORRRRRRKKKKED!  

Thank you sooo much.  It WAS grub.  Now I tried the ctrl keys and again they are dead.  Any Ideas because this is the only way i can get to my XP.  If I go to it again, I would have to shutdown via tower and I will corrupt grub again.  It isnt VB I believe, it has something to do with the OS.  It worked fine until 5 days ago and I just tried to copy and paste using my ctrl keys and still nothing.

---

### Post by coffeecat on 2010-03-23
> **misswham said:**
>   Now I tried the ctrl keys and again they are dead.

....


It isnt VB I believe

It might be Virtual Box's fault though. I've done a bit of googling and control keys going dead (as well as alt and shift for some people) happens because of a bug in VMWare. I know VMWare is different from VirtualBox, but I found one hit where this seems to have happened in VB. The fix that worked for some people is to run the following terminal command (not in the live CD - from your booted Mint):

```
setxkbmap
```

See how it goes.

---

### Post by misswham on 2010-03-23
i tried the command in the terminal

setxkbmap

and nothing happened.  I hit enter afterwards and it didnt even ask me for my passwordl

---

### Post by misswham on 2010-03-23
I have backed up all of my stuff and I have done alll the research and still found nothing on why my ctrl keys arent working.  So I have decided to just reinstall mint.  Is there any easy way to reinstall mint over the existing mint and will I have to reinstall VM?  If I cant preserve VM I will just have to reinstall it also.  I dual boot with windows7 and mint.

---

### Post by coffeecat on 2010-03-24
> **misswham said:**
> I have backed up all of my stuff and I have done alll the research and still found nothing on why my ctrl keys arent working.  So I have decided to just reinstall mint.  Is there any easy way to reinstall mint over the existing mint and will I have to reinstall VM?  If I cant preserve VM I will just have to reinstall it also.  I dual boot with windows7 and mint.

If you choose 'manual' at the partitioning stage of the installer, simply designate your existing sda5 partition as '/' (shorthand for root) and mark it for reformatting as ext4. The installer will pick up the swap partition automatically - you don't have to do anything about that. It will also reinstall grub, detect Windows 7 and set you up with a dual-booting menu as before.

But before you do that, you say 'VM' in this post whereas you were talking about VirtualBox before. Which are you using, VMWare or VirtualBox? If VMWare, you might want to do a bit of googling around VMWare and setxkbmap. There were a couple of threads on this forum iirc. For some the simple command 'setxkbmap' worked but there was a more complex script posted which some needed. It might be worth trying. And the command 'setxkbmap' did do something, by the way, even if it didn't fix the problem. In the terminal, if you get no output, that means that the command terminated successfully and there was nothing to report.

But if you are running VirtualBox, have a look in ~/.VirtualBox/HardDisks/. Where ~ = your home folder. You need to View > Show hidden files in the Nautilus window (since ctrl-H won't work) to show the hidden folder .VirtualBox. In the HardDisks folder, you'll find the vdi file for your virtual XP. That's the actual virtual hard disk. Back the file up somewhere safe. When you've reinstalled Mint  and reinstalled VirtualBox, go through the procedure to set up a new virtual XP machine but don't install from the XP disc. Simply copy the old vdi file overwriting the old into the new ~/.VirtualBox/HardDisks/ and you'll be able to carry on with XP where you left off.

---

### Post by misswham on 2010-03-24
I am sorry, I meant VB.  I will try this evening and let you know what happens.

---

