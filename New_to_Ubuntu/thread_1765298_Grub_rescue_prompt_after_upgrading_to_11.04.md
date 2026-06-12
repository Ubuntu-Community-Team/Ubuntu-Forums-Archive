---
title: "Grub rescue prompt after upgrading to 11.04"
date: 2011-05-22
forum: New to Ubuntu
---

### Post by diablo75 on 2011-05-22
A friend of of mine asked me last night if it was safe to upgrade to Ubuntu 11.04 and I said he should go ahead and do it.  He has been running Windows XP dual-booting with Ubuntu 10.10 for a while now.

After the upgrade finished it booted into the grub rescue prompt with the following error: symbol not found:  'grub_env_export'.

I figured the simplest way to fix this problem would be to use the "Restore GRUB After Installing Windows" guide in the community documentation, [found here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Restoring%20GRUB").

Whoever wrote this guide needs to be shot in the face because of instructions like this:

> **Note:**

You should have mounted the partition which has your Linux system before typing this command.

It is SOOO nice to be told to do something AFTER you were supposed have done it already.  I'll probably take it upon myself to rewrite this guide after I figured out the "best" way to fix this problem; first I have to fix the problem before I can fix this poorly written guide.

Anyway, so it says I should have mounted the root partition.  In this case they have the following setup:

sdb1 is a FAT32 system recovery partition
sdb2 is their Windows partition (and default boot partition, denoted by the * by the entry with **fdisk -l**)
sdb3 is their / Linux partition
sdb4 is the extended partition and within that container is sdb5, the swap.

There is no separate partition for /home or /boot, so it is assumed (from the instructions, or lack of them) that the only partition that needs to be mounted is /dev/sdb3

I created a new directory in /media called "linux" as a mountpoint to put /sdb3.  I then ran:

```
sudo mount /dev/sdb3 /media/linux
```

and browsed to that new folder in Nautilus to confirm the partition had been mounted correctly and it was; I could browse into the boot folder and anywhere else for that matter.

Going back to the guide, I ran the "grub" command (by the way, this "grub" package isn't included on the 11.04 CD; I had to use apt-get to install it).

In the grub command prompt now I typed "find /boot/grub/stage1".

It would return an error saying nothing could be found.  At a loss, I CTRL-C'ed to kill the process and return to the command prompt.

Not knowing how else to use the grub program and given no troubleshooting tips in the guide at this point on what to do if this "Not Found" issue happens, I decided to try and find a different guide.  I came across [this one]("https://odzangba.wordpress.com/2011/05/14/455/").

Judging by the instructions it listed and the progress I had made so far (just mounting the root partition to /media/linux and nothing further) I proceeded to execute the following command:

```
sudo grub-install --root-directory=/media/linux /dev/sdb
```

The command executed and reported no errors.  I then restarted the computer.  This seemed to make a bit of progress but now I am faced with a new problem.

The grub rescue prompt was fixed but the main grub menu didn't appear on screen and the system boots strait into command line interface asking for the username and password.  You are able to login.  My assumption was that the next thing we needed to do was run the "grub-update" command from the command prompt.  This went through and detected several kernals, and I was doing this over the phone with them so I couldn't see the output, but assumed the command did what it was suppose to do (repopulate the grub menu list file with entries based on auto-detecting all kernals and other bootable partitions).

After rebooting, we were right back at the same user login prompt.  No grub menu appeared along the way.

So I'm pretty well stumped and frustrated.  I'm also dismayed that this kind of stuff happens after upgrades "Successfully complete".  Like there's no way for the installer to check the integrity and stability of grub before telling he user it's safe to reboot and then discover they can't user their computer at all.

Where did I go wrong and what do I need to do to fix this system?

---

### Post by Hedgehog1 on 2011-05-23
That is quite a post.

Between the rant, there is enough data to get your friends system working again.

You **_MUST_** use and 11.04/Natty LiveCD/LiveUSB for these two steps **if you want GRUB to work correctly**. Grub has been updated for the 11.04 release:

```
sudo mount /dev/sdb3 /mnt
```

```
sudo grub-install --root-directory=/mnt /dev/sdb
```

I know you have done these steps already - but it appears to me you did not do them with a Nattty/11.04 CD.  Please repeat them with the 11.04/Natty LiveCD/LiveUSB 

This will give you grub to Ubuntu.  You can force the grub menu to show by holding down the [shift] key when booting.

Once you have booted into Ubuntu, you will need to run this command:

```
sudo update-grub
```

It should be more successful with the correct grub loaded on the PC, and you should see Windows show in the grub menu.

***The Hedge***

:KS

p.s. Rather than have you act as a go between, can you friend post on the forum directly and we get rid of one layer of translation?

---

### Post by jtarin on 2011-05-23
> **diablo75 said:**
> I figured the simplest way to fix this problem would be to use the "Restore GRUB After Installing Windows" guide in the community documentation, [found here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Restoring%20GRUB").
No the simplest way would have been to have your friend register on the forum and ask the question.

[Finding the right source is invaluable.]("https://help.ubuntu.com/community/Grub2#METHOD%203%20-%20CHROOT")

---

### Post by diablo75 on 2011-05-23
> **Hedgehog1 said:**
> That is quite a post.

Between the rant, there is enough data to get your friends system working again.

You **_MUST_** use and 11.04/Natty LiveCD/LiveUSB for these two steps **if you want GRUB to work correctly**. Grub has been updated for the 11.04 release:

```
sudo mount /dev/sdb3 /mnt
```

```
sudo grub-install --root-directory=/mnt /dev/sdb
```

I know you have done these steps already - but it appears to me you did not do them with a Nattty/11.04 CD.  Please repeat them with the 11.04/Natty LiveCD/LiveUSB 

This will give you grub to Ubuntu.  You can force the grub menu to show by holding down the [shift] key when booting.

Once you have booted into Ubuntu, you will need to run this command:

```
sudo update-grub
```

It should be more successful with the correct grub loaded on the PC, and you should see Windows show in the grub menu.

***The Hedge***

:KS

p.s. Rather than have you act as a go between, can you friend post on the forum directly and we get rid of one layer of translation?

I am sorry but this was done with a fresh copy of Ubuntu 11.04 Live 32-bit, just downloaded and burned yesterday.

He's also not a very technically savvy person and coincidentally his laptop is on the fritz so he doesn't have a very direct way to access the forum at this time.  I plan to visit his house on Tuesday to address the problem first hand, and at this point I am probably going to just backup his /home folder and format the Linux partition, reinstalling after that.

---

### Post by Hedgehog1 on 2011-05-23
> **diablo75 said:**
> ...I plan to visit his house on Tuesday to address the problem first hand, and at this point I am probably going to just backup his /home folder and format the Linux partition, reinstalling after that.

That seems the best plan of attack to get his PC running again.

Hope it goes well this time!

***The Hedge***

:KS

---

