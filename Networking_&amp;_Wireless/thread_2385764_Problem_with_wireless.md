---
title: "Problem with wireless"
date: 2018-02-24
forum: Networking &amp; Wireless
---

### Post by undajf90 on 2018-02-24
Hi!

I'm new to Ubuntu and I have a problem with my wifi on ubuntu 17.10. My laptop is Acer Aspire E1-572. My Fn + F3 doesn't work and my airplane mode button is greyed out. This is as far as i have come:

rfkill list all gave me:

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

lsmod gave me:

```
Module                  Size  Used by
nls_iso8859_1          16384  1
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
uvcvideo               90112  0
snd_soc_rt5640        118784  0
kvm_intel             200704  0
snd_soc_rl6231         16384  1 snd_soc_rt5640
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
snd_soc_core          229376  1 snd_soc_rt5640
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
videodev              176128  3 uvcvideo,videobuf2_core,videobuf2_v4l2
media                  40960  2 uvcvideo,videodev
snd_hda_codec_realtek    94208  1
snd_hda_codec_hdmi     49152  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
kvm                   581632  1 kvm_intel
snd_compress           20480  1 snd_soc_core
snd_hda_intel          40960  8
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
arc4                   16384  2
snd_hwdep              20480  1 snd_hda_codec
ac97_bus               16384  1 snd_soc_core
ath9k                 151552  0
ath9k_common           36864  1 ath9k
snd_pcm_dmaengine      16384  1 snd_soc_core
ath9k_hw              462848  2 ath9k,ath9k_common
irqbypass              16384  1 kvm
ath                    28672  3 ath9k_hw,ath9k,ath9k_common
snd_pcm                98304  7 snd_hda_intel,snd_hda_codec,snd_pcm_dmaengine,snd_hda_core,snd_soc_rt5640,snd_hda_codec_hdmi,snd_soc_core
mac80211              778240  1 ath9k
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
intel_cstate           20480  0
intel_rapl_perf        16384  0
cfg80211              610304  4 mac80211,ath9k,ath,ath9k_common
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
mei_me                 40960  0
joydev                 20480  0
snd_timer              32768  2 snd_seq,snd_pcm
mei                    98304  1 mei_me
input_leds             16384  0
serio_raw              16384  0
dw_dmac                16384  0
shpchp                 36864  0
lpc_ich                24576  0
snd                    81920  29 snd_compress,snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_soc_core,snd_pcm
snd_soc_sst_acpi       16384  0
dw_dmac_core           24576  1 dw_dmac
snd_soc_sst_match      16384  1 snd_soc_sst_acpi
elan_i2c               36864  0
8250_dw                16384  0
soundcore              16384  1 snd
spi_pxa2xx_platform    24576  0
wmi_bmof               16384  0
soc_button_array       16384  0
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              24576  0
x_tables               40960  1 ip_tables
autofs4                40960  2
algif_skcipher         20480  0
af_alg                 16384  1 algif_skcipher
dm_crypt               36864  1
hid_generic            16384  0
usbhid                 49152  0
uas                    24576  0
usb_storage            69632  1 uas
i915                 1798144  25
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
pcbc                   16384  0
i2c_algo_bit           16384  1 i915
drm_kms_helper        167936  1 i915
aesni_intel           188416  2
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
aes_x86_64             20480  1 aesni_intel
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
cryptd                 24576  4 crypto_simd,ghash_clmulni_intel,aesni_intel
drm                   356352  25 i915,drm_kms_helper
ahci                   36864  3
psmouse               147456  0
libahci                32768  1 ahci
wmi                    24576  1 wmi_bmof
sdhci_acpi             16384  0
video                  40960  1 i915
sdhci                  45056  1 sdhci_acpi
i2c_hid                20480  0
hid                   118784  3 i2c_hid,hid_generic,usbhid
```

cat /sys/class/rfkill/rfkill0/hard gave me:

1

i also tried:

sudo -i
echo 0 > /sys/class/rfkill/rfkill0/hard

