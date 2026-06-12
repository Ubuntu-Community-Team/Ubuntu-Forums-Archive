---
title: "RTL8723BE &amp; kernel 4.15.0-33"
date: 2018-08-23
forum: Networking &amp; Wireless
---

### Post by PippoPalmieri on 2018-08-23
Hello guys, 

Wondering if anyone with the same issue around here. 

I'm a very unhappy owner of the above wifi chipset (RTL8723BE). On my laptop it has never worked out of the box, but I've learnt what it likes and it's been doing fine with the ant_sel parameter set to 2. 

It's been working right up until the last update to kernel 4.15.0-33. Now its behaving like it would with a wrong ant_sel value, but no matter what i set this parameter to the wifi signal is very weak. Seems like it's ignoring my configuration. I will post a few show commands in a second.
I'm on kubuntu 18.04.1

edit: here comes some info about the wifi

> 
uname -a
Linux sf71h 4.15.0-33-generic #36-Ubuntu SMP Wed Aug 15 16:00:05 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux


lspci -knn | grep Net -A3
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
Subsystem: Hewlett-Packard Company RTL8723BE PCIe Wireless Network Adapter [103c:81c1]
Kernel driver in use: rtl8723be
Kernel modules: rtl8723be




lshw -class network
*-network
description: Wireless interface
product: RTL8723BE PCIe Wireless Network Adapter
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:03:00.0
logical name: wlo1
version: 00
serial: 3c:a0:67:67:2e:89
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=rtl8723be driverversion=4.15.0-33-generic firmware=N/A latency=0 link=yes multicast=yes wireless=IEEE 802.11
resources: irq:17 ioport:3000(size=256) memory:c1100000-c1103fff



ifconfig
wlo1: flags=4099<UP,BROADCAST,MULTICAST> mtu 1500
ether 3c:a0:67:67:2e:89 txqueuelen 1000 (Ethernet)
RX packets 32 bytes 4760 (4.7 KB)
RX errors 0 dropped 0 overruns 0 frame 0
TX packets 92 bytes 17816 (17.8 KB)
TX errors 0 dropped 0 overruns 0 carrier 0 collisions 0

iwconfig
wlo1 IEEE 802.11 ESSIDff/any 
Mode:Managed Access Point: Not-Associated Tx-Power=20 dBm 
Retry short limit:7 RTS thr=2347 B Fragment thrff
Power Managementn


modinfo
filename: /lib/modules/4.15.0-33-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko
firmware: rtlwifi/rtl8723befw_36.bin
firmware: rtlwifi/rtl8723befw.bin
description: Realtek 8723BE 802.11n PCI wireless
license: GPL
author: Realtek WlanFAE <wlanfae@realtek.com>
author: PageHe <page_he@realsil.com.cn>
srcversion: 4460AA5584590927164B1F2
alias: pci:v000010ECd0000B723sv*sd*bc*sc*i*
depends: rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
retpoline: Y
intree: Y
name: rtl8723be
vermagic: 4.15.0-33-generic SMP mod_unload 
signat: PKCS#7
signer: 
sig_key: 
sig_hashalgo: md4
parm: swenc:Set to 1 for software crypto (default 0)
(bool)
parm: ips:Set to 0 to not use link power save (default 1)
(bool)
parm: swlps:Set to 1 to use SW control power save (default 0)
(bool)
parm: fwlps:Set to 1 to use FW control power save (default 1)
(bool)
parm: msi:Set to 1 to use MSI interrupts mode (default 0)
(bool)
parm: aspm:Set to 1 to enable ASPM (default 1)
(int)
parm: debug_level:Set debug level (0-5) (default 0) (int)
parm: debug_mask:Set debug mask (default 0) (ullong)
parm: disable_watchdog:Set to 1 to disable the watchdog (default 0)
(bool)
parm: ant_sel:Set to 1 or 2 to force antenna number (default 0)
(int)

