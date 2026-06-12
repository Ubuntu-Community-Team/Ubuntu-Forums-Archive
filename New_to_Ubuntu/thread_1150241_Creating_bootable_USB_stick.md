---
title: "Creating bootable USB stick"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by jwaclawsky on 2009-05-05
I am trying to get the Ubuntu image 9,04 for my netbook installed on my 4GB USB drive. I am following the instructions on the Web page, which state:

1- Download the desired .img file - Did that and checked with MD%SUMS and everything is ok File name is: ubuntu-9.04-netbook-remix-i386.img which is on my Desktop

2 - Open a terminal and insert your flash media - that's easy enough. Done

3 - Look at the output of dmesg | tail -20 to determine the device node assigned to your flash media (e.g. /dev/sdb) - now here is where I am running into problems. I don't know what I am looking at????   The output from the command is: 

[ 2171.972056] usb-storage: device found at 11
[ 2171.972074] usb-storage: waiting for device to settle before scanning
[ 2176.967123] usb-storage: device scan complete
[ 2176.968018] scsi 4:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  3.27 PQ: 0 ANSI: 2
[ 2176.969045] scsi 4:0:0:1: CD-ROM            SanDisk  U3 Cruzer Micro  3.27 PQ: 0 ANSI: 2
[ 2176.971940] sd 4:0:0:0: [sdf] 8015502 512-byte hardware sectors (4104 MB)
[ 2176.973569] sd 4:0:0:0: [sdf] Write Protect is off
[ 2176.973592] sd 4:0:0:0: [sdf] Mode Sense: 03 00 00 00
[ 2176.973604] sd 4:0:0:0: [sdf] Assuming drive cache: write through
[ 2176.977676] sd 4:0:0:0: [sdf] 8015502 512-byte hardware sectors (4104 MB)
[ 2176.978445] sd 4:0:0:0: [sdf] Write Protect is off
[ 2176.978460] sd 4:0:0:0: [sdf] Mode Sense: 03 00 00 00
[ 2176.978471] sd 4:0:0:0: [sdf] Assuming drive cache: write through
[ 2176.978489]  sdf: sdf1
[ 2176.981725] sd 4:0:0:0: [sdf] Attached SCSI removable disk
[ 2176.981825] sd 4:0:0:0: Attached scsi generic sg6 type 0
[ 2176.986765] sr1: scsi3-mmc drive: 8x/40x writer xa/form2 cdda tray
[ 2176.986903] sr 4:0:0:1: Attached scsi CD-ROM sr1
[ 2176.986997] sr 4:0:0:1: Attached scsi generic sg7 type 5
[ 2183.600494] usb 5-1: reset high speed USB device using ehci_hcd and address 11

Step 4 is that I am supposed to use the information above to run the following 2 commands 

sudo umount /dev/device/node

and

sudo dd if=/path/to/downloaded.img of=/dev/device/node bs=1M

(and then Remove your flash media when the command completes)

My question is what do I plug in the commands for /dev/device/node? Could someone tell me exactly what the two commands I am supposed to be entering are? ...any further explanation would be helpful too or a pointer. Many thanks

---

### Post by Didius Falco on 2009-05-05
Look in **System/Administration/USB Startup Disk Creator**. Unless you are running something older than (I think) 8.10, it should be there. If it's not, right click on your menu to edit it, maybe it's just set to not display...

Regards,

Didius

---

### Post by jwaclawsky on 2009-05-05
I am running Ubuntu 8.04. I do not have USB Startup Disk Creator under System/Administration/? What do you mean by"If it's not, right click on your menu to edit it, maybe it's just set to not display.."?

---

### Post by jwaclawsky on 2009-05-05
Ok, I figure out what is meant by:"If it's not, right click on your menu to edit it, maybe it's just set to not display.."?  It is not there. I apparently do not have this. I still have my original question.

---

### Post by pastalavista on 2009-05-05
Are you wanting to install a full system to the flash drive or just a Live CD. For a Live CD you can download [Unetbootin]("http://unetbootin.sourceforge.net/").

I believe your device would be /dev/sdf, so you should enter
```
sudo umount /dev/sdf
``` and then
```
sudo dd if=/home/username/Desktop/ubuntu-9.04-netbook-remix-i386.img of=/dev/sdf/sdf1 bs=1M
```

but, I am a newb... that's just what I would try if there wasn't an easier way

---

### Post by jwaclawsky on 2009-05-05
I wanted to install a full system on the USB drive so I could try out 9.04  with my hardware and also get the new open office and make sure things are ok before I commit to it

---

### Post by Didius Falco on 2009-05-05
sdf1 is that USB Flash drive. 

I'd still recommend getting the automatic tool. I've used it several times and it works very well.

If you decide to install it at some point, here is the command:

```
sudo apt-get install usb-creator
```