it gave me:

Permission denied

so i tried:

chmod 744 hard

and tried the same thing again but this time I got:

-bash: echo: write error: Input/output error


This is as far as i have come so i would like some help :)

---

### Post by wildmanne39 on 2018-02-24
If the Fn + F3 key combination turns your airplane mode on and off and there is no other means of doing it, then I am sure you need to find a way to fix the buttons if they are broken, because there is things we can try if it is a software issue but if it is a hardware issue then no other option but to fix it.

Does it work in windows? if you have windows installed make sure it is enabled in windows before you boot ubuntu.

---

### Post by kerry_s on 2018-02-24
go into your bios & enable from there

---

### Post by undajf90 on 2018-02-24
Shouldn't you be able to switch the airplane on and off in ubuntu (and that "button" is also greyed out in settings)? I hope it's not a hardware issue, thats is why i turned to this forum it's my last resort (i changed the networkadapter a couple of weeks ago). I had windows first so I had the problem there first and I tried all sort of things. So my last try before i was about to dispose of my laptop was to try ubuntu and then when i changed operatingsystem it worked. And a couple of days passed and now im back with the same problem... I would really appreciate if i could get some advise if it is a software issue. 

I forgot to mention that the wifi turned off after i performed the commands "apt-get update" and "apt-get upgrade".

> **kerry_s said:**
> go into your bios & enable from there

i tried pressing F2 when restarting (thats the bios on acer right?) but couldn't find anything about wifi there. Where I in the wrong place?

---

### Post by kerry_s on 2018-02-24
on my laptop, its called "enable network on boot" took me a while to figure that out cause i was looking for wifi.

so look for any network setting.

---

### Post by undajf90 on 2018-02-24
> **kerry_s said:**
> on my laptop, its called "enable network on boot" took me a while to figure that out cause i was looking for wifi.

so look for any network setting.

Found it and unfortunetly it didn't work :(

---

### Post by jeremy31 on 2018-02-24
Try going into UEFI/BIOS settings and reset to defaults.  That might clear the hard block if no switch is present

---

### Post by slackartist2 on 2018-02-24
to clear the hardblock check on this <a href="https://wiki.archlinux.org/index.php/Wireless_network_configuration#Rfkill_caveat">archwiki wireless page</a> i learned how to deal with wireless smoothly from here.

use rfkill to clear the hardblock:
```
rfkill unblock wifi
```

---

### Post by undajf90 on 2018-02-24
> **jeremy31 said:**
> Try going into UEFI/BIOS settings and reset to defaults.  That might clear the hard block if no switch is present

Didn't work :(

> **slackartist2 said:**
> to clear the hardblock check on this <a href="https://wiki.archlinux.org/index.php/Wireless_network_configuration#Rfkill_caveat">archwiki wireless page</a> i learned how to deal with wireless smoothly from here.

use rfkill to clear the hardblock:
```
rfkill unblock wifi
```

