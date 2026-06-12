---
title: "Wireless does'nt work at X40"
date: 2006-08-13
forum: Networking &amp; Wireless
---

### Post by higepon on 2006-08-13
I installed Ubuntu Dapper on my Thinkpad X40.
But wireless doesn't work.

Here is the result of ifconfig
% ifconfig
ath0      Link encap:Ethernet  HWaddr 00:0E:9B:90:9B:A9
          inet6 addr: fe80::20e:9bff:fe90:9ba9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:1 dropped:0 overruns:0 frame:1
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:209 Memory:f8b20000-f8b30000

eth0      Link encap:Ethernet  HWaddr 00:0A:E4:2F:B1:2B
          inet addr:192.168.11.4  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e4ff:fe2f:b12b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3766 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3700 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:3095708 (2.9 MiB)  TX bytes:603761 (589.6 KiB)
          Base address:0x7000 Memory:d0220000-d0240000

Here is the result of iwconfig:

% iwconfig
lo        no wireless extensions.

irda0     no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11  ESSID:""
          Mode:Managed  Frequency:2.442 GHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

I entered my ESSID and WEP key, but it doesn't work.
Any help would be appreciated.

---

### Post by meng on 2006-08-13
How did you enter the ESSID and WEP key? From the command-line or through the GUI?

---

### Post by stormblue on 2006-08-13
Try this:

```
sudo ifconfig ath0 up
sudo iwconfig ath0 essid Networkname
sudo iwconfig ath0 key XXXXXXXXXXXXXX
sudo dhclient ath0
```

---

### Post by higepon on 2006-08-13
> **stormblue said:**
> Try this:

```
sudo ifconfig ath0 up
sudo iwconfig ath0 essid Networkname
sudo iwconfig ath0 key XXXXXXXXXXXXXX
sudo dhclient ath0
```

Thank you for your replay.
The result is 
nobita% sudo ifconfig ath0 up Password:
nobita% sudo iwconfig ath0 essid 000D0xxxxxx
nobita% sudo iwconfig ath0 key "s:mypassword"
nobita% sudo dhclient ath0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/ath0/00:0e:9b:90:9b:a9
Sending on   LPF/ath0/00:0e:9b:90:9b:a9
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by stormblue on 2006-08-13
Try turning WEP off and dropping the key command in the list.  We'll see if this helps at all.

---

### Post by higepon on 2006-08-13
> **stormblue said:**
> Try turning WEP off and dropping the key command in the list.  We'll see if this helps at all.

The result is
nobita% sudo ifconfig ath0 up
nobita% sudo iwconfig ath0 essid 000D0xxxxxx
nobita% sudo dhclient ath0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/ath0/00:0e:9b:90:9b:a9
Sending on   LPF/ath0/00:0e:9b:90:9b:a9
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by higepon on 2006-08-13
I found some messages at /var/log/messages

Aug 13 23:39:41 local kernel: [4300149.740000] ath0: ath_chan_set: unable to reset channel 8 (2447 Mhz)
Aug 13 23:39:41 local kernel: [4300150.555000] ath0: ath_chan_set: unable to reset channel 12 (2467 Mhz)
Aug 13 23:39:46 local kernel: [4300154.716000] ath0: ath_chan_set: unable to reset channel 12 (2467 Mhz)
Aug 13 23:39:49 local kernel: [4300157.775000] ath0: ath_chan_set: unable to reset channel 8 (2447 Mhz)

---

### Post by higepon on 2006-08-13
I can get IP address !
Like this
nobita% sudo ifconfig ath0 up
nobita% sudo iwconfig ath0 key "s:mypassword"
nobita% sudo iwconfig ath0 essid 000D0xxxxx
nobita% sudo iwconfig ath0 channel 11
nobita% sudo dhclient ath0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/ath0/00:0e:9b:90:9b:a9
Sending on   LPF/ath0/00:0e:9b:90:9b:a9
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 192.168.11.1
DHCPREQUEST on ath0 to 255.255.255.255 port 67
DHCPACK from 192.168.11.1


I have checked my Wireless AP and found channel is 11(auto)
Is there any good way not to set channel and works fine?

---

### Post by JDAAINOKI on 2006-08-13
This is a long shot, but try the follwing. 

what's your output for:
```
cat /proc/interrupts
```

what's your output for:
```
lspci | grep VGA 
```

lastly, what's your output for:
```
dmesg | grep Disabling 
```

Also, boot with your recovery mode option (ie just commandline) and try to configure your wireless interface from there. 

