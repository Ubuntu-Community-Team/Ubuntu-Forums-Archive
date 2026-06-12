---
title: "Boot from USB very slow- new to Ubuntu (Desktop Edition USB 10.10)"
date: 2011-01-21
forum: New to Ubuntu
---

### Post by claxie on 2011-01-21
I have no idea what information is needed to solve this problem.

I wasn't installing, only trying it out. I followed all the instructions from ubuntu.com for the desktop edition.

Here's some info from PC Wizard 2010:

Mainboard :	Gigabyte 7VM400AM-RZ
Chipset :	VIA KM400
Processor :	AMD Athlon XP @ 1916MHz
Physical Memory :	512MB (1 x 512 DDR-SDRAM )
Video Card :	VT82C570 MV IDE Controller KM400 Graphics Adapter
Hard Disk :	Maxtor 6Y200P0 (204GB)
Hard Disk :	Seagate ST380011A (80GB)
CD-Rom Drive :	Toshiba-Samsung CD-R/RW SH-R522C
Network Card :	Atheros Communications AR5005G 802.11a/b/g Wireless Network Adapter
Network Card :	VIA Technologies VT6102 Rhine II Fast Ethernet Adapter
Operating System :	Microsoft Windows XP Home Edition 5.01.2600 Service Pack 2 (32-bit)


What do you need to know?

---

### Post by Linyx on 2011-01-21
USB flash drive is not faster then Your HDD, so if your are Trying From Live-USB, it must be slow....

Once you installed it on your hdd, it will be operating normal,

---

### Post by robert shearer on 2011-01-21
May be that your usb ports are usb1.1 and not usb2 ?

If you can boot into ubuntu then open a terminal
Applications>accessories>terminal
and type ```
lsusb
```
then post the output back here.

Otherwise in windows check the hardware in Device manager and under usb see if it lists "Enhanced" anywhere. That is usb2. otherwise its usb1 and slooow.

---

### Post by RichieB07 on 2011-01-21
The USB is going to be a LOT slower than your hard drive as it's just using what it has for memory.  When it's fully installed on your computer it will be way faster.  The USB is more for a test drive to see if everything works on your computer, it's no real measure of how fast it'll be though.

---

### Post by mastablasta on 2011-01-21
live USB loads the OS to RAM. so more and newer ram means faster OS.
as mentioned porpper install will make it run much faster.
 
anothe reason for slow performace can be graphics card (bad or worng drivers). try turning off any desktop effects.
 
also service pack 2? feeling adventurous are we? :-)

---

### Post by nilraj23 on 2013-04-30
ubuntu@ubuntu:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 004: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 003 Device 003: ID 125f:b19a A-DATA Technology Co., Ltd. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 8086:0189 Intel Corp. 
Bus 001 Device 004: ID 0c45:6483 Microdia 
ubuntu@ubuntu:~$ 

i did what say and i got this. now what do you say ?

---

### Post by fuzzer37 on 2013-04-30
If you were using a USB 3.0 drive with, compatible ports, it may run faster. But it will run faster on a HDD

---

### Post by oldos2er on 2013-04-30
nilraj23, please start a new thread in accordance with the posting tips:

[COLOR=#000000]If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.[/COLOR]

---

