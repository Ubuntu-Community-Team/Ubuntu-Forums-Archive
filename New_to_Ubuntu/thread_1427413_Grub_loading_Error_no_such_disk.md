---
title: "Grub loading Error no such disk"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by PhatScurl on 2010-03-11
okay i've already googled this problem, and found several possible answers, so i feel bad putting up another thread dealing with this problem, but I honestly can't make heads or tails of the code language in the other threads.

I recently (just yesterday) downloaded Ubuntu onto my external hard drive, because I'm running vista on my laptop and i finally got fed up with how much RAM its taking up. I've honestly loved Ubuntu so far and I decided I was going to start moving files over to ubuntu.
So just so we're clear:
Vista is on my internal Hard drive
Ubuntu on the external

So today i shut down my computer, unplugged the external hard drive and turned it back on assuming it would run Vista because its the only operating system available. I was wrong. I got this message:

GRUB loading.
error: no such disk
GRUB rescue>

So I plugged the external hard drive back in, hoping it would run Ubuntu so i can come here see if i could find a solution. I just got the same message.

So right now I'm running on downloaded CD, and i was hoping somebody could give me some advice on how i can get back on to Windows on my internal, and then back on to Ubuntu on my external. Please treat me like a moron as far as coding goes and tell me everything that is happening when i type stuff in. this is a rather new experience for me, and the less i have i have to come back to you guys the better for the both of us.

Thank you very much!

---

### Post by KirbySmith on 2010-04-10
I just had that problem, and after messing up my Windows installation trying to repair the hard drive that wasn't broken, I discovered that somehow when either running a 9.10 or 10.04B live cd or installing 9.10 to a separate drive, GRUB was installed on an NTFS drive holding data that has nothing to do with ubuntu or a windows installation.  Somehow sometime this drive became first in the BIOS boot order.  Changing the boot order got the Windows drive to work again (not optimally).  In windows, I can't even see GRUB there, so I'm unclear at the moment how to move it when I'm back in ubuntu.

kirby

---

### Post by KirbySmith on 2010-04-10
And I'm also curious what the reply should be to "grub rescue >"?

kirby

---

### Post by ranch hand on 2010-04-10
PhatScurl
If you have the install disk for you MS install I understand that you can recover your MS boot loader.  There are a couple threads that have mentioned it.  You might look into that.

What has happened is that when you installed Ubuntu grub was placed  on the MBR.  If you were to go into bios and shut down your internal drive I bet you couldn't boot Ubuntu from the external either as it is going to look for it on the turned off drive and the drive number is going to be wrong anyway.

You need to check your bios and see if you can turn off the internal.  If so do so and then put your Live CD (DVD) in and boot from that with the external connected and on.

Use these instructions to install grub on the MBR of your external;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

ignoring the part about editing files as that should be taken care of when "update-grub" is run.

You may want to get into your /boot/grub/grub.cfg file and copy the menuentry that is for your MS install before running any commands to "update-grub".

This can be used in your /etc/grub.d/40_custom file to make MS boot from the external even after you fix the MS boot loader.

There is more basic info in the link in my sig.  The best in depth stuff is here;

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

The links at the bottom of that post will take you to more great posts by the perpetrator drs305.

There may well be something about MS recovery some where there too.  I will not have that in my house. let alone on my box, so I am pretty ignorant about fixing it (well I could fix it but you probably don't want to format the drive and install Linux - worked for me).

One thing you could do, if you have room on the drive, is do an install of Ubuntu on it (6Gb should do it) and boot from that.  Don't use it or add anything to it, just use it for the grub loader.  I did this on my Dreaded Mother in Laws MS box and it boots faster.  You should visit it on occasion for updates and to do anything you need to grub.

---

### Post by drs305 on 2010-04-10
For an initial step you can try to restore the MBR from the Ubuntu LiveCD so Windows can boot .

Open a terminal (Applications, Accessories, Terminal).
Install "lilo", an alternative bootloader:
```
sudo apt-get install lilo
```
Enter your password when asked and press ENTER - you won't see it.

Next, restore the MBR so Windows can use it. 
```
sudo lilo -M /dev/sda mbr
```

This should restore Windows, then you can work on Ubuntu from the LiveCD.

Here is a good link for restoring Windows and Ubuntu when you lose a working install due to the installation of the other.
[How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)]("http://ubuntuforums.org/showthread.php?t=1014708")

---

