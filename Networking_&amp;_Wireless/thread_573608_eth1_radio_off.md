---
title: "eth1 radio off"
date: 2007-10-11
forum: Networking &amp; Wireless
---

### Post by fdrake on 2007-10-11
i have a vaio vgn-fj170  laptop with ubuntu gutsy. I have been using this laptop for almost 2 years and almost everything was working just fine (but the Magic Gate stick card reader). After i updated my computer a couple of weeks ago i started noticing that the led of my wifi adapter was off even if the switcher was on. After realizing this I tried to use the wi-fi and I noticed that i couldn't scan or connect anymore. this is my iwconfig output.

eth1      radio off  ESSID:"dragon"  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

any advice will be appreciated.

---

### Post by fdrake on 2007-10-11
anyone?

---

### Post by fdrake on 2007-10-12
:(

---

### Post by fdrake on 2007-10-12
now this is getting very weird. I tried to boot with the Feisty live cd and typed iwconfig. I got the same response : radio off . why? does anybody else that have a vaio laptop has encountered this problem?please help , i really need to fix my wifi interface as soon as possible.

---

### Post by fdrake on 2007-10-12
bump!

---

### Post by android6011 on 2007-10-12
if your wireless worked fine with feisty originally, then it seems that it is probably not a settings issue. do you have a button on the computer that might disable/enable the wireless card? Have you tried typing "ifconfig eth1 up" at the terminal? Post any information on your card including dmesg and lsusb if it is a usb adapter or lspci if it is internal.

---

### Post by fdrake on 2007-10-14
```
$ sudo ifconfig eth1 up
[sudo] password for user:
user@vaio-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

i don't know what to do it's been almost 2 weeks and a half now and still no wifi .

my network [specifications]("http://reviews.cnet.com/laptops/sony-vaio-vgn-fj170/4507-3121_7-31554111.html") are:
    *  Data link protocol
    * Ethernet, IEEE 802.11b, IEEE 802.11g, Fast Ethernet

    * Networking standards
    * IEEE 802.11b, IEEE 802.11g

---

### Post by fdrake on 2007-10-15
i get this errors when i try to configure the power menagment
```
~$ sudo  iwconfig eth1 txpower on
Error for wireless request "Set Tx Power" (8B27) :
    GET failed on device eth1 ; Operation not supported.
~$ sudo  iwconfig eth1 txpower fixed
Error for wireless request "Set Tx Power" (8B27) :
    GET failed on device eth1 ; Operation not supported.
:~$ sudo  iwconfig eth1 txpower auto
Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device eth1 ; Operation not supported.
~$ 

```

---

### Post by noob12 on 2007-10-16
Check BIOS settings as well.

Can you post the output of 
```

lspci -nn

sudo lshw -C network

```

Had you set any special options on the driver earlier?

---

### Post by fdrake on 2007-10-16
```
$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller [8086:2668] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation 82801FBM (ICH6M) SATA Controller [8086:2653] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 03)
06:08.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
06:09.0 CardBus bridge [0607]: Texas Instruments PCI7420 CardBus Controller [104c:ac8e]
06:09.2 FireWire (IEEE 1394) [0c00]: Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller [104c:802e]
06:09.3 Mass storage controller [0180]: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller [104c:ac8f]
06:0a.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG Network Connection [8086:4220] (rev 05)
```

```
$ sudo lshw -C network
[sudo] password for jorid:
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@0000:06:08.0
       logical name: eth0
       version: 10
       serial: 00:01:4a:ca:d5:2b
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.4 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: a
       bus info: pci@0000:06:0a.0
       logical name: eth1
       version: 05
       serial: 00:13:ce:7f:a7:12
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.0kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=32 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=radio off

```
Note my switcher is on but the led (and the wireless radio) is off.

---

### Post by noob12 on 2007-10-16
First check the BIOS settings.  Make sure wireless is enabled in the BIOS.

If that does not resolve it, then try the following.

Disable wireless in Network Manager (right-click and uncheck Enable Wireless).  Then run the following sequence of commands which reloads the driver with the **led=1** option.
```

sudo ifconfig eth1 down
sudo modprobe -r ipw2200
sudo modprobe ipw2200 led=1
sudo ifconfig eth1 up

```

See if 
```

sudo lshw -C network

```
still reports **wireless=radio off** in the **configuration** line.  (We hope it does not.)

Then try to reenable wireless in Network Manager and see if you can connect or at least run a scan using **sudo iwlist scan**.

That option has been known to cause freeze-ups on some machines; if you have that problem, I don't have any good suggestions.  If it works and is stable, I'll suggest instructions for how to make the module load with the led=1 option on boot.

---

### Post by fdrake on 2007-10-17
```
~$ sudo ifconfig eth1 down
[sudo] password for jorid:
user@vaio-laptop:~$ sudo modprobe -r ipw2200
user@vaio-laptop:~$ sudo modprobe ipw2200 led=1
user@vaio-laptop:~$ sudo ifconfig eth1 up

```
```
~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@0000:06:08.0
       logical name: eth0
       version: 10
       serial: 00:01:4a:ca:d5:2b
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.4 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: a
       bus info: pci@0000:06:0a.0
       logical name: eth1
       version: 05
       serial: 00:13:ce:7f:a7:12
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.0kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=32 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=radio off

```

---

### Post by noob12 on 2007-10-17
OK.  That isn't doing it then.  

Go back over these things:
(1) Check your BIOS settings
(2) Check the hardware switch on your laptop.  This guide [http://www.iq.sony.com/srvs/DocsConnect/docget.asp?manualid=47844](http://www.iq.sony.com/srvs/DocsConnect/docget.asp?manualid=47844) indicates that your laptop has a wireless slider switch on the front left  or some other controls in the case that your laptop has bluetooth.  Check it out.

No other ideas, sorry.

---

### Post by fdrake on 2007-10-20
i did check the bios but there aren't any options available to activate or deactivate the wifi. One thing is weird for sure: my cd-rom drive it's not being recognized now neither by the bios or the OS . WTF!!!!! I think i might have done something that has damaged the hardware when i was carrying my laptop. I am going to open it and see if all the connectors are all at their place. I had this problem with my cd-rom drive before and I fixed it by pushing the connector dipper.
Thank you anyway for your help noob12  .
Best regards fdrake.

---

