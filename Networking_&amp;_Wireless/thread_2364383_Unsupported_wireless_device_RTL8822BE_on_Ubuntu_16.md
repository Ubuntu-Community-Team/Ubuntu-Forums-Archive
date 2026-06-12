---
title: "Unsupported wireless device RTL8822BE on Ubuntu 16.04"
date: 2017-06-22
forum: Networking &amp; Wireless
---

### Post by simoncks1994 on 2017-06-22
[COLOR=#333333][FONT=Ubuntu]I just bought a new Lenovo T470 preinstalled with Windows 10. After installing the latest Ubuntu 16.04 in parallel, I discovered that no wireless internet connection could be reached and displayed. A later post on AskUbuntu further ensures that my wireless device is too new to be supported by any kernel. At least claimed by a comment writer. It is a new RTL8822BE device.

```
lspci
00:00.0 Host bridge: Intel Corporation Device 5904 (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Device 5916 (rev 02)
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI (rev 21)
00:1c.0 PCI bridge: Intel Corporation Device 9d10 (rev f1)
00:1c.6 PCI bridge: Intel Corporation Device 9d16 (rev f1)
00:1d.0 PCI bridge: Intel Corporation Device 9d18 (rev f1)
00:1d.2 PCI bridge: Intel Corporation Device 9d1a (rev f1)
00:1f.0 ISA bridge: Intel Corporation Device 9d58 (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Audio device: Intel Corporation Device 9d71 (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
00:1f.6 Ethernet controller: Intel Corporation Ethernet Connection (4) I219-V (rev 21)
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device b822
3e:00.0 Non-Volatile memory controller: Toshiba America Info Systems Device 0115 (rev 01)
```
```
lsusb
Bus 002 Device 002: ID 0bda:0316 Realtek Semiconductor Corp.
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 04f2:b5ab Chicony Electronics Co., Ltd
Bus 001 Device 003: ID 0bda:b023 Realtek Semiconductor Corp.
Bus 001 Device 002: ID 058f:9540 Alcor Micro Corp. AU9540 Smartcard Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```
sudo lshw -C network
*-network
description: Ethernet interface
product: Ethernet Connection (4) I219-V
vendor: Intel Corporation
physical id: 1f.6
bus info: pci@0000:00:1f.6
logical name: enp0s31f6
version: 21
serial: 54:e1:ad:1f:de:57
capacity: 1Gbit/s
width: 32 bits
clock: 33MHz
capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=0.1-4 latency=0 link=no multicast=yes port=twisted pair
resources: irq:122 memory:ec200000-ec21ffff
lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 16.04.2 LTS
Release: 16.04
Codename: xenial
uname -a
Linux simon-ThinkPad-T470 4.8.0-36-generic #36~16.04.1-Ubuntu SMP Sun Feb 5 09:39:57 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
rfkill list
0: hci0: Bluetooth
Soft blocked: no
Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
Soft blocked: no
Hard blocked: no

```
Is there anyone who has experienced this problem? Would there be update available already to support the device? Is there anything I could attempt to solve the problem? I appreciate any suggestion/idea.
Link to my AskUbuntu post is -
[https://askubuntu.com/questions/921483/no-network-device-after-installing-ubuntu-16-04?noredirect=1#comment1455792_921483](https://askubuntu.com/questions/921483/no-network-device-after-installing-ubuntu-16-04?noredirect=1#comment1455792_921483)
[/FONT][/COLOR]

---

### Post by chili555 on 2017-06-22
>  A later post on AskUbuntu further ensures that my wireless device is too new to be supported by any kernel. At least claimed by a comment writer. As it happens, I also saw your post on Ask Ubuntu and did some research. I hoped I could find an answer and trip up my esteemed colleague Pilot6. As it turned out, and as it almost always turns out, Pilot6 is quite correct. In fact, when I get stuck, he is one of the people I can turn to for help!

The only clue is here: [https://github.com/lwfinger/rtlwifi_new/issues/233](https://github.com/lwfinger/rtlwifi_new/issues/233)> It will as soon as Realtek releases the driver to me.

L. W. Finger is involved in the development of almost all of the Realtek drivers for Linux. 

I have two suggestions. First, run: ```
lspci -nnk
```Find the pci.id for your device, perhaps something like 10ec:b822. Google it along with the keyword Linux or Ubuntu and check for yourself.

Second, get a fully supported USB wireless for US $12-15 and use it for six months or so and check back.

---

### Post by simoncks1994 on 2017-06-23
Thanks chili555. Indeed after some research on 10ec:b822, there is another post on askubuntu : [https://askubuntu.com/questions/926364/how-to-make-my-pci-wifi-card-rtl8822-working-on-ubuntu](https://askubuntu.com/questions/926364/how-to-make-my-pci-wifi-card-rtl8822-working-on-ubuntu). I think I will keep looking on Realtrek these months.

As suggested, I think I am going to buy a [COLOR=#000000]TP-Link TL-WN722N 150 Mbps USB wifi device[/COLOR]. There is another [post]("https://ubuntuforums.org/showthread.php?t=2338902") on recommended Wifi USB for Ubuntu forum.

---

### Post by johndough2 on 2017-06-23
Hi

Cannot disagree.

I see this
[http://www3.lenovo.com/gb/en/laptops/thinkpad/t-series/T470/p/20HDCTO1WWENGB1](http://www3.lenovo.com/gb/en/laptops/thinkpad/t-series/T470/p/20HDCTO1WWENGB1)


WLAN
[LIST]
[*]WiFi 802.11 ac
[*]Intel 8265 2x2 11ac
[/LIST]
 																	[h=4]Wireless[/h] 																	 																		Intel Dual Band Wireless AC(2x2) 8265, Bluetooth Version 4.1
 																

for a Lenovo T470, combined WiFi and Bluetooth. 

So it makes me think...

---

### Post by chili555 on 2017-06-24
> **johndough2 said:**
> Hi

Cannot disagree.

I see this
[http://www3.lenovo.com/gb/en/laptops/thinkpad/t-series/T470/p/20HDCTO1WWENGB1](http://www3.lenovo.com/gb/en/laptops/thinkpad/t-series/T470/p/20HDCTO1WWENGB1)


WLAN
[LIST]
[*]WiFi 802.11 ac
[*]Intel 8265 2x2 11ac
[/LIST]
 																	[h=4]Wireless[/h] 																	 																		Intel Dual Band Wireless AC(2x2) 8265, Bluetooth Version 4.1
 																

for a Lenovo T470, combined WiFi and Bluetooth. 
The Intel should work perfectly and at AC speeds. Recommended.

---

### Post by chili555 on 2017-06-26
UPDATE: My colleague Jeremy31 pointed out this site that says it includes the driver for your device: [https://github.com/rtlwifi-linux/rtlwifi-next](https://github.com/rtlwifi-linux/rtlwifi-next) He reports that the driver will not compile on his 16.04 system using kernel version 4.4-xx. It does compile, albeit with a few warnings, possibly harmless, on my 4.10-xx kernel, the default for Ubuntu 17.04.

I think you can download 17.04 and run a live session by either DVD or USB to try it. After you boot the live session and select 'Try Ubuntu,' get a working internet connection:```
sudo apt update
sudo apt install git
git clone https://github.com/rtlwifi-linux/rtlwifi-next
cd rtlwifi-next
make
sudo make install
sudo modprobe rtl8822be
```Is your wireless now working?

---

### Post by johndough2 on 2017-06-27
Hi

Are we at cross purposes in this thread?

It is supposed to have an Intel WiFi [Operating Systems Microsoft Windows 7*,Microsoft Windows 8.1*, Microsoft Windows 10*,Linux*(limited feature support), Android] - Intel 8265 2x2 802.11ac,Dual Band,80MHz, 2x2, MU-MIMO according to the Lenovo website, but it is being reported as a Realtek by the OS?

[https://www.intel.com/content/www/us/en/support/network-and-i-o/wireless-networking/000005511.html](https://www.intel.com/content/www/us/en/support/network-and-i-o/wireless-networking/000005511.html)

[TABLE]
[TR]
[TD]Intel® Dual Band Wireless-AC 8265[/TD]
			[TD]4.6 [/TD]
			[TD][iwlwifi-8265-ucode-22.361476.0.tgz]("https://wireless.wiki.kernel.org/_media/en/users/drivers/iwlwifi-8265-ucode-22.361476.0.tgz")
[/TD]
[/TR]
[/TABLE]

However if it's really a Realtek, then to complement the advice given above...
[https://zach-adams.com/2014/06/fixing-rtl8723ae-driver-ubuntu-linux/](https://zach-adams.com/2014/06/fixing-rtl8723ae-driver-ubuntu-linux/)
[https://ubuntu.pkgs.org/16.10/ubuntu-updates-main-amd64/linux-firmware_1.161.1_all.deb.html](https://ubuntu.pkgs.org/16.10/ubuntu-updates-main-amd64/linux-firmware_1.161.1_all.deb.html)

---

### Post by jeremy31 on 2017-06-27
> **johndough2 said:**
> Hi

Are we at cross purposes in this thread?

It is supposed to have an Intel WiFi [Operating Systems Microsoft Windows 7*,Microsoft Windows 8.1*, Microsoft Windows 10*,Linux*(limited feature support), Android] - Intel 8265 2x2 802.11ac,Dual Band,80MHz, 2x2, MU-MIMO according to the Lenovo website, but it is being reported as a Realtek by the OS?

[https://www.intel.com/content/www/us/en/support/network-and-i-o/wireless-networking/000005511.html](https://www.intel.com/content/www/us/en/support/network-and-i-o/wireless-networking/000005511.html)

[TABLE]
[TR]
[TD]Intel® Dual Band Wireless-AC 8265[/TD]
			[TD]4.6 [/TD]3DSP BlueW 2310U
			[TD][iwlwifi-8265-ucode-22.361476.0.tgz]("https://wireless.wiki.kernel.org/_media/en/users/drivers/iwlwifi-8265-ucode-22.361476.0.tgz")
[/TD]
[/TR]
[/TABLE]

However if it's really a Realtek, then to complement the advice given above...
[https://zach-adams.com/2014/06/fixing-rtl8723ae-driver-ubuntu-linux/](https://zach-adams.com/2014/06/fixing-rtl8723ae-driver-ubuntu-linux/)
[https://ubuntu.pkgs.org/16.10/ubuntu-updates-main-amd64/linux-firmware_1.161.1_all.deb.html](https://ubuntu.pkgs.org/16.10/ubuntu-updates-main-amd64/linux-firmware_1.161.1_all.deb.html)

This computer is not equipped with an Intel 8265 nor a Realtek 8723be.  The device is new enough that it is shows only this in lspci results
```
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device b822
```

In the source code at line 113 in [https://github.com/rtlwifi-linux/rtlwifi-next/blob/master/pci.h](https://github.com/rtlwifi-linux/rtlwifi-next/blob/master/pci.h) we see
```
#define RTL_PCI_8822BE_DID	0xB822	/*8822be*/

```

---

### Post by chili555 on 2017-06-27
The first bullet, WiFi 802.11ac, leaves Lenovo open to use any AC chipset they can. As a current and long time Thinkpad user, I assure you that during the manufacturing lifespan of most Thinkpad models, they use 3-4 wireless chipsets. 

Lenovo only meet the specification on the website because the spec is vague.

---

### Post by johndough2 on 2017-06-28
Hi

OK.  Enough egg on my face for an omelette, but I still tried.  Looking around Google I found

Opensuse has drivers for the BT part of 8822 so perhaps when I get in front of me laptop I can post a link, in the hope that the WiFi part becomes available.

---

### Post by chili555 on 2017-06-28
> **johndough2 said:**
> Hi

OK.  Enough egg on my face for an omelette, but I still tried.  Looking around Google I found

Opensuse has drivers for the BT part of 8822 so perhaps when I get in front of me laptop I can post a link, in the hope that the WiFi part becomes available.To paraphrase Tennyson, 'tis better to have tried and failed than never to have tried at all.

In my post #6 above, I opine that the wireless driver is now available; we only need to original poster to compile it and report.

---

### Post by jeremy31 on 2017-06-28
I actually found the github source code while browsing the Arch Linux forums and a poster said the module works but didn't state what kernel was being used [https://bbs.archlinux.org/viewtopic.php?id=227376](https://bbs.archlinux.org/viewtopic.php?id=227376)

---

### Post by simoncks1994 on 2017-07-16
Sorry for the late reply.

Indeed this works out. I retreated to use a wifi USB meanwhile. Finally, feel relieved.

---

### Post by simoncks1994 on 2017-07-16
After some check, I discover that the connection only lasts for the first minute. During that minute or so, I can connect to google. After so, the WiFi label shows connected with full strength although network is not reachable.
I am using PrivateInternetAccess and KillSwitch is disabled so I don't think it is relevant. I have two user accounts. One of them has its home directory encrypted. WiFi does not work in both accounts.

Meanwhile, there is new update in lshw

```
 [COLOR=#333333][FONT=&amp]sudo lshw -C network[/FONT][/COLOR]
       *-generic                      description: Wireless interface
       product: Illegal Vendor ID
       vendor: Illegal Vendor ID
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlp4s0
       version: ff
       serial: 28:56:5a:2b:97:c9
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master vga_palette cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8822be driverversion=4.10.0-041000-generic firmware=N/A latency=255 link=no maxlatency=255 mingnt=255 multicast=yes wireless=IEEE 802.11
       resources: irq:129 ioport:d000(size=256) memory:ec100000-ec10ffff
  *-network
       description: Ethernet interface
       product: Ethernet Connection (4) I219-V
       vendor: Intel Corporation
       physical id: 1f.6
       bus info: pci@0000:00:1f.6
       logical name: enp0s31f6
       version: 21
       serial: 54:e1:ad:1f:de:57
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=full firmware=0.1-4 ip=192.168.1.108 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:122 memory:ec200000-ec21ffff

```

---

### Post by chili555 on 2017-07-16
Any clues in the log?```
cat /var/log/syslog | grep -i -e wlp -e dns
```If the output is null or sparse, also try:```
cat /var/log/syslog[COLOR="#FF0000"].1[/COLOR] | grep -i -e wlp -e dns
```

---

### Post by simoncks1994 on 2017-07-17
```
[COLOR=#000000][FONT=&amp]cat /var/log/syslog[/FONT][/COLOR][COLOR=#FF0000][FONT=&amp].1[/FONT][/COLOR][COLOR=#000000][FONT=&amp] | grep -i -e wlp -e dns[/FONT][/COLOR]
```
gives the following response - 

```
Jul 17 15:57:33 simon-ThinkPad-T470 NetworkManager[11778]: <warn>  [1500278253.1037] device (wlp4s0): re-acquiring supplicant interface (#5).Jul 17 15:57:33 simon-ThinkPad-T470 wpa_supplicant[1332]: Could not set interface wlp4s0 flags (UP): Operation not permitted
Jul 17 15:57:33 simon-ThinkPad-T470 wpa_supplicant[1332]: nl80211: Could not set interface 'wlp4s0' UP
Jul 17 15:57:33 simon-ThinkPad-T470 wpa_supplicant[1332]: nl80211: deinit ifname=wlp4s0 disabled_11b_rates=0
Jul 17 15:57:33 simon-ThinkPad-T470 wpa_supplicant[1332]: Could not set interface wlp4s0 flags (UP): Operation not permitted
Jul 17 15:57:33 simon-ThinkPad-T470 wpa_supplicant[1332]: WEXT: Could not set interface 'wlp4s0' UP
Jul 17 15:57:33 simon-ThinkPad-T470 wpa_supplicant[1332]: wlp4s0: Failed to initialize driver interface
Jul 17 15:57:33 simon-ThinkPad-T470 NetworkManager[11778]: <error> [1500278253.1057] sup-iface[0x25924b0,wlp4s0]: error adding interface: wpa_supplicant couldn't grab this interface.
Jul 17 15:57:33 simon-ThinkPad-T470 NetworkManager[11778]: <info>  [1500278253.1058] device (wlp4s0): supplicant interface state: starting -> down
Jul 17 15:57:33 simon-ThinkPad-T470 NetworkManager[11778]: <info>  [1500278253.1058] device (wlp4s0): supplicant interface keeps failing, giving up

```

---

### Post by praseodym on 2017-07-17
I cannot compile the github driver here, so no statement on this.

On the Realtek HP I only find the Win drivers:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=62&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=62&Level=5&Conn=4&DownTypeID=3&GetDown=false)

Maybe trying Ndiswrapper?!

Edit: Please also show

```
dmesg | grep rtl
```

---

### Post by simoncks1994 on 2017-07-17
Thanks everyone. I am happy to provide more information.

```
[COLOR=#000000][FONT=&amp]dmesg | grep rtl[/FONT][/COLOR]
[   10.318128] Bluetooth: hci0: rtl: examining hci_ver=07 hci_rev=000b lmp_ver=07 lmp_subver=8822[   10.318129] Bluetooth: hci0: rtl: loading rtl_bt/rtl8822b_config.bin
[   10.320606] Bluetooth: hci0: rtl: loading rtl_bt/rtl8822b_fw.bin
[   10.405202] rtlwifi: loading out-of-tree module taints kernel.
[   10.405269] rtlwifi: module verification failed: signature and/or required key missing - tainting kernel
[   10.470724] rtl8822be 0000:04:00.0: enabling device (0000 -> 0003)
[   10.489713] rtl8822be: Using firmware rtlwifi/rtl8822befw.bin
[   10.499464] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   10.499675] rtlwifi: rtlwifi: wireless switch is on
[   10.746909] rtl8822be 0000:04:00.0 wlp4s0: renamed from wlan0
[ 3008.799399] rtlwifi: rtlwifi: wireless switch is on
[ 3009.773620] rtl8822be: halmac_init_hal failed
[ 3010.001657] rtl8822be: halmac_init_hal failed
[ 3010.001944] rtl8822be: halmac_init_hal failed
[ 3019.988006] rtl8822be: halmac_init_hal failed
[ 3019.988257] rtl8822be: halmac_init_hal failed
[ 3029.998833] rtl8822be: halmac_init_hal failed
[ 3029.999391] rtl8822be: halmac_init_hal failed
[ 3039.999510] rtl8822be: halmac_init_hal failed
[ 3040.000196] rtl8822be: halmac_init_hal failed
[ 3049.992280] rtl8822be: halmac_init_hal failed
[ 3049.992899] rtl8822be: halmac_init_hal failed
[ 3059.998034] rtl8822be: halmac_init_hal failed
[ 3059.998694] rtl8822be: halmac_init_hal failed
[ 6202.726505] rtlwifi: rtlwifi: wireless switch is on
[ 6203.729052] rtl8822be: halmac_init_hal failed
[ 6203.959058] rtl8822be: halmac_init_hal failed
[ 6203.959999] rtl8822be: halmac_init_hal failed
[ 6213.990747] rtl8822be: halmac_init_hal failed
[ 6213.991615] rtl8822be: halmac_init_hal failed
[ 6223.993583] rtl8822be: halmac_init_hal failed
[ 6223.994306] rtl8822be: halmac_init_hal failed
[ 6233.989168] rtl8822be: halmac_init_hal failed
[ 6233.989489] rtl8822be: halmac_init_hal failed
[ 6243.995984] rtl8822be: halmac_init_hal failed
[ 6243.996557] rtl8822be: halmac_init_hal failed
[ 6253.992773] rtl8822be: halmac_init_hal failed
[ 6253.993057] rtl8822be: halmac_init_hal failed
[ 6595.104277] rtlwifi: rtlwifi: wireless switch is on
[ 6596.054786] rtl8822be: halmac_init_hal failed
[ 6596.287311] rtl8822be: halmac_init_hal failed
[ 6596.287590] rtl8822be: halmac_init_hal failed
[ 6606.997956] rtl8822be: halmac_init_hal failed
[ 6606.998330] rtl8822be: halmac_init_hal failed
[ 6617.000266] rtl8822be: halmac_init_hal failed
[ 6617.000537] rtl8822be: halmac_init_hal failed
[ 6627.004098] rtl8822be: halmac_init_hal failed
[ 6627.004700] rtl8822be: halmac_init_hal failed
[ 6636.996901] rtl8822be: halmac_init_hal failed
[ 6636.997200] rtl8822be: halmac_init_hal failed
[ 6646.996878] rtl8822be: halmac_init_hal failed
[ 6646.997632] rtl8822be: halmac_init_hal failed

```

---

### Post by jeremy31 on 2017-07-17
What does ```
lspci -nn
```
Show as part of your last results for lshw showed illegal vendor ID

---

### Post by simoncks1994 on 2017-07-18
```
lscpi -nn
00:00.0 Host bridge [0600]: Intel Corporation Device [8086:5904] (rev 02)00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:5916] (rev 02)
00:14.0 USB controller [0c03]: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller [8086:9d2f] (rev 21)
00:14.2 Signal processing controller [1180]: Intel Corporation Sunrise Point-LP Thermal subsystem [8086:9d31] (rev 21)
00:16.0 Communication controller [0780]: Intel Corporation Sunrise Point-LP CSME HECI [8086:9d3a] (rev 21)
00:1c.0 PCI bridge [0604]: Intel Corporation Device [8086:9d10] (rev f1)
00:1c.6 PCI bridge [0604]: Intel Corporation Device [8086:9d16] (rev f1)
00:1d.0 PCI bridge [0604]: Intel Corporation Device [8086:9d18] (rev f1)
00:1d.2 PCI bridge [0604]: Intel Corporation Device [8086:9d1a] (rev f1)
00:1f.0 ISA bridge [0601]: Intel Corporation Device [8086:9d58] (rev 21)
00:1f.2 Memory controller [0580]: Intel Corporation Sunrise Point-LP PMC [8086:9d21] (rev 21)
00:1f.3 Audio device [0403]: Intel Corporation Device [8086:9d71] (rev 21)
00:1f.4 SMBus [0c05]: Intel Corporation Sunrise Point-LP SMBus [8086:9d23] (rev 21)
00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (4) I219-V [8086:15d8] (rev 21)
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:b822]
3e:00.0 Non-Volatile memory controller [0108]: Toshiba America Info Systems Device [1179:0115] (rev 01)



```

---

### Post by gerard22 on 2017-11-26
Hi everyone, 

It's just to say that we found a solution for this wifi card using ubuntu 16.04 (the link is in french, [https://forum.ubuntu-fr.org/viewtopic.php?id=2018167](https://forum.ubuntu-fr.org/viewtopic.php?id=2018167) ). Two persons have this card with ubuntu 16.04, the first one can compile with
> sudo apt install build-essential git
git clone [https://github.com/rtlwifi-linux/rtlwifi-next](https://github.com/rtlwifi-linux/rtlwifi-next)
cd rtlwifi-next
make
sudo make install
sudo modprobe rtl8822be
The second can't compile without making a little change in the source code. The change is to add the line
> #define IEEE80211_NUM_BANDS NUM_NL80211_BANDS
in two files: 
----in wifi.h after
> #ifndef __RTL_WIFI_H__
#define __RTL_WIFI_H__
and before #include lines

---in base.c before #include lines

After, we can compile (i used 4.4.0-101) and wifi works.

At this time, bluetooth doesn't work, and wifi doesn't work with ubuntu 17.10. Maybe forks of 
[https://github.com/rtlwifi-linux/rtlwifi-next](https://github.com/rtlwifi-linux/rtlwifi-next)
can solve this problem.

---

### Post by nick-hems on 2017-12-18
I just got this working, it is fairly easy all up (after googling etc.)


 1. Install the latest 4.14 kernel with the driver code, (from the instructions [here]([http://ubuntuhandbook.org/index.php/2017/11/install-linux-kernel-4-14-ubuntu-linux-mint/](http://ubuntuhandbook.org/index.php/2017/11/install-linux-kernel-4-14-ubuntu-linux-mint/)))


        wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.14/linux-headers-4.14.0-041400_4.14.0-041400.201711122031_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.14/linux-headers-4.14.0-041400_4.14.0-041400.201711122031_all.deb)


        wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.14/linux-headers-4.14.0-041400-generic_4.14.0-041400.201711122031_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.14/linux-headers-4.14.0-041400-generic_4.14.0-041400.201711122031_amd64.deb)


        wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.14/linux-image-4.14.0-041400-generic_4.14.0-041400.201711122031_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.14/linux-image-4.14.0-041400-generic_4.14.0-041400.201711122031_amd64.deb)


        sudo dpkg -i linux*.deb


 2. Download the `rtl8822befw.bin` firmware file from [here]([https://github.com/wkennington/linux-firmware/raw/master/rtlwifi/rtl8822befw.bin](https://github.com/wkennington/linux-firmware/raw/master/rtlwifi/rtl8822befw.bin)).


 3. Save it in `/lib/firmware/rtfwifi`.


 4. Reboot.


Enjoy


Please note that this driver is still in staging at the moment, so use at your own risk!

---

### Post by linksskull on 2018-02-22
You are a life-saver!

> **nick-hems said:**
> I just got this working, it is fairly easy all up (after googling etc.)


 1. Install the latest 4.14 kernel with the driver code, (from the instructions [here]([http://ubuntuhandbook.org/index.php/2017/11/install-linux-kernel-4-14-ubuntu-linux-mint/](http://ubuntuhandbook.org/index.php/2017/11/install-linux-kernel-4-14-ubuntu-linux-mint/)))


        wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.14/linux-headers-4.14.0-041400_4.14.0-041400.201711122031_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.14/linux-headers-4.14.0-041400_4.14.0-041400.201711122031_all.deb)


        wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.14/linux-headers-4.14.0-041400-generic_4.14.0-041400.201711122031_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.14/linux-headers-4.14.0-041400-generic_4.14.0-041400.201711122031_amd64.deb)


        wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.14/linux-image-4.14.0-041400-generic_4.14.0-041400.201711122031_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.14/linux-image-4.14.0-041400-generic_4.14.0-041400.201711122031_amd64.deb)


        sudo dpkg -i linux*.deb


 2. Download the `rtl8822befw.bin` firmware file from [here]([https://github.com/wkennington/linux-firmware/raw/master/rtlwifi/rtl8822befw.bin](https://github.com/wkennington/linux-firmware/raw/master/rtlwifi/rtl8822befw.bin)).


 3. Save it in `/lib/firmware/rtfwifi`.


 4. Reboot.


Enjoy


Please note that this driver is still in staging at the moment, so use at your own risk!

---

### Post by fizikz on 2018-02-25
I know this thread is about 16.04, but just to let you know, RTL8822BE works out of the box in 18.04 (alpha daily build), and works quite well. Something to look forward to in the next release.

Just note that Secure Boot needs to be disabled or the driver module won't get loaded, due to missing a required key.

---

### Post by naiibaf on 2018-03-12
worked for me too on Lenovo E480! Thx alot, really really thx!

---

### Post by raymond30031 on 2018-03-13
Hello All,

I have Ubuntu 16.04 with kernel 4.15.8-041508-generic and my secure boot is disabled

Here is my lspci -nnk output
```

04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTL8822BE 802.11a/b/g/n/ac WiFi adapter [10ec:b822] (rev ff)
    Kernel driver in use: r8822be
    Kernel modules: r8822be
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:5066]
    Kernel driver in use: r8169
    Kernel modules: r8169


```

I do not see wifi
or enable wifi under enable networking after clicking the internet symbol on the top right corner

I tried this method and it worked for me before until recently. I had to reinstall my ubuntu due to nvidia driver installation disaster. my id is juichung_kuo in this thread.
[https://askubuntu.com/questions/864066/ubuntu-16-04-wifi-keep-disconnecting](https://askubuntu.com/questions/864066/ubuntu-16-04-wifi-keep-disconnecting)

I also tried these instructions in one of 4.15.x kernet and it worked once, but after reinstalling ubuntu it stopped working and I have not been able to get this to work
> 
[COLOR=#000000]2. Download the `rtl8822befw.bin` firmware file from [here]([/COLOR][https://github.com/wkennington/linux-firmware/raw/master/rtlwifi/rtl8822befw.bin](https://github.com/wkennington/linux-firmware/raw/master/rtlwifi/rtl8822befw.bin)[COLOR=#000000]).[/COLOR]
 
[COLOR=#000000]3. Save it in `/lib/firmware/rtlwifi`.[/COLOR]

[COLOR=#000000]4. Reboot.[/COLOR]


I tried putting the rtl8822befw.bin while the 8821ce is installed and not installed, there was no difference.

For the rtlwifi-next method, i get the following error. At first, I thought it was the same error as the timer error in the endless driver, but the function calls are different.
```

jkuo@jkuo-pc:~/rtlwifi-next$ make
make -C /lib/modules/4.15.8-041508-generic/build M=/home/jkuo/rtlwifi-next modules
make[1]: Entering directory '/usr/src/linux-headers-4.15.8-041508-generic'
Makefile:941: "Cannot use CONFIG_STACK_VALIDATION=y, please install libelf-dev, libelf-devel or elfutils-libelf-devel"
  CC [M]  /home/jkuo/rtlwifi-next/base.o
/home/jkuo/rtlwifi-next/base.c: In function ‘_rtl_init_deferred_work’:
/home/jkuo/rtlwifi-next/base.c:460:2: error: implicit declaration of function ‘setup_timer’ [-Werror=implicit-function-declaration]
  setup_timer(&rtlpriv->works.watchdog_timer,
  ^
/home/jkuo/rtlwifi-next/base.c: In function ‘rtl_check_beacon_key’:
/home/jkuo/rtlwifi-next/base.c:2360:48: warning: ‘ht_cap_ie’ may be used uninitialized in this function [-Wmaybe-uninitialized]
   bcn_key.ht_cap_info = __le16_to_cpu(ht_cap_ie->cap_info);
                                                ^
cc1: some warnings being treated as errors
scripts/Makefile.build:316: recipe for target '/home/jkuo/rtlwifi-next/base.o' failed
make[2]: *** [/home/jkuo/rtlwifi-next/base.o] Error 1
Makefile:1515: recipe for target '_module_/home/jkuo/rtlwifi-next' failed
make[1]: *** [_module_/home/jkuo/rtlwifi-next] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.15.8-041508-generic'
Makefile:100: recipe for target 'all' failed
make: *** [all] Error 2

```

Does anyone have any clue?
Thanks,
JC

---

### Post by camilhord on 2018-03-13
Worked for me too in HP Envy 17t, thanks [**[COLOR=#000000]nick-hems[/COLOR]**]("https://ubuntuforums.org/member.php?u=2035118")!

---

### Post by chili555 on 2018-03-13
> **raymond30031 said:**
> Hello All,

I have Ubuntu 16.04 with kernel 4.15.8-041508-generic and my secure boot is disabled

Here is my lspci -nnk output
```

04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTL8822BE 802.11a/b/g/n/ac WiFi adapter [10ec:b822] (rev ff)
    Kernel driver in use: r8822be
    Kernel modules: r8822be
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:5066]
    Kernel driver in use: r8169
    Kernel modules: r8169


```

I do not see wifi
or enable wifi under enable networking after clicking the internet symbol on the top right corner

I tried this method and it worked for me before until recently. I had to reinstall my ubuntu due to nvidia driver installation disaster. my id is juichung_kuo in this thread.
[https://askubuntu.com/questions/864066/ubuntu-16-04-wifi-keep-disconnecting](https://askubuntu.com/questions/864066/ubuntu-16-04-wifi-keep-disconnecting)

I also tried these instructions in one of 4.15.x kernet and it worked once, but after reinstalling ubuntu it stopped working and I have not been able to get this to work


I tried putting the rtl8822befw.bin while the 8821ce is installed and not installed, there was no difference.

For the rtlwifi-next method, i get the following error. At first, I thought it was the same error as the timer error in the endless driver, but the function calls are different.
```

jkuo@jkuo-pc:~/rtlwifi-next$ make
make -C /lib/modules/4.15.8-041508-generic/build M=/home/jkuo/rtlwifi-next modules
make[1]: Entering directory '/usr/src/linux-headers-4.15.8-041508-generic'
Makefile:941: "Cannot use CONFIG_STACK_VALIDATION=y, please install libelf-dev, libelf-devel or elfutils-libelf-devel"
  CC [M]  /home/jkuo/rtlwifi-next/base.o
/home/jkuo/rtlwifi-next/base.c: In function ‘_rtl_init_deferred_work’:
/home/jkuo/rtlwifi-next/base.c:460:2: error: implicit declaration of function ‘setup_timer’ [-Werror=implicit-function-declaration]
  setup_timer(&rtlpriv->works.watchdog_timer,
  ^
/home/jkuo/rtlwifi-next/base.c: In function ‘rtl_check_beacon_key’:
/home/jkuo/rtlwifi-next/base.c:2360:48: warning: ‘ht_cap_ie’ may be used uninitialized in this function [-Wmaybe-uninitialized]
   bcn_key.ht_cap_info = __le16_to_cpu(ht_cap_ie->cap_info);
                                                ^
cc1: some warnings being treated as errors
scripts/Makefile.build:316: recipe for target '/home/jkuo/rtlwifi-next/base.o' failed
make[2]: *** [/home/jkuo/rtlwifi-next/base.o] Error 1
Makefile:1515: recipe for target '_module_/home/jkuo/rtlwifi-next' failed
make[1]: *** [_module_/home/jkuo/rtlwifi-next] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.15.8-041508-generic'
Makefile:100: recipe for target 'all' failed
make: *** [all] Error 2

```

Does anyone have any clue?
Thanks,
JCPlease try this instead: [https://github.com/lwfinger/rtlwifi_new/archive/extended.zip](https://github.com/lwfinger/rtlwifi_new/archive/extended.zip)

Post back if you need a step-by-step.

---

### Post by raymond30031 on 2018-03-14
> **chili555 said:**
> 
Please try this instead: [https://github.com/lwfinger/rtlwifi_new/archive/extended.zip](https://github.com/lwfinger/rtlwifi_new/archive/extended.zip)

Post back if you need a step-by-step.


So to try this extended.zip, I first sudo make uninstall 8821ce and removed the [COLOR=#000000][I]rtl8822befw.bin from the /lib/firmware/rtlwifi
[/I][/COLOR]Then I make and sudo make install the extended driver

```

jkuo@jkuo-pc:~/Downloads/rtlwifi_new-extended$ sudo make install
[sudo] password for jkuo: 
make -C /lib/modules/4.15.8-041508-generic/build M=/home/jkuo/Downloads/rtlwifi_new-extended modules
make[1]: Entering directory '/usr/src/linux-headers-4.15.8-041508-generic'
Makefile:941: "Cannot use CONFIG_STACK_VALIDATION=y, please install libelf-dev, libelf-devel or elfutils-libelf-devel"
  Building modules, stage 2.
  MODPOST 19 module
make[1]: Leaving directory '/usr/src/linux-headers-4.15.8-041508-generic'
Install rtlwifi SUCCESS

```

After reboot, I get Wifi-Network Device not ready now.
output from lspci -nnk.
I noticed that there are two kernel modules, is the rtl8822be the one installed from the extended?
```

04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTL8822BE 802.11a/b/g/n/ac WiFi adapter [10ec:b822]
	Subsystem: Lenovo Device [17aa:b023]
	Kernel driver in use: r8822be
	Kernel modules: r8822be, rtl8822be
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:5066]
	Kernel driver in use: r8169
	Kernel modules: r8169

```

What should I do now? What information do you need?
should I do a clean install and try the extended driver?
or how do i know if there is a bios update such that the realtek wifi device is whitelisted or not?

Thanks.

---

### Post by chili555 on 2018-03-14
> **raymond30031 said:**
> So to try this extended.zip, I first sudo make uninstall 8821ce and removed the [COLOR=#000000][I]rtl8822befw.bin from the /lib/firmware/rtlwifi
[/I][/COLOR]Then I make and sudo make install the extended driver

```

jkuo@jkuo-pc:~/Downloads/rtlwifi_new-extended$ sudo make install
[sudo] password for jkuo: 
make -C /lib/modules/4.15.8-041508-generic/build M=/home/jkuo/Downloads/rtlwifi_new-extended modules
make[1]: Entering directory '/usr/src/linux-headers-4.15.8-041508-generic'
Makefile:941: "Cannot use CONFIG_STACK_VALIDATION=y, please install libelf-dev, libelf-devel or elfutils-libelf-devel"
  Building modules, stage 2.
  MODPOST 19 module
make[1]: Leaving directory '/usr/src/linux-headers-4.15.8-041508-generic'
Install rtlwifi SUCCESS

```

After reboot, I get Wifi-Network Device not ready now.
output from lspci -nnk.
I noticed that there are two kernel modules, is the rtl8822be the one installed from the extended?
```

04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTL8822BE 802.11a/b/g/n/ac WiFi adapter [10ec:b822]
	Subsystem: Lenovo Device [17aa:b023]
	Kernel driver in use: r8822be
	Kernel modules: r8822be, rtl8822be
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:5066]
	Kernel driver in use: r8169
	Kernel modules: r8169

