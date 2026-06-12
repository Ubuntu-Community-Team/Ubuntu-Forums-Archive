---
title: "Problems installing W7 &amp; Ubuntu for dual boot. Grub Fail. Problem due to RAID config."
date: 2010-07-13
forum: New to Ubuntu
---

### Post by d3mncln3r on 2010-07-13
Hi, I tried dual booting Windows 7 and Ubuntu about 6 months ago and I could not get it to work. GRUB kept failing and I couldn't figure out why. Many people helped me along my quest (thanks to all of them) and I have come to a conclusion but I would like some last advice.

I have a Sony VAIO with two hard drives that were automatically configured in RAID by the manufacturer. I used the ubuntu live cd to try and install my dual boot, and this is why it failed.

I've been told I need to use the alt installation, which will be compatible with RAID.

The advice I was given leaves me with two choices, and I'd like your opinion on what you think is best for a beginner.

Option 1: Dual boot over the RAID using the "alt install" for ubuntu.

Option 2: Disable the RAID, install W7 and Ubuntu on one drive, and use the second drive as a data disk.

If you have some input please let me know, thanks in advance for the advice.

---

### Post by YesWeCan on 2010-07-13
If you want an easy life I would disable the HW RAID in the bios and use a tool like cfdisk to remove all RAID labels. I would then install Windows on one disk and Ubuntu and grub on the other. Set it to boot off the Ubuntu disk and you can then select Windows from the grub menu. I would also uninstall dmraid from Ubuntu. I had a hell of a problem trying to get my dual boot working because of flags in my disks and/or bios that my two disks were part of a hardware RAID and Ubuntu's dmraid drivers detected this and sort of forced a RAID configuration during boot. Wasted hours of my life trying to diagnose the problem.
Clean up the two disks. Install Ubuntu on one of them and then uninstall dmraid. Then install Windows on the other disk. Then boot off the Ubuntu disk and run update-grub to include the Windows OS on the grub menu. Set your bios to always boot off the Ubuntu disk. Only change to boot off Windows disk if you need to update XP or upgrade to Win7.
If you are expert you can do all sorts of fun stuff but if you are a novice I would recommend keeping Windows in its own containment zone.

---

### Post by oldfred on 2010-07-13
+1 for YesWeCan's suggestions

I am not a fan of raid on desktops. RAID on servers is a different animal. Many put raid on a desktop thinking it adds security which is wrong. The servers we had at work still had nightly backups and had at least 5 drives so if one failed it could be replaced on the fly. But raid was to improve performance not backup. On a desktop your RAID will not let you type faster or download from Internet faster (the main bottlenecks on a desktop pc). So unless you are running a large database or web servers on you desktop why have RAID?

---

### Post by d3mncln3r on 2010-07-14
hey, thanks for the responses, I'm sorry, I neglected to give system specs etc. on my machine: I am running Win 7 on my SONY vaio laptop, 2.4GHZ core 2 duo, 3GB RAM, Nvida 8600GM.

I am no expert so I will most likely research your post a little bit and probably attempt to go that route.

---

### Post by oldfred on 2010-07-14
If you want to keep your RAID do NOT do any of this.

To remove the raid settings:

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

sudo apt-get remove dmraid
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/461470](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/461470)

---

### Post by d3mncln3r on 2010-07-15
ok, lets just say for the sake of argument and information that I did want to keep my raid setup. What to do differently when trying to dual boot windows and ubuntu?

---

### Post by d3mncln3r on 2010-07-15
actually nevermind, talked to one of my IT friends at work and he basically recommended I do what has already been suggested... I shall-- embark!

---

### Post by d3mncln3r on 2010-07-17
For posterity I will finish up by saying, I successfully disabled the RAID on my machine, made 3 partitions on disk 1 (the second disk) for Ubuntu, one for the OS, one for storage, and one for swap. I then made 2 partitions on disk 0 (the first disk) Installed windows on the smaller one and it worked!

Thanks to everyone recently and in the past who helped me out, maybe it's time to graduate from absolute beginner talk.

---

