---
title: "Incomplete Ubuntu OS Fixed DIRECTLY from Internet?"
date: 2009-05-27
forum: New to Ubuntu
---

### Post by AvocadoNia on 2009-05-27
Can I repair and/or upgrade Ubuntu DIRECTLY from an online repository?

In mid-March 2009 I used the synaptic manager to delte Evolution--all the items suggested to make the un-installation complete.

The result was the diappearance of all panels

eeePC partitiond HD 15%  MS, 85% UBUNTU was partitioned using a live CD in a peripheral device compatible only with MS, not with Linnux.

I have tried all previous suggestions... [URL="http://ubuntuforums.org/showthread.php?t=1099714"]http://ubuntuforums.org/showthread.php?t=1099714
[/URL]
Apparently my installation, what is left of it, cannot access the repositories.

So, since I can go to us.archieve.ubuntu.com or presumably anyother public repository of ubuntu...can I fix/re-install/upgrade DIRECTLY from internet? 

Any CD that I create/burn cannot be used by me on the UBUNTU side of the partition. I don't have the proper hardware.

UBUNTU 8.10 willing to upgrade to 9.04. Understand Evolution is part of package and should not be removed completely. Got that part...now.

Although "crude" and amateurish...well...I thnk that I need to remove the partition, hae only MS OS and then re-partition and have the Ubunu OS on the onther side of the partition.

a link to a step by step, for an amateur, would be appreciated. :)

---

### Post by Didius Falco on 2009-05-27
Try this:

Boot into Recovery Mode, Root Shell

when you get to the command line, type ```
cd /var/cache/apt/archives
```That will put you in the directory where all the Deb files you have installed are kept. 

Now type ```
sudo dpkg -i *.deb
```Provided you haven't cleaned out the cache, everything should still be in there and it will reinstall all of it.

After it's done, reboot.

I hope it helps...

Regards,

Didius

---

### Post by AvocadoNia on 2009-05-27
Thanks, it's definitely worth trying!

---

### Post by Didius Falco on 2009-05-27
Please post back and let us know how it works out.


Regards,

Didius

---

### Post by AvocadoNia on 2009-05-28
Results for inputting the first string...
"no such file or directory found"

I will try again. I copied my bookmarks and moved items on my desktop that I wanted to salvage into a memory stick yesterday. I recall seing "debian" and the idon of a brown box partially open. But I put "moved to trash". Now of course I have a desktop withoout any panels or visible trash.

How can I retrieve that from trash? I'll work on that.;)

---

### Post by Didius Falco on 2009-05-28
You might be better off at this stage just salvaging what you want to save, burning a CD from a downloaded iso file (you can download & burn it from the Windows side, or even from another PC) and install right over the top of your current install.

The easiest way to do that would be to:

1. Set up your Bios to boot from a CD first. Most modern Bioses have a key you can press at boot up that lets you pick what the first boot device is. If you have youir manual, it will tel you what key it is, other wise, just start the pc and watch the Bios screen. After you knowwhich key to press, just restart with the CD in the drive and press that key.

2. Choose the "Make no changes" option and let the CD boot to the desktop.

3. Start the installer. When it gets to the Partitioner part, choose **Manual (advanced)**. Don't worry, it isn't all that advanced...

4. Once the Partitioner is open, you should see your Ubuntu partitions. If you went for the default install, you'll probably have 2 partitions; an EXT3 partition, which will the Ubuntu partition, and a Linux Swap partition.

5. Highlight the EXT3 partition and click the "edit partition" button at the bottom of the partitioner screen. Set it to "use", "EXT3", and "/", which will make it your Root Partition - the one that holds Ubuntu. Be sure and tell it to Format the partition.

6. Highlight the Linux Swap partition and repeat the above, except set it to Swap instead of EXT3.

7. Continue on with the installation and you should soon be in a brand spanking new installation.

8. Enjoy your new install!!

Regards,

Didius

---

### Post by AvocadoNia on 2009-05-28
Thank you. When ever this challenge is resolved I'll definitely close this thread.I appreciate your help. :)

---

