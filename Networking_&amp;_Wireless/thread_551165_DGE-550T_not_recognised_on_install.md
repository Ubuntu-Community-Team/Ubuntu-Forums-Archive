---
title: "DGE-550T not recognised on install"
date: 2007-09-14
forum: Networking &amp; Wireless
---

### Post by jasthom69 on 2007-09-14
Total newbie  - help needed with my first ever linux install using Ubuntu 6.06.01 LTS - LAMP

On the install the "Configuring the network with DHCP" failed together with "Configure the network, unfortunately I can't remember the exact message that was displayed, but I continued the install expecting I would be able to rectify this later.

After the install I did ifconfig to see only the Loopback configured and no ethernet interfaces.
I can see the NIC card under the PCI list as D-Link DL2000-based Gigabit Ethernet.
I have copied over the driver from the D-Link install cd (which states that it supports Linux kernel 2.4 and above), extracted it.

My problem is when I come to "make install" (what I believe to be the next step) I get the following "bash: make: command not found" please below output. 
This is where I come unstuck and haven't a clue what to do or if there are other ways to get the NIC recognised. 

Please can someone help? 

Cheers in advance

Jas


 

root@xxx:/home/jas# uname -a
Linux xxx 2.6.15-26-server # 1 SMP Thu Aug 3 04:09:15 UTC 2006 i686 GNU/Linux


sudo apt-get install linux-headers-2.6.15-26-server
sudo apt-get install gcc

root@xxx:/usr/src# ls
linux-headers-2.6.15-26  linux-headers-2.6.15-26-server
root@jaslin:~#gcc --version
gcc (GCC) 4.0.3 (Ubuntu 4.0.3-1ubuntu5)

root@xxx:~# lspci
0000:00:00.0 Host bridge: Intel Corperation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
0000:00:01.0 PCI bridge: Intel Corperation 82815 815 Chipset AGP Bridge (rev 02)
0000:00:1e.0 PCI bridge: Intel Corperation 82801 PCI Bridge (rev 02)
0000:00:1f.0 ISA bridge: Intel Corperation 82801BA ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corperation 82801BA IDE Bridge U100 (rev 02)
0000:00:1f.2 USB Controller: Intel Corperation 82801BA/BAM USB (Hub #1) (rev 02)
0000:00:1f.3 SMBus: Intel Corperation 82801BA/BAM SMBus (rev 02)
0000:00:1f.4 USB Controller: Intel Corperation 82801BA/BAM USB (Hub #2) (rev 02)
0000:01:00.0 VGA compatible Controller: ATI Technologies Inc Rage 128PF/PRO AGP 4x TMDS
0000:02:0a.0 Ethernet Controller: D-Link System Inc DL2000-based Gigabit Ethernet (rev 0c)

root@xxx:/usr/src/dl2k-1.19# ls
dl2k-1.19.tgz

root@xxx:/usr/src/dl2k-1.19# tar xfvz dl2k-1.19.tgz
dl2k-1.19/
dl2k-1.19/Makefile
tar: dl2k-1.19/Makefile: time stamp 2004-03-01 03:47:56 is 131392822 s in the future
dl2k-1.19/dl2k.txt
tar: dl2k-1.19/dl2k.txt: time stamp 2003-12-22 07:31:45 is 125358251 s in the future
dl2k-1.19/crc32.h
tar: dl2k-1.19/crc32.h: time stamp 2003-12-22 07:31:45 is 125358251 s in the future
dl2k-1.19/dl2k.c
tar: dl2k-1.19/dl2k.c: time stamp 2003-12-22 07:31:45 is 125358251 s in the future
dl2k-1.19/dl2k.h
tar: dl2k-1.19/dl2k.h: time stamp 2003-12-22 07:31:45 is 125358251 s in the future
tar: dl2k-1.19: time stamp 2003-12-22 07:31:45 is 125358251 s in the future

root@xxx:/usr/src/dl2k-1.19/dl2k-1.19# ls
crc32.h  dl2k.c  dl2k.h  dl2k.txt  Makefile

root@xxx:/usr/src/dl2k-1.19/dl2k-1.19#make install
bash: make: command not found

---

### Post by jasthom69 on 2007-09-15
Found a thread in another forum with the same problem with a DGE-530T where he upgraded from 2.6.15-26  to 2.6.17.13  which did the job.

I've just done the "sudo apt-get install make" instead of "make install" which seems to have taken and showed "1 newly installed" then did a "sudo modprobe dl2k" but still can't see the ethernet interface when I do a "ifconfig"

I'm not sure where to get the 2.6.17.13 kernel or how to upgrade it.
Does anyone know any other way of verifying the new NIC card driver has taken and if "sudo apt-get install make" is the same as "make install"?

Maybe I'm missing something here?

---

