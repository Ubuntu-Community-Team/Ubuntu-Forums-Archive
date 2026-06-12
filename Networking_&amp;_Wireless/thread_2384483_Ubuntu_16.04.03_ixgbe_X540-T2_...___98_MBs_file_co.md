---
title: "Ubuntu 16.04.03 ixgbe X540-T2 ...   98 MB/s file copy speed"
date: 2018-02-07
forum: Networking &amp; Wireless
---

### Post by twoj on 2018-02-07
Hello
I have been trying to squeeze out more speed from my X540-T2 nic.


I'm copying a file from windows 2012R2 Share, on a very fast NVMe SSD (3000MB/s read/write speed), to Ubuntu 16.04.03 with upgraded ixgbe driver (from [https://sourceforge.net/projects/e1000/files/ixgbe%20stable/](https://sourceforge.net/projects/e1000/files/ixgbe%20stable/))
I test the connection with iperf, output is below.   I can fully saturate the NIC with 3 process:



> 
E:\iperf-2.0.9-win64>iperf -c 192.168.0.179 -P 2 -w 512K4
------------------------------------------------------------
Client connecting to 192.168.0.179, TCP port 5001
TCP window size:  512 KByte
------------------------------------------------------------
[  3] local 192.168.0.150 port 54942 connected with 192.168.0.179 port 5001
[  4] local 192.168.0.150 port 54943 connected with 192.168.0.179 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec  4.57 GBytes  3.92 Gbits/sec
[  4]  0.0-10.0 sec  4.69 GBytes  4.03 Gbits/sec
[SUM]  0.0-10.0 sec  9.26 GBytes  7.95 Gbits/sec


E:\iperf-2.0.9-win64>iperf -c 192.168.0.179 -P 3 -w 512K4
------------------------------------------------------------
Client connecting to 192.168.0.179, TCP port 5001
TCP window size:  512 KByte
------------------------------------------------------------
[  4] local 192.168.0.150 port 54981 connected with 192.168.0.179 port 5001
[  5] local 192.168.0.150 port 54982 connected with 192.168.0.179 port 5001
[  3] local 192.168.0.150 port 54980 connected with 192.168.0.179 port 5001
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-10.0 sec  3.70 GBytes  3.18 Gbits/sec
[  5]  0.0-10.0 sec  3.60 GBytes  3.10 Gbits/sec
[  3]  0.0-10.0 sec  3.66 GBytes  3.14 Gbits/sec
[SUM]  0.0-10.0 sec  11.0 GBytes  9.41 Gbits/sec


E:\iperf-2.0.9-win64>




So my assumption is that I do have a good TCP connection.

However when I copy a 16GB file from the Win2012R2 to Ubuntu, I only get between 98-112 MB/s transfer speed.
There are only NVMe drives involved, copy/paste of the 16GB file on 2012R2 goes at ~1GB/s;  and the same file on ubuntu is ~500MB/s

I changed the MTU on the ubuntu side to 9000.

Any ideas as to what may be going on?  It seems that only 10% of available speed is utilized.

---

### Post by TheFu on 2018-02-08
I have ZERO experience with 10Gbps networking.  But I'm good at troubleshooting.

Simplify and test.  Simplify and test.
Things to be considered.

What protocols are being used?
What encryption levels are being used? Is the encryption performed in HW or software?
What cabling is being used?  Is it too long?
Could the network ports on the switch be set different?
What are the CPUs doing?
Are the internal motherboard buses up to the task?

Do you have other 10Gbps systems that can be used to isolate the issue?

Also, don't forget that every vendor tests on Windows and works very hard to make the best performance happen with Windows-standard things. Linux testing is an after thought almost always.

---

### Post by twoj on 2018-02-08
Hey TheFu

