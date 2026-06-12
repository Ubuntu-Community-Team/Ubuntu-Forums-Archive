---
title: "Dell Wireless Mini 1390 on Dell D820/Ubuntu 6.10"
date: 2006-10-31
forum: Networking &amp; Wireless
---

### Post by Jan Hrbacek on 2006-10-31
I am very happy with Ubuntu 6.10, but one think is driving me crazy. I have a wireless DELL 1390 and cannot make it to work. Previously, I have been using Fedora Core 5 and there I managed to make it work via ndiswrapper.

THIS IS WHAT I GET AFTER INSTALLING NDISWRAPPER:

jan@electron:~/drivers$ tail /var/log/messages
Oct 28 19:19:47 electron kernel: [17182411.292000] sd 5:0:0:0: Attached scsi generic sg2 type 0
Oct 28 19:24:03 electron kernel: [17182666.512000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
Oct 28 19:24:03 electron kernel: [17182666.584000] ndiswrapper: driver bcmwl5 (Broadcom,11/02/2005, 4.10.40.0) loaded
Oct 28 19:24:03 electron kernel: [17182666.584000] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 177
Oct 28 19:24:03 electron kernel: [17182666.592000] ndiswrapper: using irq 177
Oct 28 19:24:03 electron kernel: [17182667.308000] wlan0: vendor: ''
Oct 28 19:24:03 electron kernel: [17182667.308000] wlan0: ethernet device 00:16:cf:12:78:27 using NDIS driver bcmwl5, 14E4:4312.5.conf
Oct 28 19:24:03 electron kernel: [17182667.308000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Oct 28 19:24:03 electron kernel: [17182667.312000] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
Oct 28 19:24:03 electron kernel: [17182667.360000] ADDRCONF(NETDEV_UP): eth1: link is not ready


OTHER INFORMATION ABOUT WIRELESS:

*-network
                description: Wireless interface
                product: BCM4310 UART
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0c:00.0
                logical name: eth1
                version: 01
                serial: 00:16:cf:12:78:27
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ndiswrapper driverversion=1.22 firmware=Broadcom,11/02/2005, 4.10.40.0 link=no multicast=yes wireless=IEEE 802.11g
                resources: iomemory:dcffc000-dcffffff irq:177

0c:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 01)
        Subsystem: Dell Unknown device 0007
        Flags: bus master, fast devsel, latency 0, IRQ 177
        Memory at dcffc000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

0c:00.0 0280: 14e4:4312 (rev 01)


MY WPA_SUPPLICANT SETTING:

network={
        bssid=00:c0:49:f3:c3:02
        scan_ssid=1
        auth_alg=OPEN
        ssid=4361726c6f
        key_mgmt=WPA-PSK
        proto=WPA
        pairwise=TKIP
        group=TKIP
        psk=********
        }


DUMP FROM WPA_SUPPLICANT:

jan@electron:~$ sudo wpa_supplicant -ieth1 -c/etc/wpa_supplicant.conf -dd -Dndiswrapper
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ndiswrapper' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Line: 4 - start of a new network block
BSSID - hexdump(len=6): 00 c0 49 f3 c3 02
scan_ssid=1 (0x1)
auth_alg: 0x1
ssid - hexdump_ascii(len=5):
     43 61 72 6c 6f                                    Carlo           
key_mgmt: 0x2
proto: 0x1
pairwise: 0x8
group: 0x8
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='Carlo'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=20 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:16:cf:12:78:27
Driver does not support WPA.
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
Setting scan request: 0 sec 100000 usec
Added interface eth1
Wireless event: cmd=0x8b06 len=8
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=5):
     43 61 72 6c 6f                                    Carlo           
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 258 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
0: 00:13:49:16:14:15 ssid='Studifisk' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 0 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
No suitable AP found.
Setting scan request: 5 sec 0 usec
CTRL-EVENT-TERMINATING - signal 2 received
Removing interface eth1
State: SCANNING -> DISCONNECTED
WEXT: Operstate: linkmode=-1, operstate=5
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Failed to disable WPA in the driver.
No keys have been configured - skip key clearing
WEXT: Operstate: linkmode=0, operstate=6
Cancelling scan request


Obviously, I encounter some problems on hardware level. Notice the line eth1: link is not ready in /etc/tail/messages after ndiswrapper is installed. 

