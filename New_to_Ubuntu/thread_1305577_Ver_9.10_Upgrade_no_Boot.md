---
title: "Ver 9.10 Upgrade no Boot"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by rkher531 on 2009-10-30
I upgraded 9.04 to 9.10 and as suggested went for walk. After rebooting I find that i get the following message

[I]One or more of the mount listed in /etc/fstab cannot yet be mounted: ESC for recovery shell
/: waiting fro dev/disk/by-uuid/9a8e6ad3-a16a-4572-92f8-05c66185f4ac
/tmp: waiting for nul
swap: waiting for uuid=7f6e7937-dc45-43e1-9736-34993dbd5724

then I wait for GODOT the ever blinking cursor. 
Pressing ESC mountall:cancelled and it goes to root file


What should I do. 
Can I restore to 9.04 with my data files safe?


Rajesh Kher[/I]:sad:

---

### Post by ElvisTheKing on 2009-10-30
Ditto, exactly the same problem.

---

### Post by ikt on 2009-10-30
Can possibly try this, it has been suggested that the update was incomplete and it rebooted before it was finished,

if you head into grub (hold down shift during bootup), head into the 'recovery mode' of the latest kernel available (2.6.31.14) go to root shell with networking, and run sudo apt-get update and then sudo apt-get upgrade and even sudo apt-get dist-upgrade, does anything happen?

---

### Post by ranch hand on 2009-10-30
You actually should hold down the Esc key because you should be using grub-legacy on an upgrade.

Before running the apt commands, I would run;
```

sudo dpkg --configure -a

```
This may do nothing at all.  Great.  If there is something stuck in the system this should clear it.

And folks ask why I never do an upgrade.  Beats me.

---

### Post by shizow on 2009-10-30
same problem here
i can only choose a lot of kernels from 9.04 in grub, no from 9.10
when i boot the latest kernel from 9.04 in recovery mode the same problem comes up

what is the difference between grub-legacy and grub?

---

### Post by xoorox on 2009-10-30
I'm hitting this wonderful problem as well :/  ...same problem in recovery console and pressing Esc doesn't seem to get me anywhere.

I've seen someone elsewhere suggest it was an upgrade problem and the answer was to get into the recovery console and finish the upgrade, but the problem is getting a working console... [http://ubuntuforums.org/showthread.php?t=1301766](http://ubuntuforums.org/showthread.php?t=1301766)

I'm playing around trying to alter my /etc/fstab as documented here at the mo to see if it gets me in [http://www.ubuntu.com/getubuntu/releasenotes/910#Login%20screen%20presented%20before%20optional%20filesystems%20are%20mounted](http://www.ubuntu.com/getubuntu/releasenotes/910#Login%20screen%20presented%20before%20optional%20filesystems%20are%20mounted)

---

### Post by philinux on 2009-10-30
> **shizow said:**
> 

what is the difference between grub-legacy and grub?

Good question. Answer **MAJOR**. 

