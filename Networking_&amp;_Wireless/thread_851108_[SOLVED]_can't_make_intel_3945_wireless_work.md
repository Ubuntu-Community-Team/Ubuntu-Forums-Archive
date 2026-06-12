---
title: "[SOLVED] can't make intel 3945 wireless work"
date: 2008-07-06
forum: Networking &amp; Wireless
---

### Post by Nycticorax on 2008-07-06
I can't get my intel 3945 wireless working under hardy currently. It worked under gutsy, and I believe it worked immediately after the upgrade to hardy, but since then a kernel update or something has knocked it out. I'd appreciate any advice on what the strategy is for sorting this out. Which kernel version should I be using, what other packeges do I need to have or not have installed?

Currently I have
```
~> uname -a
Linux Tichodroma 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux
~> lspci | grep [Ww]ireless
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
~> lsmod | egrep 'module|iwp|iwl'
iwl3945                89844  0 
iwlwifi_mac80211      219108  1 iwl3945
cfg80211               15112  1 iwlwifi_mac80211
~> iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.
~> dpkg -l *backports*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                        Version                     Description
+++-===========================-===========================-======================================================================
ii  linux-backports-modules-2.6 2.6.24-19.17                Ubuntu supplied Linux modules for version 2.6.24 on x86/x86_64
ii  linux-backports-modules-har 2.6.24.19.21                Backported drivers for generic kernel image

```

I just tried booting into the 2.6.24.19 kernel, and although I couldn't make the wireless work, iwconfig did report a network interface for it, and the gnome network-manager panel thing gave some extra options like "new wireless connection" which I'm not getting with the 2.6.24.16 kernel. However the whole system was seizing up and was virtually unusable so I had to boot back into 2.6.24.16. It wasn't obvious from 'top' that iwl3945 was to blame, to the extent that top was usable.

Right, I am happy to provide any further details, under any combination of kernels and installed packages etc, to any kind person who can be bothered to help me out here!

Thanks,

Dan

---

### Post by chili555 on 2008-07-06
> However the whole system was seizing up and was virtually unusable so I had to boot back into 2.6.24.16. It wasn't obvious from 'top' that iwl3945 was to blame, to the extent that top was usable.While you are booted into -16, please open Synaptic and find linux-image-2.6.24-19-generic, right-click it and 'Mark for Reinstallation.' Press 'Apply,' and let it reinstall. 

I am not quite sure how to interpret your backports status; please install or reinstall the -19 version.

Now boot into -19 and see if your instability and wireless are fixed. Post back and we'll try to get it fixed.

---

### Post by Nycticorax on 2008-07-06
OK I'm in the -19 kernel (and there is no instability now). iwconfig is showing an entry for eth1. When I try to connect to a network we get the following logged to /var/log/messages:
```

Jul  6 17:10:59 Tichodroma kernel: [  134.109326] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 21
Jul  6 17:10:59 Tichodroma kernel: [  134.112256] ACPI: PCI interrupt for device 0000:05:00.0 disabled

```
NB that PCI address seems to be my wireless card:
```

~> lspci | grep [Ww]ireless
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

```
I'm going to put a bunch of details below here in case they're useful, but that's basically the state of things. I'm going out for a bit now but I very much appreciate your help.
Dan

I've got the linux-backports-modules-2.6.24-19-generic package installed.

Here's the iwconfig entry
```
~> iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11a  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
here's what lshw (as i learned from one of your posts on another thread) says:
```

~> lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 12
       serial: 00:17:42:0e:9b:54
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=192.168.0.100 latency=0 module=sky2 multicast=yes
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 02
       serial: 00:13:02:9b:cb:20
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11a

```

---

### Post by chili555 on 2008-07-06
> NB that PCI address seems to be my wireless cardIndeed! I suggest checking in the computer's BIOS to see how the IRQs are set up. On several of my computers, including this one using a 3945ABG wireless, the setting 'Auto Detect' seems to work and play well with Linux. There may also be a setting for 'plug and play operating system.' You might change it to whatever it isn't now.

Then see if the disabled IRQ message disappears. Note that *messages* saves messages for several days. Make sure you look for entries past Jul  6 17:10:59.

---

### Post by Nycticorax on 2008-07-07
The only BIOS options that mention IRQs and "plug and play" operating system are settings for serial, parallel and infra-red ports. I tried setting them to 'auto' (which the BIOS explains means plug and play OS controls them), but those should all be irrelevant right? None of them mentioned IRQ 21 or a PCI address with a 5 in it. The BIOS also allows one to disable/enable the wireless (it was enabled), and there was something called "hardware power management" which I tried disabling. Still getting the messages constantly in the background (two of them come in quick succession, then some singles with gaps of up to a couple of minutes, then the double again). 
```

