---
title: "How to uninstall Ubuntu"
date: 2009-11-26
forum: New to Ubuntu
---

### Post by Crosboro on 2009-11-26
Have a problem.  I installed Ubuntu (twice) alongside Windows XP.  However, when I start up, get this message:
GRUB Loading.
error: no such partition
grub rescue>
Beyond that, nothing happens.

However, I can get to Ubuntu by putting the CD in and going to using Ubuntu w/o installing again.  But, I cannot get to Windows at all.  
When I get to Ubuntu, when I check the systems, it shows IMB Preload, 3.2 GB Filesystem and 3.5 GB Filesystem.  I unmounted the 3.5 GB, went to System/Admin/Disk Utility and then clicked Delete, and the 3.5 GB has disappeared, but that probably means nothing,

So, how can I totally uninstall Ubuntu?  I've gone through the forums, read the guide, but can't find a solution.  Also, I no longer have the Windows XP disk--have no idea where it is.

Thanks for any help.

---

### Post by arochester on 2009-11-26
"HowTo: Remove Ubuntu (& Restore Windows)" at [http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

---

### Post by mlentink on 2009-11-26
You could help us help you.

If you boot up with the Ubuntu LiveCD, and then choose
Applications>Tools>Terminal

type the following in the window that appears, after the 'prompt' (it looks like "user@computer:~$')

```
sudo fdisk -l
```

Please take care: the last character is the undercase letter L, not the number 1!

then copy and paste the result in your answer here

---

### Post by kansasnoob on 2009-11-26
You can also use SGD to restore XP's mbr:

[http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html](http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html)

Although I'd prefer to try and work out your grub problem with Ubuntu.

I know you're bound to be frustrated, many of us have been with grub2!

If you want to try and work it out please use the following guide to run the Boot Info Script from the Live CD and post the results here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by kansasnoob on 2009-11-26
Or you can use ms-sys from an Ubuntu Live CD:

[http://members.iinet.net.au/~herman546/p18.html#Replace_GRUB_in_MBR_with_ms-sys](http://members.iinet.net.au/~herman546/p18.html#Replace_GRUB_in_MBR_with_ms-sys)

BTW, just realized that ms-sys had been removed from the repos in Karmic because Gates' Microslop needed something to complain about. You can still get the .deb however:

[http://packages.debian.org/etch/i386/ms-sys/download](http://packages.debian.org/etch/i386/ms-sys/download)

Worth burning a disc!

---

### Post by mlentink on 2009-11-26
OK guys (or gals),

However much I appreciate your efforts, to me it is obvious that the OP (=Original Poster) is not someone conversant with the ubuntu/gnu-linux lingo:
> it shows IMB Preload, 3.2 GB Filesystem and 3.5 GB Filesystem.  I unmounted the 3.5 GBWhen was the last time you saw a 6GiB disk?

So, to Crosboro: Would you mind trying to do what I asked? If you run into trouble, please come back and ask. This is, for all intents and purposes, the 'Absolute Beginner Talk'-forum.

---

### Post by kansasnoob on 2009-11-26
> **mlentink said:**
> OK guys (or gals),

However much I appreciate your efforts, to me it is obvious that the OP (=Original Poster) is not someone conversant with the ubuntu/gnu-linux lingo:
When was the last time you saw a 6GiB disk?

So, to Crosboro: Would you mind trying to do what I asked? If you run into trouble, please come back and ask. This is, for all intents and purposes, the 'Absolute Beginner Talk'-forum.

Not sure what you're saying there honestly. If you look at the OP's previous posts the most recent:

[http://ubuntuforums.org/showthread.php?t=1323158&page=2](http://ubuntuforums.org/showthread.php?t=1323158&page=2)

(S)he had:

> Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

Device Boot Start End Blocks Id System
/dev/sda1 * 1 3977 31945221 7 HPFS/NTFS
/dev/sda2 3978 4864 7124827+ 5 Extended
/dev/sda5 3978 4371 3164773+ 83 Linux
/dev/sda6 4820 4864 361431 82 Linux swap / Solaris
/dev/sda7 4372 4792 3381651 83 Linux
/dev/sda8 4793 4819 216846 82 Linux swap / Solaris

Partition table entries are not in disk order

In the same thread I asked for output from the Boot Info Script and I was ignored. Now, there may be a language barrier, or maybe this is a case where the OP is clueless. BTW: I'm not being rude but I've been clueless and the only way to get a clue is to keep digging for an answer, which the OP has not done.

But the OP clearly knew how to find the terminal once. Yet today we get no response when we make suggestions, etc. Getting help requires a "back-n-forth" because we don't have the machine right in front of us.

I did just test a new procedure (new to me), and after reviewing the previous posts and seeing this is XP, and if the previous fdisk -l is still the way things are, and if they want to just go back to Windows do this:

Boot the Live CD, once in the Live desktop go to terminal and run:

```
sudo apt-get install mbr
```

```
sudo install-mbr /dev/sda
```

```
sudo reboot
```

If Windows boots then boot the Live CD again to get rid of all Ubuntu. To do so go to System > Administration > Gparted and delete all partitions **other than sda1**. **[COLOR="Red"]You must keep sda1! [/COLOR]**Then click on sda1 **and be sure to untick the "round to cylinders" block.** Then choose resize/move and expand it all the way to the right.

Now, review the changes, make darn sure that sda1 is being kept and taking up the free space, then click on the big green check mark to apply the changes. Wait until it is completely finished before restarting.

I really don't think I can simplify things anymore than that.

---

### Post by mlentink on 2009-11-26
Apologies kansasnoob, I had not seen the other posts, was just trying to tackle this one.

And I'm with you as to the solution.

@Crosboro: It is not considered polite forum conduct to double post.

---

### Post by kansasnoob on 2009-11-26
> **mlentink said:**
> Apologies kansasnoob, I had not seen the other posts, was just trying to tackle this one.

And I'm with you as to the solution.

@Crosboro: It is not considered polite forum conduct to double post.

No apologies necessary. I'm a cranky old man :p

Definitely less cranky since I discovered Ubuntu!

---

### Post by Crosboro on 2009-11-27
> **kansasnoob said:**
> Not sure what you're saying there honestly. If you look at the OP's previous posts the most recent:

[http://ubuntuforums.org/showthread.php?t=1323158&page=2](http://ubuntuforums.org/showthread.php?t=1323158&page=2)

(S)he had:



In the same thread I asked for output from the Boot Info Script and I was ignored. Now, there may be a language barrier, or maybe this is a case where the OP is clueless. BTW: I'm not being rude but I've been clueless and the only way to get a clue is to keep digging for an answer, which the OP has not done.

But the OP clearly knew how to find the terminal once. Yet today we get no response when we make suggestions, etc. Getting help requires a "back-n-forth" because we don't have the machine right in front of us.

I did just test a new procedure (new to me), and after reviewing the previous posts and seeing this is XP, and if the previous fdisk -l is still the way things are, and if they want to just go back to Windows do this:

Boot the Live CD, once in the Live desktop go to terminal and run:

```
sudo apt-get install mbr
```

```
sudo install-mbr /dev/sda
```

```
sudo reboot
```

If Windows boots then boot the Live CD again to get rid of all Ubuntu. To do so go to System > Administration > Gparted and delete all partitions **other than sda1**. **[COLOR="Red"]You must keep sda1! [/COLOR]**Then click on sda1 **and be sure to untick the "round to cylinders" block.** Then choose resize/move and expand it all the way to the right.

Now, review the changes, make darn sure that sda1 is being kept and taking up the free space, then click on the big green check mark to apply the changes. Wait until it is completely finished before restarting.

I really don't think I can simplify things anymore than that.

Sorry for the double post, but I did post the results of  sudu fdisk - l, and there was no response.  I just re-read your post that suggested this, and there were no other questions asked.  And, I don't take offense at being clueless, because I am when it comes to this stuff.  I'm going to try out all of the suggestions in this thread over the next couple of days and let you all know what happens.    
I appreciate all of your efforts.  Be back soon.

---

### Post by Crosboro on 2009-11-28
I've been trying the above suggestions, and have the following results:

1.  Anything that requires Windows won't work, as I can't boot Windows.

2.  When I boot with the UbuntuCD, I do not get Applications/Tools/Terminal.  Instead, I get Applications/Accessories/Terminal.  When I go there, I get:

ubuntu@ubuntu:~$ sudu fdisk -l
No command 'sudu' found, did you mean:
 Command 'tudu' from package 'tudu' (universe)
 Command 'sudo' from package 'sudo' (main)
 Command 'sudo' from package 'sudo-ldap' (universe)
sudu: command not found
ubuntu@ubuntu:~$ 

No matter what I put in there, or reset and clear, I get the same results.

3.  The debian suggestion doesn't get me to a download--just a page of letters and symbols.

4.  In Gparted, there is /dev/sda1 and /dev/sda2.  Only the sda1 will allow a delete command to work (which I haven't done).  

That's it for now.  I'm still trying to figure out a couple of the other suggestions, but so far have not been able to figure them out.  I would try the XP recovery disk approach, but it seems I would need the XP install disk afterward, and that I don't have.

Thanks for putting up with an inept user.

---

### Post by Crosboro on 2009-12-08
I have solved my problems, using this:
[http://robert.penz.name/221/mini-howto-restore-windows-mbrbootloader-with-linux/](http://robert.penz.name/221/mini-howto-restore-windows-mbrbootloader-with-linux/)
Method 2 worked just fine.
I'm done with my little experiment.
See ya!

---

### Post by Cuco3 on 2009-12-08
Glad it worked out for you. Ubuntu has a couple quirks that might arise when you first install it. Once you get them out the way, the experience is life-changing. :D

---

### Post by Crosboro on 2009-12-09
> **Cuco3 said:**
> Glad it worked out for you. Ubuntu has a couple quirks that might arise when you first install it. Once you get them out the way, the experience is life-changing. :D
 
I may try it again.  It's an older laptop that I've replaced, but had to get back into Windows to make sure I'd cleared out/transferred everything I needed.  Now that I did, I've cleaned all the files out and have 50% of the GBs available.  So, I'm thinking maybe just install this again and totally wipe out Windows, as I have no need for XP anymore.
We'll see......

---

