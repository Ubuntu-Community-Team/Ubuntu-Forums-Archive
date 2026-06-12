---
title: "Ubuntu 7 Wi-Fi Network"
date: 2007-07-23
forum: Networking &amp; Wireless
---

### Post by Phuggoid Effect on 2007-07-23
Hello Everyone,

I´ve just installed Ubuntu version 7.04 in a PC that already had Windows XP Professional with a working wireless network.
I think Ubuntu already detected my wireless device, because it appears in the "Network Settings" window, like this:

Wireless connection (wmaster0)
Wireless connection (wlan0) - I´ve already configured and activated this one!
Modem connection

What I think is strange is that wmaster0, as I only have one wireless device connected to my PC. I don´t have any Ethernet "cable" device.

My Wi-Fi device is an USB D-Link G122 C1.

When I open the "Devices - Network Tools" window and select network device "Wireless Interface (wlan0) I have these informations shown bellow:

Hardware address: ...........
Multicast: Enabled
MTU: 1500
Link speed: not available
State: Active

I can see also some transmitted bytes and packets, NO transmission errors and NO received anything.

My network is WEP based and I have configured it correctly (at least I think that), as I set the correct "password".

As I´m a "starter edition" LINUX user, I really don´t know how to fix this.

Thank you for any help.


Rgds,

Phuggoid Effect

---

### Post by Phuggoid Effect on 2007-07-23
I´ve tried to install ndiswrapper and other native driver, but no success. My biggest problem is that in my case apt-get whatsoever DOESN´T work, as I don´t have any kind of connectivity, which is what I´m trying to get.

Thanks.


Rgds,

PE

---

### Post by kevdog on 2007-07-24
Please post the following and then I think I could at least get you pointed in the right direction:

Type the commands at the command line (might need to cut and paste output to a USB stick and bring to a computer with an internet connection):
lshw -C network <---- Only looking for the wireless interface (not a wired),
lspci -nn

---

### Post by Phuggoid Effect on 2007-07-24
Hi!

Thanks for your help.
I had to use a floppy disk, because my USB flashdrive is considered Read-Only by Ubuntu! Actually I can also access my NTFS partition in the same PC, but only for reading!
Anyway, these are the results:

lshw -C network <---- Only looking for the wireless interface (not a wired)

me@mypc:~$ sudo lshw -C network
Password:
  *-network               
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: ..:..:..:..:..:.. [COLOR="DarkRed"](I omitted the MAC for security reasons)[/COLOR]
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=10.1.1.5 multicast=yes wireless=IEEE 802.11g
me@mypc:~$ 

lspci -nn

me@mypc:~$ sudo lspci -nn
00:00.0 Host bridge [0600]: Silicon Integrated Systems [SiS] SiS645DX Host & Memory & AGP Controller [1039:0646]
00:01.0 PCI bridge [0604]: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP) [1039:0001]
00:02.0 ISA bridge [0601]: Silicon Integrated Systems [SiS] SiS961 [MuTIOL Media IO] [1039:0961] (rev 10)
00:02.1 SMBus [0c05]: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller [1039:0016]
00:02.5 IDE interface [0101]: Silicon Integrated Systems [SiS] 5513 [IDE] [1039:5513] (rev d0)
00:05.0 Multimedia audio controller [0401]: C-Media Electronics Inc CM8738 [13f6:0111] (rev 10)
00:0a.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. IEEE 1394 Host Controller [1106:3044] (rev 46)
00:0b.0 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 43)
00:0b.1 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 43)
00:0b.2 USB Controller [0c03]: NEC Corporation USB 2.0 [1033:00e0] (rev 04)
00:0d.0 Communication controller [0780]: Tiger Jet Network Inc. Tiger3XX Modem/ISDN interface [e159:0001]
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV350 AR [Radeon 9600] [1002:4152]
01:00.1 Display controller [0380]: ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary) [1002:4172]
me@mypc:~$

---

### Post by kevdog on 2007-07-25
I had forgotten your device is a USB device.  Can you instead post 
lsusb

I need to attempt to try to find the chipset of your device.

---

