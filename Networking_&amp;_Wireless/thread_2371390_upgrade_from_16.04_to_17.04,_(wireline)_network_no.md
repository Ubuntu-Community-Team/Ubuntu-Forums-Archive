---
title: "upgrade from 16.04 to 17.04, (wireline) network not working"
date: 2017-09-14
forum: Networking &amp; Wireless
---

### Post by bnebenda on 2017-09-14
Hello all,

I recently upgraded to 17.04 and the networking stopped working. When booting 17.04 from Live USB networking is ok. I tried to find a solution myself but I'm not really knowledgable. So far I found that it would be usefull to run the script found at 
[https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info](https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info)

Below is the output of the script.
Maybe someone has advice how to fix the problem.

Thank you,
Bernd

```
########## wireless info START ##########

Report from: 14 Sep 2017 08:27 CEST +0200

Booted last: 14 Sep 2017 00:00 CEST +0200

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 17.04
Release:    17.04
Codename:    zesty

##### kernel ############################

Linux 4.10.0-33-generic #37-Ubuntu SMP Fri Aug 11 10:55:28 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, hpet=disable, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: ASUSTeK Computer Inc. P8P67 and other motherboards [1043:8432]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID abcd:1234 Unknown 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 1d57:ac01 Xenta Wireless Receiver (Keyboard and Mouse)
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 2548:1002  
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

wmi                    16384  0

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp3s0: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 5892914  bytes 21737624829 (21.7 GB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 5892914  bytes 21737624829 (21.7 GB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

##### iwconfig ##########################

lo        no wireless extensions.

enp3s0    no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

nameserver 127.0.0.53

##### network managers ##################

Installed:

    NetworkManager

Running:

root       860     1  0 Sep13 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (P8P67 and other motherboards)
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          10 (unmanaged)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /virtual/device/placeholder/1
GENERAL.IP-IFACE:                       enp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     no
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
IP4.GATEWAY:                            
IP6.GATEWAY:                            

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

##### NetworkManager profiles ###########

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

global
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (6, 20), (N/A)
    (2457 - 2482 @ 20), (6, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 80), (6, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (5250 - 5330 @ 80), (6, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (6, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp3s0    no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp3s0    Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/open-vm-tools-dkms.conf]
install pcnet32 /sbin/modprobe -q --ignore-install vmxnet; /sbin/modprobe -q --ignore-install pcnet32 $CMDLINE_OPTS; /bin/true;

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

########## wireless info END ############
```

---

### Post by HankB on 2017-09-14
By 'wireline' are you saying that wired Ethernet (not WiFi) is not working? From the dump I see

```
enp3s0: flags=4098<BROADCAST,MULTICAST> mtu 1500
ether <MAC address> txqueuelen 1000 (Ethernet)
RX packets 0 bytes 0 (0.0 B)
RX errors 0 dropped 0 overruns 0 frame 0
TX packets 0 bytes 0 (0.0 B)
TX errors 0 dropped 0 overruns 0 carrier 0 collisions 0
```

I think this means that the driver is loaded and Ethernet is working but not being configured. Dig into Network Settings (Settings -> Network -> Wired) and make sure it is on. Go into options and check on the various tabs:
General - Automatically connect
IPV4 Settings - Automatic (DHCP) (*)
IPV6 Settings - Automatic (*)

(*) This assumes you are getting network settings via DHCP. These should be settings that you get when booting from USB. You can also explore the network settings and compare between installation and USB boot to see what is different.

Note: I'm looking at the settings for Unity on 16.04 so things might look a little different for 17.04

HTH,
hank

---

### Post by TheFu on 2017-09-14
That is a wireless/wifi info script. Doesn't help for wired.