```

What should I do now? What information do you need?
should I do a clean install and try the extended driver?
or how do i know if there is a bios update such that the realtek wifi device is whitelisted or not?

Thanks.Let's dig a bit deeper. Please run and post:```
lsmod | grep 8822
dmesg | grep 8822
```I'll bet it wants the firmware that you carefully removed!

---

### Post by raymond30031 on 2018-03-15
Hello Chili555,

So after another nvidia driver installation disaster, I reinstalled ubuntu again.
This time I start with a clean slate.
I download the extended and installed it.
I have Wifi network but it is disconnected.

Thanks in advance and here are the outputs

output from lspci -nnk
I believe the extended includes rtl8822be? becuz i can find it under /lib/firmware/rtlwifi
```

04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTL8822BE 802.11a/b/g/n/ac WiFi adapter [10ec:b822] (rev ff)
	Kernel driver in use: r8822be
	Kernel modules: r8822be, rtl8822be
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:5066]
	Kernel driver in use: r8169
	Kernel modules: r8169

```

output from lsmod | grep 8822
```

jkuo@jkuo-pc:~/Downloads$ lsmod | grep 8822
r8822be               851968  0
mac80211              778240  3 rtl_pci,r8822be,rtlwifi
cfg80211              622592  3 mac80211,r8822be,rtlwifi

