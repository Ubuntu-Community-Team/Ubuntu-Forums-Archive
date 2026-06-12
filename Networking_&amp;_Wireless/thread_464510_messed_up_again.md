---
title: "messed up again"
date: 2007-06-04
forum: Networking &amp; Wireless
---

### Post by petercarter on 2007-06-04
my computer reboots by itself at times. I know you dont care but it caused the following problem:
My Wifi connection dissapeared, now I have to go in the terminal and write the following
sudo depmod
sudo modprobe ndis wrapper
this is the only way I found to get it back up:;When I do a ndiswrapper -m it says
module already contains alias directive. What are the steps to take to remove this directive and reinstall it.
thanks a lot in advance
Peter

---

### Post by chili555 on 2007-06-05
Please open up a terminal and let us see the output of these two commands:```
cat /etc/modules
iwconfig
```> I know you dont careOf course we care; why else would we be answering literally thousands of posts instead of watching our investments, instant messaging and downloading pr0n?

Any idea why your computer reboots randomly? Overheating, faulty or too small power supply or RAM going bad? Or what?

---

### Post by petercarter on 2007-06-05
here it is sorry for being a smart ***
peter@peter-desktop:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
peter@peter-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate=2 Mb/s   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by petercarter on 2007-06-05
well it is not the ram not the power supply not overheating my son had issues with this motherboard now I am stuck with them. I am trying to locate the problem but the process is long and ardeous. It may be a loose connection somewhere. If I cannot get it t work properly will buy another one.
thanks for your concern

---

### Post by chili555 on 2007-06-05
Well, the alias directive does not appear to be where I believe it should be. Let's try *sudo gedit /etc/modules* (substitute *kate* or *nano* or *vim* or your favorite text editor here) to add:```
alias wlan0 ndiswrapper
```The next time it reboots, let us know if that did the job.

If this does not work, instead add a line *modprobe ndiswrapper* in /etc/rc.local.

---

### Post by petercarter on 2007-06-05
Well it did not work. Just to save everyone problems, is there away to reinstall Ubuntu over the existing one. The last time I tried it created a secondary partition and I had Two Ubuntus. I understand that you are all quite busy and I believe it simpler and faster to reinstall if possible. Because knowing certain people they go all out when something does not work and try to solve it to the point to get ill. This is not a complaint but a compliment regarding your work. As I continue fudging through I will get quite competent in Linux. Just need paractice and a refressher course.
Thank you for everything
Peter

---

### Post by kevdog on 2007-06-05
chili555

shouldn't alias wlan0 ndiswrapper be included in the /etc/modprobe.d/ndiswrapper file??

---

### Post by petercarter on 2007-06-05
All right it is there. I can always access my wireless with
sudo depmod
sudo modprobe ndiswrapper
I will just have to live with this for a while, I do not think it is the end of the world for now. If you think of something while helping others please let me know otherwise do not loose too much time over it. You have enough on your plates with all the requests for help. Thank you very much for trying to solve my silly problem. 
Peter

---