Regards,

Didius

---

### Post by jwaclawsky on 2009-05-05
I get an error message E: Couldn't find package usb-creator. Do you have a pointer to this package?

---

### Post by pastalavista on 2009-05-05
You could burn an 8.10 or 9.04 iso to disk and boot from it and then install it to the USB drive from the disk. Those releases have USB creator included. Then you could do a persistant install.

---

### Post by jwaclawsky on 2009-05-06
The web page says I can use a windows machine to create my USB image but I am trying to do this without windows. So you are saying that I can't simply follow the command line interface instructions at [https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles) and build a bootable USB drive. All I need is the correct information for the two commands I mentioned in my first post?  Am I misunderstanding something here?

---

### Post by Didius Falco on 2009-05-06
> **jwaclawsky said:**
> I get an error message E: Couldn't find package usb-creator. Do you have a pointer to this package?

This is from a Community Help Document on that - it will give you info on doing it yourself too:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

> **Recomended Default method** 
Ubuntu USB desktop image creator (usb-creator) 
From the 8.10 release on, Ubuntu includes the usb-creator by default on all liveCDs and installations. 
This is a simple utility designed to make bootable USB desktop images from Ubuntu CDs. Booting from this USB drive will behave just as if you had booted from the install CD. It will show the language selection and then the install menu, from which you can install Ubuntu onto the computer's hard drive or launch the LiveCD environment. 
You can find it in intrepid in System-->Administration-->Create a USB startup disk, if it is not there then as normal run the following command in the terminal : 
sudo apt-get install usb-creatorMake sure the software-sources are activated if you are on a live cd (software sources or sudo gedit /etc/apt/sources.list).  You may need to install the python-gnome2 package as well. 
It should do everything needed you just need to have a live cd in you CD-Rom or show the usb-creator the ISO image of it and the rest of the process is automatic! (for more info how to use this tool directly by just popping in a liveCD to a Drive in a running Ubuntu desktop see also "Live USB creator" below, note that it also works directly with downloaded .iso images) 

---

### Post by jwaclawsky on 2009-05-06
This seems awfully complicated. Let me reboot. I have a netbook with Ubuntu 8.04. And 

1 - I do not have windows on my machine  -  I am not using it. No windows!

2 - I just want to "try out" Ubuntu 9.04. And from my reading/questions I "believe" that I can install it on a USB drive and run it from there so if it doesn't work with my hardware or I have some issues I can simply remove the UBS drive and reboot in Ubuntu 8.04 and all my 8.04 files and settings are safe. Is this possible?????? I currently believe it is but might be wrong. So...  

3 - I am now using the information at [https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles) to build a bootable USB drive using the command line interface. 

If item #2 is possible I just need some help answering the question on my first post. Thanks.

---

### Post by pastalavista on 2009-05-06
I found [this tutorial]("http://www.pendrivelinux.com/ubuntu-810-install-using-the-built-in-usb-installer/") for 8.10... should work the same for 9.04

sorry, I'm not geek enough to answer your first question.

---

### Post by jwaclawsky on 2009-05-06
Are you telling me I can't create a bootable 9.04 image on a USB drive using an 8.04 system? Is that correct?

---

### Post by pastalavista on 2009-05-06
Yeah, you can. Download [USB creator here]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=usb+creator")

---

### Post by jim87410 on 2009-05-06
Maybe I missed something.  [https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)  was referenced to create a bootable USB stick to install Remix.

Hope it helps.

---

### Post by anjilslaire on 2009-05-06
Ok, here's the deal:
The usb-creator/Create a USB Startup disk option usede to create a bootable install disk from an ubuntu iso WILL NOT WORK with the Netbook 9.04  img file.

What you need to do to do this is get the Ubuntu Image Writer, and point it at your .img file as the source and your usb as the destination. Read & follow this:
[https://wiki.ubuntu.com/UNR#Easy%20(graphical)%20Way](https://wiki.ubuntu.com/UNR#Easy%20(graphical)%20Way)

I have already done this on my mini 9.

---

### Post by pastalavista on 2009-05-06
there are ways to convert an img file to an iso. I did some research and found that you can do it with [this guide]("http://www.mopedia.co.uk/2008/02/convert-img-to-iso-in-ubuntu.html")

---

### Post by jim87410 on 2009-05-06
Good point, however post #1 says he is trying to load the Remix img, not an iso.  I loaded this on my Aspire One last week.  I happened to use the Win 32 Disk Imager but the help shows a Imagewriter that can be downloaded from [http://shounen.ru/soft/flashnul](http://shounen.ru/soft/flashnul).

Read about it [http://bloggajim.com/blog1.php/2009/04/27/acer-aspire-one-performance-enhancement](http://bloggajim.com/blog1.php/2009/04/27/acer-aspire-one-performance-enhancement)

---

