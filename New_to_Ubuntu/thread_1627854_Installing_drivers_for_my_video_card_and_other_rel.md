---
title: "Installing drivers for my video card and other related things."
date: 2010-11-21
forum: New to Ubuntu
---

### Post by mandar9589 on 2010-11-21
I have installed ubuntu10.10 and is happy with the performance.
The size of application windows(e.g. Mozilla FireFox) is very big.
So I went to Systems>>Preferences>>Monitor and changed the resolution from 800x600(default) to 1024x768. On clicking Apply, the next screen I got was very small(it gave me a black patch of about 4cm from bottom and 4cms from right of my monitor).So I installed updated the driver using this code ```
sudo add-apt-repository ppa:glasen/intel-driver 
``` and ```
sudo apt-get update && sudo apt-get upgrade
```.

Then I tried to load the drivers from Systems>>Adminstration>>Additional Drivers. for which the reply was there are no proprietary drivers...

What should I do next I am completely new user of linux,I searched on net and went through forum, but still stuck.

These are my specifications:
> 00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Inte
rface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics 
Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory
 Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Contr
oller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Contr
oller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Contr
oller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Contr
oller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Cont
roller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Brid
ge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller 
(rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 0
2)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) A
C'97 Audio Controller (rev 02)
01:08.0 Ethernet controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) integrate
d LAN Controller (rev 02)


---

### Post by deanjm1963 on 2010-11-21
Firstly, there are no "restricted drivers" for intel graphics. All intel graphics on linux are open-source. Those drivers are automatically installed when you install ubuntu. The drivers you installed from that PPA you added might actually do more harm than good. You were better off sticking with the default drivers for your intel chipset.

Also, if you're not using DVI or HDMI to connect to your monitor, you may have to manually adjust size and position of your screen via your monitor control panel (the buttons on your monitor).

Hope this helps.

---

### Post by mandar9589 on 2010-11-22
First of all thank you for replying.
When previously I had windows, I had 1024x768 desktop, then I loaded ubuntu 10.10  along with windows(partition), at this time ubuntu10.10 supported 1024x768 but gave a blinking effect.
Then I uninstalled  windows and only kept ubuntu10.10. Now its not supporting 1024x768, how can this happen (As in previous post I mentioned,I am just a beginner in linux) ?

Here is something that I get after putting the following command 
```
$ xrandr
Screen 0: minimum 320 x 200, current 800 x 600, maximum 2048 x 2048
VGA1 connected 800x600+0+0 (normal left inverted right x axis y axis) **267mm x 200mm**
   800x600        85.1*+   72.2     75.0     60.3     56.2  
   1024x768       60.0  
   832x624        74.6  
   640x480        85.0     72.8     75.0     66.7     60.0  
   720x400        70.1  

```
this 267mmx200mm remains same for all resolutions, is there any way by which this value can be increased?

---

### Post by deanjm1963 on 2010-11-22
Under the "System > Preferences > Monitors" have you tried to adjust your monitor with this? It should allow you to adjust size and timing. It might work for you. If not, there are many threads that cover this particular issue.

---