Jul  7 07:22:07 Tichodroma kernel: [  171.199357] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 21
Jul  7 07:22:07 Tichodroma kernel: [  171.202190] ACPI: PCI interrupt for device 0000:05:00.0 disabled

```
Given that it was working previously, and I hadn't touched the BIOS settings in the interim, is it reasonable to think that I should have to alter the BIOS settings to make it work again? (i.e. could a software change cause one to have to mess with this IRQ stuff or are they fixed properties of the hardware?) BTW, under the -16 kernel I got a different message (something like 'MAC in deep sleep! Can't activate nic').

---

### Post by Nycticorax on 2008-07-08
So, now I don't know what to do next. Wireless was working previously under hardy with a different kernel vesion; it must be possible to get it working again?

---

### Post by chili555 on 2008-07-08
Does it scan correctly?```
sudo iwlist wlano scan
```Any change in your ability to connect if you do:```
sudo rmmod iwl3945
sudo modprobe iwl3945 disable_hw_scan=1
```Thanks.

---

### Post by Nycticorax on 2008-07-08
OK, I've followed your suggestion to investigate iwlist scan and rmmod/modprobe. The messages about the PCI interrupt being disabled have stopped. If I disable ethernet and enable wireless, it looks promising but doesn't work, saying that I have 0% signal. I'm going to provide a full annotated session below, but basically what I'm finding is: (i) it says it doesn't support scanning, (ii) I can successfully remove iwl3945 and then replace it with modprobe; when I modprobe it, plenty of happy-sounding messages get logged to /var/log/messages saying that iwl3945 has detected my wireless card, and udev says it's renamed wlan0 to eth1. iwconfig then reports an entry for a wireless interface as eth1, but this is always reported as "Not-Associated". 
Whenever the module is loaded, instead of the previous bad sounding PCI interrupt messages, I get 
```

kernel: [  298.322682] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 21

```

If I use the gnome panel network manager to tell it to connect to my wireless network then I get this message on /var/log/messages:
```
dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
``` 
However my guess is that this is unimportant as I also get similar messages concerning eth0 when starting networking.

Here's a full session:
```
## ifconfig shows normal entries for eth0 and lo
~> iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11a  ESSID:"linksys"  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Tx-Power=0 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

~> lsmod | grep iwl
iwl3945                93940  0
iwlwifi_mac80211      219108  1 iwl3945
cfg80211               15112  1 iwlwifi_mac80211
led_class               6020  1 iwl3945
~> date && sudo rmmod iwl3945 && echo $?
Tue Jul  8 15:04:29 BST 2008
0
~> lsmod | grep iwl
iwlwifi_mac80211      219108  0
cfg80211               15112  1 iwlwifi_mac80211
## OK so removed module, now replace it
~> date && sudo modprobe iwl3945 disable_hw_scan=1 && echo $?
Tue Jul  8 15:05:55 BST 2008
0
~> lsmod | grep iwl
iwl3945                93940  0
iwlwifi_mac80211      219108  1 iwl3945
cfg80211               15112  1 iwlwifi_mac80211
led_class               6020  1 iwl3945

## OK well that got the module running, and resulted in the following	being logged to	/var/log/messages:
Jul  8 15:05:56 Tichodroma kernel: [  160.256238] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.25
Jul  8 15:05:56 Tichodroma kernel: [  160.256248] iwl3945: Copyright(c) 2003-2007 Intel Corporation
Jul  8 15:05:56 Tichodroma kernel: [  160.256409] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 21
Jul  8 15:05:56 Tichodroma kernel: [  160.256460] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
Jul  8 15:05:56 Tichodroma kernel: [  160.312464] udev: renamed network interface wlan0 to eth1
Jul  8 15:05:56 Tichodroma kernel: [  160.330947] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 21
Jul  8 15:05:56 Tichodroma kernel: [  160.347604] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 21
Jul  8 15:05:56 Tichodroma kernel: [  160.511288] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 21
Jul  8 15:05:56 Tichodroma kernel: [  160.514766] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 21


## now try to connect wireless network with network manager applet