>>[COLOR=#000000]What protocols are being used?
From Ubuntu side the W2012 drive is exposed as smb share.  I'll try to mount it in fstab directly as ntfs and see what happens.

>>[/COLOR][COLOR=#000000]What encryption levels are being used? Is the encryption performed in HW or software?
[/COLOR][COLOR=#000000]No encryption on either end.

[/COLOR][COLOR=#000000]>>What cabling is being used? Is it too long?
[/COLOR][COLOR=#000000]Cables are 3-4 feet long.  Cat6 cables

[/COLOR][COLOR=#000000]>>Could the network ports on the switch be set different?
[/COLOR][COLOR=#000000]I have XS716E and it reports all connection are 10GB.

[/COLOR][COLOR=#000000]>>Are the internal motherboard buses up to the task?
[/COLOR][COLOR=#000000]Good question.  I was wondering about that as well.  Nic is Pcie3.0 so this should be good, SSD is Pcie2.0 and its max is 1.3GB/s  so its less than the max for the slot, so it should be good.[/COLOR]

[COLOR=#000000]In line with your testing methodology, I just installed 'indicator-multiload' applet and tried  my 16GB file once again.
[/COLOR]The network speed was about 100MB/s  but the Disk speed was 0MB/s.  I was patient and I waited..  and all of a sudden the Disk reports ~500MB/s for a quick burst, then back to 0MB/s...  then few seconds later its up to 1.3GB/s (NVMe Drive's max speed) ...
So is there some caching going on when the SMB is used?  Since iperf was able to max out the connection consistently, some sort of caching would make sense?!?

Update:  Mounted the remote win2012 share via fstab,  now copy paste in ubuntu is running about ~178MB/s, however the drive speed still is pokey.  Drive 'spins' up and 'down'  with high burst write speeds.

[IMG]https://imgur.com/7AelRkv[/IMG]
So in this pic the swap space grows from 18GB to 50GB and after copy it goes back down to 18GB.

When I use  cp command the transfer rate moves up to ~260MB/s with the same behavior in mem cache and nvme write pattern.

Is there anyway to try to disable mem cache for cp?

Rsync over fstab mount performs ~110MB/s.  Cache and drive burst performance is the same

And finally dd approach:

dd if=/path/to/source of=/path/to/destination bs=4M iflag=direct oflag=directThis yielded the best results with ~500MB/s throughput and steady drive write ~500MB/s

So at least I achieved 5Gb/s network speed.  Do you feel this is the max for 10Gb/s connection?  Can other copy methods be optimized to come closer to dd numbers?

Perhaps Ubuntu caches the data during the regular copy/paste and cp on the system drive, which is SATA SSD Samsung PRO 860 which in turn causes slowdowns?

Thanks!

---

### Post by TheFu on 2018-02-08
Some of the testing isn't clearly described. It isn't clear which system(s) are being used for what aspects.  It isn't clear which is local-only testing.
Seems you have the networking good.  I'd move on. BTW, my first look at the post #1 showed 30-40% use. I've not seen the numbers like that. Guess 10Gbps makes the testing time segments different.  I see my mistake now. Sorry.

Always use fstab mounts, when possible.  Using a GUI will mount using gvfs which is known to be slow.  Mounts have many different options. Using the mount command directly from a shell will let you change the options quickly for different test cases.  Use the -o remount option to change if you don't want to umount.

Also, when trying to move data around as quickly as possible, don't use a GUI.  GUIs muck things up on Linux.  Stay in a shell.

Every protocol has overhead. Often those are tunable.  The dd test should be pretty raw, but I prefer using bonnie++.  Is 1.3Gbps really the limit?
Different NVMe devices have different limitations.  I've heard there are 32Gbps NVMe storage devices.   For example: [https://www.amazon.com/HighPoint-SSD7101A-1-dedicated-32Gbps-Controller/dp/B073W71K4Z](https://www.amazon.com/HighPoint-SSD7101A-1-dedicated-32Gbps-Controller/dp/B073W71K4Z)

So, the network seems fine.  Storage devices often claim higher performance than they can actually deliver.  There should be posts about real-world limits for each specific device.

What is left is tuning the disk and tuning the protocol.

Have you checked that the CPUs aren't pegged too?

---

### Post by Morbius1 on 2018-02-08
Your network is out of my league but ...
> Update:  Mounted the remote win2012 share via fstab,  now copy paste in  ubuntu is running about ~178MB/s, however the drive speed still is  pokey.  Drive 'spins' up and 'down'  with high burst write speeds.
Did you specify what version of the SMB dialect to use in your fstab mount? And what version of the Linux kernel are you using?

Prior to the 4.13 Linux kernel a cifs mount will use version 1 of SMB by default. SMB1 is considered "chatty" with lots of cross-talk between client and server just to confirm status. From 4.13 on it will use version 3 which is what I believe Win2012R2 can use and is considered more fluid.

So if you are using an earlier Linux kernel specify the version of smb by adding the option: [COLOR=#0000cd]**vers=3.0**[/COLOR] to your list in fstab and see if there is a difference.

---

### Post by twoj on 2018-02-08
As my NVMe Drive I'm using:  

Intel SSD DC P3520 			   
Sequential Read (up to) 1700 MB/s
Sequential Write (up to) 1300 MB/s


The Fu

[COLOR=#000000]>>Some of the testing isn't clearly described. It isn't clear which system(s) are being used for what aspects. It isn't clear which is local-only testing.
Sorry about that.  It kinda grew organically.

I can summarize my tests into 2 categories:
 1) Over-Lan (another NVMe ) to ubuntu [/COLOR]P3520 [COLOR=#000000]NVM[/COLOR][COLOR=#000000]
2) Inside same ubuntu box, drive to drive=>  [/COLOR]P3520 [COLOR=#000000]NVMe to 860 Pro SSD  and vice versa[/COLOR]

[COLOR=#000000]Over the lan the best performance I get is:  dd  :  ~475MB/s over the lan written to the NVMe
[/COLOR]Locally disk to disk the best one so far:  pv      :   here it reports 1.14GiB/s  15.2GiB written in 13 secs,  from 860 pro to the NVMe.   This number here is bogus!  860 Pro is the system drive and gets 450-500MB/s max.  So caching is helping me here somewhere...


>>[COLOR=#000000][FONT=Ubuntubeta]Every protocol has overhead. Often those are tunable. The dd test should be pretty raw, but I prefer using bonnie++. Is 1.3Gbps really the limit?
[/FONT][/COLOR]1.3GB is what I see in the GUI performance monitor as disk write, this is in line with NVMe advertised speed 1300MB/s  This number FLASHES for only a few secs..   I was able to catch 1.1GB/s in one of the pics above.


[COLOR=#000000][FONT=Ubuntubeta]>>Different NVMe devices have different limitations. I've heard there are 32Gbps NVMe storage devices. For example: [/FONT][/COLOR][https://www.amazon.com/HighPoint-SSD.../dp/B073W71K4Z]("https://www.amazon.com/HighPoint-SSD7101A-1-dedicated-32Gbps-Controller/dp/B073W71K4Z")
Yea, I'm aware if these....  They are crazy!  Not sure if they work only with the newest Intel chipsets, I'd love to get one of those to work with the AMD chips!

[COLOR=#000000][FONT=Ubuntubeta]>>What is left is tuning the disk and tuning the protocol.
[/FONT][/COLOR]Any recommendations where to start?

[COLOR=#000000][FONT=Ubuntubeta]>>Have you checked that the CPUs aren't pegged too?
No.  I have some big CPUs in this box.  CPUs barely move.


[/FONT][/COLOR][[COLOR=#000000]Morbius1[/COLOR]]("https://ubuntuforums.org/member.php?u=982144")
[COLOR=#000000][FONT=Ubuntubeta]I'm running 16.04.03:

[/FONT][/COLOR][COLOR=#000000]Linux ubuntu-gpu 4.4.0-112-generic #135-Ubuntu SMP Fri Jan 19 11:48:36 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

[/COLOR][COLOR=#000000][FONT=Ubuntubeta]
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntubeta]>>So if you are using an earlier Linux kernel specify the version of smb by adding the option: [/FONT][/COLOR][COLOR=#0000cd][FONT=Ubuntubeta]**vers=3.0**[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntubeta] to your list in fstab and see if there is a difference.[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntubeta]
I tried that, in the dd test nothing improved.
[/FONT][/COLOR]



When I look at these numbers as a whole there is not a best way to copy files, dd works OK over LAN and pv for disk to disk for now.  Unless there are some NVMe or SSD tweaks to be made or perhaps copy cache tuned, is there anything else  that can play a part in this?
As The Fu noted, the network most likely is not the problem.  The disk to disk, pv, copy gives me good speeds, so it has to be something tunable in the ubuntu stack....  Its is almost as if ubuntu insists on caching the copy but that is what slows the process down.


Thanks for you help 'The Fu' and Morbius1

---

### Post by TheFu on 2018-02-09
[https://superuser.com/questions/927545/intel-ssd-dc-p3600-1-2tb-performance](https://superuser.com/questions/927545/intel-ssd-dc-p3600-1-2tb-performance) says there might be a HW issue.
It would really help me if all numbers were in Mbps, not mixed with MBps. Network and disk performance is almost always shown in Mbps (bits), not bytes.  

I wouldn't trust anything that a GUI monitoring tool shows, until that is backed up from a text/cli tool first.

For copying large files or lots of files, I tend to use rsync.  The performance hit is worth the ability to pick up later from the middle.  rsync has some unexpected behavior for local and network copies, but it is a tool very worth learning.

For disk tuning, I haven't any idea for NVMe storage or PCIe v3 controllers.  For spinning disks, I've used hdparm a bunch.  Different devices have different optimal settings, IME.  Different workloads matter too.

Specs that say "up to" mean "nowhere near". ;)  Learned that from wifi, powerline ethernet, USB-anything, and ISP vendors.
Only if all the stars, planets, moons, and supernovas are aligned with 50 deities all pushing their "luck" onto the system will that happen.  So ... forgetaboutit.

Intel's installation guide references this: [https://github.com/linux-nvme/nvme-cli](https://github.com/linux-nvme/nvme-cli)  a PPA is referenced. Might have some helpful tools.

---

