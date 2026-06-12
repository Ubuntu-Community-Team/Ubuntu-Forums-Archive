---
title: "won't boot......busybox prompt..."
date: 2009-08-06
forum: New to Ubuntu
---

### Post by STUMPOFWAR on 2009-08-06
OK...I have a HP DV6815NR laptop......AMD64...running 9.04 64 bit. It's been running Ubuntu for about a year without any problems.

It won't boot. Grub loads up....I then get the Ubuntu progress bar which starts progressing and then:

failed to mount /dev
failed to mount /sys
failed to mount /proc
target file system doesn't have /sbin/init

Then I get the Busybox prompt

I recently put in new RAM in the computer, but I've rebooted this machine over a dozen times without issue since then. 

The last thing I did this morning was sync my iPod in Rhtyhmbox. I was running late for work, so I stopped the file transfer and ejected the iPod and then turned the laptop off. Before the laptop shutdown I got a message saying Rhythmbox wasn't responding. I clicked "logout anyway" and it shut down. When I arrived at work it wouldn't boot.

I went into the Grub menu and tried recovery mode without any luck. I also went into BIOS and had it check the HD and RAM and both passed the tests.

I imagine that I screwed up some permissions or something when I stopped the file transfer.

Not sure what to do now.....

---

### Post by STUMPOFWAR on 2009-08-06
Also.... the specs for my laptop can be found here: [http://shopper.cnet.com/notebooks/hp-pavilion-dv6815nr/4014-3121_9-32976283.html#info-5](http://shopper.cnet.com/notebooks/hp-pavilion-dv6815nr/4014-3121_9-32976283.html#info-5)

and the HD is not original.....I upgraded it to a bigger faster Western Digital Drive 10 months ago.... but I don't think that matters.....but just in case....

I did a fresh install of 9.04 when it was released and I have no other OSes or partitions installed.

---

### Post by ptn107 on 2009-08-06
I recently had the same exact problem with Debian testing x86-64 last week.  I thought it had to do with me using ext4 on my / (and therefore /boot) partition and the kernel 2.6.26 not being able to boot from ext4 partitions.  Formatting to ext3 fixed it for me.

As for your problem I think just a reinstall of GRUB to the mbr will fix things (maybe): _[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")_

---

### Post by MelDJ on 2009-08-06
try scanning and fixing your discs for errors

---

### Post by utnubuuser on 2009-08-06
I've heard iPods sometimes cause of the problem.

---

### Post by STUMPOFWAR on 2009-08-06
Thanks for the responses everyone.

I am trying to reinstall grub right now....

On the second response..... how do I scan for errors? What would the command prompt be?

---

### Post by LewRockwell on 2009-08-06
> **STUMPOFWAR said:**
> Thanks for the responses everyone.

I am trying to reinstall grub right now....

On the second response..... how do I scan for errors? What would the command prompt be?

[http://ubuntuforums.org/showthread.php?t=1162513](http://ubuntuforums.org/showthread.php?t=1162513)

.

---

### Post by john.quinn on 2012-05-25
In my case, I received the same errors as you. But I was able to use a very simple fix, because disk sectors needed fixing. So I just booted Ubuntu from CD (or DVD) - it was an older version, too. Then, once completely booted, I ran "Disk Utility" from the launcher. Clicked on my hard drive, and clicked "Check Filesystem". Then I chose "Restart" from the normal system menu, removed the CD when instructed to do so, and booted from the hard drive, and it worked.

---

### Post by lisati on 2012-05-25
A lot has happened in three years. Thread closed.

---

