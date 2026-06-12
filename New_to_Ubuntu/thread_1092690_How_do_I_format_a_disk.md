---
title: "How do I format a disk?"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by sp176 on 2009-03-10
I am looking to format my USB drive.  It is probably FAT32, but I am wanting to format for just FAT.  This will allow me to use it for my nintendo wii.

---

### Post by cmay on 2009-03-10
you can use gparted on the live cd. or download it via apt-get or add/remove in the menu. or using synaptic.

---

### Post by sp176 on 2009-03-10
Thanks cmay.  It seems I already have that program, but I cannot figure out how to get it to format.  I can see a whole lot of information about my drives, but there are very few options to change anything.

---

### Post by kansasnoob on 2009-03-10
Are you able to mount the drive?

If not try installing pmount from synaptic or:

```
sudo apt-get install pmount
```

If it's ntfs install ntfsprogs (also in the repos).

---

### Post by sp176 on 2009-03-10
No problems mounting the drive.  I can see now that it is definetely FAT32 format, my problem is carrying the info I put on the drive to my nintendo.  It will only read FAT.

That NTFS looks promising, and I already have it installed from what synaptic is telling me, where can I find it in my menu?

---

### Post by kansasnoob on 2009-03-10
> **sp176 said:**
> Thanks cmay.  It seems I already have that program, but I cannot figure out how to get it to format.  I can see a whole lot of information about my drives, but there are very few options to change anything.

So, if you go to System > Administration > Partition editor with that drive plugged in you should be able to "toggle" to it:

[ATTACH]106031[/ATTACH]

See in the upper right hand corner where I highlighted and where my mouse pointer is?

---

### Post by kansasnoob on 2009-03-10
Sorry, I know nothing about Nintendo.

---

### Post by sp176 on 2009-03-10
Sorry if there is a problem communicating here.  I want to change the format.  In old DOS versions it was done simply by "format e:"  finished!

You do not need to know nintendo, that is simply the application I was gonna use it for.

That picture you show me has your mouse pointer over the drives, all it does for me is change which drive I wish to look at.  I cannot see any other function to it.

---

### Post by jward3010 on 2009-03-10
Well using Gparted is easy, its usually located in the "System" menu > "Administration" and then its called "Partition Editor". If its not there like above install it by going to a terminal window and typing 
```
sudo apt-get install gparted
``` 
(be on the internet at the time).

NOTE: The instructions I give will WIPE the stick completely, make a backup of data on the stick now.

1. When GParted is running, up at the top right is a drop down menu with all the drives connected to your system, it'll probably say "/dev/sda (160GB)" or something. 

2. Go into that menu and select your USB key (you may only be able to know it by size, so for example it might appear as a 4GB or 8GB disk, not 320GB!). 

3. After you've selected the key its partition(s) will appear in the main section. Right click on the partition (which will be a large coloured bar) and select "unmount", then right click again and select "Delete" (this wont delete it yet, it will just add a job to the queue).

4. After above step, right click again and select "New". An options menu will appear where you can set filesystem type, size of partition etc. just make sure to make the partition "Primary partition". 

5. When you're happy with what you've set click "+ Add" adn you'll go back to the main GParted screen. Along the top you'll notice an "Apply" button. This will now carry out the tasks you've set - 1. Delete old FAT32 partition | 2. Create new FAT partition and make it primary.

6. Job done. Stick will be still unmounted from system so just disconnect it physically and plug it back in to test in Ubuntu.

---

### Post by kansasnoob on 2009-03-10
> **sp176 said:**
> Sorry if there is a problem communicating here.  I want to change the format.  In old DOS versions it was done simply by "format e:"  finished!

You do not need to know nintendo, that is simply the application I was gonna use it for.

That picture you show me has your mouse pointer over the drives, all it does for me is change which drive I wish to look at.  I cannot see any other function to it.

Jward already explained that better than I could. I was only pointing to where you can select the drive you want to work on. Right now I'm just using an old 30 GB drive for Jaunty testing and I have no other drives connected.

---

### Post by sp176 on 2009-03-10
Thanks.

My problem before had been when clicking unmount, the partition editor closes.  I had assumed this did nothing.

My question now is about the file type.  I am going for FAT16, and when trying to set the size, it seems to be a maximum of 4 GB, whereas before it was 8 GB.  Do I lose space due to changing the format?

---

### Post by jward3010 on 2009-03-10
By the way, I'm pretty surprised that your Wii can't read a FAT32 stick. Almost 100% of all USB sticks at least up to 16GB would be formatted as FAT32, not FAT due to its inefficiencies, lack of compatibility with larger filesizes etc. but anyway.

---

### Post by jward3010 on 2009-03-10
> **sp176 said:**
> Thanks.

My problem before had been when clicking unmount, the partition editor closes.  I had assumed this did nothing.

My question now is about the file type.  I am going for FAT16, and when trying to set the size, it seems to be a maximum of 4 GB, whereas before it was 8 GB.  Do I lose space due to changing the format?
Unfortunately, thats the problem with FAT (or FAT16), it only supports filesystem sizes of up to 4GB, its the way its file allocation table is designed. Which is why FAT32 was designed, I thinkit supports up to 32GB.

---

### Post by linuxisevolution on 2009-03-10
Here's my howto for gparted.

[http://98.219.177.90/apache2-default/thelinuxhowto/createfilesystem.html](http://98.219.177.90/apache2-default/thelinuxhowto/createfilesystem.html)

---

### Post by sp176 on 2009-03-10
Much appreciated everyone.  I dont like that I am losing diskspace, but I have it working.  Thanks for the help.

---

### Post by yther on 2009-03-10
According to [this article]("http://en.wikipedia.org/wiki/Wii#Hardware"), a Wii memory card holds a maximum of 2 GiB, so FAT16 (with standard 32 KiB clusters) would be OK.

Simplest way I know of to do this is (assuming your card shows up as /dev/sdc1, for example; watch /var/log/messages while inserting the card to find out) open a terminal window and type:

```
sudo mkdosfs -F 16 /dev/sdc1
```

I use a similar method to format flash drives.  You can add a name (up to 11 characters) with the -n option.  See "man mkdosfs" for details.

---

### Post by lalawawa on 2009-03-27
I want to format my usb disk so I can access it from Linux or a Mac.  A friend of mine who has a Mac told me to use fat32.  I used the instructions on this thread to format my disk with fat32, which gparted was happy to do, but now I can't figure out how to mount it on Linux.  I tried

sudo mount -t fat  /dev/sdg $dir_name -o force

and

sudo mount -t vfat /dev/sdg $dir_name -o force

and neither worked.

---

