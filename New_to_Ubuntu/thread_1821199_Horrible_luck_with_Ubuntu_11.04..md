---
title: "Horrible luck with Ubuntu 11.04."
date: 2011-08-08
forum: New to Ubuntu
---

### Post by thatguy93 on 2011-08-08
Hey guys,
So first I deleted some files, and cant recover them, then my user account did not have admin rights, well now Ubuntu is not even booting properly.

The screen is black, and says:

*Stopping Sytem V runlevel compatibility          [OK]
*Stopping cold plug devices                       [OK]
*Stopping log initial device creation             [OK]
*Starting configure virtual network devices       [OK]
*Stopping configure virtual network devices       [OK]
*Starting configure network device security       [OK]
*Starting CUPS printing spooler/server            [OK]

Thats all it does. 
What do I need to do?

I think I am going to throw this laptop in the trash once I get my files back.

---

### Post by JC Cheloven on 2011-08-08
It's difficult to guess in which state your system could be with only the info you provide. Perhaps if you could be more specific on what you did we could step into it.

To simply recover files (and maybe throw away the box later lol), the easiest method is to boot from live cd.

---

### Post by thatguy93 on 2011-08-08
> **JC Cheloven said:**
> It's difficult to guess in which state your system could be with only the info you provide. Perhaps if you could be more specific on what you did we could step into it.

To simply recover files (and maybe throw away the box later lol), the easiest method is to boot from live cd.

I tried to use "foremost" to get my files back. I typed in something along the lines of ```
sudo foremost -T doc -i /dev/sdb1 
```

After that, my whole file system was filled(I had around 15GB free, before).
Then I logged out to try and log into root so I could delete some files, but I could not get into root, or my user account (BTW the login was blue and gray, instead of the regular colours).
So i restarted, and got the stuff in my OP.

When I boot with the Live USB I am able to get onto the computer, but cant access files since they are all locked.

---

### Post by elgordodude on 2011-08-08
Try:

sudo chown -R username /location_of_files_or_folders

Remember you can drag folders into terminal to save yourself some time. Just went through this when my 11.04 could only boot to a black screen. Currently reinstalling 10.10....

Also remember the super useful "sudo nautilus"

---

### Post by thatguy93 on 2011-08-08
> **elgordodude said:**
> Try:

sudo chown -R username /location_of_files_or_folders

Remember you can drag folders into terminal to save yourself some time. Just went through this when my 11.04 could only boot to a black screen. Currently reinstalling 10.10....

Also remember the super useful "sudo nautilus"

That is all giberish for me lol.

---

### Post by sandyd on 2011-08-08
> **thatguy93 said:**
> That is all giberish for me lol.

Well, you can't boot because your hard disk is full.

Go to a livecd/usb/whatever, and boot.

Go to Applications/Accessories/Terminal.

Type in gksudo nautilus, mount the partition, and begin deleting.

---

### Post by thatguy93 on 2011-08-08
> **sandyd said:**
> Well, you can't boot because your hard disk is full.

Go to a livecd/usb/whatever, and boot.

Go to Applications/Accessories/Terminal.

Type in gksudo nautilus, mount the partition, and begin deleting.

Okay I do that, and it opens the root home folder.
However, nothing is in there, I cant find my user home folder.

---

### Post by sandyd on 2011-08-08
> **thatguy93 said:**
> Okay I do that, and it opens the root home folder.
However, nothing is in there, I cant find my user home folder.

as said, you have to mount the partition, then go into the folder where the partition is mounted to delete stuff.

Post the output of ```
 sudo fdisk -l
``` if you don't know how to do that.

---

### Post by thatguy93 on 2011-08-08
> **sandyd said:**
> as said, you have to mount the partition, then go into the folder where the partition is mounted to delete stuff.

Post the output of ```
 sudo fdisk -l
``` if you don't know how to do that.

```
sudo fdisk -l
``` results:

```

Device boot    start      end    blocks   ID   System

/dev/sda1 *     1        4800   38554624   83   linux
/dev/sda2       4801     4864   513025     5   extended
/dev/sda5       4801     4864   513024     82   Linux swap/solaris
```

```

Device boot   start     end     blocks   ID    system

/dev/sdb1 *      1      515    4128736+   b    W96 FAT32
Partition 1 has different physical/logical endings:
phys= (513, 254, 63) logical= 9514, 1, 630
```

Hope that is the right stuff.

---

### Post by JC Cheloven on 2011-08-09
> **thatguy93 said:**
> I tried to use "foremost" to get my files back. I typed in something along the lines of ```
sudo foremost -T doc -i /dev/sdb1 
```

After that, my whole file system was filled(I had around 15GB free, before).
Then I logged out to try and log into root so I could delete some files, but I could not get into root, or my user account (BTW the login was blue and gray, instead of the regular colours).
So i restarted, and got the stuff in my OP.

When I boot with the Live USB I am able to get onto the computer, but cant access files since they are all locked.
I think (looking at [this]("http://linux.die.net/man/1/foremost")) that you used capital "-T" switch (wich means "add time stamp") instead of "-t", which is the right switch to specify the file type. Also, I don't see a "-i" option. To bad the command has can lead to unpredictable results instead of returning an error :(

I'm not clear yet why you used a forensic tool like foremost in the first place. Perhaps you had previous problems? Anyway.

Ok, I don't want to get you confused with multiple advice: what the other forumites said should work. Only, I don't know where foremost may have placed the offending files. I'd look at /home/yourusername...

---

### Post by thatguy93 on 2011-08-09
> **JC Cheloven said:**
> I think (looking at [this]("http://linux.die.net/man/1/foremost")) that you used capital "-T" switch (wich means "add time stamp") instead of "-t", which is the right switch to specify the file type. Also, I don't see a "-i" option. To bad the command has can lead to unpredictable results instead of returning an error :(

I'm not clear yet why you used a forensic tool like foremost in the first place. Perhaps you had previous problems? Anyway.

Ok, I don't want to get you confused with multiple advice: what the other forumites said should work. Only, I don't know where foremost may have placed the offending files. I'd look at /home/yourusername...

Ya I had tried -t, and it gave me an error, so I used -T. I followed this from a website.
I used foremost to try and recover some deleted files.
Foremost created two folders. But one of them is locked, I cant delete anything from it.

---

### Post by thatguy93 on 2011-08-09
Alright well I guess I am going to have to reinstall ubuntu.
How do I do that without losing any current files? Defined steps would be awesome.

---

### Post by JC Cheloven on 2011-08-10
> **thatguy93 said:**
> Alright well I guess I am going to have to reinstall ubuntu.
How do I do that without losing any current files? Defined steps would be awesome.

Well, this should be easy. Boot from live CD, use the live session to access the partition where the data are (your ubuntu partition I presume), and save them in an external disk or whatever. This obviously doesn't apply to those files you deteted.

Then proceed to install from the same live session to your hard disk.

If you have more specific questions, please don't hesitate to ask.

---