[http://www.gnu.org/software/grub/grub-2.en.html](http://www.gnu.org/software/grub/grub-2.en.html)

Also click the grub2 link below.

---

### Post by ikt on 2009-10-30
> **xoorox said:**
> same problem in recovery console and pressing Esc doesn't seem to get me anywhere.

Does it just not do anything or do you end up in terminal?

Just need a prompt at this point!

---

### Post by crazycatlady0 on 2009-10-30
I am having this same problem.  I upgraded from 9.04 to 9.10 yesterday and now I cannot boot.

I also noticed that my menu.lst file did not get updated.

---

### Post by xoorox on 2009-10-30
Hi ikt... it just complains about one or more of the mounts listed in /etc/fstab not being able to me mounted yet... keeps on waiting and blinking and Esc doesn't get you out of there.

My editing of /etc/fstab (i booted off a usbdrive) and adding of the bootwait option for each drive didn't do any good unfortunately.

---

### Post by muteXe on 2009-10-30
What was wrong with 9.04?

---

### Post by xoorox on 2009-10-30
> **muteXe said:**
> What was wrong with 9.04?

:p that's not the most helpful reply...
There were some niggles with the box I tried the upgrade on, it's a mythtv box... I'd hoped some of the minor problems might have been fixed ....but now of course it's not working well at all!

---

### Post by TheBuzzSaw on 2009-10-30
> **ranch hand said:**
> And folks ask why I never do an upgrade.  Beats me.

Agreed. This is the second time I have attempted an upgrade. They never go well. They leave messes behind, and they fail to install everything I wanted.

I am reinstalling. KK has things I want, but it's not worth tweaking every step of the way.

---

### Post by muteXe on 2009-10-30
> **xoorox said:**
> :p that's not the most helpful reply...
There were some niggles with the box I tried the upgrade on, it's a mythtv box... I'd hoped some of the minor problems might have been fixed ....but now of course it's not working well at all!

Sorry mate, but i'm finding i'm posting those words quite a lot. However, I do agree with you though. If you think it's gonna sort out problems you're experiencing with your current system then I can see why you'd go for it.

---

### Post by ikt on 2009-10-30
> **muteXe said:**
> Sorry mate, but i'm finding i'm posting those words quite a lot.

The problem is that it doesn't help and isn't particularly useful either, we need to sort out these issues so they don't reoccur in the 9.10 to 10.04 transition etc

Be aware that people are making bug reports about these issues and they are being looked into, the other issue is that you say what was wrong with 9.04, but someone using 8.10 might say the same (what was wrong with 8.10?) to you if you have any issues with 9.04, and the same for someone with 8.04 etc

> **xoorox said:**
> :p that's not the most helpful reply...
There were some niggles with the box I tried the upgrade on, it's a mythtv box... I'd hoped some of the minor problems might have been fixed ....but now of course it's not working well at all!

Grub2 really is starting to shine through in some areas such as these, for a quick result I'd backup all my data and reinstall, if you've got some time I'd keep looking around, certainly you're not the only person with this issue.

---

### Post by xoorox on 2009-10-30
Ah well that's what I like about Ubuntu, the community approach to things... if someone has a problem they're bound to be not the only one... and people are vocal about fixing things as well as having the problem in the first place.

As for backing up etc... well I should know a lot better :)

---

### Post by TheBuzzSaw on 2009-10-30
Well, I successfully reinstalled. As expected, it was relatively painless. (If you do not own an external hard drive yet, go buy one right now.)

As much as I love Ubuntu, the upgrade process is still a mess for me. (In its defense, Windows upgrades are not much better.) Fresh installs are just better. They're faster, easier, and more direct. I'm not desperate enough to keep my current documents/programs/etc. Thanks to the repository system, it is simple enough to install the necessary software.

---

### Post by rkher531 on 2009-10-30
I did try recovery.
1. I had to press ESC and not Shift Key.
2. The version available was 28 instead of 31 and no Network mode.
3. It was for 9.04
4. After going thru recovery mode I was back to the same point as in my first post.

---

### Post by QIII on 2009-10-30
There seem to have been problems with -11

I was running into the same problem, although I could boot.

Drop to the command line in recovery mode.

```
apt-get dist-upgrade
```

might help.  But, like I said, I was able to boot.  I had been seeing those messages while the boot spash was on screen, so I did dist-upgrade in the terminal.

---

### Post by ajmatson on 2009-10-30
Delete your menu.lst file and then:

```
$sudo update-grub
```

This works for me every time

---

### Post by joshuabettigole on 2009-11-08
I had a similar issue.  After upgrade, I got "error 15: file not found" when Grub attempted to load.  I used a live CD, mounted (making sure to mount /proc and /dev as well) and chrooted my installed Kubuntu, and after upgrading Grub to Grub2 ([https://wiki.ubuntu.com/KernelTeam/Grub2Testing](https://wiki.ubuntu.com/KernelTeam/Grub2Testing) - ignoring the UUID stuff) I landed on the same issue you're having.

My /boot directory gets mounted from /dev/sda1 and was ext2. (Not sure if that was relevant) I upgraded it to ext4 without issue ([http://maketecheasier.com/how-to-upgrade-from-ext3-to-ext4-without-formatting-the-hard-disk/2009/04/21](http://maketecheasier.com/how-to-upgrade-from-ext3-to-ext4-without-formatting-the-hard-disk/2009/04/21)) but was probably not necessary.

The problem lies in the fact that fstab is set to mount volumes using the block device's UUID and not the /dev/sd** entry.  When I ran the command "blkid", I found that /dev/sda1 did not show in the list.  After some digging, I found the answer that solved my problem.  Here it is: [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1844532.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1844532.html)

After following those instructions, "blkid" showed my device, and the UUID matched the entry that was already in /etc/fstab.  Rebooted the system, and got to the login screen without issue.

Hope this helps...  Cheers

---