Jul  8 15:13:16 Tichodroma dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Jul  8 15:13:17 Tichodroma kernel: [  209.979193] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 21
Jul  8 15:13:17 Tichodroma kernel: [  210.037490] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 21

```
## This doesn't result in a functioning connection. iwconfig still reports eth1 as "Not-Associated". If I try to connect via System->Administration->Network it spins for a while, then puts a tick mark next to the wireless connection, but there is no network connectivity.

---

### Post by chili555 on 2008-07-08
We can make the 'disable hw_scan=1' permanent with:```
sudo su
echo -e 'alias wlan0 iwl3945 \noptions iwl3945 disable_hw_scan=1' > etc/modprobe.d/iwl3945
reboot
```Can you connect the old fashioned way?```
sudo iwconfig eth1 essid linksys
sudo iwconfig eth1 key <any_encryption_here?>
sudo dhclient eth1
```

---

### Post by Nycticorax on 2008-07-09
I have saved your code to make the disable_hw_scan=1 permanent, but I haven't executed it, as I'd like to avoid making such alterations unless absolutely necessary. I assume that for now I can have the same effect just by remembering to pass disable_hw_scan=1 to modprobe? (Why is this disabling necessary?)

When I try to connect from the command line (after modprobing with the disable_hw_scan=1) I get

```

There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
wmaster0: unknown hardware address type 801
Listening on LPF/eth1/00:13:02:9b:cb:20
Sending on   LPF/eth1/00:13:02:9b:cb:20
Sending on   Socket/fallback
receive_packet failed on eth1: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
send_packet: Network is down

```

---

### Post by Master Chief on 2008-07-09
Interesting, we seem to be using the same kind of hardware. Or at least parts of it.

I have 8.04.1 installed though, but whatever I select; roaming, DHCP or a static IP# it all worked right away, thus I wonder why it doesn't work for you.

Please do a *dmesg:grep udev* and check if it swaps your ports.  I had that once, and that turned out to whack my InterWobble access.

I fixed this in 70-persistent-net.rules manually, then I found out about that script (which I cannot recollect right now).

---

### Post by chili555 on 2008-07-09
> I'd like to avoid making such alterations unless absolutely necessary.I fully agree. My statement, in this regard, was to ask if this made any difference in your ability to connect? Does it? If so, it's necessary. If not, then don't do it.> Please do a dmesg:grep udev and check if it swaps your ports. I had that once, and that turned out to whack my InterWobble access.My 3945ABG runs fine as eth1, rather than wlan0.> send_packet: Network is downThis is troubling. May we see:```
ifconfig
sudo iwlist eth1 scan
```Thanks.

---

### Post by Nycticorax on 2008-07-10
OK, solved! Firstly I was checking /var/log/messages, but not dmesg. Had I done so we would have seen
```
iwl3945: iwlwifi-3945-1.ucode firmware file req failed: Reason -2
```
I believe that despite having linux-backports-modules-2.6.24-19-generic, the appropriate firmware microcode is missing:
```
~> ls /lib/firmware/$(uname -r)
iwlwifi-4965-1-lbm.ucode

```
So I've extracted the 3945 microcode from [URL="http://www.intellinuxwireless.org/iwlwifi/downloads/iwlwifi-3945-ucode-2.14.1.5.tgz"]http://www.intellinuxwireless.org/iwlwifi/downloads/iwlwifi-3945-ucode-2.14.1.5.tgz
[/URL] and placed it in the firmware directory. That gets rid of the "firware file req failed" message in dmesg, and moves us to a new problem: the following is logged in dmesg and /var/log/messages
```
iwl3945: Radio disabled by HW RF Kill switch

```
I didn't know where my wireless switch was, but now that I do, I see that it was indeed off. dhclient eth1 now succeeds. (Lucky for me in a sense that there was that missing firmware or I'd have been asking a pretty stupid question:))

One question I have is could you tell me the motivation for the disable_hardware_scan=1 option? I didn't mean to give the impression that I was incapable of creating that entry in /etc/modprobe.d and getting rid of it if needed:), but I am currently not using it. Any reason to? An unexplained issue is why didn't I have the 3945 firmware microcode? I didn't have to manually install it previously, so presumably there's no licencing problems and it should be a dependency of the backports package? But otherwise thanks very much for the help from chili555; I have learned several useful commands for querying hardware and modules and managing network interfaces in the process.

---

