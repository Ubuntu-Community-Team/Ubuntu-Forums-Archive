---
title: "How To Disable Airplane Mode On ubuntu 19.04"
date: 2019-09-30
forum: Networking &amp; Wireless
---

### Post by amrali on 2019-09-30
My wireless adapter on my laptop works well on windows 10 but on ubuntu 18.04.3 and 19.04 doesn't work, i tried everything i seared all over the web but useless. 
this is what i tried to do in order to fix this issue
```
nmcli r
WIFI-HW  WIFI      WWAN-HW  WWAN     
enabled  disabled  enabled  disabled

```
and the ```
nmcli radio wifi on
``` 
then 
```
nmcli r
WIFI-HW  WIFI      WWAN-HW  WWAN     
enabled  disabled  enabled  disabled
```
and check this file on ubuntu 18.04.3 i found it 2 then i changed it to 3 to enable it and then reboot the system but useless here on 19.04 is already 3
```
       /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf                
[connection]
wifi.powersave = 3
```
the out put of lshw -C network command is 
```
*-network DISABLED        
       description: Wireless interface
       product: RT3290 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlo1
       version: 00
       serial: 34:23:87:b4:e7:2d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=5.0.0-29-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:19 memory:d0610000-d061ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: enp5s0
       version: 07
       serial: 9c:b6:54:1e:91:b6
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.1.13 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:17 ioport:2000(size=256) memory:d0404000-d0404fff memory:d0400000-d0403fff

```
the ouput of iwconfig is ```
wlo1      IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short  long limit:2   RTS thr:off   Fragment thr:off
          Power Management:off
          
enp5s0    no wireless extensions.

lo        no wireless extensions.
```
the output of lsmod | grep hp ```
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
hp_accel               28672  0
lis3lv02d              24576  1 hp_accel
hp_wireless            16384  0
wmi                    28672  2 hp_wmi,wmi_bmof

```
output of lsusb```
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 04f2:b372 Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge
Bus 001 Device 003: ID 138a:003d Validity Sensors, Inc. VFS491
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
output of lspci```
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C216 Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C216 Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C216 Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C216 Chipset Family PCI Express Root Port 4 (rev c4)
00:1c.5 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 6 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C216 Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Thames [Radeon HD 7550M/7570M/7650M]
03:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 30)
03:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 30)
03:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 30)
04:00.0 Network controller: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe
04:00.1 Bluetooth: Ralink corp. RT3290 Bluetooth
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 07)

```
output of rfkill list all ```
0: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes

```
i used "rfkill unblock wifi" and also useless , i followed some useful liks like this link
[https://ubuntuforums.org/showthread.php?t=2384309](https://ubuntuforums.org/showthread.php?t=2384309)
[https://ubuntuforums.org/showthread.php?t=1795211](https://ubuntuforums.org/showthread.php?t=1795211)
[https://www.linuxbabe.com/ubuntu/connect-to-wi-fi-from-terminal-on-ubuntu-18-04-19-04-with-wpa-supplicant](https://www.linuxbabe.com/ubuntu/connect-to-wi-fi-from-terminal-on-ubuntu-18-04-19-04-with-wpa-supplicant)

i tried also these code
```
sudo iwlist wlo1 scan | grep ESSID
wlo1      Interface doesn't support scanning : Network is down

```

```
sudo ifconfig wlo1 down
sudo ifconfig wlo1 up
SIOCSIFFLAGS: Operation not possible due to RF-kill

```
the output of sudo /etc/init.d/networking status 
```
&#9679; networking.service - Raise network interfaces
   Loaded: loaded (/lib/systemd/system/networking.service; enabled; vendor preset: enabled)
   Active: active (exited) since Mon 2019-09-30 05:53:10 EET; 1h 10min ago
     Docs: man:interfaces(5)
 Main PID: 460 (code=exited, status=0/SUCCESS)
    Tasks: 0 (limit: 4915)
   Memory: 0B
   CGroup: /system.slice/networking.service

