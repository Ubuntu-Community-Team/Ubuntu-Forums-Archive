---
title: "Can i try ubuntu for my machine?"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by ale_ramesh on 2008-12-25
Hi All,

I really fed up with Windows and want to try Ubuntu.

My doubt is can i try ubuntu for my machine? Here is my system spec:


[B]Windows:            	Windows XP5.1 (Build 2600) Service Pack 2
Internet Explorer:  	6.0.2900.2180
Memory (RAM):       	2048 MB
CPU Info:           	AMD Athlon(tm) 64 X2 Dual Core Processor 3600+
CPU Speed:          	2008.1 MHz
Sound card:         	Realtek HD Audio output
Display Adapters:   	NVIDIA GeForce 6100 | NetMeeting driver | RDPDD Chained DD
Screen Resolution:  	1024 X 768 - 32 bit
Network:            	Network Present
Network Adapters:   	NVIDIA nForce Networking Controller - Packet Scheduler Miniport | WAN (PPP/SLIP) Interface
CD / DVD Drives:    	G: LITE-ON DVDRW LH-16A1P
COM Ports:          	COM1 | COM2
LPT Ports:          	LPT1
Mouse:              	3 Button Wheel Mouse Present
Hard Disks:         	C:  19.5GB | D:  39.1GB | E:  39.1GB | F:  51.4GB
Hard Disks - Free:  	C:  13.8GB | D:  2.5GB | E:  402.4MB | F:  1.1GB
USB Controllers:    	2 host controllers.
Firewire (1394):    	1 host controllers.
PCMCIA (Laptops):   	Not Installed
Manufacturer:       	Award Software International, Inc.
Product Make:       	 
AC Power Status:    	OnLine
BIOS Info:          	AT/AT COMPATIBLE | 05/22/07 | GBT    - 42302e31
Time Zone:          	India Standard Time
Battery:            	No Battery
Motherboard:        	Gigabyte Technology Co., Ltd. GA-M51GM-S2G
Modem:              	Not detected
:                   	
:[/B]                   	

1)The problem is Except c other drives are NTFS file format.And i have nearly 120 GB of data in those drives.I cannot loose those data in any case.Please suggest me if there is any solution.
 
2) I want to  download ubuntu using torrents so i am downloading this:ubuntu-8.10-desktop-amd64.iso.torrent Is it the right one?

3) I dont think i will not face any problems in running java on ubuntu basically i am java developer.

Thanks in Advance
Ramesh Ale

---

### Post by Vakman on 2008-12-25
That computer would have no trouble running Ubuntu. The specs are just fine. In terms of not losing your data. You should always do backups before installing anything major anyway. You would want to install it to another partition. Now if you have a portable hard drive back up your data to that and then just use the whole disk. That is only if you have backed it up and are sure you will no longer need Windows. You can also just try it out without affecting anything by using the LiveCD. It will not be very fast but will also not affect anything. If you do wish to install it post back here and people, including myself, will most likely help.

Also check out "Is Ubuntu for You?" ([http://ubuntuforums.org/showthread.php?t=63315](http://ubuntuforums.org/showthread.php?t=63315))
As well as [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) (A tutorial of how to go about dual booting with Windows)
Remember to back up!

---

### Post by ale_ramesh on 2008-12-25
Thisislaw,

Thanks for your reply.I just want to ask you if i am downloading the correct one for my machine.ubuntu-8.10-desktop-amd64.iso.torrent



Regards
Ramesh Ale

---

### Post by zakirs on 2008-12-25
ramesh , 
yes thats the correct one .. also u will be able to write and read on the NTFS paritions from ubuntu ... just be careful when the partition selection thing comes up ..

---

### Post by Vakman on 2008-12-25
Hm, I swear I answered that :lolflag:
Looks like I didn't. 
Either way, yes that would be the correct one.

---

### Post by zakirs on 2008-12-25
> just be careful when the partition selection thing comes up ..


by this i meant selection the partition thing during installation ..

---

### Post by ale_ramesh on 2008-12-25
Thisislaw & zakirs 

Thanks for your replies.

I have a doubt here:
I am just going through this article([http://www.psychocats.net/ubuntu/installing).Doubt](http://www.psychocats.net/ubuntu/installing).Doubt) is here in these screenshots [Screenshot1]("http://www.psychocats.net/ubuntu/images/installinghardyplus10.png") [Screenshot2]("http://www.psychocats.net/ubuntu/images/installinghardyplus11.png") It shows some space(2.1GB and something).Is it the space of C drive divided or what?

What would be the possible values i would get in these steps while installing?And what to select to be on safeside?

I think i am over cautious by asking this silly question?:P

Regards
Ramesh Ale

---

### Post by ale_ramesh on 2008-12-25
Many questions are popping up in mymind after reading this [tutorial on partitions]("http://www.psychocats.net/ubuntu/partitioning").

I have only one hard disk which is partitioned into four logical drives as below:
13.0 GB free space on C Drive which uses FAT32 file system.
8.80 GB free space on D Drive which uses NTFS file system.
4.74 GB free space on E Drive which uses NTFS file system.
1.05 GB free space on F Drive which uses NTFS file system.

[B]How do i partition so that i can use all the data present in all the drives from both the operating systems(ubuntu and windows).(I am planning to go for dual boot).
[/B]

Thanks in Advance
Ramesh Ale

---

### Post by Moop on 2008-12-25
Ubuntu will be able to see and use all your partitions no matter where you install it. It looks like your only choice is to resize your c: partition and install Ubuntu in the free space.

---

### Post by ale_ramesh on 2008-12-25
> resize your c: partition and install Ubuntu in the free space. 

Thanks Moop for your advice..I want to ask one more thing..should i divide resize C drive into two partitions in Windows or i will get this option while installing ubuntu.

Regards
Ramesh Ale

---

### Post by albinootje on 2008-12-25
> **ale_ramesh said:**
> 
Memory (RAM):       	2048 MB
CPU Info:           	AMD Athlon(tm) 64 X2 Dual Core Processor 3600+
You can indeed run Ubuntu 64-bit on this.
That can however make things a bit more difficult installing Java and Flash-player compared to the 32 bit Ubuntu installation.
Not sure whether that would make things also a bit more difficult for proprietary drivers, anyone ?

If you want less hassle installing, go for the 32-bit Ubuntu installation.

---

