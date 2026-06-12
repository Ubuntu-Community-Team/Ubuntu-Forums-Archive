---
title: "I changed a partition and now can't see it"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by Enkidux on 2009-06-24
Please help me someone, because I really feel dumb. I have just got this alarm clock that has about 15 MB memory, so I plug it in, I delete the songs that came with it and tried to put another song. It gave me the message that it was not possible, (how come?the song is only 5 Mb) it seems that it didn't delete the original songs. 

then I did something even more stupid, went to gparted, and tried to format the memory, I changed it into ext2 and then it became grey and I coudn't access it at all. I restarted the pc and I cannot access it or even see it.

I feel very stupid, I love using ubuntu, but I am really sick that a simple thing like this becomes such an impossible task for me. 

i would really thank anyone that can give me a clue or redirect me to the correct post-tutorial or whatever, I am sure it's quite simple to do but it's just giving me hell.

thanks

---

### Post by WRDN on 2009-06-24
First, ensure Ubuntu can see the device, by opening the Terminal, and typing:

```
sudo fdisk -l
```

If you can see it, create a mount point:

```
sudo mkdir /media/player
```

Feel free to replace the name "player".

You can then mount it manually:

```
sudo mount /dev/sdb0 /media/player
```

Or Force mount:

```
sudo mount /dev/sdb0 /media/player -o force
```

The device may not be called sdb0 (see fdisk -l output), so just replace the text with the appropriate device name.

The name stands contains both the disk number and the partition number. For example, with "sdb0", b means its the second disk (a would be the first, c would be the third etc), and 0 means its the first partition (1 refers to the second, 2 to the third partition etc).

---

### Post by ajgreeny on 2009-06-24
No, sdb0 will not exist;  you are mixing up the device naming system (/dev/sda1) with grub naming system (hd0,0).  Only grub starts from zero, and it uses hd0,0 etc, that is the first partition on the first disk, which in the device naming is sda1.

Otherwise the suggestion is a good one, let's see what the disk is called and then it can be put right.

It should, however, be very easy to find it using gparted, simply by looking for that sized disk, and then formatting the whole disk to whatever filesystem you think would fit best, though if it was fat32, I suggest you keep it that way or it may break the way the thing works.  If it is then plugged in using a usb port, I would expect it to mount automatically

---

### Post by Enkidux on 2009-06-25
thank you very much for the replies, I couldn't check it before because my laptop's battery just finished. 

how do I know the name of the device? I just bought it.. is it importat or shall I just give it another name??? how??

Also, I disconnected the device and plugged it again and the pc couldn't detect it.... how can i format it again like this...

thanks for your answers please keep helping me

E.

---

### Post by Divider on 2009-06-25
I cant belive i kno this.


On windows right click my computer go to manage


click on disk management

Find the disk with the wierd partition.

reformat.

YAY!! :P

---

### Post by Enkidux on 2009-06-25
Is there a tutorial where i can read about all this stuff???

I have been having problems with deleting files in devices, reading devices, mounting them and so on, al related to mounting I guess.

Any help or advice is very welcome, thanks again.

E.

---

### Post by ajgreeny on 2009-06-25
> **Enkidux said:**
> thank you very much for the replies, I couldn't check it before because my laptop's battery just finished. 

how do I know the name of the device? I just bought it.. is it importat or shall I just give it another name??? how??

Also, I disconnected the device and plugged it again and the pc couldn't detect it.... how can i format it again like this...

thanks for your answers please keep helping me

E.
Try again plugging it in to your ubuntu system, then open gparted, and in the drop down box top right look for the device, which you surely will know from its reported size.  If there are partitions showing on it, delete them, and then make a new partition and format it to whatever the alarm clock had on it before you started playing around.

If gparted can't see it I suspect there is something very wrong with the item as gparted is extremely versatile and can see just about any filesystem you may have formatted to, or even no filesystem at all.

If by "name of the device" you mean the /dev/sdx# that gparted will normally see, there is no need to do anything; the computer will name it for you.  If there is no proper formatted filesystem on the disk, then Ubuntu will not "see" the disk, but gparted should.

---