```
by the way switch button on the laptop on win10 switchs on(wite light) and off(orange light) but on ubuntu it is still (orange light) even if i hit it the Airplane appear every hit and the light rea\mains orange ..  And on Network setting ==> wi-fi ======> Airplane Mod on Turn Off to use Wi-Fi
Can i get any advice here ......Thanks

---

### Post by chili555 on 2019-09-30
The issue of HP wireless being inoperable because of a hard block and therefore the usual wireless key not toggling wireless on and off is long-standing. There are only a few things you can try.

First, try removing the helper module hp_wmi and then try to switch the wireless on with the key combination. 

You could also try:

```
sudo modprobe -r hp_wmi
sudo rfkill unblock all
rfkill list all

```
Second, check the user guide for your HP laptop and be certain that the wireless key combination you are using is correct. Be certain that you are not using Fn+F12, for example, if the user guide says it is simply F12. On the other hand, if you are certain you are using the correct sequence, try the wrong sequence as an experiment; i.e., use Fn+F12 (or whatever your sequence is) if the user guide says it’s F12 and vice versa.

Next, you can remove the card, tape off pin 20 and re-insert it: [https://ubuntuforums.org/showthread.php?t=2150597](https://ubuntuforums.org/showthread.php?t=2150597)

You can, if all these steps fail, file a bug report against the module hp_wmi: [https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)

Finally, in many, but not every case, a USB wireless will also be hard blocked for the same reasons. If you want to try one, be certain to try it within a return period.

I regret that there isn’t a better answer for HP laptops.

-----------------------------------

Possibly related: [https://askubuntu.com/questions/965595/why-does-airplane-mode-keep-toggling-on-my-hp-laptop-in-ubuntu-18-04/965596#965596](https://askubuntu.com/questions/965595/why-does-airplane-mode-keep-toggling-on-my-hp-laptop-in-ubuntu-18-04/965596#965596)

---

### Post by amrali on 2019-09-30
> **chili555 said:**
> The issue of HP wireless being inoperable because of a hard block and therefore the usual wireless key not toggling wireless on and off is long-standing. There are only a few things you can try.

First, try removing the helper module hp_wmi and then try to switch the wireless on with the key combination. 

You could also try:

```
sudo modprobe -r hp_wmi
sudo rfkill unblock all
rfkill list all

```
Second, check the user guide for your HP laptop and be certain that the wireless key combination you are using is correct. Be certain that you are not using Fn+F12, for example, if the user guide says it is simply F12. On the other hand, if you are certain you are using the correct sequence, try the wrong sequence as an experiment; i.e., use Fn+F12 (or whatever your sequence is) if the user guide says it’s F12 and vice versa.

Next, you can remove the card, tape off pin 20 and re-insert it: [https://ubuntuforums.org/showthread.php?t=2150597](https://ubuntuforums.org/showthread.php?t=2150597)

You can, if all these steps fail, file a bug report against the module hp_wmi: [https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)

Finally, in many, but not every case, a USB wireless will also be hard blocked for the same reasons. If you want to try one, be certain to try it within a return period.

I regret that there isn’t a better answer for HP laptops.

-----------------------------------

Possibly related: [https://askubuntu.com/questions/965595/why-does-airplane-mode-keep-toggling-on-my-hp-laptop-in-ubuntu-18-04/965596#965596](https://askubuntu.com/questions/965595/why-does-airplane-mode-keep-toggling-on-my-hp-laptop-in-ubuntu-18-04/965596#965596)
Thanks for your reply i'm really appreciate that .... i followed your answer in a magnificent threat here talking about hp_wmi but also useless ... I tried also centos 7 and fedora on the same machine and the same problem occurs  .... But it is on win 10 works well with this wireless card RT3290 ,,, here is the question why this card works on windows well and didn't work on linux at all ......
Thanks again sir

---

### Post by chili555 on 2019-09-30
It works because a great many things work well in Windows and not at all in Linux, and vice versa.

Linux isn't "Windows Lite." It is a completely and entirely different operating system.

---

### Post by amrali on 2019-11-20
Thanks a lot Mr [chili555]("https://ubuntuforums.org/member.php?u=35909") finally we replaced the card itself by a new one , And it works fine now

---