dmesg | grep rtl8723be
[ 33.260643] rtl8723be: Using firmware rtlwifi/rtl8723befw_36.bin
[ 33.419742] rtl8723be 0000:03:00.0 wlo1: renamed from wlan0



Rolling back to previous kernel 4.15.0-32 returns correct functionality.

Thank you.

---

### Post by jeremy31 on 2018-08-23
In kernel 4.15.0-33, delete the conf file from /etc/modprobe.d where you set the parameter, likely ant_sel=2, then lets test the other options
```
sudo modprobe -r rtl8723be
sudo modprobe rtl8723be ant_sel=0
iwlist scan | egrep -i 'ssid|quality'
sudo modprobe -r rtl8723be
sudo modprobe rtl8723be ant_sel=1
iwlist scan | egrep -i 'ssid|quality'
sudo modprobe -r rtl8723be
sudo modprobe rtl8723be ant_sel=2
iwlist scan | egrep -i 'ssid|quality'
```
Post results

---

### Post by PippoPalmieri on 2018-08-23
Thank you for your help!

Here's the output.
I have removed the modprobe.d conf file before running the commands as asked.

> 
cj@sf71h:~$ sudo modprobe -r rtl8723be
cj@sf71h:~$ sudo modprobe rtl8723be ant_sel=0
cj@sf71h:~$ iwlist scan | egrep -i 'ssid|quality'
vmnet1    Interface doesn't support scanning.

vmnet8    Interface doesn't support scanning.

virbr0-nic  Interface doesn't support scanning.

enp2s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

virbr0    Interface doesn't support scanning.

                    Quality=34/70  Signal level=-76 dBm  
                    ESSID:"WiFi_2.4"



cj@sf71h:~$ sudo modprobe -r rtl8723be
cj@sf71h:~$ sudo modprobe rtl8723be ant_sel=1
cj@sf71h:~$ iwlist scan | egrep -i 'ssid|quality'
vmnet1    Interface doesn't support scanning.

vmnet8    Interface doesn't support scanning.

virbr0-nic  Interface doesn't support scanning.

enp2s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

virbr0    Interface doesn't support scanning.

                    Quality=34/70  Signal level=-76 dBm  
                    ESSID:"WiFi_2.4"




cj@sf71h:~$ sudo modprobe -r rtl8723be
cj@sf71h:~$ sudo modprobe rtl8723be ant_sel=2
cj@sf71h:~$ iwlist scan | egrep -i 'ssid|quality'
vmnet1    Interface doesn't support scanning.

vmnet8    Interface doesn't support scanning.

virbr0-nic  Interface doesn't support scanning.

enp2s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

virbr0    Interface doesn't support scanning.

                    Quality=26/70  Signal level=-84 dBm  
                    ESSID:"WiFi_2.4"


It would seem that ant_sel 2 yields even worse results than 0 or 1 now.

---

### Post by jeremy31 on 2018-08-23
Not the results I was expecting as I expected ant_se; set to 0 or 1 to be a much higher signal strength

---

### Post by PippoPalmieri on 2018-08-24
I will try posting somewhere else too to get a few more eyeballs on this. I will report if I find something.
I would think it's an issue with the latest kernel.

edit: after some googling i found the following