Tried it but no diffrence :(

---

### Post by kerry_s on 2018-02-24
run "nm-applet" in term, you should get another wifi icon, go into the settings on that. it has more settings than the standard applet.

try deleting your current connection & reboot.

try to run your live installer, see if it's working when your running live.

---

### Post by jeremy31 on 2018-02-24
See the wireless script link in my signature and post results

---

### Post by undajf90 on 2018-02-25
> **kerry_s said:**
> run "nm-applet" in term, you should get another wifi icon, go into the settings on that. it has more settings than the standard applet.

try deleting your current connection & reboot.

try to run your live installer, see if it's working when your running live.

Tried that but half of the options are greyed out ("Wi-Fi Networks", "WiFi is disabled" and "Connection information") the only visible ones are VPN Connections, Enable Networking, Enable Wi-Fi and Edit connections...

What exactly do you mean by "run your live installer, see if it's working when you're runninglive."?

---

### Post by wildmanne39 on 2018-02-25
He means when you installed ubuntu you if you created a livecd or liveusb it gives you the option to try before you install ubuntu and you want to select the try option and see if wifi works.

---

### Post by undajf90 on 2018-02-25
> **wildmanne39 said:**
> He means when you installed ubuntu you if you created a livecd or liveusb it gives you the option to try before you install ubuntu and you want to select the try option and see if wifi works.

Tried that and it didn't make any diffrence :/

---

### Post by wildmanne39 on 2018-02-25
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created.

---

### Post by undajf90 on 2018-02-25
> **wildmanne39 said:**
> Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created.

i tried doing it "without internet connection" way but exactly how do you run it when you open the wireless-info.txt?

i tried running it through command with "bash wireless-info.txt" and then the "hard blocked" said no but when i tried to connect with my wifipassword it didn't connect it just bounced and i had to write my password again. so i tried restart and then the wifi was gone again... and bash didn't work...

---

### Post by wildmanne39 on 2018-02-25
The script just provides information to help us diagnose your issue, it does not fix the issue so if your wifi showed up again it is just coincidence, if it is showing up and then disappearing in my opinion it is a hardware issue most likely. You can tether your cell phone to your laptop and run the script that way.

---

### Post by undajf90 on 2018-02-25
> **wildmanne39 said:**
> The script just provides information to help us diagnose your issue, it does not fix the issue so if your wifi showed up again it is just coincidence, if it is showing up and then disappearing in my opinion it is a hardware issue most likely. You can tether your cell phone to your laptop and run the script that way.

Okay can the script tell you if it's a hardware issue?

Do you have a guide how i tether my phone to my laptop and run a script? :)

---

### Post by wildmanne39 on 2018-02-25
Try to turn your wifi on with the key combination and make sure that is the only way to enabled it on your laptop because some laptops have more then one way to do it then run:
```
rfkill list all
```
does that clear the block?

Tether to your cell phone it has to be capable of being used as a hotpot and a tethering device but most are these days. You plug the usb charging cable into your cell phone then the other end into your computer and turn on tethering in settings.

Go to the top right corner of the screen and click on the internet connection icon then settings and at the top of the window that opens is a tab that says airplane mode make sure it is turned off, please refer to the attached screenshot.

The screenshot will not upload so you will have to do it without it.

---

### Post by undajf90 on 2018-02-26
> **wildmanne39 said:**
> Try to turn your wifi on with the key combination and make sure that is the only way to enabled it on your laptop because some laptops have more then one way to do it then run:
```
rfkill list all
```
does that clear the block?

Tether to your cell phone it has to be capable of being used as a hotpot and a tethering device but most are these days. You plug the usb charging cable into your cell phone then the other end into your computer and turn on tethering in settings.

Go to the top right corner of the screen and click on the internet connection icon then settings and at the top of the window that opens is a tab that says airplane mode make sure it is turned off, please refer to the attached screenshot.

The screenshot will not upload so you will have to do it without it.

it didn't clear the block :/

internet works now when i tetherd but the laptop is still in airplanemode and the airplane mode button is still greyed out...

---

### Post by undajf90 on 2018-02-26
Here is what i got from the wireless-info.txt:

