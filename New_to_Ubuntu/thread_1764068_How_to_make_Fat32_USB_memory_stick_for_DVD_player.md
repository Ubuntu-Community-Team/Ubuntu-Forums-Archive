---
title: "How to make Fat32 USB memory stick for DVD player"
date: 2011-05-21
forum: New to Ubuntu
---

### Post by resander on 2011-05-21
.avi files containing xDiv or DivX video data are often used for downloading videos from Internet. They can be played on the PC or on many portable video players, but usually not on older dvd layers connected to the TV.

I plan to buy a modern DivX® compatible dvd player (£30-35) with USB port that supports file extensions .avi, .divx and .xvid. The idea is to copy the .avi file on to a USB memory stick and move it to the usb port of the video player and playback from the memory stick. This is a lot more convenient than using the DeVeDe program to convert the avi to PAL/NTSC format (takes more then 3 hours) and burn an iso DVD.

All dvd players I have been considering require a USB memory stick with a FAT32 file system. How do I make this from Ubuntu? I have a dual-boot Ubuntu 10.04 and Windows XP. 

Ken

---

### Post by Rex Bouwense on 2011-05-21
Can't you just mount the flash drive, right click the icon, and choose to format it.  Select FAT 32 and let it do its magic?  That is what I do.

---

### Post by Lateralis on 2011-05-21
There are several ways.  You can use gparted, a graphical partition editing tool, to select the partition and change the format to fat 32.  Or, I think you can do the following:

```

sudo mkfs.vfat /dev/sdXY

```

where X is the device and Y is the partition.  

Also, I know this is like stating the obvious, but whenever you format any drive using any method, ensure you have selected the correct drive!


Eidt: And what Rex Bouwense says!  That's the quickest way.

---

### Post by 3rdalbum on 2011-05-21
USB flash drives are still often Fat32 formatted already, when you buy them. The bigger ones might be NTFS-formatted so you can have 4 GiB+ files, but I think a lot of DVD players now can understand NTFS too.

If I ever have to change the format of a flash drive I use Gparted, which is in the Software Center. It can do a lot more than just formatting.

---

### Post by perspectoff on 2011-05-21
It's a lot of work to modify FAT32 drives for use with files greater than 4 Gb, and I've never been successful or satisfied with it. (In the past, FAT32 didn't natively support files greater than 4 Gb without some modifications, but perhaps this has changed recently, depending how the USB drive is formatted?).

For me, it has been much easier to reformat the USB drive to something other than FAT32. (NTFS, ext3/4, whatever). +1 for GParted, which may be what is referred to as the Disk Utility in Ubuntu. (In Kubuntu, the KDE Partition Manager is also available as a disk utility, as of Natty).

Then again, I use portable USB-connected hard drives to store the videos which I later want to play, anyway, not USB flash drives.

I find smaller formats such as .mp4 or .mkv actually give me better resolution and quality than MPEG-2 .mpg files or .avi files (which are larger), anyway. If my DVD player accepts those formats (as my newer DVD player does) instead of only .mpg, .avi, or .vbo (commercial DVD) formats (as my older DVD player does), then the question becomes moot.

These days new DVD players are only about $30 at Walmart or something like that.

---

### Post by JustinR on 2011-05-21
The Disk Utility included with Ubuntu by befault does a great job, and can tell you which drive is the USB drive.

---

### Post by resander on 2011-05-21
Many thanks All,

I don't use memory sticks very often and had forgotten they come preformatted with FAT or FAT32 depending on storage capacity. Thinking back, I have never reformatted memory sticks but still used them on Ubuntu and Windows, which means that Ubuntu must know how to read FAT32 file systems.

So I just need to get a 4gb or larger memory stick that would come preformatted with FAT32.

Ken

---