```

output from dmesg | grep 8822
```

jkuo@jkuo-pc:~/Downloads$ dmesg | grep 8822
[    3.539878] Bluetooth: hci0: rtl: examining hci_ver=07 hci_rev=000b lmp_ver=07 lmp_subver=8822
[    3.539879] Bluetooth: hci0: rtl: loading rtl_bt/rtl8822b_config.bin
[    3.540211] Bluetooth: hci0: rtl: loading rtl_bt/rtl8822b_fw.bin
[    3.568811] r8822be: module is from the staging directory, the quality is unknown, you have been warned.
[    3.589144] r8822be 0000:04:00.0: enabling device (0000 -> 0003)
[    3.618141] r8822be: Using firmware rtlwifi/rtl8822befw.bin
[    3.623287] r8822be: rtlwifi: wireless switch is on
[    3.626627] Modules linked in: rtlwifi(OE+) ghash_clmulni_intel(+) pcbc arc4 snd_hda_codec_hdmi nvidia(POE-) aesni_intel snd_hda_codec_conexant snd_hda_codec_generic r8822be(C) aes_x86_64 crypto_simd glue_helper cryptd snd_hda_intel mac80211 snd_hda_codec intel_cstate snd_hda_core uvcvideo snd_hwdep intel_rapl_perf videobuf2_vmalloc btusb btrtl btbcm snd_seq_midi btintel snd_seq_midi_event bluetooth videobuf2_memops snd_pcm cfg80211 input_leds videobuf2_v4l2 joydev videobuf2_core serio_raw thinkpad_acpi videodev ecdh_generic nvram snd_rawmidi mei_me media intel_pch_thermal mei shpchp wmi snd_seq snd_seq_device snd_timer snd soundcore acpi_pad mac_hid tpm_crb parport_pc ppdev lp parport autofs4 hid_generic usbhid hid i915 i2c_algo_bit drm_kms_helper syscopyarea sysfillrect psmouse sysimgblt sdhci_pci
[    3.633562] phydm_mod: exports duplicate symbol rtl_phydm_get_ops_pointer (owned by r8822be)
[    3.740853] r8822be 0000:04:00.0 wlp4s0: renamed from wlan0
[    7.873519] r8822be: [ERR]Pwr cmd polling timeout!!
[    7.873522] r8822be: [ERR]Pwr cmd offset : 5!!
[    7.873522] r8822be: [ERR]Pwr cmd value : 0!!
[    7.873523] r8822be: [ERR]Pwr cmd msk : 2!!
[    7.873524] r8822be: [ERR]Read offset = 5 value = 2!!
[    7.873524] r8822be: [Err]pwr sub seq parser fail, status = 0x28!
[    7.873526] r8822be: Handle power off cmd error
[    7.896201] r8822be: halmac_init_hal failed
[    7.896315] r8822be: halmac_init_hal failed
[    7.896427] r8822be: halmac_init_hal failed
[    7.896540] r8822be: halmac_init_hal failed
[    7.896652] r8822be: halmac_init_hal failed
[    7.896765] r8822be: halmac_init_hal failed
[    7.896877] r8822be: halmac_init_hal failed
[    7.896990] r8822be: halmac_init_hal failed
[    7.897102] r8822be: halmac_init_hal failed
[    7.897214] r8822be: halmac_init_hal failed
[    7.897264] WARNING: CPU: 2 PID: 130 at /home/kernel/COD/linux/drivers/staging/rtlwifi/rtl8822be/fw.c:239 rtl8822be_fill_h2c_cmd+0x1ac/0x660 [r8822be]
[    7.897264] Modules linked in: rfcomm bnep nls_iso8859_1 intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp wmi_bmof intel_wmi_thunderbolt kvm irqbypass crct10dif_pclmul crc32_pclmul btcoexist(OE) rtl_pci(OE) rtlwifi(OE) ghash_clmulni_intel pcbc arc4 snd_hda_codec_hdmi aesni_intel snd_hda_codec_conexant snd_hda_codec_generic r8822be(C) aes_x86_64 crypto_simd glue_helper cryptd snd_hda_intel mac80211 snd_hda_codec intel_cstate snd_hda_core uvcvideo snd_hwdep intel_rapl_perf videobuf2_vmalloc btusb btrtl btbcm snd_seq_midi btintel snd_seq_midi_event bluetooth videobuf2_memops snd_pcm cfg80211 input_leds videobuf2_v4l2 joydev videobuf2_core serio_raw thinkpad_acpi videodev ecdh_generic nvram snd_rawmidi mei_me media intel_pch_thermal mei shpchp wmi snd_seq snd_seq_device snd_timer snd soundcore
[    7.897320] RIP: 0010:rtl8822be_fill_h2c_cmd+0x1ac/0x660 [r8822be]
[    7.897335]  halbtc_fill_h2c_cmd+0x2f/0x40 [r8822be]
[    7.897342]  halbtc8822b1ant_query_bt_info+0x4c/0xa0 [r8822be]
[    7.897347]  ex_btc8822b1ant_ips_notify+0xb4/0x170 [r8822be]
[    7.897353]  exhalbtc_ips_notify+0x5a/0x60 [r8822be]
[    7.897360]  rtl_btc_ips_notify+0x26/0x50 [r8822be]
[    7.897365]  rtl_ips_nic_on+0xc2/0xe0 [r8822be]
[    7.897369]  rtl_op_config+0x252/0x490 [r8822be]
[   14.452706] r8822be: [ERR]Pwr cmd polling timeout!!
[   14.452715] r8822be: [ERR]Pwr cmd offset : 5!!
[   14.452733] r8822be: [ERR]Pwr cmd value : 0!!
[   14.452734] r8822be: [ERR]Pwr cmd msk : 2!!
[   14.452735] r8822be: [ERR]Read offset = 5 value = 2!!
[   14.452736] r8822be: [Err]pwr sub seq parser fail, status = 0x28!
[   14.452739] r8822be: Handle power off cmd error
[   32.004771] r8822be: halmac_init_hal failed
[   32.004892] r8822be: halmac_init_hal failed
[   32.005006] r8822be: halmac_init_hal failed
[   32.005119] r8822be: halmac_init_hal failed
[   32.005233] r8822be: halmac_init_hal failed
[   32.005348] r8822be: halmac_init_hal failed
[   32.005477] r8822be: halmac_init_hal failed
[   32.005610] r8822be: halmac_init_hal failed
[   32.005735] r8822be: halmac_init_hal failed
[   32.005864] r8822be: halmac_init_hal failed
[   37.733624] r8822be: [ERR]Pwr cmd polling timeout!!
[   37.733627] r8822be: [ERR]Pwr cmd offset : 5!!
[   37.733628] r8822be: [ERR]Pwr cmd value : 0!!
[   37.733628] r8822be: [ERR]Pwr cmd msk : 2!!
[   37.733629] r8822be: [ERR]Read offset = 5 value = 2!!
[   37.733630] r8822be: [Err]pwr sub seq parser fail, status = 0x28!
[   37.733631] r8822be: Handle power off cmd error
[   65.206051] r8822be: halmac_init_hal failed
[   65.206186] r8822be: halmac_init_hal failed
[   65.206316] r8822be: halmac_init_hal failed
[   65.206447] r8822be: halmac_init_hal failed
[   65.206579] r8822be: halmac_init_hal failed
[   65.206708] r8822be: halmac_init_hal failed
[   65.206837] r8822be: halmac_init_hal failed
[   65.206966] r8822be: halmac_init_hal failed
[   65.207095] r8822be: halmac_init_hal failed
[   65.207224] r8822be: halmac_init_hal failed
[   71.082613] r8822be: [ERR]Pwr cmd polling timeout!!
[   71.082623] r8822be: [ERR]Pwr cmd offset : 5!!
[   71.082627] r8822be: [ERR]Pwr cmd value : 0!!
[   71.082630] r8822be: [ERR]Pwr cmd msk : 2!!
[   71.082634] r8822be: [ERR]Read offset = 5 value = 2!!
[   71.082637] r8822be: [Err]pwr sub seq parser fail, status = 0x28!
[   71.082641] r8822be: Handle power off cmd error
[  108.199825] r8822be: halmac_init_hal failed
[  108.199960] r8822be: halmac_init_hal failed
[  108.200090] r8822be: halmac_init_hal failed
[  108.200219] r8822be: halmac_init_hal failed
[  108.200348] r8822be: halmac_init_hal failed
[  108.200477] r8822be: halmac_init_hal failed
[  108.200606] r8822be: halmac_init_hal failed
[  108.200735] r8822be: halmac_init_hal failed
[  108.200864] r8822be: halmac_init_hal failed
[  108.200993] r8822be: halmac_init_hal failed
[  114.081170] r8822be: [ERR]Pwr cmd polling timeout!!
[  114.081178] r8822be: [ERR]Pwr cmd offset : 5!!
[  114.081182] r8822be: [ERR]Pwr cmd value : 0!!
[  114.081185] r8822be: [ERR]Pwr cmd msk : 2!!
[  114.081189] r8822be: [ERR]Read offset = 5 value = 2!!
[  114.081192] r8822be: [Err]pwr sub seq parser fail, status = 0x28!
[  114.081196] r8822be: Handle power off cmd error
[  161.203168] r8822be: halmac_init_hal failed
[  161.203307] r8822be: halmac_init_hal failed
[  161.203438] r8822be: halmac_init_hal failed
[  161.203567] r8822be: halmac_init_hal failed
[  161.203724] r8822be: halmac_init_hal failed
[  161.203853] r8822be: halmac_init_hal failed
[  161.203982] r8822be: halmac_init_hal failed
[  161.204111] r8822be: halmac_init_hal failed
[  161.204239] r8822be: halmac_init_hal failed
[  161.204367] r8822be: halmac_init_hal failed
[  167.096064] r8822be: [ERR]Pwr cmd polling timeout!!
[  167.096077] r8822be: [ERR]Pwr cmd offset : 5!!
[  167.096081] r8822be: [ERR]Pwr cmd value : 0!!
[  167.096086] r8822be: [ERR]Pwr cmd msk : 2!!
[  167.096090] r8822be: [ERR]Read offset = 5 value = 2!!
[  167.096094] r8822be: [Err]pwr sub seq parser fail, status = 0x28!
[  167.096099] r8822be: Handle power off cmd error
[  224.198486] r8822be: halmac_init_hal failed
[  224.198607] r8822be: halmac_init_hal failed
[  224.198724] r8822be: halmac_init_hal failed
[  224.198840] r8822be: halmac_init_hal failed
[  224.198957] r8822be: halmac_init_hal failed
[  224.199074] r8822be: halmac_init_hal failed
[  224.199190] r8822be: halmac_init_hal failed
[  224.199307] r8822be: halmac_init_hal failed
[  224.199424] r8822be: halmac_init_hal failed
[  224.199540] r8822be: halmac_init_hal failed
[  230.082378] r8822be: [ERR]Pwr cmd polling timeout!!
[  230.082386] r8822be: [ERR]Pwr cmd offset : 5!!
[  230.082390] r8822be: [ERR]Pwr cmd value : 0!!
[  230.082393] r8822be: [ERR]Pwr cmd msk : 2!!
[  230.082396] r8822be: [ERR]Read offset = 5 value = 2!!
[  230.082400] r8822be: [Err]pwr sub seq parser fail, status = 0x28!
[  230.082403] r8822be: Handle power off cmd error
[  287.199089] r8822be: halmac_init_hal failed
[  287.199225] r8822be: halmac_init_hal failed
[  287.199357] r8822be: halmac_init_hal failed
[  287.199489] r8822be: halmac_init_hal failed
[  287.199619] r8822be: halmac_init_hal failed
[  287.199747] r8822be: halmac_init_hal failed
[  287.199876] r8822be: halmac_init_hal failed
[  287.200038] r8822be: halmac_init_hal failed
[  287.200169] r8822be: halmac_init_hal failed
[  287.200305] r8822be: halmac_init_hal failed
[  293.080234] r8822be: [ERR]Pwr cmd polling timeout!!
[  293.080242] r8822be: [ERR]Pwr cmd offset : 5!!
[  293.080246] r8822be: [ERR]Pwr cmd value : 0!!
[  293.080249] r8822be: [ERR]Pwr cmd msk : 2!!
[  293.080253] r8822be: [ERR]Read offset = 5 value = 2!!
[  293.080256] r8822be: [Err]pwr sub seq parser fail, status = 0x28!
[  293.080260] r8822be: Handle power off cmd error
[  350.201205] r8822be: halmac_init_hal failed
[  350.201340] r8822be: halmac_init_hal failed
[  350.201469] r8822be: halmac_init_hal failed
[  350.201598] r8822be: halmac_init_hal failed
[  350.201727] r8822be: halmac_init_hal failed
[  350.201856] r8822be: halmac_init_hal failed
[  350.201984] r8822be: halmac_init_hal failed
[  350.202113] r8822be: halmac_init_hal failed
[  350.202242] r8822be: halmac_init_hal failed
[  350.202371] r8822be: halmac_init_hal failed
[  356.106919] r8822be: [ERR]Pwr cmd polling timeout!!
[  356.106929] r8822be: [ERR]Pwr cmd offset : 5!!
[  356.106933] r8822be: [ERR]Pwr cmd value : 0!!
[  356.106936] r8822be: [ERR]Pwr cmd msk : 2!!
[  356.106940] r8822be: [ERR]Read offset = 5 value = 2!!
[  356.106943] r8822be: [Err]pwr sub seq parser fail, status = 0x28!
[  356.106947] r8822be: Handle power off cmd error
[  413.201983] r8822be: halmac_init_hal failed
[  413.202118] r8822be: halmac_init_hal failed
[  413.202248] r8822be: halmac_init_hal failed
[  413.202376] r8822be: halmac_init_hal failed
[  413.202505] r8822be: halmac_init_hal failed
[  413.202634] r8822be: halmac_init_hal failed
[  413.202762] r8822be: halmac_init_hal failed
[  413.202891] r8822be: halmac_init_hal failed
[  413.203019] r8822be: halmac_init_hal failed
[  413.203147] r8822be: halmac_init_hal failed
[  419.105505] r8822be: [ERR]Pwr cmd polling timeout!!
[  419.105514] r8822be: [ERR]Pwr cmd offset : 5!!
[  419.105518] r8822be: [ERR]Pwr cmd value : 0!!
[  419.105521] r8822be: [ERR]Pwr cmd msk : 2!!
[  419.105525] r8822be: [ERR]Read offset = 5 value = 2!!
[  419.105528] r8822be: [Err]pwr sub seq parser fail, status = 0x28!
[  419.105532] r8822be: Handle power off cmd error
[  476.207841] r8822be: halmac_init_hal failed
[  476.207977] r8822be: halmac_init_hal failed
[  476.208107] r8822be: halmac_init_hal failed
[  476.208240] r8822be: halmac_init_hal failed
[  476.208398] r8822be: halmac_init_hal failed
[  476.208529] r8822be: halmac_init_hal failed
[  476.208660] r8822be: halmac_init_hal failed
[  476.208789] r8822be: halmac_init_hal failed
[  476.208918] r8822be: halmac_init_hal failed
[  476.209047] r8822be: halmac_init_hal failed
[  482.132389] r8822be: [ERR]Pwr cmd polling timeout!!
[  482.132398] r8822be: [ERR]Pwr cmd offset : 5!!
[  482.132402] r8822be: [ERR]Pwr cmd value : 0!!
[  482.132405] r8822be: [ERR]Pwr cmd msk : 2!!
[  482.132409] r8822be: [ERR]Read offset = 5 value = 2!!
[  482.132412] r8822be: [Err]pwr sub seq parser fail, status = 0x28!
[  482.132415] r8822be: Handle power off cmd error
[  539.200806] r8822be: halmac_init_hal failed
[  539.200947] r8822be: halmac_init_hal failed
[  539.201080] r8822be: halmac_init_hal failed
[  539.201211] r8822be: halmac_init_hal failed
[  539.201339] r8822be: halmac_init_hal failed
[  539.201468] r8822be: halmac_init_hal failed
[  539.201597] r8822be: halmac_init_hal failed
[  539.201726] r8822be: halmac_init_hal failed
[  539.201854] r8822be: halmac_init_hal failed
[  539.201983] r8822be: halmac_init_hal failed
[  545.070367] r8822be: [ERR]Pwr cmd polling timeout!!
[  545.070376] r8822be: [ERR]Pwr cmd offset : 5!!
[  545.070380] r8822be: [ERR]Pwr cmd value : 0!!
[  545.070384] r8822be: [ERR]Pwr cmd msk : 2!!
[  545.070387] r8822be: [ERR]Read offset = 5 value = 2!!
[  545.070391] r8822be: [Err]pwr sub seq parser fail, status = 0x28!
[  545.070394] r8822be: Handle power off cmd error
[  602.204925] r8822be: halmac_init_hal failed
[  602.205068] r8822be: halmac_init_hal failed
[  602.205200] r8822be: halmac_init_hal failed
[  602.205333] r8822be: halmac_init_hal failed
[  602.205462] r8822be: halmac_init_hal failed
[  602.205590] r8822be: halmac_init_hal failed
[  602.205719] r8822be: halmac_init_hal failed
[  602.205848] r8822be: halmac_init_hal failed
[  602.205976] r8822be: halmac_init_hal failed
[  602.206105] r8822be: halmac_init_hal failed
[  608.176556] r8822be: [ERR]Pwr cmd polling timeout!!
[  608.176565] r8822be: [ERR]Pwr cmd offset : 5!!
[  608.176569] r8822be: [ERR]Pwr cmd value : 0!!
[  608.176572] r8822be: [ERR]Pwr cmd msk : 2!!
[  608.176576] r8822be: [ERR]Read offset = 5 value = 2!!
[  608.176579] r8822be: [Err]pwr sub seq parser fail, status = 0x28!
[  608.176583] r8822be: Handle power off cmd error