```

########## wireless info START ##########

Report from: 26 Feb 2018 12:34 CET +0100

Booted last: 26 Feb 2018 00:00 CET +0100

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 17.10
Release:    17.10
Codename:    artful

##### kernel ############################

Linux 4.13.0-36-generic #40-Ubuntu SMP Fri Feb 16 20:07:48 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu on Xorg

##### lspci #############################

01:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: Lite-On Communications Inc QCA9565 / AR9565 Wireless Network Adapter [11ad:0642]
    Kernel driver in use: ath9k

##### lsusb #############################

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 04f2:b3d6 Chicony Electronics Co., Ltd 
Bus 002 Device 003: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 002 Device 002: ID 2a70:f00e  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

##### lsmod #############################

ath9k                 151552  0
snd_soc_rt5640        118784  0
ath9k_common           36864  1 ath9k
snd_soc_rl6231         16384  1 snd_soc_rt5640
ath9k_hw              471040  2 ath9k,ath9k_common
snd_soc_core          229376  1 snd_soc_rt5640
snd_pcm                98304  7 snd_hda_intel,snd_hda_codec,snd_pcm_dmaengine,snd_hda_core,snd_soc_rt5640,snd_hda_codec_hdmi,snd_soc_core
ath                    28672  3 ath9k_hw,ath9k,ath9k_common
mac80211              782336  1 ath9k
cfg80211              614400  4 mac80211,ath9k,ath,ath9k_common
wmi_bmof               16384  0
wmi                    24576  1 wmi_bmof

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp0s20u1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN group default qlen 1000
    link/ether <MAC 'enp0s20u1' [IF1]> brd <MAC address>
    inet 192.168.42.197/24 brd 192.168.42.255 scope global dynamic enp0s20u1
       valid_lft 3480sec preferred_lft 3480sec
    inet6 fe80::6706:253:cde8:a3c5/64 scope link 
       valid_lft forever preferred_lft forever
3: wlp1s0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether <MAC 'wlp1s0' [IF2]> brd <MAC address>

##### iwconfig ##########################

lo        no wireless extensions.

enp0s20u1  no wireless extensions.

wlp1s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

default via 192.168.42.129 dev enp0s20u1 proto static metric 100 
169.254.0.0/16 dev enp0s20u1 scope link metric 1000 
192.168.42.0/24 dev enp0s20u1 proto kernel scope link src 192.168.42.197 metric 100 

##### resolv.conf #######################

nameserver 127.0.0.53

##### network managers ##################

Installed:

    NetworkManager

Running:

root       808     1  0 12:32 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp0s20u1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         OnePlus
GENERAL.PRODUCT:                        OnePlus
GENERAL.DRIVER:                         rndis_host
GENERAL.DRIVER-VERSION:                 22-Aug-2005
GENERAL.FIRMWARE-VERSION:               RNDIS device
GENERAL.HWADDR:                         <MAC 'enp0s20u1' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.0/net/enp0s20u1
GENERAL.IP-IFACE:                       enp0s20u1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 2
GENERAL.CON-UUID:                       c2e831b6-d40c-4bb5-b32c-193dd47f5b6d
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        yes (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   c2e831b6-d40c-4bb5-b32c-193dd47f5b6d | Wired connection 2
IP4.ADDRESS[1]:                         192.168.42.197/24
IP4.GATEWAY:                            192.168.42.129
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.42.129
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.42.129
DHCP4.OPTION[5]:                        ip_address = 192.168.42.197
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.42.129
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.42.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 3150
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.42.129
DHCP4.OPTION[16]:                       dhcp_renewal_time = 1800
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       requested_routers = 1
DHCP4.OPTION[19]:                       expiry = 1519648377
DHCP4.OPTION[20]:                       requested_wpad = 1
DHCP4.OPTION[21]:                       host_name = andreas-Aspire-E1-572
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.42.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       vendor_encapsulated_options = ANDROID_METERED
DHCP4.OPTION[28]:                       next_server = 192.168.42.129
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_lease_time = 3600
DHCP4.OPTION[31]:                       requested_ntp_servers = 1
IP6.ADDRESS[1]:                         fe80::6706:253:cde8:a3c5/64
IP6.GATEWAY:                            --

GENERAL.DEVICE:                         wlp1s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA9565 / AR9565 Wireless Network Adapter
GENERAL.DRIVER:                         ath9k
GENERAL.DRIVER-VERSION:                 4.13.0-36-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp1s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlp1s0
GENERAL.IP-IFACE:                       --
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
CAPABILITIES.SRIOV:                     no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 

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

[device]
wifi.scan-rand-mac-address=no

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/TeliaGateway30-91-8F-E1-B7-3B]] (600 root)
[connection] id=TeliaGateway30-91-8F-E1-B7-3B | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp1s0' [IF2]> | mac-address-blacklist= | ssid=TeliaGateway30-91-8F-E1-B7-3B
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: Europe/Stockholm (based on set time zone)

global
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp0s20u1  no frequency information.

wlp1s0    13 channels in total; available frequencies :
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

wlp1s0    Interface doesn't support scanning : Network is down

enp0s20u1  Interface doesn't support scanning.

##### module infos ######################

[ath9k]
filename:       /lib/modules/4.13.0-36-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     55EFCC9F539475103977285
depends:        mac80211,ath9k_hw,ath9k_common,cfg80211,ath
intree:         Y
name:           ath9k
vermagic:       4.13.0-36-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           led_active_high:Invert LED polarity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)

[ath9k_common]
filename:       /lib/modules/4.13.0-36-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     8A1D2C60031409F8A50F895
depends:        ath9k_hw,cfg80211,ath
intree:         Y
name:           ath9k_common
vermagic:       4.13.0-36-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[ath9k_hw]
filename:       /lib/modules/4.13.0-36-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     BF13127B5F7FC2736913C0C
depends:        ath
intree:         Y
name:           ath9k_hw
vermagic:       4.13.0-36-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[ath]
filename:       /lib/modules/4.13.0-36-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     555BBBB9D4FCA58A05E7C0D
depends:        cfg80211
intree:         Y
name:           ath
vermagic:       4.13.0-36-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[mac80211]
filename:       /lib/modules/4.13.0-36-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B8F500F2EE3AF9C7436BAEE
depends:        cfg80211
intree:         Y
name:           mac80211
vermagic:       4.13.0-36-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.13.0-36-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     A5EDD7467E172A70410EBCD
depends:        
intree:         Y
name:           cfg80211
vermagic:       4.13.0-36-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
led_active_high: -1
nohwcrypt: 0
ps_enable: 0
use_chanctx: 0

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
blacklist acer-wmi

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   21.147712] ath: phy0: WB335 2-ANT card detected
[   21.147714] ath: phy0: Set BT/WLAN RX diversity capability
[   21.154316] ath: phy0: Enable LNA combining
[   21.155406] ath: phy0: ASPM enabled: 0x42
[   21.155407] ath: EEPROM regdomain: 0x65
[   21.155408] ath: EEPROM indicates we should expect a direct regpair map
[   21.155409] ath: Country alpha2 being used: 00
[   21.155409] ath: Regpair used: 0x65
[   21.870009] rndis_host 2-1:1.0 enp0s20u1: renamed from usb0
[   22.884635] ath9k 0000:01:00.0 wlp1s0: renamed from wlan0
[   34.790413] IPv6: ADDRCONF(NETDEV_UP): enp0s20u1: link is not ready
[   34.896883] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready

########## wireless info END ############

```