[https://bugzilla.kernel.org/show_bug.cgi?id=83641#c23](https://bugzilla.kernel.org/show_bug.cgi?id=83641#c23)

also plenty of results googling rtl8723be with kernel 4.16, I think the problem looks the same

---

### Post by adrian-z on 2018-08-24
I'm having the same problem here - everything was just fine on 4.15.0-32, no wireless networks visible on 4.15.0-33, and the ant-sel trick doesn't change it. Cold boot makes no difference in -33, booting back to -32 works instantly.
RTL4723BE on an HP 24-g080 all-in-one, showing fine in lspci in -33.

Originally building the machine needed the ant-sel to get anything but the very weakest of signal. Now, there's just zero.

The "pending patch" (from March...?) at [https://bugzilla.kernel.org/show_bug.cgi?id=83641#c9](https://bugzilla.kernel.org/show_bug.cgi?id=83641#c9) patches rt8723be/hw.c - but where am I looking for that? The only thing in /lib/modules/4.15.0-33-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/ is  rtl8723be.ko and that's non-text.

---

### Post by PippoPalmieri on 2018-08-24
> **adrian-z said:**
>  but where am I looking for that? The only thing in /lib/modules/4.15.0-33-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/ is  rtl8723be.ko and that's non-text.

I believe they're talking about what you'll find in the kernel source. So if you want to use 4.15.0-33 it would be about downloading the source, patching the modules and recompiling I think.
Also,before doing that, it's worth a shot trying to use the module provided here [https://github.com/lwfinger/rtlwifi_new](https://github.com/lwfinger/rtlwifi_new)
If that has the same commit it might work.

But anyway, I found a very good explanation of the issue here (that also explains why bluetooth has been working like crap):
[https://git.kernel.org/pub/scm/linux/kernel/git/stable/linux.git/commit/?h=v4.16.8&id=709c26e9c81f4c600df7ec0d5749a90a87dc5081](https://git.kernel.org/pub/scm/linux/kernel/git/stable/linux.git/commit/?h=v4.16.8&id=709c26e9c81f4c600df7ec0d5749a90a87dc5081)

Anyway, I am using the old kernel until my workaround arrives, an intel wifi chipset...

---

### Post by adrian-z on 2018-08-24
> **PippoPalmieri said:**
> Also,before doing that, it's worth a shot trying to use the module provided here [https://github.com/lwfinger/rtlwifi_new](https://github.com/lwfinger/rtlwifi_new)
If that has the same commit it might work.
Goes fine right up until the modprobe line to install - "required key not available".

> Anyway, I am using the old kernel until my workaround arrives, an intel wifi chipset...
Now, there's a thought... <reaches for TPLink USB adapter>
<edit> That works, but a poor signal...

---

### Post by PippoPalmieri on 2018-08-24
> **adrian-z said:**
> Goes fine right up until the modprobe line to install - "required key not available".



Try disabling secure boot from bios.

---

### Post by adrian-z on 2018-08-24
> **PippoPalmieri said:**
> Try disabling secure boot from bios.
<slaps forehead> Of course.

Disable secure boot, into -33, and the Realtek WiFi is working straight off. Thanks, guys!

---

### Post by hheckhoff on 2018-08-24
same story here, used to work like a charm up and until 4.15.0-32 with ant_sel=2...
secure boot is disabled...
by the way ant_sel was the best  choice for 16.04

- Heribert

---

### Post by PippoPalmieri on 2018-08-24
> **hheckhoff said:**
> same story here, used to work like a charm up and until 4.15.0-32 with ant_sel=2...
secure boot is disabled...
by the way ant_sel was the best  choice for 16.04

- Heribert

Install the module you find here [https://github.com/lwfinger/rtlwifi_new](https://github.com/lwfinger/rtlwifi_new)
It's working for me and adrian-z

---

### Post by arpi732 on 2018-08-25
> **PippoPalmieri said:**
> Hello guys, 

Wondering if anyone with the same issue around here. 


Exact same issue but rolling back to the 4.15.0-32 kernel doesn't work. I tried to intall the 4.15.0-30 kernel and then the system doesn't boot up.

---

### Post by matanjonas on 2018-08-27
I've had this problem since installing a fresh Ubuntu 18.04 (dual-boot with Win10). I had some network problems with 16.04 as well but not like this.

I did the rtlwifi_new fix that was suggested here but it doesn't seem to be doing much good. I still had to reboot about 4 times just to be able to write this forum reply.
Any other ideas for this? I'm desperate.

---

### Post by jeremy31 on 2018-08-28
Check to see if parameter settings make a difference
```
sudo modprobe -r rtl8723be
sudo modprobe rtl8723be ant_sel=1
iwlist scan | egrep -i 'SSID|level'
sudo modprobe -r rtl8723be
sudo modprobe rtl8723be ant_sel=2
iwlist scan | egrep -i 'SSID|level'
```

---

### Post by janemann.lang on 2018-08-30
Hi there!

Sorry already, I didnt even see, that there is a second page to the thread. will try solution suggested by PippoPalmieri and write back if it works for me
Ok, i am very happy: The rtlwifi_new from Larry Finger worked!

BUT:
For the last 9 month my laptop was always running with the ant_sel=1 parameter. now it didnt work, but i have read before, that sometimes the parameter changes. So I tried ant_sel=2 (this was actually my last hope before giving up for the day) and voila. Sitting 10 meters away from my router and have still good signal strength. Big thanks Ubuntuforums and Lwfinger!!

ORIGINAL:
I am new to Ubuntu forums and kind of a noob in Ubuntu anyways, but I think I have the same problem. I am using my laptop since 10 months now (HP 15-ba520ng), also with the RTL8723be. So far the workaround with the "options ant_sel=1" (for me 1 works usually and 2 doesnt) always worked fine, but since the last update (I did one in 16.04, when the ant_sel stopped working, then updated to 18.04) the ant_sel is not working anymore. I checked and the kernel is also version 4.15.0-33. No matter if i set the value at Quality at around 40/70 and Signal level at around -70dBm (sitting next to the router).

@adrian-z: your last post makes me believe, that you solved the problem, but what did you do? Did you download the module suggested by PippoPalmieri, run it and the the ant_sel worked again?

Thank you very much (already by finding the thread I feel not so alone with my problem anymore)

---

### Post by Schugy on 2018-09-23
Thank you guys for this great topic. If I reinstall I will switch off the legacy mode and use UEFI. I testet my Lenovo G50-45 80E3 with an 18.04.1 USB stick (kernel 4.15.0-29).
With the network manager disabled, a wpa_supplicant.conf file and udhcpc I could get good WiFi (4MB/sec) speed with the Fritz!Boxes after a short:
> sudo -s
echo "options rtl8723be fwlps=0 ips=0 swenc=1 msi=0 ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723be.conf
rmmod rtl8723be btcoexist rtl-common rtl-pci rtlwifi
modprobe rtl8723be
modprobe btcoexist
My rtl8723be could also authenticate with my OpenWRT routers (TP-Link WR1043ND_v1) but there was no data transfer with a fixed IP. It couldn´t obtain an IP using udhcpc either. I have to force my TP-Link routers into 40Mhz bandwidth mode (uci set wireless.radio0.noscan='1';uci commit ) and then suddenly my WiFi works (and even simultaneously with a BT mouse). Maybe this helps someone with a connection over which no data can be transferred at all. I hope that later versions -34/-35 work better again.

---

### Post by jeremy31 on 2018-09-24
> **Schugy said:**
> Thank you guys for this great topic. If I reinstall I will switch off the legacy mode and use UEFI. I testet my Lenovo G50-45 80E3 with an 18.04.1 USB stick (kernel 4.15.0-29).
With the network manager disabled, a wpa_supplicant.conf file and udhcpc I could get good WiFi (4MB/sec) speed with the Fritz!Boxes after a short:

My rtl8723be could also authenticate with my OpenWRT routers (TP-Link WR1043ND_v1) but there was no data transfer with a fixed IP. It couldn´t obtain an IP using udhcpc either. I have to force my TP-Link routers into 40Mhz bandwidth mode (uci set wireless.radio0.noscan='1';uci commit ) and then suddenly my WiFi works (and even simultaneously with a BT mouse). Maybe this helps someone with a connection over which no data can be transferred at all. I hope that later versions -34/-35 work better again.

I don't think Lenovo laptops will have the same issue as HP laptops have as HP started using just one antenna wire on the rtl8723be wifi cards about 3 years ago

---

### Post by chili555 on 2018-09-24
Please see my post #4 and following here: [https://ubuntuforums.org/showthread.php?t=2401794](https://ubuntuforums.org/showthread.php?t=2401794)

---

