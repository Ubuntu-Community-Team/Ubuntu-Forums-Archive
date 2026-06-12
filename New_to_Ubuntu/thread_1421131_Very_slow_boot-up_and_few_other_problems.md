---
title: "Very slow boot-up and few other problems"
date: 2010-03-03
forum: New to Ubuntu
---

### Post by dpacmittal on 2010-03-03
I am a new ubuntu user and have run into quite a few problems lately:

1) My bootup has become extremely slow. I had upgraded from Jaunty to Karmic and the bootup is very slow. I did something and the splash screen was gone. I was shown the processes while booting. I was fine with this, I didn't need the splash. However after pressing enter on the GRUB menu, it shows black screen for 25 seconds and only after which processes list start to come up. I am not able to identify the problem. Here's the snippet of kern.log which shows my bootup:

[http://pastebin.com/dEycKgSB](http://pastebin.com/dEycKgSB)

Help me find out what's causing the problem and any possible solution.

2)I tried following a tutorial which showed converting my existing Karmic to Linux Mint Helena. It did convert to Helena but after removing the packages, the grub menu still shows Linux Mint on the list. How do I fix that?

3) I've got multiple DE's installed (I love to try out things). And my login screen has stuck up in XFCE. I want the default karmic login screen back but so far I haven't been able to. I want to know this too.

---

### Post by quixote on 2010-03-04
The splash screen disappears either when a line similar to the following in the /etc/default/grub file does not have "quiet" : ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```or when there is an error message during the boot process.  It can go by too fast to read, which is frustrating, but if you can spot it, it should be in red.  

I don't know the reason for the slow boot time (I'm not too good at reading kernel log files :)), but I notice you have some virtualbox drivers working in there.  They can sometimes take a very long time.  It looks like they're for vbox 3.1.2, and at this point they're up to version 3.1.4.  Maybe try upgrading that??  Who knows, they may have better kernel modules now.  (I use 3.1.4 and haven't noticed slow booting, but I don't remember it with 3.1.2 either. So it may have nothing to do with it.)

The Linux Mint is still showing up because it's still somewhere in grub's lists, even though it's no longer on the drive.  I'm not sure where that goes in the new grub.  Check the files in /etc/grub.d.  It may have it's own entry, in which case I think you can just delete it, or have a few lines in ##_custom (usually something like 40_custom), in which case delete those.

After making changes to grub, run ```
sudo update-grub
```

The splash screen depends on files in, I think, /usr/share/images/xsplash.  But I'm pretty sure you have to do something besides put an image there to get it to work in a splash screen, unless the only thing that needs changing is the background jpg.  Search for "ubuntu boot splash" and see if something useful comes up.

---

### Post by dpacmittal on 2010-03-05
Thanks for the reply.
I checked out my /etc/default/grub and it does have 'quiet' in it.

Also, updated the virtualbox but it still is slow.

/etc/grub.d file cannot be opened by a text-editor.

However, the main problem is the slow booting as of now. It has gone slower after upgrading to Karmic. I will clean install lucid lynx this time but theres still lot of time for lucid lynx to be launched.

---

### Post by r-senior on 2010-03-05
You could try [profiling your boot]("http://ubuntuforums.org/showthread.php?t=254263")?

Or you could try bootchart?

$ sudo apt-get install bootchart

The latter produces a log in /var/log/bootchart which may help you narrow things down.

---

### Post by dpacmittal on 2010-03-05
I tried bootchart and I found out that ureadahead is taking almost 20seconds. What is it? Can I disable it? Is it worth keeping when it takes 20seconds of boot-up time?

---

### Post by Enigmapond on 2010-03-05
This thread may be of assistance to you. It will enable you to customize the boot and disable certain processes and services that you are not using. I know it helped me a lot.

[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

Cheers!

---

### Post by quixote on 2010-03-05
This is what it says about [ureadahead on the launchpad page]("https://launchpad.net/ubuntu/+source/ureadahead"): > über-readahead is used during boot to read files in advance of when they are needed such that they are already in the page cache, improving boot performance. Its data files are regenerated on the first boot after install, and either monthly thereafter or when packages with init scripts or configs are installed or updated. ureadahead requires a kernel patch included in the Ubuntu kernel.There's some bugs associated with it that mention slow boot times....  Sort of ironic.  But anyway, since it doesn't do anything absolutely essential, you could try turning it off and see if that helps.

---

### Post by dpacmittal on 2010-03-06
^Couldn't find a single tutorial which showed how to disable/remove ureadahead. I guess I can't remove it.

---

### Post by skymera on 2010-03-06
sudo apt-get remove ureadahead

that should remove it for you.

When ureadahead profiles my boot it takes ~27secs to boot from GRUB to desktop
The next boot takes ~16secs to boot from GRUB to desktop.

Bootchart will show if ureadahead is profiling.

---

### Post by oldfred on 2010-03-06
If you have multiple drive grub adds about 20 sec to search. Some other issues solved different ways:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933)
Slow boot, multi drives, known issue, move boot to same drive & adjust BIOS
sudo dpkg-reconfigure grub-pc
Very long boot solved with experimental grub1.98 post8
[http://ubuntuforums.org/showthread.php?t=1367488](http://ubuntuforums.org/showthread.php?t=1367488)
Slow boot change device.map
[http://ubuntuforums.org/showthread.php?t=1313207](http://ubuntuforums.org/showthread.php?t=1313207)

---