Does this message give anything? :)

---

### Post by wildmanne39 on 2018-02-26
On a quick look I see a couple of things but not sure if one or both of them is the issue.

I see ```
root       808     1  0 12:32 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

```
where it says 808 I believe that is usually 600, I do not know why that permission is set like that, I will have to do some research and then you have ```
acer-wmi
```
Blacklisted that turns your wifi on and off, when you have a softblock on old laptops mainly, blacklisting that module would make the wifi work but then the wifi can not be turn on or off, I recommend we load that module and see if you can activate it with the key combination but do not restart your computer or the module will not be loaded anymore, if it works we will make it load all the time.

Please do:
```
sudo modprobe acer-wmi
```
Did wifi come on? if not press the key combination and you check after your press the key combination with.
```
rfkill list all
```
Thanks

---

### Post by undajf90 on 2018-02-26
> **wildmanne39 said:**
> On a quick look I see a couple of things but not sure if one or both of them is the issue.

I see ```
root       808     1  0 12:32 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

```
where it says 808 I believe that is usually 600, I do not know why that permission is set like that, I will have to do some research and then you have ```
acer-wmi
```
Blacklisted that turns your wifi on and off, when you have a softblock on old laptops mainly, blacklisting that module would make the wifi work but then the wifi can not be turn on or off, I recommend we load that module and see if you can activate it with the key combination but do not restart your computer or the module will not be loaded anymore, if it works we will make it load all the time.

