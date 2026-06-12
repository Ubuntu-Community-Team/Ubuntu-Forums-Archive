---
title: "Booting from a flash drive with plug-ins"
date: 2011-02-05
forum: New to Ubuntu
---

### Post by MuleSkinner on 2011-02-05
In the first response in[this]("http://ubuntuforums.org/showthread.php?t=1678696") thread, **diablo75** mentioned that I could boot Ubuntu from a flash drive with the plug-ins I'd need to watch videos. Well, I sent for a flash drive and I just got it in the mail today and I'd love to try doing this. :) Can someone point me towards the directions I'd need? I found these two webpages:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)

but I'm not sure which set of directions I should follow if any. Thanks.

---

### Post by MuleSkinner on 2011-02-05
Okay, I followed the directions [here]("http://www.howtogeek.com/howto/22145/how-to-create-your-own-customized-ubuntu-live-cd/") and I went into the BIOS and there were four choices to change the boot order that started with USB (USB-FDD, USB- ZIP, USB-CDROM and USB-HDD). One at a time I changed the boot order to the four choices to 'First Boot Device' and restarted the PC and it never booted Ubuntu, it just booted to Windows XP as usual. Is there something else I'm supposed to do to make the PC boot to Ubuntu, or is it most likely that I did something wrong creating the bootable thumb drive?

---

### Post by MuleSkinner on 2011-02-05
Okay, I'm getting a little closer. In the BIOS I went to 'Hard Disk Boot Priority' and I was able to change to 'USB-HDDD KingstonDT 101 G2" and boot from the thumb drive. I chose 'Run Ubuntu from this USB' and got to a screen that said 'Ubuntu" with five flashing dots underneath. I waiter for over five minutes and nothing happened. Any ideas?

---

### Post by MuleSkinner on 2011-02-06
I've tried from scratch and using different Ubuntu versions and I'm still getting hung up on the loading screen. I tried following the directions [here]("http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/") and it worked fine, but those directions don't entail being able to have programs on the thumb drive that load with Ubuntu (so I can watch flash videos). I'm guessing the problem is with the use of the Universal USB Installer software. 

Does anyone know of any easy to follow instructions for booting Ubuntu on a thumb drive that will also load programs without using Universal USB Installer?

---

### Post by C.S.Cameron on 2011-02-06
Does your machine have at least 512MB of RAM?
I recall getting the 5 flashing dots trying to boot on a machine with 256MB.

I have heard of a lot of complaints about Universal installer. 
The Startup Disk Creator that comes with Ubuntu seems to work about the best for making a persistent install.
You can use it booting from the Live CD or you can extract usb-creator.exe from the Ubuntu iso file for use in Windows.

You can also add a persistent partition to a non persistent install, UNetbootin for example:

This is how I made a Unetbootin install to flash drive persistent.
Booted Live CD, (Live USB should also work)
Plugged in target flash drive.
Started Partition Editor
Created 1GB FAT32 partition, (on the left side of the bar).
Created a 2GB ext3 partition to the right of this, labeled it "casper-rw".
Created a ext2 partition in the remaining space and labeled it "home-rw".
Closed Partition Editor.
Un-mounted and re-mounted flash drive.
Started Windows, started Unetbootin, selected Diskimage, located the iso, selected Type = USB Drive, selected correct drive letter
Pressed OK, waited 5 minutes.
When Unetbootin finished, shutdown, booted thumbdrive.
At boot menu hit Tab, then typed "(space)persistent"
Ran "gksu nauilus", opened filesystem / cdrom and then opened syslinux.cfg with text editor.
Added "persistent" as shown below:
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent
Rebooted, changes were persistent.

---

### Post by MuleSkinner on 2011-02-06
I have 4GB RAM.

**C.S.Cameron**, before I try your method, I have more information that may be useful in determining what's going on. I tried doing this again with another program, this one called LinuxLive USB Creator and the same thing happened. I pressed the escape key and I see the messages "failed due to unknown user id" and "Buffer I/0 Error on device fd0, logical block 0". Any ideas?

---

### Post by MuleSkinner on 2011-02-06
> **C.S.Cameron said:**
> 
Started Partition Editor
Created 1GB FAT32 partition, (on the left side of the bar).
Created a 2GB ext3 partition to the right of this, labeled it "casper-rw".
Created a ext2 partition in the remaining space and labeled it "home-rw".
Closed Partition Editor
Okay, I'm up to this part and I'm not sure what to do. I went to System > Administration > GParted Partition Editor. A box pops up. Now what?

---

### Post by C.S.Cameron on 2011-02-06
In the top right corner is a drop down box, find your flash drive, it is probably sdb, select this. (confirm this drive is the same size as your flash drive).
There should be only one partition, FAT32, showing green, right click on this and select Unmount, then right click again and Resize/Move, drag the right side to the left until it is 1GB. click the tab that says Resize/Move.
Now click the green check mark at the top of the page.
Right click the gray space and select new. choose 0 preceding and 2GB for size, Primary partition, File system ext2, and Label Casper-rw, click ADD then click the green check mark at the top of the page.
Do similar for the home-rw partition, (if you wish a separate home partition), this is optional, if not you can make the casper-rw partition larger.

---

### Post by MuleSkinner on 2011-02-06
Okay, I'm almost there. I finally didn't get hung up this time and Ubuntu started (I'm there now).
I still have to do the following:
> **C.S.Cameron said:**
> 
Ran "gksu nauilus", opened filesystem / cdrom and then opened syslinux.cfg with text editor.
Added "persistent" as shown below:
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent
Rebooted, changes were persistent.
Can you tell me how to run "gksu nautilus"?

Also, if the rest isn't noob friendly, step by step instructions would be appreciated. :)

---

### Post by MuleSkinner on 2011-02-06
I did some Googling and found this is how you get gksu nautilus:

sudo apt-get install nautilus-gksu

Don't know how to "opened filesystem / cdrom and then opened syslinux.cfg with text editor."

---

### Post by C.S.Cameron on 2011-02-06
Press Alt F2 and type "gksu nautilus"
Or you can open terminal and type  "gksu nautilus"
(this opens nautilus as super user).
Now click file system, then double click cdrom, then you right click on syslinux.cfg and open with text editor.

Another option is to become persistent each time you boot, press shift when booting a alternate boot window will open, press F6 and type " persistent", (note the space before persistent). The first method is probably easiest.

---

### Post by MuleSkinner on 2011-02-28
C.S.Cameron, I'm hoping you can still help me. I'm trying to follow your directions in posts #5 and #11. In post #5 you wrote:
> Added "persistent" as shown below:
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent
Rebooted, changes were persistent.It's a read only file and I can't make changes to it. :confused:

---