Please use code tags (Adv Reply #) and post the command and output for:
* ifconfig
* route -n
* sudo lshw -C network
and perhaps
* contents of /etc/network/interfaces

And please, please, please use code tags to make it readable and mono-spaced font.

Looking at the ifconfig above, it looks like the ethernet port isn't connected or doesn't have a driver.  So - swap the cable. Try a different switch port.

---

### Post by Bucky Ball on 2017-09-14
Welcome. A caveat to post #2 above: IPv6 in the Network settings should be set to 'Ignore'. It can cause issues.

(The post that was 'above' has vanished, but IPv6 to ignore still applies.) 

Also, you might try 17.10 as now that you have, for some reason, decided to leave the LTS release, you are going to need to install 17.10 at some stage anyway and it is released at the end of next month so getting there. 

You probably know this, but 16.04 LTS is a long-term support release, supported for five years until 2021. The release you have chosen to install is an interim release. They have nine months support life. 17.04 dies in January 2018 at which time you are going to need to upgrade to 17.10 anyway. In April 2018, you will then be able to upgrade to the next LTS release, 18.04 LTS.

I suggest you stay there when you get there and enjoy the long-term support release unless you have a very good reason to use an interim after that (and don't mind upgrading your install to the latest, possibly not very stable release, every six months).

Good luck. ;)

(PS: Perhaps you could change the tags around your terminal output in the first post to [code] tags? Looks like you have used [quote] tags or something else. Cheers. ;))

---

### Post by slickymaster on 2017-09-14
*Thread moved to **Networking & Wireless**.*

---

### Post by HankB on 2017-09-14
> **Bucky Ball said:**
> Welcome. A caveat to post #2 above: IPv6 in the Network settings should be set to 'Ignore'. It can cause issues.


Hi Bucky Ball,
Thanks for following up on my post. Can you elaborate on this? Is this 'growing pains' for IPV6 or an Ubuntu issue? I've been annoyed by a 'slow update' issue that seems to be resolved by the change described in [https://askubuntu.com/questions/574569/apt-get-stuck-at-0-connecting-to-us-archive-ubuntu-com](https://askubuntu.com/questions/574569/apt-get-stuck-at-0-connecting-to-us-archive-ubuntu-com). Will the change you suggest disable IPV6? I've had that going on my PCs for a couple years now with no other obvious problem. (I have not been running Ubuntu in the interim having left it when Unity became the default desktop, but I'm testing it on a couple PCs now. I have recently been seeing a similar delay on Debian Stretch systems.)

thanks,
hank

---

### Post by bnebenda on 2017-09-14
Just a quick response: I doubt that swaping the cable or using a different port would solve the problem, since it was running using the exact same HW under 16.04 and is running with the same HW when booting 17.04 using Live USB, which should not be the case in case of a HW issue, right?

I will however post the output the commands you mention on a second post.

Thanks so far,
Bernd

---

### Post by bnebenda on 2017-09-14
sorry for using "quote" instead of "code". I'll try to improve.;) The reason for trying 17.04 was that I have an issue with Kodi and Audio. From what I have found the issue should be solved with pulseaudio 9 which as far as I have learned is not available for 16.04. As soon as there is an LTS version that is working for me I will switch to that version for sure.

Bernd

---

### Post by TheFu on 2017-09-14
Ah ... kodi.  I'm running 14.04 on my kodi machine.  Maintaining the correct WAF is critical, so it won't be moved off 14.04 until 2019 sometime. ;)

I only use Pulse Audio on 1 machine - my only 16.04 desktop which isn't used for anything important.

And you are correct - if the HW setup works on other releases and the live boot, then it isn't likely a cable or switch port issue.
I'm leaning towards a new driver getting installed that doesn't behave the same as the old one.  Probably a realtek.

---

### Post by bnebenda on 2017-09-14
> **HankB said:**
> By 'wireline' are you saying that wired Ethernet (not WiFi) is not working? From the dump I see

```
enp3s0: flags=4098<BROADCAST,MULTICAST> mtu 1500
ether <MAC address> txqueuelen 1000 (Ethernet)
RX packets 0 bytes 0 (0.0 B)
RX errors 0 dropped 0 overruns 0 frame 0
TX packets 0 bytes 0 (0.0 B)
TX errors 0 dropped 0 overruns 0 carrier 0 collisions 0
```