```
ifconfig ath0 up
ifconfig ath0 192.168.0.125 -----change to an ip in your subnet
route add default gw 192.168.0.1 -------change to the ap's ip
iwconfig ath0 essid "blahblah" ----------change to ap's essid
dhclient ath0 ---- just to make sure 
ping 192.168.0.1 -----change to ap's ip
ping www.google.com
```

One more thing to try:
on boot press e, e again on the kernel image your booting, append irqpoll at the end of the image and boot that thing. I think you push enter and then b to boot it.  It is not a very efficient way to run things, but it got my wifi working with xwindows too.  

My video and wireless share an interrupt line, but I think the video isn't allowing it to be shared. I think in Linux both sides must have an IRQ sharing flag checked or one gets bumped, but all that's a bit above my level. Anyway, the above commands should hopefully show if your video and wifi are sharing an IRQ and if it's being disabled for your wifi. If all this is way off we could try the boot option reserve=0x1e0000 etc... Are you using an internal mini-pci or pcmcia? I had a problem with a PCMCIA once and reserving memory at boot sorted it out.  We'll try that later. 

Good Luck,
Jay

note - Im on Japan time so I'll check back in the AM.

---

### Post by stormblue on 2006-08-13
You should be able to set the channel number in /etc/network/interfaces. Just open it in a text editor.

---

### Post by higepon on 2006-08-13
[QUOTE=JDAAINOKI;1375117]This is a long shot, but try the follwing. 

Thank you for your reply.

nobita% cat /proc/interrupts
           CPU0
  0:    1960534    IO-APIC-edge  timer
  1:       4408    IO-APIC-edge  i8042
  8:          3    IO-APIC-edge  rtc
  9:       2705   IO-APIC-level  acpi
 12:      66308    IO-APIC-edge  i8042
 14:      13150    IO-APIC-edge  ide0
169:     129255   IO-APIC-level  uhci_hcd:usb1, yenta, i915@pci:0000:00:02.0
177:       6417   IO-APIC-level  Intel 82801DB-ICH4, sdhci:slot0
185:          0   IO-APIC-level  uhci_hcd:usb3
193:          0   IO-APIC-level  uhci_hcd:usb2
201:          0   IO-APIC-level  ehci_hcd:usb4
209:      13630   IO-APIC-level  eth0
217:          0   IO-APIC-level  ath0
NMI:          0
LOC:    1596189
ERR:          0
MIS:          0
nobita% lspci|grep VGA
0000:00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
nobita% dmesg |grep Disabling
 -> no results

---

### Post by higepon on 2006-08-13
[QUOTE=JDAAINOKI;1375117]This is a long shot, but try the follwing. 

thank you for your help.

result is 
nobita% cat /proc/interrupts
           CPU0
  0:    5220390    IO-APIC-edge  timer
  1:      10835    IO-APIC-edge  i8042
  8:          3    IO-APIC-edge  rtc
  9:       5000   IO-APIC-level  acpi
 12:     185834    IO-APIC-edge  i8042
 14:      24984    IO-APIC-edge  ide0
169:     349066   IO-APIC-level  uhci_hcd:usb1, yenta, i915@pci:0000:00:02.0
177:       6652   IO-APIC-level  Intel 82801DB-ICH4, sdhci:slot0
185:          0   IO-APIC-level  uhci_hcd:usb3
193:          0   IO-APIC-level  uhci_hcd:usb2
201:          0   IO-APIC-level  ehci_hcd:usb4
209:      31800   IO-APIC-level  eth0
217:      42518   IO-APIC-level  ath0
NMI:          0
LOC:    4394916
ERR:          0
MIS:          0
nobita% lspci|grep VGA
0000:00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
nobita% dmesg |grep Disabling

---

### Post by higepon on 2006-08-14
I got wifi!

Thank you for your helps.

I reinstall the madwifi!
sudo apt-get install linux-headers-2.6.15-23-386
apt-get install sharutils
wget [http://superb-east.dl.sourceforge.net/sourceforge/madwifi/madwifi-0.9.2.tar.gz](http://superb-east.dl.sourceforge.net/sourceforge/madwifi/madwifi-0.9.2.tar.gz)
KERNELPATH=/usr/src/linux-headers-`uname -r`; export KERNELPATH
KERNELRELEASE=`uname -r`; export KERNELRELEASE
cd madwifi
make
make install
sudo cp /lib/modules/2.6.15-23-386/net/ath_rate_sample.ko lib/modules/2.6.15-23-386/kernel/drivers/net/wireless/
sudo cp /lib/modules/2.6.15-23-386/net/ath_hal.ko /lib/modules/2.6.15-23-386/kernel/drivers/net/wireless/
sudo cp /lib/modules/2.6.15-23-386/net/ath_pci.ko /lib/modules/2.6.15-23-386/kernel/drivers/net/wireless/
reboot

---

