---
title: "[SOLVED] &amp;quot;NO DHCPOFFERS&amp;quot;  Wifi Dell Inspiron 9400"
date: 2007-10-12
forum: Networking &amp; Wireless
---

### Post by di98mase on 2007-10-12
I have read a lot about this issue on the forum but the solutions provided have not solved my problem. I have an wifi network inteface (eth1) that has a signal but I cant connect to the Internet since I dont get an IP address from the dhcp-server (as far as I understand). I run Ubuntu 6.0.6 (Dapper) These are the outputs I get when I run different commands:


> 

ifconf:

eth0      Link encap:Ethernet  HWaddr 00:18:00:00:24:56  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 

eth1      Link encap:Ethernet  HWaddr 00:1B:77:24:56:4F  
          inet6 addr: fe80::21b:77ff:fe24:564f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31232 errors:39 dropped:354 overruns:0 frame:0
          TX packets:11 errors:0 dropped:172 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14577 (14.2 KiB)  TX bytes:7948 (7.7 KiB)
          Interrupt:177 Memory:efcff000-efcfffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:781 errors:0 dropped:0 overruns:0 frame:0
          TX packets:781 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:58992 (57.6 KiB)  TX bytes:58992 (57.6 KiB)


my interfaces file looks like (passw removed):


# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp
wpa-driver wext
wpa-ssid Hemnet
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk c5b5454545454545454545454545455482593b50929e80e17dfee69b1a12beeb

pre-up wpa_supplicant -Bw -DLinux -ieth1 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
wireless-essid Hemnet
wireless-key s:ABCDEFG


my wpa_supplicatn.conf:


# Minimal /etc/wpa_supplicant.conf to associate with open
# access points. Please see
# /usr/share/doc/wpasupplicant/examples/README.wpa_s upplicant.conf.gz
# for more complete configuration parameters.
#
# Also see the other files in /usr/share/doc/wpasupplicant/examples/ for
# specific configuration examples.

# path to UNIX socket control interface
ctrl_interface=/var/run/wpa_supplicant

### Example of basic WPA-PSK secured AP
#network={
# ssid="ournet"
# psk="w243sd5f324asdf5123sadf54324"
#}

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=wheel

network={
ssid="Hemnet"
psk="c787878789789789789797afb99a0b8f82593b50929e80e17dfee69b1a12beeb"
}


iwconfig:


eth1      IEEE 802.11g  ESSID:"Hemnet"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:19:5B:D9:E0:DC   
          Bit Rate:24 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=55/100  Signal level=-75 dBm  Noise level=-76 dBm
          Rx invalid nwid:0  Rx invalid crypt:39  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:315   Missed beacon:0


iwlist:

eth1      Scan completed :
 
          Cell 10 - Address: 00:19:00:00:00:DC
                    ESSID:"Hemnet"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=55/100  Signal level=-79 dBm  Noise level=-75 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : TKIP CCMP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 1708ms ago


lshw:

  *-network
       description: Wireless interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0c:00.0
       logical name: eth1
       version: 02
       serial: 00:1b:77:24:56:4f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 multicast=yes wireless=unassociated
       resources: iomemory:efcff000-efcfffff irq:177
  *-usb:0
       description: Bluetooth wireless interface
       product: BCM2045
       vendor: Broadcom Corp
       physical id: 1
       bus info: usb@5:1.4.1
       version: 1.00
       capabilities: bluetooth usb-2.00
       configuration: driver=hci_usb maxpower=0mA speed=12.0MB/s
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 02
       serial: 00:18:8b:d1:24:56
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 multicast=yes
       resources: iomemory:ef9fe000-ef9fffff irq:177

lsmod:

Module                  Size  Used by
isofs                  37688  1 
udf                    88452  0 
ipv6                  265728  6 
rfcomm                 40216  0 
l2cap                  26244  5 rfcomm
ppdev                   9220  0 
speedstep_centrino      8400  1 
cpufreq_userspace       4696  1 
cpufreq_stats           5636  0 
freq_table              4740  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       1920  0 
cpufreq_ondemand        6428  0 
cpufreq_conservative     7332  0 
video                  16260  0 
tc1100_wmi              6916  0 
sony_acpi               5644  0 
pcc_acpi               12416  0 
hotkey                 11556  0 
dev_acpi               11140  0 
container               4608  0 
button                  6672  0 
acpi_sbs               19980  0 
battery                 9988  1 acpi_sbs
ac                      5252  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               21904  1 i2c_acpi_ec
nls_utf8                2176  2 
ntfs                  103536  2 
nls_iso8859_1           4224  2 
nls_cp437               5888  3 
vfat                   13440  2 
fat                    53020  1 vfat
dm_mod                 58936  1 
md_mod                 72532  0 
sbp2                   24196  0 
parport_pc             35780  0 
lp                     11844  0 
parport                36296  3 ppdev,parport_pc,lp
af_packet              22920  6 
arc4                    2048  0 
ieee80211_crypt_wep     4992  0 
joydev                 10048  0 
tsdev                   8000  0 
rtc                    13492  0 
b44                    25740  0 
mii                     5888  1 b44
ipw3945               126620  1 
sdhci                  14848  0 
mmc_core               30104  1 sdhci
ieee80211              37064  1 ipw3945
ieee80211_crypt         6272  2 ieee80211_crypt_wep,ieee80211
pcspkr                  2180  0 
ieee80211_1_1_13       38216  0 
ieee80211_1_1_13_crypt     6784  1 ieee80211_1_1_13
hci_usb                16660  0 
bluetooth              49892  5 rfcomm,l2cap,hci_usb
psmouse                36100  0 
usbhid                 39904  0 
serio_raw               7300  0 
snd_hda_intel          18964  1 
snd_hda_codec         154672  1 snd_hda_intel
hw_random               5652  0 
snd_pcm_oss            53664  0 
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_hda_intel,snd_pcm
shpchp                 45632  0 
pci_hotplug            29236  1 shpchp
intel_agp              22940  1 
agpgart                34888  1 intel_agp
sr_mod                 16932  1 
cdrom                  38560  1 sr_mod
sg                     37920  0 
evdev                   9856  3 
ext3                  135688  1 
jbd                    58772  1 ext3
ide_generic             1536  0 
ohci1394               35124  0 
ieee1394              299832  2 sbp2,ohci1394
ehci_hcd               34184  0 
uhci_hcd               33680  0 
usbcore               130692  5 hci_usb,usbhid,ehci_hcd,uhci_hcd
sd_mod                 19984  7 
generic                 5124  0 
ata_piix               11012  13 
libata                 78992  1 ata_piix
scsi_mod              139496  5 sbp2,sr_mod,sg,sd_mod,libata
thermal                13576  0 
processor              23360  2 speedstep_centrino,thermal
fan                     4868  0 
capability              5000  0 
commoncap               7296  1 capability
vga16fb                13704  1 
vgastate               10368  1 vga16fb
fbcon                  42784  72 
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit





Also I use WPA and I have not tried to remove the encryption.

What seems to be the problem?  I have spent a long time trying to solve the problem but this is my last try...

/di98

---

### Post by Lambert on 2007-10-13
Try setting your config file up like this

```

network={
       ssid="example"
       proto=WPA
      key_mgmt=WPA-PSK
      pairwise=CCMP TKIP
      group=CCMP TKIP 
       psk=06b4be19da289f475aa46a33cb793029d4ab3db7a23ee92382eb0106c72ac7bb
       priority=2
}

```

And if your ssid is not broadcasted add this line in there

scan_ssid=1

Also cycle your router off for 30 seconds and then power on and try to connect.

---

### Post by kevdog on 2007-10-13
There are so many things wrong with your configuration -- in so many ways!!

#1. Reset or delete or just copy your current /etc/network/interfaces file to a backup location, and just make a basic one:

auto lo
iface lo inet loopback

auto eth0
iface eth1 inet dhcp

auto eth1
iface eth1 inet dhcp

#2. Although it seems like want WPA2, I think you need to set up your wpa_supplicant.conf file like the following (yes I know this is different than what you have read):

ap_scan=1
ctrl_interface=/var/run/wpa_supplicant 

network={
        ssid="ESSID_IN_QUOTES"
        scan_ssid=0
        proto=WPA
        key_mgmt=WPA-PSK
        psk="ASCII PSK Password in Quotes"    <----- Can put hex key here without quotes but make sure it is correct
        pairwise=TKIP
        group=TKIP
}

Im basing this on the following:
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK 

Im just trying to match what is states about wpa2 on your iwlist scan statement to the settings in the file (you must have a linksys router)

Then try just connecting from the command line with the following (for you <interface>=eth1):
sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo wpa_supplicant -w -Dipw -i<interface> -c/etc/wpa_supplicant.conf -dd 
sudo ifconfig <interface> up
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>

Give me any output you generate if it doesnt work.  We may have to play around with the cipher, key-mngmt in the conf file.
**[SIZE="3"]Are you certain it can connect to an unencrypted network??? Id confirm this first![/SIZE]**

---

### Post by di98mase on 2007-10-13
Hi all,
 
thanks for your help.
 
This is the solution that made it work for me:
 
I removed the encryption on the router and restored interfaces according to you suggestions in the thread. The network worked immediately. After this I run with WEP also no problem. The next thing will be to run WPA but I will do that some other time...
 
Thanks.

---