I think this means that the driver is loaded and Ethernet is working but not being configured. Dig into Network Settings (Settings -> Network -> Wired) and make sure it is on. Go into options and check on the various tabs:
General - Automatically connect
IPV4 Settings - Automatic (DHCP) (*)
IPV6 Settings - Automatic (*)



(*) This assumes you are getting network settings via DHCP. These should be settings that you get when booting from USB. You can also explore the network settings and compare between installation and USB boot to see what is different.


I compared the setting (live USB and from HD) as far as I can see they are identical.

Bernd

---

### Post by bnebenda on 2017-09-15
> **TheFu said:**
> That is a wireless/wifi info script. Doesn't help for wired.

Please use code tags (Adv Reply #) and post the command and output for:
* ifconfig
* route -n
* sudo lshw -C network
and perhaps
* contents of /etc/network/interfaces

And please, please, please use code tags to make it readable and mono-spaced font.

Looking at the ifconfig above, it looks like the ethernet port isn't connected or doesn't have a driver.  So - swap the cable. Try a different switch port.

Here is the output of the commands you suggested:

```
ifconfig>>
lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Lokale Schleife)
        RX packets 8301211  bytes 31766137831 (31.7 GB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 8301211  bytes 31766137831 (31.7 GB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

route -n>>
Kernel-IP-Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface

sudo lshw -C network>>
  *-network DEAKTIVIERT
       Beschreibung: Ethernet interface
       Produkt: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       Hersteller: Realtek Semiconductor Co., Ltd.
       Physische ID: 0
       Bus-Informationen: pci@0000:03:00.0
       Logischer Name: enp3s0
       Version: 06
       Seriennummer: 14:da:e9:ea:df:ea
       Größe: 1Gbit/s
       Kapazität: 1Gbit/s
       Breite: 64 bits
       Takt: 33MHz
       Fähigkeiten: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       Konfiguration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=no multicast=yes port=MII speed=1Gbit/s
       Ressourcen: irq:26 ioport:e800(Größe=256) memory:fdfff000-fdffffff memory:fdff8000-fdffbfff

cat /etc/network/interfaces>>
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```

Does this tell me the network is not activated? If so, why is that and how would I activate it?

Bernd

---

### Post by bnebenda on 2017-09-15
Hello all,

I went through the output of the script again and noticed something that I would like you to comment on. The HW reported in the first output line of lspci command does not match the Kernel driver name (RTL8111/8168/8411 vs. r8169). Should I be concerned about that? How would I fix that if that's a problem?

Bernd

```
########## wireless info START ##########
.
.
.
##### lspci #############################

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. **RTL8111/8168/8411** PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: ASUSTeK Computer Inc. P8P67 and other motherboards [1043:8432]
    Kernel driver in use: **r8169**

```

---

### Post by funmaker-11 on 2017-09-15
I  have been  following this thread since I have a similar problem with my Ethernet. Realtek RTL8101/2/6E PCI express Fast/Gigabit Ethernet controller (rev 02) No connection.
Using Kubuntu 14.04 I had to manually use my Amazon Kindle to download packages from the ubuntu repos and then install them in order to get the wifi working. I recently did a fresh install. I had no networking in the live dvd either. Wifi = Broadcom BCM 4322. I see lots of problems all over ubuntu and kubuntu forums about this wifi card.

---

### Post by TheFu on 2017-09-15
> **bnebenda said:**
> Hello all,

I went through the output of the script again and noticed something that I would like you to comment on. The HW reported in the first output line of lspci command does not match the Kernel driver name (RTL8111/8168/8411 vs. r8169). Should I be concerned about that? How would I fix that if that's a problem?
 

Exactly.  That is where I'd start.  There are lots of people here with that same NIC with the same issue. Search based on those terms to see how they solved it.  Could be a different driver. Could be blacklisting the r8169. Could be adding some options to the driver config.  Could be a little of each.  I don't know.  I avoid Realtek stuff.   Find that $25 for an Intel PRO/1000 NIC prevents this issue completely and the Intel NICs offload more work to the NIC, so the CPU isn't as involved.  An intel NIC doing 920Mbps uses about 3% of 1 CPU. A Realtek uses significantly more and isn't as well supported by BSD.

I googled for a solution, but decided that you should fine it as the answer I found had a 3pg description including way to many commands as the person looked for a solution.  The solution was relatively simple (which is usually the case).

Until we had the NIC and driver known (code tags!!!!), we weren't gonna see this.  I'm old and just don't use the commands the wireless script does to get the data.  For example, lspci - I find it shows way too much for things that aren't related.  lshw -C network shows exactly what I needed to see.

Just one more thing - is the system fully patched?
```
$ sudo apt update && sudo apt dist-upgrade
```
That will get the current kernel from Canonical and any driver updates.  It would be smart to ensure you have a a know-you-can-restore backup too.  I run those commands every week across almost all my systems.  Don't worry. It doesn't upgrade Ubuntu releases. It will take a 16.04.2 system to 16.04.3. It will not take a 16 system to 17.

---

### Post by HankB on 2017-09-15
> **bnebenda said:**
> Hello all,

I went through the output of the script again and noticed something that I would like you to comment on. The HW reported in the first output line of lspci command does not match the Kernel driver name (RTL8111/8168/8411 vs. r8169). Should I be concerned about that? How would I fix that if that's a problem?



The laptop I'm using shows
```
hbarta@yggdrasil:~$ lspci|grep Ethernet
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)
hbarta@yggdrasil:~$ lsmod  |grep r8169
r8169                  81920  0
mii                    16384  1 r8169
hbarta@yggdrasil:~$ 

```

I just plugged in the Ethernet cable and the network came up It seems like the right driver is in use.

Have you tried simply typing 'sudo ifup enp3s0'?

Have you looked through 'sudo dmesg' output for any indication of a problem?

---

### Post by bnebenda on 2017-09-15
> **TheFu said:**
> 
Just one more thing - is the system fully patched?
```
$ sudo apt update && sudo apt dist-upgrade
```
That will get the current kernel from Canonical and any driver updates.  It would be smart to ensure you have a a know-you-can-restore backup too.  I run those commands every week across almost all my systems.  Don't worry. It doesn't upgrade Ubuntu releases. It will take a 16.04.2 system to 16.04.3. It will not take a 16 system to 17.

I don't know if the system is fully patched. Since I don't have a network connection I probably need some help in how to figure out what needs to be patched, how to get those patches using a different computer and then loading the patches to the system. I can read and write to a USB mass storage but that's it basically. No network currently whatsoever.

Bernd

PS I'll try to connect a USB Wlan dongle, hopefully this will connect me to the wireless network. If so then of course patching the system would be simple.

---

### Post by bnebenda on 2017-09-15
> **HankB said:**
> The laptop I'm using shows
```
hbarta@yggdrasil:~$ lspci|grep Ethernet
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)
hbarta@yggdrasil:~$ lsmod  |grep r8169
r8169                  81920  0
mii                    16384  1 r8169
hbarta@yggdrasil:~$ 

```

I just plugged in the Ethernet cable and the network came up It seems like the right driver is in use.

Have you tried simply typing 'sudo ifup enp3s0'?

Have you looked through 'sudo dmesg' output for any indication of a problem?

Not yet, what I also intend to do is booting live USB and then compare driver version and so on (since in live USB the network is working).

Bernd

---

### Post by TheFu on 2017-09-15
Ah - chicken/egg problem.  You can boot off a flash drive/cdrom/dvd, setup a chroot with the HDD being used using your install, and if the networking works there, use that.  If the networking never worked, I'm at a loss.

Plus, I don't really do upgrades in-place.  Tend to do fresh installs since I'm usually going 10.04 --> 14.04 --> 18.04 --> 22.04 ... you get the idea.  4 yrs from an install is just long enough to limit the effort needed for me.  Of course, everyone is different.  In the early/mid 1990s, I did my bleeding edge time. Never again.

I don't run non-LTS releases.  I'm actually using a 14.04 Desktop now.  Learned long ago that newer isn't better.  Most of my systems run 14.04 - actually only 2 run 16.04 - waiting for it to be stable (systemd has been a problem on both those systems).

---

### Post by bnebenda on 2017-09-15
> **TheFu said:**
> Ah - chicken/egg problem.  You can boot off a flash drive/cdrom/dvd, setup a chroot with the HDD being used using your install, and if the networking works there, use that.  If the networking never worked, I'm at a loss.
...
I don't run non-LTS releases. 
...


I wasn't aware of the "chroot" thing. That might be a good thing. I would probably also not have moved to a newer system if I did not had the anoying problem with the audio output on HDMI lost afer suspend/resume which is suposed to be fixed in 17.04.

Bernd

---

### Post by Bucky Ball on 2017-09-15
As I suggested, see if 17.10 gives a different result. You're down that track now so, unless you're going to downgrade, no harm giving it a shot. It's released officially in late October anyhow, so not far away and even if you get this working, you can upgrade to 17.10 anytime from then (and will need to have done so by next January).

You might want to install 17.10 to a different partition if the internet is working on 17.10 in 'Try Ubuntu'.

Good luck.

(PS: Will make you aware, though, that 17.10 is not yet released and therefore may be unstable. While the internet may work, the next update may break something, usually temporarily. This should settle down after release. On the other hand, it may work pretty well faultlessly from install. Hard to know from one to the next.)

---

### Post by bnebenda on 2017-09-15
> **bnebenda said:**
> I don't know if the system is fully patched. Since I don't have a network connection I probably need some help in how to figure out what needs to be patched, how to get those patches using a different computer and then loading the patches to the system. I can read and write to a USB mass storage but that's it basically. No network currently whatsoever.

Bernd

PS I'll try to connect a USB Wlan dongle, hopefully this will connect me to the wireless network. If so then of course patching the system would be simple.

I tried the USB Wlan dongle. The wireless networks that I would have expected to see (mine and the one from the neighbour) are listed. But I cannot connect to the network. To be sure that it is not a security problem I temporarily allowed all wifi devices to connect to my network and also disable all security (normally I run WPA + WPA2). 

I'll post the wireless info script output here as well, later today.

Bernd

---

### Post by bnebenda on 2017-09-15
> **Bucky Ball said:**
> As I suggested, see if 17.10 gives a different result. You're down that track now so, unless you're going to downgrade, no harm giving it a shot. It's released officially in late October anyhow, so not far away and even if you get this working, you can upgrade to 17.10 anytime from then (and will need to have done so by next January).

You might want to install 17.10 to a different partition if the internet is working on 17.10 in 'Try Ubuntu'.

Good luck.

(PS: Will make you aware, though, that 17.10 is not yet released and therefore may be unstable. While the internet may work, the next update may break something, usually temporarily. This should settle down after release. On the other hand, it may work pretty well faultlessly from install. Hard to know from one to the next.)

I don't see how that would help. 17.04 is running from live USB. What you suggest is a clean install. I can do that with 17.04 but then I would have to install all the packages (kodi, tvheadend, ...) again or am I missing something here?

Bernd

---

### Post by bnebenda on 2017-09-16
> **bnebenda said:**
> I tried the USB Wlan dongle. The wireless networks that I would have expected to see (mine and the one from the neighbour) are listed. But I cannot connect to the network. To be sure that it is not a security problem I temporarily allowed all wifi devices to connect to my network and also disable all security (normally I run WPA + WPA2). 

I'll post the wireless info script output here as well, later today.


As promised here is the output of the wireless info script. As I believe one can see, there are two different networks (privat and guest). Both networks are available through two different wlan access points. However I don't get connected but from what I can see the wlan usb dongle seems to work to some extent (I can see all of the networks, there are entries for signal strength and so on). Could the problem I see with wlan dongle have the same (root) cause I can't use my wired lan connection?

Bernd

```
########## wireless info START ##########

Report from: 16 Sep 2017 09:10 CEST +0200

Booted last: 16 Sep 2017 00:00 CEST +0200

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 17.04
Release:    17.04
Codename:    zesty

##### kernel ############################

Linux 4.10.0-33-generic #37-Ubuntu SMP Fri Aug 11 10:55:28 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, hpet=disable, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: ASUSTeK Computer Inc. P8P67 and other motherboards [1043:8432]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID abcd:1234 Unknown 
Bus 002 Device 003: ID 0cf3:7015 Atheros Communications, Inc. TP-Link TL-WN821N v3 / TL-WN822N v2 802.11n [Atheros AR7010+AR9287]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 1d57:ac01 Xenta Wireless Receiver (Keyboard and Mouse)
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 2548:1002  
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath9k_htc              77824  0
ath9k_common           36864  1 ath9k_htc
ath9k_hw              466944  2 ath9k_htc,ath9k_common
ath                    28672  3 ath9k_htc,ath9k_hw,ath9k_common
mac80211              782336  1 ath9k_htc
cfg80211              602112  4 ath9k_htc,mac80211,ath,ath9k_common
wmi                    16384  0

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp3s0: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 4085  bytes 9272358 (9.2 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 4085  bytes 9272358 (9.2 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlx64700220a340: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

##### iwconfig ##########################

lo        no wireless extensions.

enp3s0    no wireless extensions.

wlx64700220a340  IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

nameserver 127.0.0.53

##### network managers ##################

Installed:

    NetworkManager

Running:

root       934     1  0 09:04 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlx64700220a340
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         ATHEROS
GENERAL.PRODUCT:                        USB WLAN
GENERAL.DRIVER:                         ath9k_htc
GENERAL.DRIVER-VERSION:                 4.10.0-33-generic
GENERAL.FIRMWARE-VERSION:               1.4
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:13.2/usb2/2-3/2-3:1.0/net/wlx64700220a340
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2,0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   03f84a61-ff67-4479-973f-2a7e4ca52eb2 | Warmbronner Weg 2/1
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   b307ee63-c760-480b-b81a-477ba70b9e29 | Montanistas

GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (P8P67 and other motherboards)
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          10 (unmanaged)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /virtual/device/placeholder/1
GENERAL.IP-IFACE:                       enp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     no
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
IP4.GATEWAY:                            
IP6.GATEWAY:                            

SSID                 BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
Montanistas          <MAC 'Montanistas' [AC2]>  Infra  6     2437 MHz  54 Mbit/s  77      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
Warmbronner Weg 2/1  <MAC 'Warmbronner Weg 2/1' [AC4]>  Infra  6     2437 MHz  54 Mbit/s  74      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
Warmbronner Weg 2/1  <MAC 'Warmbronner Weg 2/1' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  39      &#9602;&#9604;__  WPA1 WPA2  no        
Montanistas          <MAC 'Montanistas' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA1 WPA2  no        

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Warmbronner Weg 2*1]] (600 root)

[[/etc/NetworkManager/system-connections/Montanistas]] (600 root)
[connection] id=Montanistas | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Montanistas
[ipv4] method=auto
[ipv6] method=ignore

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

global
country CN: DFS-FCC
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 23), (N/A), AUTO-BW
    (5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS, AUTO-BW
    (5735 - 5835 @ 80), (N/A, 30), (N/A)
    (57240 - 59400 @ 2160), (N/A, 28), (N/A)
    (59400 - 63720 @ 2160), (N/A, 44), (N/A)
    (63720 - 65880 @ 2160), (N/A, 28), (N/A)

phy#0
country CN: DFS-FCC
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 23), (N/A), AUTO-BW
    (5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS, AUTO-BW
    (5735 - 5835 @ 80), (N/A, 30), (N/A)
    (57240 - 59400 @ 2160), (N/A, 28), (N/A)
    (59400 - 63720 @ 2160), (N/A, 44), (N/A)
    (63720 - 65880 @ 2160), (N/A, 28), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp3s0    no frequency information.

wlx64700220a340  13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp3s0    Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.437 GHz (Channel 6)

wlx64700220a340  Scan completed :
          Cell 01 - Address: <MAC 'Montanistas' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"Montanistas"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000006f9e9050d
                    Extra: Last beacon: 952ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Montanistas' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"Montanistas"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000024566efe
                    Extra: Last beacon: 532ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Warmbronner Weg 2/1' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"Warmbronner Weg 2/1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000006f9e7ca75
                    Extra: Last beacon: 1008ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Warmbronner Weg 2/1' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"Warmbronner Weg 2/1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000024567c95
                    Extra: Last beacon: 528ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[ath9k_htc]
filename:       /lib/modules/4.10.0-33-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
firmware:       ath9k_htc/htc_9271-1.4.0.fw
firmware:       ath9k_htc/htc_7010-1.4.0.fw
description:    Atheros driver 802.11n HTC based wireless devices
license:        Dual BSD/GPL
author:         Atheros Communications
srcversion:     1EC4A00E649159E522D39C7
depends:        mac80211,ath9k_hw,ath9k_common,ath,cfg80211
intree:         Y
vermagic:       4.10.0-33-generic SMP mod_unload 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_dev_fw:Use development FW version (int)
parm:           blink:Enable LED blink on activity (int)

[ath9k_common]
filename:       /lib/modules/4.10.0-33-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     AAF3B58F80FF1BAC17759BC
depends:        ath9k_hw,cfg80211,ath
intree:         Y
vermagic:       4.10.0-33-generic SMP mod_unload 

[ath9k_hw]
filename:       /lib/modules/4.10.0-33-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     B69AC5BDB1497312F28332E
depends:        ath
intree:         Y
vermagic:       4.10.0-33-generic SMP mod_unload 

[ath]
filename:       /lib/modules/4.10.0-33-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     4B8612B6FF71DD27AE8CE67
depends:        cfg80211
intree:         Y
vermagic:       4.10.0-33-generic SMP mod_unload 

[mac80211]
filename:       /lib/modules/4.10.0-33-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     309C9ACED540FCAA1DE7422
depends:        cfg80211
intree:         Y
vermagic:       4.10.0-33-generic SMP mod_unload 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.10.0-33-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D77C8F93375950F3BA95B16
depends:        
intree:         Y
vermagic:       4.10.0-33-generic SMP mod_unload 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath9k_htc]
blink: 1
btcoex_enable: 0
nohwcrypt: 0
ps_enable: 0
use_dev_fw: 0

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/open-vm-tools-dkms.conf]
install pcnet32 /sbin/modprobe -q --ignore-install vmxnet; /sbin/modprobe -q --ignore-install pcnet32 $CMDLINE_OPTS; /bin/true;

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   30.518985] usb 2-3: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[   30.519060] usbcore: registered new interface driver ath9k_htc
[   30.674477] usb 2-3: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[   30.743906] ath9k_htc 2-3:1.0: ath9k_htc: HTC initialized with 45 credits
[   30.930485] ath9k_htc 2-3:1.0: ath9k_htc: FW Version: 1.4
[   30.930486] ath9k_htc 2-3:1.0: FW RMW support: On
[   30.930487] ath: EEPROM regdomain: 0x809c
[   30.930488] ath: EEPROM indicates we should expect a country code
[   30.930489] ath: doing EEPROM country->regdmn map search
[   30.930489] ath: country maps to regdmn code: 0x52
[   30.930490] ath: Country alpha2 being used: CN
[   30.930490] ath: Regpair used: 0x52
[   31.089012] ath9k_htc 2-3:1.0 wlx64700220a340: renamed from wlan0
[   37.880395] IPv6: ADDRCONF(NETDEV_UP): wlx64700220a340: link is not ready (repeated 5 times)
[  234.203362] wlx64700220a340: authenticate with <MAC 'Montanistas' [AC2]>
[  234.457508] wlx64700220a340: send auth to <MAC 'Montanistas' [AC2]> (try 1/3)
[  234.461076] wlx64700220a340: authenticated
[  239.458136] wlx64700220a340: aborting authentication with <MAC 'Montanistas' [AC2]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  239.814961] wlx64700220a340: authenticate with <MAC 'Montanistas' [AC1]>
[  240.064306] wlx64700220a340: send auth to <MAC 'Montanistas' [AC1]> (try 1/3)
[  240.067380] wlx64700220a340: authenticated
[  245.069120] wlx64700220a340: aborting authentication with <MAC 'Montanistas' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  246.494006] wlx64700220a340: authenticate with <MAC 'Montanistas' [AC2]>
[  246.742498] wlx64700220a340: send auth to <MAC 'Montanistas' [AC2]> (try 1/3)
[  246.746344] wlx64700220a340: authenticated
[  251.745453] wlx64700220a340: aborting authentication with <MAC 'Montanistas' [AC2]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  253.001746] wlx64700220a340: authenticate with <MAC 'Montanistas' [AC1]>
[  253.251392] wlx64700220a340: send auth to <MAC 'Montanistas' [AC1]> (try 1/3)
[  253.254741] wlx64700220a340: authenticated
[  258.090884] wlx64700220a340: aborting authentication with <MAC 'Montanistas' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  258.183136] IPv6: ADDRCONF(NETDEV_UP): wlx64700220a340: link is not ready (repeated 5 times)
[  329.162759] wlx64700220a340: authenticate with <MAC 'Warmbronner Weg 2/1' [AC4]>
[  329.414132] wlx64700220a340: send auth to <MAC 'Warmbronner Weg 2/1' [AC4]> (try 1/3)
[  329.418034] wlx64700220a340: authenticated
[  334.418971] wlx64700220a340: aborting authentication with <MAC 'Warmbronner Weg 2/1' [AC4]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  334.774291] wlx64700220a340: authenticate with <MAC 'Warmbronner Weg 2/1' [AC3]>
[  335.027201] wlx64700220a340: send auth to <MAC 'Warmbronner Weg 2/1' [AC3]> (try 1/3)
[  335.031554] wlx64700220a340: authenticated
[  340.029719] wlx64700220a340: aborting authentication with <MAC 'Warmbronner Weg 2/1' [AC3]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  341.481317] wlx64700220a340: authenticate with <MAC 'Warmbronner Weg 2/1' [AC4]>
[  341.735493] wlx64700220a340: send auth to <MAC 'Warmbronner Weg 2/1' [AC4]> (try 1/3)
[  341.739117] wlx64700220a340: authenticated
[  346.740237] wlx64700220a340: aborting authentication with <MAC 'Warmbronner Weg 2/1' [AC4]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  347.997023] wlx64700220a340: authenticate with <MAC 'Warmbronner Weg 2/1' [AC3]>
[  348.247817] wlx64700220a340: send auth to <MAC 'Warmbronner Weg 2/1' [AC3]> (try 1/3)
[  348.253130] wlx64700220a340: authenticated
[  353.082624] wlx64700220a340: aborting authentication with <MAC 'Warmbronner Weg 2/1' [AC3]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  353.170963] IPv6: ADDRCONF(NETDEV_UP): wlx64700220a340: link is not ready (repeated 2 times)

########## wireless info END ############
```

---

### Post by bnebenda on 2017-09-16
I was able to get at least the wireless networking up and running. The problem for wireless was solved by creating the file:

/etc/NetworkManager/NetworkManager.conf

and add:

 ```

[device]
wifi.scan-rand-mac-address=no

```

After having the wifi working I could update the system. However wired networking is still not working and staying with wifi is not my preferred option. Wifi is slower and the wifi router is not always switched on.

Bernd

---

### Post by bnebenda on 2017-09-16
I finally found a solution to my problem. I just had to comment out any entries in 

/usr/lib/NetworkManager/conf.d/10-globally-managed-devices.conf

The file now contains:

```

#[keyfile]
#unmanaged-devices=*,except:type:wifi,except:type:wwan

```

Thanks to everybody who helped me find my way to that solution.

Bernd

---

### Post by TheFu on 2017-09-16
a) Glad you found a solution.  I never would have gone that direction, since I purge network-manager* from all my systems. It just causes issues, as you can attest.

b) Please make this thread as SOLVED - to help others - seeking answers.

c) THANKS for saying what the fix was. That is crazy helpful.

---

