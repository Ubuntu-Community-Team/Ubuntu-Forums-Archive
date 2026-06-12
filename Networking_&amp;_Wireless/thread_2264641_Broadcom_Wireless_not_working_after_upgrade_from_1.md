---
title: "Broadcom Wireless not working after upgrade from 12 LTS to 14 LTS"
date: 2015-02-09
forum: Networking &amp; Wireless
---

### Post by mfrag on 2015-02-09
Thanks in advance for any help offered.  I upgraded from 12 LTS to 14 LTS today and my wireless is not working.  I do have access to internet through an ethernet connection.  I have tried to follow all the suggestions in various threads to no avail.  The output of ```
lspci -nn -d 14e4:
``` gives the following: ```
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5761e Gigabit Ethernet PCIe [14e4:1680] (rev 10)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
```

I ran ```
sudo apt-get purge bcmwl-kernel-source
``` and updated and then ran ```
sudo apt-get install firmware-b43-installer
```

After a reboot wireless was still not working.  

Can anyone offer suggestions?  Again, many thanks in advance.

---

### Post by chili555 on 2015-02-09
Is the wireless switch or key combination set to enable wireless?```
rfkill list all
```Does it scan and see networks?```
sudo iwlist wlan0 scan
```Is the driver actually loading?```
lsmod | grep b43
```Are there any clues in the log?```
dmesg | grep b43
```Thanks.

---

### Post by mfrag on 2015-02-09
Thanks for your help, chili555. When you ask about a wireless switch, I assume you are referring to a physical switch, correct?  It is indeed on.  However, the blue "wifi" light is not coming on as it usually does (everything was fine before the upgrade).  Here is the output of the commands you posted:

```
mragland@wielandt:~$ rfkill list all
0: dell-wifi: Wireless LAN
        Soft blocked: no
        Hard blocked: no
1: dell-bluetooth: Bluetooth
        Soft blocked: no
        Hard blocked: no
2: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
mragland@wielandt:~$ sudo iwlist wlan0 scan
[sudo] password for mragland: 
wlan0     Interface doesn't support scanning.

mragland@wielandt:~$ lsmod | grep b43
mragland@wielandt:~$ dmesg | grep b43


```
Note the last two came up with nothing.

Here is the output of ```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```