```

---

### Post by chili555 on 2018-03-15
This may be helpful: [https://bugzilla.redhat.com/show_bug.cgi?id=1464731](https://bugzilla.redhat.com/show_bug.cgi?id=1464731) Especially see comment #20.

Does your version of the driver have the quoted parameter?```
modinfo r8822be | grep parm
```Is one of the parameters aspm? If so, try the suggested change:```
sudo modprobe -r r8822be
sudo modprobe r8822be aspm=0
```Any improvement? If so, let's make it persistent.```
sudo -i 
echo "options r8822be aspm=0"  >  /etc/modprobe.d/r8822be.conf
exit
```

---

### Post by raymond30031 on 2018-03-15
Yes there is a param aspm.
I couldn't do ```
[COLOR=#000000][FONT=&amp]sudo modprobe -r r8822be [/FONT][/COLOR]
``` because it was being used.
so I blacklist it and reboot
I checked lspci -nnk and see the other driver is being used
```

04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTL8822BE 802.11a/b/g/n/ac WiFi adapter [10ec:b822] (rev ff)
    Kernel driver in use: rtl8822be
    Kernel modules: r8822be, rtl8822be

```

Then I get the following error
```

jkuo@jkuo-pc:~$ sudo modprobe r8822be aspm=0
modprobe: ERROR: could not insert 'r8822be': Exec format error



```

---

### Post by raymond30031 on 2018-03-15
@chili555

It works now, I just assumed that the option works and did your suggestion
```

sudo -i 
echo "options r8822be aspm=0"  >  /etc/modprobe.d/r8822be.conf
exit
```

and i get wifi 

Thank you so much.

---

### Post by chili555 on 2018-03-15
> **raymond30031 said:**
> @chili555

It works now, I just assumed that the option works and did your suggestion
```

sudo -i 
echo "options r8822be aspm=0"  >  /etc/modprobe.d/r8822be.conf
exit
```

and i get wifi 

Thank you so much.
Awesome! Glad to hear that it's now working.

------------------------------

Note to searchers: raymond30031 is using the r8822be driver that is built-in to his 4.15.8-041508-generic kernel; not the compiled driver. If you are using the default Ubuntu kernel version, 4.13.0-xx as of this writing, this fix probably doesn't apply to you. If in doubt, post a new thread and ask us for help.

---

### Post by sergiosierram on 2018-03-21
This also worked for me!!

I have an HP laptop by OMEN.

> **nick-hems said:**
> I just got this working, it is fairly easy all up (after googling etc.)


 1. Install the latest 4.14 kernel with the driver code, (from the instructions [here]([http://ubuntuhandbook.org/index.php/2017/11/install-linux-kernel-4-14-ubuntu-linux-mint/](http://ubuntuhandbook.org/index.php/2017/11/install-linux-kernel-4-14-ubuntu-linux-mint/)))


        wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.14/linux-headers-4.14.0-041400_4.14.0-041400.201711122031_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.14/linux-headers-4.14.0-041400_4.14.0-041400.201711122031_all.deb)


        wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.14/linux-headers-4.14.0-041400-generic_4.14.0-041400.201711122031_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.14/linux-headers-4.14.0-041400-generic_4.14.0-041400.201711122031_amd64.deb)


        wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.14/linux-image-4.14.0-041400-generic_4.14.0-041400.201711122031_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.14/linux-image-4.14.0-041400-generic_4.14.0-041400.201711122031_amd64.deb)


        sudo dpkg -i linux*.deb


 2. Download the `rtl8822befw.bin` firmware file from [here]([https://github.com/wkennington/linux-firmware/raw/master/rtlwifi/rtl8822befw.bin](https://github.com/wkennington/linux-firmware/raw/master/rtlwifi/rtl8822befw.bin)).


 3. Save it in `/lib/firmware/rtfwifi`.


 4. Reboot.


Enjoy


Please note that this driver is still in staging at the moment, so use at your own risk!

---

### Post by signitary on 2018-04-25
None of these solutions worked for me. My machine is an HP Envy x360 Convertible 15z-bq100 running Ubuntu Xenial. I was able to get the wifi working by installing a development environment, downloading a github project, making and installing the result, thus:

sudo apt update
sudo apt install git gcc g++ build-essential
git clone [https://github.com/synthtc/rtlwifi-next.git](https://github.com/synthtc/rtlwifi-next.git)
cd rtlwifi-next
sudo make
sudo make install
sudo modprobe -av rtl8822be
reboot

---

### Post by seymar2 on 2018-05-06
None of the things above worked for me:
Motherboard: ASUS ROG STRIX X370-I, RTL8822BE connected via USB (internal)

The newest kernel version >4.17-rc3 now has support for the RTL8822BE chip.
[http://kernel.org/](http://kernel.org/)

---

### Post by sailee1811dalvi on 2018-07-23
The main repo at [https://github.com/rtlwifi-linux/rtlwifi-next](https://github.com/rtlwifi-linux/rtlwifi-next) did not compile. I used [https://github.com/synthtc/rtlwifi-next](https://github.com/synthtc/rtlwifi-next) which was one commit ahead and compiled.
Now Fedora recognizes the wireless device. We can also list the networks around us using lsmod.

Use the below commands to fix this issue:

 [CENTER]$ git clone [https://github.com/synthtc/rtlwifi-next](https://github.com/synthtc/rtlwifi-next)
$ cd rtlwifi-next
$ make
$ sudo make install
$ sudo modprobe rtl8822be
[/CENTER]

---

### Post by sailee1811dalvi on 2018-07-23
The main repo at [https://github.com/rtlwifi-linux/rtlwifi-next](https://github.com/rtlwifi-linux/rtlwifi-next) did not compile. I used [https://github.com/synthtc/rtlwifi-next](https://github.com/synthtc/rtlwifi-next) which was one commit ahead and compiled.
Now Fedora recognizes the wireless device. We can also list the networks around us using lsmod.
Use the below commands to fix this issue:
 $ git clone [https://github.com/synthtc/rtlwifi-next](https://github.com/synthtc/rtlwifi-next)
$ cd rtlwifi-next
$ make
$ sudo make install
$ sudo modprobe rtl8822be

---

### Post by kody11 on 2018-08-19
> **chili555 said:**
> Any improvement? If so, let's make it persistent.```
sudo -i 
echo "options r8822be aspm=0"  >  /etc/modprobe.d/r8822be.conf
exit
```

@chili555 thank you for this! I have an Hp Probook 430 G5 that I just bought and installed Ubuntu 18.04.1 LTS and this worked to get the wifi to show.... super odd.

Here was the wireless script that I ran before I updated it: [http://pastebin.ubuntu.com/p/ZrMqrDqmp4/](http://pastebin.ubuntu.com/p/ZrMqrDqmp4/)

Shouldnt this have been fixed in this version of Ubuntu by now (via the bug report you linked to originally)? 

Last, what is aspm anyways, and what does setting it to 0 actually do if you dont mind me asking?

---

### Post by chili555 on 2018-08-20
> Shouldnt this have been fixed in this version of Ubuntu by now (via the bug report you linked to originally)? 

Last, what is aspm anyways, and what does setting it to 0 actually do if you dont mind me asking?Please see:  [https://en.wikipedia.org/wiki/Active_State_Power_Management](https://en.wikipedia.org/wiki/Active_State_Power_Management) and also:[https://wireless.wiki.kernel.org/en/users/documentation/aspm](https://wireless.wiki.kernel.org/en/users/documentation/aspm) As you can see, part of the process depends on correct implementation in the BIOS:> ASPM should automatically be negotiated by the BIOS based on all the endpoints connected on a root complex. IF your device has ASPM disabled it is likely because:

* the BIOS determined that needed to happen
* PCIE requires ASPM but L0s is optional so you might have L0s disabled and only L1 enabled
* you have a buggy BIOS
* you have no BIOS and your systems programmers didn't address ASPM yetSo, even if the bug has been addressed, the BIOS may not yet respond correctly. I suspect the BIOS is why some of the posters above get the device working with aspm=0 and many others don't need it, or, if they did, they didn't mention it.

I was also struck by this:> Testing on battery lifetime shows that the difference between having L1 and L1/L0s both could at max save up to five minutes of battery life in the best possible scenario Yes, I agree that we should all save energy every place possible, but ASPM seems to me to be a barely working technology, if your BIOS is just perfect, if the wind is coming from the east and if you have a rabbit's foot in your left pocket that saves....get this!...FIVE minutes.

In my opinion, if it gets your wireless working, switch it off and don't look back.

---

### Post by faaldovahkiin on 2018-09-30
This worked on my HP omen 15-dc0030nr. I went through a lot of threads but nothing seemed to work, but thanks to you guys who dug the hell out of this problem, finally my RTL8822be is working.

---

### Post by batman-with-a-gun on 2019-08-17
[SIZE=2][FONT=arial]Hello everyone!
Chili555's solution from thread [https://ubuntuforums.org/showthread.php?t=862651](https://ubuntuforums.org/showthread.php?t=862651) worked for me just fine.
Execute following:[/FONT][/SIZE]

[FONT=courier new]sudo apt-get update
sudo apt-get install b43-fwcutter[/FONT]

[SIZE=2][FONT=arial]Then restart your laptop and the wifi networks will show up.[/FONT][/SIZE]

---

### Post by chili555 on 2019-08-17
> **batman-with-a-gun said:**
> [SIZE=2][FONT=arial]Hello everyone!
Chili555's solution from thread [https://ubuntuforums.org/showthread.php?t=862651](https://ubuntuforums.org/showthread.php?t=862651) worked for me just fine.
Execute following:[/FONT][/SIZE]

[FONT=courier new]sudo apt-get update
sudo apt-get install b43-fwcutter[/FONT]

[SIZE=2][FONT=arial]Then restart your laptop and the wifi networks will show up.[/FONT][/SIZE]Then yours is not an rtl8822be device, the subject of this thread. You must have a Broadcom.

---

### Post by QIII on 2019-08-17
And, with that, closed.

RIP old thread.

---