Please do:
```
sudo modprobe acer-wmi
```
Did wifi come on? if not press the key combination and you check after your press the key combination with.
```
rfkill list all
```
Thanks

Okay, thank you in advance for the research :). 

No nothing happend when i tried the code even after the key combination, still hard blocked: yes :/

---

### Post by wildmanne39 on 2018-02-26
We can try:
```
sudo modprobe -r ath9k
sudo rfkill unblock wifi
sudo modprobe ath9k
```
Does wifi come on or is the block removed, please check with:
```
rfkill list all
```
I think it is a hardware issue, I am happy to have someone else give it a try.

---

### Post by kerry_s on 2018-02-26
i think its hardware as well. have you tried tapping that wifi key several times to make sure its not stuck?

also you said it didn't work live, so i don't think its the os.

---

### Post by wildmanne39 on 2018-02-26
> **kerry_s said:**
> i think its hardware as well. have you tried tapping that wifi key several times to make sure its not stuck?

also you said it didn't work live, so i don't think its the os.

In post 4 he says.
> I had windows first so I had the problem there first and I tried all sort of things. So my last try before i was about to dispose of my laptop was to try ubuntu and then when i changed operatingsystem it worked. And a couple of days passed and now im back with the same problem...
That statement is pretty much a dead give away, in very rare cases it might be something else but I am not sure I have ever seen one.

---

### Post by jeremy31 on 2018-02-26
If nothing else you should be able to put a small piece of tape on one pin of the wifi card and have it work
[https://www.youtube.com/watch?v=yzAKcmlaH1M](https://www.youtube.com/watch?v=yzAKcmlaH1M)

---

### Post by kerry_s on 2018-02-26
yeah, sounds like it was already on its way out from the get go.

---

### Post by undajf90 on 2018-02-26
> **wildmanne39 said:**
> We can try:
```
sudo modprobe -r ath9k
sudo rfkill unblock wifi
sudo modprobe ath9k
```
Does wifi come on or is the block removed, please check with:
```
rfkill list all
```
I think it is a hardware issue, I am happy to have someone else give it a try.

I tried that and that didn't work either.. :( Yeah i'm beginning to suspect that aswell. The thing I find so werid is that when I had windows it worked and all of a sudden it didn't work and I tried everything.. and then I changed to ubuntu and then it worked like a charm for ~ 1 week and when i ran an "apt update" and "apt upgrade" it died.. Is there any way to see with some sort of "check" to see exactly where the hardware issue is?

And ofcourse thank you so much for all the help

---

### Post by undajf90 on 2018-02-26
> **kerry_s said:**
> i think its hardware as well. have you tried tapping that wifi key several times to make sure its not stuck?

also you said it didn't work live, so i don't think its the os.

Yeah i think so too. Tried that and that didn't work either :)

---

### Post by undajf90 on 2018-02-26
> **jeremy31 said:**
> If nothing else you should be able to put a small piece of tape on one pin of the wifi card and have it work
[https://www.youtube.com/watch?v=yzAKcmlaH1M](https://www.youtube.com/watch?v=yzAKcmlaH1M)

Haha in all of my research I never stumbled across this, I will try this and get back to you guys (think it will take some time), maybe this will be the final try before i'll send it to the yard ^^.

---

### Post by undajf90 on 2018-02-26
> **kerry_s said:**
> yeah, sounds like it was already on its way out from the get go.

Haha yeah, but I don't like not figuring things out before I sack them. But isn't there any check you could run to see where the hardware issue lies? :)

---

### Post by kerry_s on 2018-02-26
> **undajf90 said:**
> Haha yeah, but I don't like not figuring things out before I sack them. But isn't there any check you could run to see where the hardware issue lies? :)

when i used to fix those kind of things. the first thing i would have done was pull the wifi card, clean the connecting edge with a little alcohol & put it back together making sure all connections were tight, no loose wires. also i would have blown out the slot, dust gets everywhere.