```

########## wireless info START ##########

Report from: 09 Feb 2015 07:45 CST -0600

Booted last: 09 Feb 2015 01:05 CST -0600

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID: Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:        14.04
Codename:       trusty

##### kernel ############################

Linux 3.13.0-45-generic #74-Ubuntu SMP Tue Jan 13 19:36:28 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

, ro, quiet,

##### desktop ###########################

Ubuntu

##### lspci #############################

09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5761e Gigabit Ethernet PCIe [14e4:1680] (rev 10)
        Subsystem: Dell Device [1028:0263]
        Kernel driver in use: tg3

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
        Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 009: ID 413c:8156 Dell Computer Corp. Wireless 370 Bluetooth Mini-card
Bus 008 Device 008: ID 413c:8158 Dell Computer Corp. Integrated Touchpad / Trackstick
Bus 008 Device 007: ID 413c:8157 Dell Computer Corp. Integrated Keyboard
Bus 008 Device 006: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

##### rfkill ############################

0: dell-wifi: Wireless LAN
        Soft blocked: no
        Hard blocked: no
1: dell-bluetooth: Bluetooth
        Soft blocked: no
        Hard blocked: no
3: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no

##### lsmod #############################

dell_wmi               12761  0
sparse_keymap          13948  1 dell_wmi
dell_laptop            18168  0
dcdbas                 14928  1 dell_laptop
wmi                    19177  1 dell_wmi

##### interfaces ########################

auto lo
iface lo inet loopback
iface wlan0 inet dhcp
wpa-ssid whitecat
wpa-psk <WPA key removed>

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>
          inet addr:192.168.1.8  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::225:64ff:fe42:6920/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20262 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1593 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3161677 (3.1 MB)  TX bytes:204731 (204.7 KB)
          Interrupt:16

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.8
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Auto *dev*null]] (600 root)

[[/etc/NetworkManager/system-connections/WarHawk-FacStaff]] (600 root)
[ipv6] method=auto
[connection] id=WarHawk-FacStaff | type=802-11-wireless
[802-11-wireless] ssid=WarHawk-FacStaff | mac-address=<MAC address>
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Auto EnglishPad]] (600 root)
[connection] id=Auto EnglishPad | type=802-11-wireless | permissions=user:mragland:;
[802-11-wireless] ssid=EnglishPad

[[/etc/NetworkManager/system-connections/whitecat 1]] (600 root)
[connection] id=whitecat 1 | type=802-11-wireless
[802-11-wireless] ssid=whitecat | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto AUM-FacStaff]] (600 root)
[ipv6] method=ignore
[connection] id=Auto AUM-FacStaff | type=802-11-wireless | permissions=user:mragland:;
[802-11-wireless] ssid=AUM-FacStaff
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Auto AUM-WebPortal]] (600 root)
[connection] id=Auto AUM-WebPortal | type=802-11-wireless | permissions=user:mragland:;
[802-11-wireless] ssid=AUM-WebPortal

[[/etc/NetworkManager/system-connections/Auto linksys]] (600 root)
[connection] id=Auto linksys | type=802-11-wireless | permissions=user:mragland:; | autoconnect=false
[802-11-wireless] ssid=linksys

[[/etc/NetworkManager/system-connections/Auto wirelessnetwork]] (600 root)
[connection] id=Auto wirelessnetwork | type=802-11-wireless | permissions=user:mragland:;
[802-11-wireless] ssid=wirelessnetwork

[[/etc/NetworkManager/system-connections/Verizon MIFI2200 0244]] (600 root)
[connection] id=Verizon MIFI2200 0244 | type=802-11-wireless | permissions=user:mragland:;
[802-11-wireless] ssid=Verizon MIFI2200 0244

[[/etc/NetworkManager/system-connections/2WIRE959]] (600 root)
[connection] id=2WIRE959 | type=802-11-wireless
[802-11-wireless] ssid=2WIRE959 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto Guestnet 539]] (600 root)
[connection] id=Auto Guestnet 539 | type=802-11-wireless | permissions=user:mragland:;
[802-11-wireless] ssid=Guestnet 539

[[/etc/NetworkManager/system-connections/whitecat]] (600 root)
[connection] id=whitecat | type=802-11-wireless
[802-11-wireless] ssid=whitecat
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto seahawks]] (600 root)
[connection] id=Auto seahawks | type=802-11-wireless | permissions=user:mragland:;
[802-11-wireless] ssid=seahawks

[[/etc/NetworkManager/system-connections/Resnet3]] (600 root)
[connection] id=Resnet3 | type=802-11-wireless | permissions=user:mragland:;
[802-11-wireless] ssid=Resnet3

[[/etc/NetworkManager/system-connections/dj]] (600 root)
[connection] id=dj | type=802-11-wireless
[802-11-wireless] ssid=dj | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto UKYResnet6]] (600 root)
[connection] id=Auto UKYResnet6 | type=802-11-wireless | permissions=user:mragland:;
[802-11-wireless] ssid=UKYResnet6

[[/etc/NetworkManager/system-connections/Auto Insight_WiFi_4701]] (600 root)
[connection] id=Auto Insight_WiFi_4701 | type=802-11-wireless | permissions=user:mragland:;
[802-11-wireless] ssid=Insight_WiFi_4701

[[/etc/NetworkManager/system-connections/Auto Ray-El-Guest-2.4GHz]] (600 root)
[connection] id=Auto Ray-El-Guest-2.4GHz | type=802-11-wireless | permissions=user:mragland:;
[802-11-wireless] ssid=Ray-El-Guest-2.4GHz

[[/etc/NetworkManager/system-connections/Auto daveandsandy]] (600 root)
[connection] id=Auto daveandsandy | type=802-11-wireless | permissions=user:mragland:;
[802-11-wireless] ssid=daveandsandy

[[/etc/NetworkManager/system-connections/ratliff]] (600 root)
[connection] id=ratliff | type=802-11-wireless
[802-11-wireless] ssid=ratliff | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto 2WIRE820]] (600 root)
[connection] id=Auto 2WIRE820 | type=802-11-wireless | permissions=user:mragland:;
[802-11-wireless] ssid=2WIRE820

[[/etc/NetworkManager/system-connections/Auto belkin54g]] (600 root)
[connection] id=Auto belkin54g | type=802-11-wireless | permissions=user:mragland:; | autoconnect=false
[802-11-wireless] ssid=belkin54g

[[/etc/NetworkManager/system-connections/Auto Wireless]] (600 root)
[connection] id=Auto Wireless | type=802-11-wireless | permissions=user:mragland:;
[802-11-wireless] ssid=Wireless

##### iw reg get ########################

Region: America/Chicago (based on set time zone)

country 00:
        (2402 - 2472 @ 40), (6, 20)
        (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN, NO-IBSS
        (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
        (5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN, NO-IBSS
        (5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS
        (5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

##### /etc/modules ######################

lp
rtc

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

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/oss-compat.conf]
install snd-pcm modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq $CMDLINE_OPTS && { modprobe --quiet snd-seq-midi ; modprobe --quiet snd-seq-oss ; : ; }

[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss

                 [/etc/modprobe.d/wireless-bcm43142-dkms.conf]
blacklist b44
blacklist b43legacy
blacklist b43
blacklist brcm80211
blacklist brcmsmac
blacklist ssb

##### rc.local ##########################

nmcli con up id whitecat

exit 0

##### pm-utils ##########################

[/etc/pm/sleep.d/98gsynaptics] (644 root)
if [[ ${1} =~ (thaw|resume) ]] ; then
  synaptics() {
    # sleep to give time for X
    sleep 4s
    who | while read line ; do
      a=(${line})
      regex="^:[[:digit:]]"
      if [[ ${a[1]} =~ $regex ]] ; then
        init="sudo -H -u ${a[0]} DISPLAY=${a[1]}
gsynaptics-init"
        eval "${init}"
      fi
    done
  }
  # run in background so sleep doesn't hold up resume
  synaptics &
  # disown so exiting shell doesn't kill function
  disown %1
fi

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x14e4:0x1680 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4315 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.5/0000:20:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"
# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1c.1/0000:08:00.0 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

########## wireless info END ############

```

