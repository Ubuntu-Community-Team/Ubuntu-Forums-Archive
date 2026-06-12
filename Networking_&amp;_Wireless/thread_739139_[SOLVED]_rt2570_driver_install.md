---
title: "[SOLVED] rt2570 driver install"
date: 2008-03-29
forum: Networking &amp; Wireless
---

### Post by acad1 on 2008-03-29
[https://help.ubuntu.com/community/WifiDocs/Device/DWL-G122_%28Rev_B%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/DWL-G122_%28Rev_B%29?highlight=%28WifiDocs%2FDevice%29)

I am trying to install the driver rt 2570 into Ubuntu 7.10, and find the documentation given in the above link confusing as it appears to have been written for earlier versions. As I am new to Linux, would it be possible for someone to update the documentation so that I can install this driver into 7.10 and get a wireless connection. Many thanks.

---

### Post by pytheas22 on 2008-03-29
Since Ubuntu 7.10, stable drivers for rt2570 have been included with the release--in other words, you shouldn't need to do anything to get your device working; it should "just work" and connect after you plug it in.  If you've had trouble connecting, please describe the problems, and also give more information about your wireless card, which you can find with the command "lsusb" (or lspci if it's an internal device, but I think all rt2570 cards are USB).  I've found that the driver that ships with Ubuntu for Ralink cards can be flaky sometimes, but there are other versions of the driver to try if that's the case.

---

### Post by JafaarNhh on 2008-03-29
You can install Wireless drivers in Add\Remove application you can search for many updates like wireless drivers and many more.:)

---

### Post by pytheas22 on 2008-03-29
> You can install Wireless drivers in Add\Remove application you can search for many updates like wireless drivers and many more.

This is true for some kinds of drivers, but just to be clear: the rt2570 drivers should already be installed; no need to do anything else.  This is one of the places where Linux is fundamentally different than Windows: the drivers are already built into the kernel; they don't have to be installed later.  Of course, in some cases Ubuntu does not include drivers in the kernel because they might be unstable or whatever; those are the ones that you'd need to install later, and these do not include the rt2570 driver.

---

### Post by acad1 on 2008-03-29
I have attached the readouts of the lsusb, iwconfig, ifconfig, and lsmod | grep rt commands using Ubuntu 7.04 with which I get internet access, and Ubuntu 7.10 with which I do not get internet access, using the same computer. I do not have a wired connection to the internet - no firewire port on this PIII, 1 GHz old computer.

Ubuntu 7.04

ndy@andy-desktop:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 2001:3c00 D-Link Corp. [hex] DWL-G122 802.11g rev. B1 [ralink]
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
andy@andy-desktop:~$ iwconfig
lo        no wireless extensions.

rausb1    RT2500USB WLAN  ESSID:"G604T-WIRELESS"  Nickname:""
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:1B:2F:72:75:A8   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=86/100  Signal level:-53 dBm  Noise level:-200 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

andy@andy-desktop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:84 (84.0 b)  TX bytes:84 (84.0 b)

rausb1    Link encap:Ethernet  HWaddr 00:13:46:63:1E:AE  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:46ff:fe63:1eae/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:201700 (196.9 KiB)  TX bytes:9730 (9.5 KiB)

andy@andy-desktop:~$ lsmod | getrep rt
bash: getrep: command not found
andy@andy-desktop:~$ sudo lsmod | grep rt
Password:
rt2570                186432  1 
snd_mpu401_uart         9472  1 snd_mpu401
snd_rawmidi            25472  2 snd_seq_midi,snd_mpu401_uart
gameport               16520  1 analog
snd                    54020  15 snd_intel8x0,snd_ac97_codec,snd_seq_oss,snd_bt87x,snd_mpu401,snd_mpu401_uart,snd_seq,snd_pcm_oss,snd_mixer_oss,snd_rawmidi,snd_pcm,snd_timer,snd_seq_device
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
agpgart                35400  2 intel_agp
iTCO_vendor_support     4868  1 iTCO_wdt
usbcore               134280  6 rt2570,usbhid,ehci_hcd,ohci_hcd,uhci_hcd
andy@andy-desktop:~$ andy@andy-desktop:~$ lsmod | getrep rt
andy@andy-desktop:~$ lsmod | getrep rt
bash: andy@andy-desktop:~$: command not found
bash: getrep: command not found
andy@andy-desktop:~$ andy@andy-desktop:~$ lsmod | getrep rt
andy@andy-desktop:~$ lsmod | getrep rt
bash: andy@andy-desktop:~$: command not found
bash: getrep: command not found
andy@andy-desktop:~$ andy@andy-desktop:~$ lsmod | getrep rt
bash: getrep: command not found
bash: andy@andy-desktop:~$: command not found
andy@andy-desktop:~$ 

Ubuntu 7.10 ( No internet access)

andy@andy-desktop:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 005: ID 13fe:1a00  
Bus 003 Device 002: ID 2001:3c00 D-Link Corp. [hex] DWL-G122 802.11g rev. B1 [ralink]
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
andy@andy-desktop:~$ iwconfig
lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"G604T-WIRELESS"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1B:2F:72:75:A8   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

andy@andy-desktop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1184 (1.1 KB)  TX bytes:1184 (1.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:13:46:63:1E:AE  
          inet6 addr: fe80::213:46ff:fe63:1eae/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:5855 (5.7 KB)

wlan0:ava Link encap:Ethernet  HWaddr 00:13:46:63:1E:AE  
          inet addr:169.254.5.167  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-13-46-63-1E-AE-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

andy@andy-desktop:~$ lsmod | grep rt
rt2500usb              22016  0 
rt2x00usb              12032  1 rt2500usb
rt2x00lib              19584  2 rt2500usb,rt2x00usb
rfkill                  8208  1 rt2x00lib
mac80211              171016  3 rc80211_simple,rt2x00usb,rt2x00lib
snd_mpu401_uart         9600  1 snd_mpu401
input_polldev           5896  1 rt2x00lib
crc_itu_t               3072  1 rt2x00lib
snd_rawmidi            25728  2 snd_mpu401_uart,snd_seq_midi
gameport               16776  1 analog
snd                    54660  15 snd_bt87x,snd_mpu401,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_seq_device,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
iTCO_vendor_support     4868  1 iTCO_wdt
agpgart                35016  2 intel_agp
usbcore               138632  9 usb_storage,libusual,rt2500usb,rt2x00usb,usbhid,ehci_hcd,ohci_hcd,uhci_hcd
andy@andy-desktop:~$ 

Ubuntu 7.04 was installed from a CD and worked straight away, but after two weeks or more, I am still struggling to get Ubuntu 7.10 to get internet access. Any help would be appreciated.

---

### Post by pytheas22 on 2008-03-29
How are you trying to connect?  It looks like your rt2570 card is installed and recognized without a problem, since it's listed by ifconfig.  What is the output of

```
iwlist wlan0 scan
```

And if you click on the Network Manager icon, can you select any network to connect to?  If you can, what happens after you try to connect?

---

### Post by acad1 on 2008-03-29
The result of iwlist wlan0 scan is:

wlan0 No scan result

When I click on  the monitor icons, it shows the correct essid, correct WEP password in hex and automatic DHCP config.

When I try to connect to Firefox it is trying to connect for a good two minutes, and then reverts to "Server not found"

---

### Post by pytheas22 on 2008-03-29
That behavior is strange.  You could try installing the legacy drivers, which I've always had better luck with.  Here are directions:

1. download the driver from [http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz) and extract it (right click on its icon on your desktop and select "Extract Here."

2. make sure you have the stuff installed to compile the driver.  Put your Ubuntu install CD in the drive and type:

```
sudo apt-get install build-essential
```

3. build and install the new driver:
```

cd ~/Desktop/rt*
cd Module
make
sudo make install
```

4. blacklist the default drivers, which apparently don't work for you:

sudo -s
echo "blacklist rt73usb" >> /etc/modprobe.d/blacklist
echo "blacklist rt2500usb" >> /etc/modprobe.d/blacklist
echo "blacklist rt2x00usb" >> /etc/modprobe.d/blacklist
echo "blacklist rt2x00lib" >> /etc/modprobe.d/blacklist
echo "blacklist ndiswrapper" >> /etc/modprobe.d/blacklist
exit

5. modprobe the new driver and bring up the interface:
```

sudo modprobe rt2500
ifconfig wlan0 up
```

Post if you have any problems.  I wrote this really quickly and may have forgotten something.

---

### Post by acad1 on 2008-03-30
pytheas222,

many thanks for taking the trouble to help me.
I have attached a copy of the steps I took, and you will note that at the end,
[COLOR="Red"]"SIOCSIFFLAGS: Permission denied"[/COLOR]is the message I received.

Perhaps you could look at the steps I took and let me know if there is something I missed out along the way.


andy@andy-desktop:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
andy@andy-desktop:~$ cd ~/Desktop/rt*
andy@andy-desktop:~/Desktop/rt2500-cvs-2008033008$ cd Module
andy@andy-desktop:~/Desktop/rt2500-cvs-2008033008/Module$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
andy@andy-desktop:~/Desktop/rt2500-cvs-2008033008/Module$ sudo make install
2.6 module install
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/andy/Desktop/rt2500-cvs-2008033008/Module  modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  INSTALL /home/andy/Desktop/rt2500-cvs-2008033008/Module/rt2500.ko
  DEPMOD  2.6.22-14-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
/sbin/depmod -a
*** Update /etc/modprobe.d/ralink alias for ra0
andy@andy-desktop:~/Desktop/rt2500-cvs-2008033008/Module$ sudo -s
root@andy-desktop:~/Desktop/rt2500-cvs-2008033008/Module# echo "blacklist rt73usb" >> /etc/modprobe.d/blacklist
root@andy-desktop:~/Desktop/rt2500-cvs-2008033008/Module# echo "blacklist rt2x00usb" >> /etc/modprobe.d/blacklist
root@andy-desktop:~/Desktop/rt2500-cvs-2008033008/Module# echo "blacklist rt2500usb" >> /etc/modprobe.d/blacklist
root@andy-desktop:~/Desktop/rt2500-cvs-2008033008/Module# echo "blacklist rt2x00lib" >> /etc/modprobe.d/blacklist
root@andy-desktop:~/Desktop/rt2500-cvs-2008033008/Module# echo "blacklist ndiswrapper" >> /etc/modprobe.d/blacklist
root@andy-desktop:~/Desktop/rt2500-cvs-2008033008/Module# exit
exit
andy@andy-desktop:~/Desktop/rt2500-cvs-2008033008/Module$ sudo modprobe rt2500
andy@andy-desktop:~/Desktop/rt2500-cvs-2008033008/Module$ ifconfig wlan0 up
SIOCSIFFLAGS: Permission denied
andy@andy-desktop:~/Desktop/rt2500-cvs-2008033008/Module$

---

### Post by pytheas22 on 2008-03-30
try "sudo ifconfig wlan0 up" ... I forgot that you need to be root to do that.  Hopefully the solution is as simple as that.  Everything else looks like it went as it should have.

---

### Post by acad1 on 2008-03-30
I have tried "sudo config wlan0 up" and I get the following error:

wlan0 : ERROR while getting interface flags:
              No such device

Also, the Wireless Connection in Network Settings has disappeared - it only shows a Modem Connection, which I don't have. The monitor icon - top right of screen also shows an orange triangle with an exclamation mark.

In Ubuntu 7.04 the device is shown as "rausb1", but I have not seen this in 7.10

---

### Post by pytheas22 on 2008-03-30
It's possible that the device is not called wlan0; I'm not sure because my Ralink device uses the rt73 driver instead of rt2570.  Run the command

```
cat /etc/modprobe.d/ralink
```  You should get output that looks like

```
alias wlan0 rt73
```

(this is what I get; yours will probably say ra0 instead of rt73 and will hopefully have an alias name that's not wlan0, explaining your problem) and it should tell you what name the interface has been assigned, which more likely than not will be rausb0 or rausb1.  Try running sudo ifconfig up again with the correct interface name.  I'm sorry this has not worked so far...

Once the interface has been brought "up," it should be recognized by the system in the Network Settings utility and the Network Manager applet (the thing currently showing a triangle with an exclamation point).

---

### Post by pytheas22 on 2008-03-30
Also, I'm not sure if I mentioned this, but I believe that Network Manager does not work with the serialmonkey drivers.  You need to use serialmonkey's connection manager, rutilt, which can be installed from [http://packages.ubuntu.com/search?keywords=rutilt&searchon=names&suite=gutsy&section=all](http://packages.ubuntu.com/search?keywords=rutilt&searchon=names&suite=gutsy&section=all) .  But first let's at least try to get the device up and see if it can scan (command: iwlist [device name, e.g. rausb0] scan")

---

### Post by acad1 on 2008-03-30
The device is known as ra0.

I have tried changing the device name in "ifconfig ra0 up" but it does not work.
Does the information below help? Sorry about the delay in replying but I have to reply with 7.04, and then close down and open up 7.10  for the next move!






andy@andy-desktop:~$ cat /etc/modprobe.d/ralink
alias ra0 rt2500
andy@andy-desktop:~$ iwlist
Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation 
andy@andy-desktop:~$ iwlist ra0 scan
ra0       Interface doesn't support scanning.

andy@andy-desktop:~$ sudo modprobe rt2500
[sudo] password for andy:
andy@andy-desktop:~$ ifconfig ra0 up
ra0: ERROR while getting interface flags: No such device
andy@andy-desktop:~$

---

### Post by pytheas22 on 2008-03-30
What is the output of "iwconfig" ?

---

### Post by acad1 on 2008-03-30
Outout of iwconfig is:

lo      no wireless extensions

---

### Post by pytheas22 on 2008-03-30
Strange, it looks like the module is not even inserted.  Sorry to make you keep rebooting, but could you post please the output of the following:

```
cat /etc/modprobe.d/blacklist

sudo modprobe -r rt2500 && sudo modprobe -v --first-time rt2500
```

then after you've done the above commands, please post again:

```

ifconfig -a

iwconfig
```

---

### Post by acad1 on 2008-03-30
andy@andy-desktop:~$ cat /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801
blacklist rt73usb
blacklist rt2500usb
blacklist rt2x00usb
blacklist rt2x00lib
blacklist ndiswrapper
blacklist rt73usb
blacklist rt2500usb
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt73usb
blacklist rt73usb
blacklist rt2x00usb
blacklist rt73usb
blacklist rt2x00usb
blacklist rt2500usb
blacklist rt2x00lib
blacklist ndiswrapper
andy@andy-desktop:~$ 
andy@andy-desktop:~$ sudo modprobe -r rt2500 &&sudo modprobe -v --first-time rt2500
[sudo] password for andy:
insmod /lib/modules/2.6.22-14-generic/extra/rt2500.ko 
andy@andy-desktop:~$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

andy@andy-desktop:~$ iwconfig
lo        no wireless extensions.

andy@andy-desktop:~$ 


I have managed to speed up the process a bit! Hope the above helps to solve the problem.I will be online for the next half hour and then have to depart. i can follow up at a later time, and thanks for your kind assistance.

---

### Post by pytheas22 on 2008-03-30
I think I know what's wrong, and it's that I had you compile the wrong driver before--you need rt2570, not rt2500.  I'm really sorry; I'm not sure how I made that mistake.  But at least it explains the problem (I think).  Do this to get the right driver:

1. download the rt2570 driver from [http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz) and extract it

2. compile

```
cd ~/Desktop/rt2570*
cd Module
make
sudo make install
```

3. insert module

```
modprobe rt2570
```

4. bring it up

```
sudo ifconfig rausb0 up
```

of course, you may have to replace "rausb0" with whatever is in the /etc/modprobe.d/ralink file

post the output of iwconfig and ifconfig -a again after doing all this.  Also post

```
iwlist rausb0 scan
```

(for this command too you may have to change rausb0 to the correct name)

---

### Post by acad1 on 2008-03-30
Thanks for your help - I will have to do this another time, and will post back tomorrow.

---

### Post by acad1 on 2008-03-31
> **pytheas22 said:**
> I think I know what's wrong, and it's that I had you compile the wrong driver before--you need rt2570, not rt2500.  I'm really sorry; I'm not sure how I made that mistake.  But at least it explains the problem (I think).  Do this to get the right driver:

1. download the rt2570 driver from [http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz) and extract it

2. compile

```
cd ~/Desktop/rt2570*
cd Module
make
sudo make install
```

3. insert module

```
modprobe rt2570
```

4. bring it up

```
sudo ifconfig rausb0 up
```

of course, you may have to replace "rausb0" with whatever is in the /etc/modprobe.d/ralink file

post the output of iwconfig and ifconfig -a again after doing all this.  Also post

```
iwlist rausb0 scan
```

(for this command too you may have to change rausb0 to the correct name)





I have run through the items above and there still seems to be a conflict. I will add the information below:

This is the readout of what I have done this evening - the second time I have run through the procedure.

andy@andy-desktop:~$ cd  ~/Desktop/rt2570*
andy@andy-desktop:~/Desktop/rt2570-cvs-2008033014$ cd Module
andy@andy-desktop:~/Desktop/rt2570-cvs-2008033014/Module$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
andy@andy-desktop:~/Desktop/rt2570-cvs-2008033014/Module$ sudo make install
[sudo] password for andy:
2.6 module install
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/andy/Desktop/rt2570-cvs-2008033014/Module  modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  INSTALL /home/andy/Desktop/rt2570-cvs-2008033014/Module/rt2570.ko
  DEPMOD  2.6.22-14-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
/sbin/depmod -a
*** Update /etc/modprobe.d/ralink alias for rausb0
andy@andy-desktop:~/Desktop/rt2570-cvs-2008033014/Module$ modprobe rt2750
FATAL: Module rt2750 not found.
andy@andy-desktop:~/Desktop/rt2570-cvs-2008033014/Module$ gedit /etc/network/interfaces
andy@andy-desktop:~/Desktop/rt2570-cvs-2008033014/Module$ gedit /etc/modprobe.d/ralink
andy@andy-desktop:~/Desktop/rt2570-cvs-2008033014/Module$ modprobe rt2570
andy@andy-desktop:~/Desktop/rt2570-cvs-2008033014/Module$ sudo ifconfig rausb0 up
rausb0: ERROR while getting interface flags: No such device
andy@andy-desktop:~/Desktop/rt2570-cvs-2008033014/Module$ sudo ifconfig ra0 up
ra0: ERROR while getting interface flags: No such device
andy@andy-desktop:~/Desktop/rt2570-cvs-2008033014/Module$ gedit /etc/modprobe.d/ralink
andy@andy-desktop:~/Desktop/rt2570-cvs-2008033014/Module$ iwconfig
lo        no wireless extensions.

wlan0     RT2500USB WLAN  ESSID:""  Nickname:""
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=11 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-120 dBm  Noise level:-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

andy@andy-desktop:~/Desktop/rt2570-cvs-2008033014/Module$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:13:46:63:1E:AE  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1355107 (1.2 MB)  TX bytes:78000 (76.1 KB)

andy@andy-desktop:~/Desktop/rt2570-cvs-2008033014/Module$ iwlist rausb0 scan
rausb0    Interface doesn't support scanning.

andy@andy-desktop:~/Desktop/rt2570-cvs-2008033014/Module$ iwlist ra0 scan
ra0       Interface doesn't support scanning.

andy@andy-desktop:~/Desktop/rt2570-cvs-2008033014/Module$ 
_________________________________________________________________________

In the /etc/modprobe.d/ralink file I found two aliases

alias ra0 rt2500
alias rausb0 rt2570

What is the next step to take please? ( maybe wait for Ubuntu 8.04!)

---

### Post by pytheas22 on 2008-03-31
iwconfig lists your device, so it should work!  This is really good news....now the interface just needs to be brought up.  The reason it didn't work yet is that you tried to bring up the ra0 device, which doesn't exist...you need to bring up wlan0 (which corresponds to the rt2570 driver) instead.  This should do it:

```
sudo modprobe rt2570
sudo ifconfig wlan0 up
```

Then try scanning:

```
sudo iwlist wlan0 scan
```

If this works, we can move on to actually connecting (which should be easier).  Note that apparently your interface is called wlan0, not rt2570 or rt2500 or anything else.

---

### Post by acad1 on 2008-03-31
The "iwlist wlan0 scan" shows three cells which are wireless connections in the vicinity, but it does not show my own oconnection!

---

### Post by pytheas22 on 2008-03-31
That's strange, but at least it shows something, which means that the card works.  Did you try the iwlist command a few times and still get nothing?  Are you sure you're within range?  Your essid isn't hidden, is it?  Which frequency is your network running at (almost everything is 802.11g these days)?  If you still can't see the network, please post the output of "iwlist wlan0 scan" and iwconfig (after the interface is up) again.

Also, as I think I mentioned before, you will need to have rutilt installed to actually connect, as NM can't handle it.  If you have an Internet connection on the machine, you can just do

sudo apt-get install rutilt

otherwise you can download the package from [http://packages.ubuntu.com/search?keywords=rutilt&searchon=names&suite=gutsy&section=all](http://packages.ubuntu.com/search?keywords=rutilt&searchon=names&suite=gutsy&section=all) and transfer it to the Ubuntu machine for installation.  I think it has a couple dependencies that you will have to install the same way.

---

### Post by acad1 on 2008-03-31
> **pytheas22 said:**
> That's strange, but at least it shows something, which means that the card works.  Did you try the iwlist command a few times and still get nothing?  Are you sure you're within range?  Your essid isn't hidden, is it?  Which frequency is your network running at (almost everything is 802.11g these days)?  If you still can't see the network, please post the output of "iwlist wlan0 scan" and iwconfig (after the interface is up) again.

Also, as I think I mentioned before, you will need to have rutilt installed to actually connect, as NM can't handle it.  If you have an Internet connection on the machine, you can just do

sudo apt-get install rutilt

otherwise you can download the package from [http://packages.ubuntu.com/search?keywords=rutilt&searchon=names&suite=gutsy&section=all](http://packages.ubuntu.com/search?keywords=rutilt&searchon=names&suite=gutsy&section=all) and transfer it to the Ubuntu machine for installation.  I think it has a couple dependencies that you will have to install the same way.



I did try the iwlist command again, and it returned nothing on both occasions, A third attempt produced the following which is my own wireless connection.


andy@andy-desktop:~$ sudo modprobe rt2570
[sudo] password for andy:
andy@andy-desktop:~$ sudo ifconfig wlan0 up
andy@andy-desktop:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:1B:2F:72:75:A8
                    Mode:Managed
                    ESSID:"G604T-WIRELESS"
                    Encryption key:on
                    Channel:11

andy@andy-desktop:~$ iwconfig
lo        no wireless extensions.

wlan0     RT2500USB WLAN  ESSID:""  Nickname:""
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=11 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-120 dBm  Noise level:-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon2570 drivert:0

andy@andy-desktop:~$ 

The other cell innformation has disappeared, although I amalmost sure it has not been switched off
I will load the rutilt by transferring the download using a usb stick. Is the method of installing this similar to what I have used before for the rt2570 driver?

---

### Post by pytheas22 on 2008-03-31
ok, it's good that you've seen your network at least once using iwlist.  iwlist is only a quick way to make sure that a wireless card is actually working; it's not unusual for it to take several tries to see a network, or for it to see different networks on different tries.  The point is that we know your card can see your network, which means you can move to the final step of actually connecting.

> I will load the rutilt by transferring the download using a usb stick. Is the method of installing this similar to what I have used before for the rt2570 driver?

No, it should be much easier.  Download the package from the website I linked to (you will need to select a mirror from which to actually download it), then simply transfer it to the Ubuntu system and double click its icon there...you'll be asked for your password and the installer will come up.  No command line!

The only hitch is that there might be other dependencies that you need to install first before rutilt can be installed.  The installer will tell you which ones it needs, and you can try to find them on packages.ubuntu.com by searching for their names, and then install them by transferring them via a USB stick and double clicking on their icons.  If you can't figure out which packages you need (I seem to recall there being two of them for rutilt), post the error that the package installer gives you and we can figure it out (the error I think looks something like "ERROR: xxx is not satisfiable," printed in red letters in the upper-right corner of the installer).

---

### Post by acad1 on 2008-03-31
I have downloaded the file "rutilt_0.15.orig.tar.gz" Will this be the correct one?

Again I must cut and run, so will continue again another time. Many thanks for your time and patience. I hope that we will get there eventually

---

### Post by pytheas22 on 2008-03-31
No, you want to download a debian package, extension .deb. The .tar.gz is what you would use if you wanted to compile rutilt from source like you did with the driver, but that's a big hassle compared to using a pre-compiled package.  Here is a direct link to one: [http://ubuntu.mirrors.tds.net/ubuntu/pool/universe/r/rutilt/rutilt_0.15-0ubuntu5_i386.deb](http://ubuntu.mirrors.tds.net/ubuntu/pool/universe/r/rutilt/rutilt_0.15-0ubuntu5_i386.deb) .  Note that this is a 32-bit package; if you are running a 64-bit kernel, you'll need to select link from [http://packages.ubuntu.com/gutsy/amd64/rutilt/download](http://packages.ubuntu.com/gutsy/amd64/rutilt/download) .

---

### Post by acad1 on 2008-04-01
I downloaded the 32-bit package .deb file for which you gave me a direct link and installed it, which as you said would be simple to do. I completed the connection details in Network manager and after re-booting was able to connect wirelessly in Ubuntu 7.10 using the D-link DWL G122 H/W ver B1, F/W ver 2.03, for the first time. I only hope that it will do the same next time I re-boot. I must offer a big THANK YOU for all of the assistance you have given me in getting set up. If you have any further advice, I would be grateful to hear from you. I must now go over the various steps and correlate all of the information for possible use with 8.04.

---

### Post by pytheas22 on 2008-04-01
I'm glad it finally worked, and sorry again for my initial mistake in telling you to compile the wrong driver.  And let's hope that in Hardy the driver will just work and this won't even be an issue.

---

### Post by acad1 on 2008-04-03
I don't think I am finally there yet! The wireless connects at startup but then seems to lose connection after about a minute The RuTilt WLAN Manager settings all show correctly, as do the Network settings under System >Admin > Network. Do I have to remove anything?

---

### Post by pytheas22 on 2008-04-03
What do you mean when you say it seems to lose connection...does Rutilt say it's lost, or are you just unable to load web pages?  Does Rutilt report a decent signal strength?

What happens if you reconnect?  I have a strange issue where, upon my first attempt to connect after a system reboot, my wireless card will appear connected (the connection light on the device lights up) but then it drops after about 15 seconds.  The second attempt to connect (i.e. pressing "Connect" again) makes it connect and stay connected.  I've never figured out why I have this problem, but maybe you have similar behavior.

If you still can't figure out the problem, try running Rutilt from the command line (just type "rutilt") and post the output you get up to the point where the connection drops.

---

### Post by acad1 on 2008-04-03
(Using 7.04!)

I have re-booted several times, and last time I have checked the readings for Rutilt at startup and also when I lost the web pages loading up., which occurs anything from one minute to 10 minutes after start up.
Link Quality remains about 84%,  Signal level is 59dBm, and Noise level is -92 dBm.
All other information in the Rutilt window is as expected: i.e essid, mode (managed), Channel.

I would like to get 7.10 up and running successfully, but maybe I should continue with 7.04, or try 8.04 when it comes out! Again thanks for your help.

---

### Post by pytheas22 on 2008-04-03
I don't really know what to make of that.  You could try blacklisting the rt2500 driver just in case it's interfering with the rt2570 module (sudo echo "blacklist rt2500" >> /etc/modprobe.d/blacklist), but I doubt this is likely.  Otherwise I really don't know...it could be that you got a bad snapshot of the driver, so you could try recompiling using a different one--they get updated every hour at [http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads) .  But again, this is unlikely to be the problem.  You might also check the serialmonkey forums at [http://rt2x00.serialmonkey.com/phpBB2/](http://rt2x00.serialmonkey.com/phpBB2/)  Or just wait for 8.04, depending on how much more work you want to put into this.  I'm really disappointed that we can't solve the problem definitively, but I don't know what else to try.

If I think of anything else that's likely to solve the problem, I'll post again.

---

### Post by acad1 on 2008-04-04
I have just taken your advice, and blacklisted rt2500, and also recompiled the rt2570 driver from today's download as given in your last post.
As far as I can see, it has been successful! I have re-booted several times, and each time, have been able to connect wirelessly wothout any problems. I should have carried out one task at a time, and then would have been able to isolate the problem.
Again I must thank you for being so patient and "talking" me through this problem. Now I can concentrate on getting to know a bit more about Ubuntu Linux. One thing I have not yet found out how to do is to mark the problem "SOLVED" Many thanks.

---

### Post by r.d. on 2008-05-02
acad1,

I've installed the rtutilt application as well as the rt2570 drivers (I also have the Dlink Rev B1 version), and while my link quality has improved to about 85%, I do not get an IP address (when looking at the Link Status screen from within rtutilt).

Do I need to clear out my /etc/network/interfaces file?  Could it be conflicting with the default Network Manager program?

I'm not sure what to try next, but I appreciate your help on this..!

---