i'm old now, so i would just stick in a usb wifi & done! :)

---

### Post by wildmanne39 on 2018-02-26
Just to be clear an usb adapter will not work in this case, as long as there is a hardblock the usb adapter will have a hardblock as well.

---

### Post by kerry_s on 2018-02-26
> **wildmanne39 said:**
> Just to be clear an usb adapter will not work in this case, as long as there is a hardblock the usb adapter will have a hardblock as well.

i never knew that. why would that be?
different driver, different everything, it would show as another device with it's own block yes/no wouldn't it? like when you turn off 1 to use the other.

tried to test with a usb wifi, but i haven't used them in ages, so none of them work, 2 actually fell apart. :(

---

### Post by wildmanne39 on 2018-02-26
> **kerry_s said:**
> i never knew that. why would that be?
different driver, different everything, it would show as another device with it's own block yes/no wouldn't it? like when you turn off 1 to use the other.
I am not a sure of why but I have seen several instances where that is the case. I just read a solution to unblock the usb adapter when the internal card is blocked is to blacklist the driver of the internal card and it is supposed to clear the block on the usb adapter but I have not tested it and I do not think that will work if the airplane switch is the cause, it is just what I read and it may or may not work in every case. If he has a usb adapter it is worth a try.

---

### Post by undajf90 on 2018-02-27
Thanks i'll try that kerry_s :)! I don't have a usb adapter, maybe i'll buy one and try, they can't be to expensive. But if the connection works when i tether my phone isn't that almost the same process as using a usb adapter? Wildmanne39 could you please link the solution about unblock the usb adapter, that you talked about above :)?

---

### Post by kerry_s on 2018-02-27
yeah, i would say your phone is exactly like a usb wifi adapter.

---

### Post by undajf90 on 2018-02-27
I think I'll try that before I pick the laptop apart and try the tapething :D

---

### Post by wildmanne39 on 2018-02-27
I can not find the link at this time but all it said to do is to blacklist your internal card, which if your issue is the switch I am not sure it will work but I would like to know for sure, just run:
```
echo "blacklist ath9k" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot and your internal card driver will be blacklisted.

---

### Post by undajf90 on 2018-02-28
> **wildmanne39 said:**
> I can not find the link at this time but all it said to do is to blacklist your internal card, which if your issue is the switch I am not sure it will work but I would like to know for sure, just run:
```
echo "blacklist ath9k" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot and your internal card driver will be blacklisted.

Thanks will try that! What is the command if i would like to reverse that command? is it just a simple "rfkill unblock all"?

---

### Post by wildmanne39 on 2018-02-28
To reverse the blacklist do:
```
sudo sed -i '/blacklist ath9k/ d' /etc/modprobe.d/blacklist.conf

```

---

### Post by undajf90 on 2018-03-01
> **wildmanne39 said:**
> To reverse the blacklist do:
```
sudo sed -i '/blacklist ath9k/ d' /etc/modprobe.d/blacklist.conf

```

Thank you, will get back to you when i've tried it :)!

---

### Post by wildmanne39 on 2018-03-01
Remember this is only if your usb adapter is hardblocked also, then this may help, it will not make your internal wifi card work it will do just the opposite.

---

### Post by undajf90 on 2018-03-01
> **wildmanne39 said:**
> Remember this is only if your usb adapter is hardblocked also, then this may help, it will not make your internal wifi card work it will do just the opposite.

Yeah i understood that, but thanks for the clarification :)

---

### Post by undajf90 on 2018-03-27
Hi!

Sorry for the slow answer :), i have successfully connected a old phone via usb to get the wifi working (maybe not much of a fix but i works for now haha :D). Maybe i will buy a usb wifi adapter and try that and also the tapething but for now this works just fine :). Will write a update in the future when i try the other ways :). 

Thank you for all the help, my first thread and i already love this community!

Cheers

---

### Post by wildmanne39 on 2018-03-27
I am glad it is working and thanks for letting us know.

Enjoy!

---