Again, thanks for any help.

---

### Post by chili555 on 2015-02-09
Please do:```
sudo rm /etc/modprobe.d/wireless-bcm43142-dkms.conf
sudo modprobe b43
```Enjoy your wireless!

---

### Post by mfrag on 2015-02-09
Thanks, chili555.  Still no wireless though.  But it appears progress is being made.  Here is the output of the commands you posted earlier:

```
mragland@wielandt:~$ !rf
rfkill list all
0: dell-wifi: Wireless LAN
        Soft blocked: no
        Hard blocked: no
1: dell-bluetooth: Bluetooth
        Soft blocked: no
        Hard blocked: no
2: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
3: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
mragland@wielandt:~$ sudo iwlist wlan0 scan
[sudo] password for mragland: 
wlan0     Interface doesn't support scanning : Network is down

mragland@wielandt:~$ lsmod | grep b43
b43                   387371  0 
bcma                   52096  1 b43
mac80211              630669  1 b43
cfg80211              484040  2 b43,mac80211
ssb                    62379  1 b43
mragland@wielandt:~$ dmesg | grep b43
[   41.331143] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   41.372236] b43-phy0: Found PHY: Analog 6, Type 5 (LP), Revision 1
mragland@wielandt:~$ 

```

Any suggestions?

---

### Post by mfrag on 2015-02-09
Found this in my logs.  Does it indicate anything?

```
** (process:2012): WARNING **: Could not initialize NMClient /org/freedesktop/NetworkManager: The name org.freedesktop.NetworkManager was not provided by any .service files
Error: nmcli (0.9.8.8) and NetworkManager (unknown) versions don't match. Force execution using --nocheck, but the results are unpredictable.

```

---

### Post by chili555 on 2015-02-09
You have faulty entries in /etc/network/interfaces; I'd eliminate them and see if NM will do the job. Please comment out your entries:```
auto lo
iface lo inet loopback
#iface wlan0 inet dhcp
#wpa-ssid whitecat
#wpa-psk <WPA key removed>

```Reboot.

---

### Post by mfrag on 2015-02-09
That did the job.  I really appreciate the help!  Posting from wireless connection now.

---

### Post by chili555 on 2015-02-09
Awesome!

Just for the benefit of you and the searchers, it's always a bit risky to mix and match manual methods like /etc/network/interfaces and Network Manager. Your entries missed the key phrase 'auto wlan0.' That means that wlan0 will *only* be brought up upon a command:```
sudo ifup wlan0
```The command never came and therefor:> mragland@wielandt:~$ sudo iwlist wlan0 scan
[sudo] password for mragland: 
wlan0     Interface doesn't support scanning : [COLOR="#FF0000"]Network is down[/COLOR]
It was down because you never asked it to stand up!

In most cases, NM will do a perfectly adequate job; that's saying a lot coming from an olde skool Linux guy like me!!!

---