### Post by Phuggoid Effect on 2007-07-25
My device is for sure the DWL-G122 C1 V3.00 USB dongle (D-Link).
Now something good happened, after I tried some other drivers. After I rebooted things seemed to start to ALMOST work, now I can see the Network Manager, and I can see the "Link Strength" (sorry, I don´t remember the terms) but it´s "empty".
The Network Manager icon remains with just one little red diamond in the right bottom corner. I went to the terminal and set everything through sudo iwconfig wlan1 (now the wmaster0 doesn´t appear anymore, another good fact, I think), from key [index], to channel, etc, and it seems to be fine. When I scan for access point/router it is found indeed. Actually there seems to have a connection now, I even can see the number 54 Mbps. The problem is that I can´t ping anything, not even my routers address. The only thing I can ping is the own IP address of the PC Ubuntu is installed.
Within some of the terminal commands I can see that the "signal" between Ubuntu and my router is about 75/100, which I think means 75% of full signal strength.

Thanks for any information.


Rgds,

PE

---

### Post by kevdog on 2007-07-25
What drivers are you trying???  I cant find a definitive answer on the web since it seems to use a ra73  ra2500 or prism_usb driver.  It would seem that compilation and use of the serial monkey (ra 73/2500) drivers would be the first method I would use to test this device.

---

### Post by Phuggoid Effect on 2007-07-25
I´ve tried several approaches and drivers, and that´s the problem, I can´t remember which one is working indeed. :-( :-) Is there any way I can discover that, so that I can post the answer to you?
When I submit "sudo ifconfig wlan1 down" and then "sudo ifconfig wlan1 up" the configuration gets lost. Then I have to submit the command to configure the WEP key and its index, the channel, the mode, etc.

---

### Post by kevdog on 2007-07-25
lshw -C network may list the device driver, however often times this doesnt work with USB devices.  I guess your choices for drivers would be ndiswrapper, serialmonkey, I didnt install any drivers, something else.

---

### Post by Phuggoid Effect on 2007-07-25
I think the last one I tried is this "serialmonkey", I will make some more checks now and post the results.


Rgds!

PE

---

### Post by Phuggoid Effect on 2007-07-25
Hi there!

I bring, somewhat, good new!
Finally I got it working, but it´s not keeping the connection alive for much time. I noticed that when I access a certain site, the connection drops. I haven´t tried many sites yet, but as for my rapid tests, I just load a site in Firefox and the connection drops.
I followed the procedures regarding that "serialmonkey" driver, but not completelly. In the end I just edited /etc/network/interfaces and put in there the parameters that were working for me in the command shell/terminal. By editing the file "interfaces" I could get Ubuntu to boot with the network already connected.
Now I will search for this new problem, but please, if you have any idea or clue, please send me.

Thanks a lot!


Rgds,

PE

---

### Post by kevdog on 2007-07-25
You will have to be more specific about your problems other than the connection just drops.  As far as the instructions, I would follow them to the letter, since I know they are very reproducible.  I also would go one extra step, compile the rutilt executable, and try to use this as a GUI to connect.  Its easy to compile and install, and know it has worked for others.  If you downloaded the serial monkey drivers, the source for this should be in the download.

---

### Post by Phuggoid Effect on 2007-07-26
I tried following the whole process, but it didn´t work for me, not even a single second of "real" connection.
The "rutilt" comes together with the serial monkey driver? I will check that, thanks!
I will have time tonight, so I will make more tests. Yesterday I could stay connected for a long time, I even updated my Ubuntu by downloading some of the updates (great download speed!), but when I went to a site via Firefox, it dropped, strange...


Rgds,

PE

---

### Post by Phuggoid Effect on 2007-07-27
Uh Oh... During the periods that the net was up and running I took the chance to update Ubuntu (update utility from the graphic environment). It seemed to work fine until it asked for a reboot. When I rebooted and came back the WiFi net was down and wouldn´t get alive again! I can´t believe I shall start it all over again... [-X
I´m afraid I will keep WinXP for a little while... :mad:

---

### Post by kevdog on 2007-07-27
Again some updates might destroy your compiled kernel

This again was taken from the rt73 thread, so some of the instructions may need to be slightly modified for your serial monkey driver version, but I think it gives you a good idea what to do:

> NOTE: As Austin_KW rightly pointed out, if you install a new kernel (this is sometimes included in the updates), you will have to recompile the module, strip it again (if necessary) and install it over the previous one. To do this, open the terminal and go to the directory where you extracted the code originally and issue the commands listed:

```

cd /usr/src/rt73-cvs-yyyymmddhh/Module  <----Or directory where you put the serial monkey source files
sudo make clean
sudo make
sudo ifdown wlan0
sudo modprobe -rv rt73
sudo make install
sudo modprobe -v rt73
sudo ifup wlan0
```

---