When I do ifconfig, I sometimes I cannot see eth1. When I do iwconfig, I can see eth1 all the time. However, I cannot set any parameter to it, such as essid or ap. If I do dmesg immediatelly after trying to set some parameter to it, I get a new line eth1: link is not ready.

If I try to lshw | grep network, I get *-network DISABLED in the dump.

If I try to bring eth1 up using ifconfig eth1 up, it becomes present again in the ifconfig dump and "DISABLED" disappears from lshw dump. However, if I try to change any parameter through iwconfig or to run wpa_supplicant, it becomes disabled again.

As I installed Ubuntu 6.10, led signalizing that wifi is enabled was off. After installing ndiswrapper it is on.

Dell offers on its web page many different drivers for this card - for different regions and of different dates. I have chosen the most recent for Europe.

What also confuses me that is is being listed in lshw dump as Broadcom, even though it is Dell Wireless 1390. 

Any tip, where to go from here? I think the most crucial is the line eth1: link is not ready that I get in lshw after installing the ndiswrapper.

However, I do not get how is it possible that I can bring wifi up and when I run wpa_supplicant it obviously scans aps. To make it more complicated unfortunately I have to connect to WPA with hidden ssid. This one I do not see in the list of scanned aps whatsoever...

Thank you for your feedback.

---

### Post by -Chi.0 on 2006-10-31
Check this link for help w/ NdisWrapper on Edgy
[http://ubuntuforums.org/showthread.php?p=1692550#post1692550]("http://ubuntuforums.org/showthread.php?p=1692550#post1692550")

---

### Post by Jan Hrbacek on 2006-10-31
Is this really related to me? I have version 1.22 installed.

driver=ndiswrapper driverversion=1.22

---

### Post by Jan Hrbacek on 2006-10-31
I have checked it. All four ndiswrapper packages included on instalation CD are installed... obviously, this is not the case. I only wonder, why is it detected as version 1.2, when in Package Manager I see version 1.18...

I didn't know there is ndiswrapper included in Ubuntu. I have first tried to compile my own from code downloaded from ndiswrapper webpage. However, I had problems with proceeding it correctly and later I found out I can install the package from Ubuntu 6.10 CD. 

Is it that there is some fragment of the unsucessful instalation of ndiswrapper from source? How do I remove it?

---

### Post by Jan Hrbacek on 2006-10-31
I have contacted Dell support. I really have Dell Wireless 1490 Minicard and I do have a proper driver for it.

I have reinstalled Ubuntu and started from the scratch (reformated system partition).
I have successfully installed ndiswrapper included on install CD.

I see eth1 with ifconfig and also iwconfig.

Still I do not understand why is version of ndiswrapper is announced as version 1.22...

Obviously link is not ready message is not a big deal
[http://linux.derkeiler.com/Mailing-Lists/Debian/2006-04/msg02288.html](http://linux.derkeiler.com/Mailing-Lists/Debian/2006-04/msg02288.html)

Why can't I change thinks using iwconfig???

---

### Post by sarmadzhiev on 2006-11-07
I have the same card with similar problem (not working).
Actually I manage to make it work for awhile but then it is failing. 

To make ndiswrapper work, first remove the bcm43xx driver that is loading automatically and capture the card. I do it with modprobe -r bcm43xx since I do not know better way to handle it. Then remove ndiswrapper with 'modprobe -r ndiswrapper' and then ifdown eth1 and ifdup eth1. Now it is working for me  for a awhile. (which mean few minutes to an hour). 
What is happened after that is the kernel stoppeds IRQ 177 (the one ndiswrapper staying) and then everything go south. Restart the machine, fixing it. 

I am really out of ideas what to do next. May be recompiling the kernel without bcm43xx seems as an option. 
anyway if anyone have an idea what to do to prevent loading bcm43xx module without recompiling is more then welcome to come up. 

the second problem is with IRQ 177 that is stopped from the kernel. 

Thx
Nikolay

P.S. I cutted the firmware from the driver for bcm43xx and put it in /lib/modules/<kernel>/firmware but it is not working for my computer. 
May be in the newer kernel it will be supported. 
the BCM card version is 4311 which is not supported currently on bcm43xx.berlios.de

---

