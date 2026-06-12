---
title: "grub rescue: no partition error"
date: 2010-06-07
forum: New to Ubuntu
---

### Post by ak79 on 2010-06-07
Hi all,
 
I have been trawling through all the treads related to my dilemma but I haven't come across an adequeate solution.
 
I am very new to Ubuntu so please be gentle.
 
So the situation:
 
I installed the Ubuntu Netbook remix on my Asus Eee Pc 1005PE, dual booting with Windows 7 Starter.
 
That worked fine. Then I stupidly went about deleting the partition that Ubuntu resides in. I realise that I have altered the Master Boot Record and have to find a way to restore it or re-install Ubuntu.
 
Now, when I start my pc, I get the following:
 
error: no such partition
grub rescue>
 
I tried to resinstall Ubuntu via the USB drive but when I do this I get the following:
 
SYSLINUX 3.85
Unknown keyword in configuration file: gfxboot
 
I still have the windows operating system, but I just cant get to the System Recovery.
 
I honestly don't know what to do from here.......

---

### Post by sidzen on 2010-06-07
See [http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/)
The same can be done (fixing Windoze) with most any live CD.  I like Puppy for this.

---

### Post by ak79 on 2010-06-07
> **sidzen said:**
> See [http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/)
The same can be done (fixing Windoze) with most any live CD. I like Puppy for this.
Hi sidzen,
 
thanks for the quick response.
 
the netbook doesnt have a cd drive as you know and i dont have a working cd drive at my disposal. can i 'burn' the Ubuntu Live CD to the USB drive and try and load it that way??
 
if so, can you recommend a program that does this please?
 
 
Cheers

---

### Post by ak79 on 2010-06-07
In addition to my previous message, here is what i did to finally get past this stage.

1. From another pc, i downloaded the torrent .iso file of the ubuntu remix that i installed previously (10.04).

2. I used Bit Torrent to download the .iso (699MB) file. I found that using uTorrent, the file got corrupted somehow.

3. I then used UNetbootin to create a USB flash to load on my netbook

4. Configure the BIOS to load the USB device

5. If you get a blue screen that says default, with a timer on a continuous loop like i did the first couple of times, then dont panic just yet. This may mean that the flash drive that you made may be corrupt or have an incorrect checksum. This may mean that you have to download the .iso file again and recreate the USB flash. It happened to me a couple of times and I was really stuck!

6. After the third time, the USB actually worked, but i did get an error message saying something like process_id (0) not found. I ignored this as i was so happy that something different happened and continued. It then should go to the Ubuntu Live desktop.

7. This is where i clicked to reinstall Ubuntu and after the reboot it works almost as good. I have noticed a slight decrease in performance, but I am much happier than where i was this afternoon.

8. I still dont have Ubuntu off my system but i can live with that for the time being. I actually wanted to allocate more disk space to the operating system which caused this frustrating journey in the first place.

So as far as this thread is concerned it is solved!

Hope this helps anyone who gets stuck in the same situation. The threads are everywhere with bits and pieces of information that others had similar problems to this one.

Good luck!

---

