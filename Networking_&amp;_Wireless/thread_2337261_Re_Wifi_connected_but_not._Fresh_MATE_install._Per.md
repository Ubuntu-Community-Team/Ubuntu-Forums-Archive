---
title: "Re: Wifi connected but not. Fresh MATE install. Persistent issue. Please help"
date: 2016-09-16
forum: Networking &amp; Wireless
---

### Post by daniel852 on 2016-09-16
Dear all,

I'm hoping someone could help me with a solution to the DNS_PROBE_FINISHED_NO_INTERNET issue that many users have had. I've searched the forums and reviewed a number of solutions but none seems to work. Connectivity is patchy, not down 100% of the time. I ran MATE for a while with no problems until I reinstalled yesterday. But previously i'd had the same issue using Linux Mint.

Here's some data that might be useful in suggesting a fix:

```
dan@dan-CF-31:~$ lspci -nnk | grep -iA2 net00:19.0 Ethernet controller [0200]: Intel Corporation 82577LM Gigabit Network Connection [8086:10ea] (rev 06)
    Subsystem: Matsushita Electric Industrial Co., Ltd. 82577LM Gigabit Network Connection [10f7:8338]
    Kernel driver in use: e1000e
    Kernel modules: e1000e
--
0a:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6200 [8086:422c] (rev 35)
    Subsystem: Intel Corporation Centrino Advanced-N 6200 2x2 AGN [8086:1301]
    Kernel driver in use: iwlwifi
dan@dan-CF-31:~$ lsusb
Bus 002 Device 003: ID 044e:3001 Alps Electric Co., Ltd UGTZ4 Bluetooth
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 04da:250e Panasonic (Matsushita) 
Bus 001 Device 004: ID 0424:2512 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 003: ID 0430:0530 Sun Microsystems, Inc. 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
dan@dan-CF-31:~$ iwconfig
lo        no wireless extensions.


enp0s25   no wireless extensions.


wlp10s0   IEEE 802.11abgn  ESSID:"EWEPEM"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: A4:2B:B0:E0:C7:6E   
          Bit Rate=130 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:97   Missed beacon:0


dan@dan-CF-31:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
dan@dan-CF-31:~$ lsmod
Module                  Size  Used by
rfcomm                 69632  14
ctr                    16384  1
ccm                    20480  1
nvram                  16384  0
msr                    16384  0
bnep                   20480  2
btusb                  45056  0
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
btintel                16384  1 btusb
bluetooth             520192  39 bnep,btbcm,btrtl,btusb,rfcomm,btintel
joydev                 20480  0
snd_hda_codec_hdmi     53248  1
snd_hda_codec_conexant    24576  1
intel_powerclamp       16384  0
coretemp               16384  0
snd_hda_codec_generic    77824  1 snd_hda_codec_conexant
kvm_intel             172032  0
arc4                   16384  2
pcmcia                 61440  0
iwldvm                233472  0
kvm                   540672  1 kvm_intel
snd_hda_intel          36864  3
snd_hda_codec         135168  4 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_codec_generic,snd_hda_intel
mac80211              737280  1 iwldvm
irqbypass              16384  1 kvm
snd_hda_core           73728  5 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
input_leds             16384  0
serio_raw              16384  0
snd_seq_midi           16384  0
iwlwifi               200704  1 iwldvm
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
yenta_socket           45056  0
pcmcia_rsrc            20480  1 yenta_socket
cfg80211              565248  3 iwlwifi,mac80211,iwldvm
pcmcia_core            24576  3 pcmcia,pcmcia_rsrc,yenta_socket
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
lpc_ich                24576  0
snd                    81920  17 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
shpchp                 36864  0
soundcore              16384  1 snd
8250_fintek            16384  0
tpm_infineon           20480  0
int3403_thermal        16384  0
int3402_thermal        16384  0
int340x_thermal_zone    16384  2 int3402_thermal,int3403_thermal
int3400_thermal        16384  0
acpi_thermal_rel       16384  1 int3400_thermal
panasonic_laptop       16384  0
mac_hid                16384  0
sparse_keymap          16384  1 panasonic_laptop
ip6t_REJECT            16384  1
nf_reject_ipv6         16384  1 ip6t_REJECT
nf_log_ipv6            16384  5
xt_hl                  16384  22
ip6t_rt                16384  3
nf_conntrack_ipv6      20480  8
nf_defrag_ipv6         36864  1 nf_conntrack_ipv6
ipt_REJECT             16384  1
nf_reject_ipv4         16384  1 ipt_REJECT
xt_comment             16384  2
nf_log_ipv4            16384  5
nf_log_common          16384  2 nf_log_ipv4,nf_log_ipv6
xt_LOG                 16384  10
xt_multiport           16384  2
xt_limit               16384  13
xt_tcpudp              16384  18
xt_addrtype            16384  4
nf_conntrack_ipv4      16384  8
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_conntrack           16384  16
ip6table_filter        16384  1
ip6_tables             28672  1 ip6table_filter
nf_conntrack_netbios_ns    16384  0
nf_conntrack_broadcast    16384  1 nf_conntrack_netbios_ns
nf_nat_ftp             16384  0
nf_nat                 24576  1 nf_nat_ftp
nf_conntrack_ftp       20480  1 nf_nat_ftp
nf_conntrack          106496  8 nf_nat_ftp,nf_conntrack_netbios_ns,nf_nat,xt_conntrack,nf_conntrack_broadcast,nf_conntrack_ftp,nf_conntrack_ipv4,nf_conntrack_ipv6
iptable_filter         16384  1
ip_tables              24576  1 iptable_filter
parport_pc             32768  0
ppdev                  20480  0
x_tables               36864  15 ip6table_filter,xt_hl,xt_comment,ip_tables,xt_tcpudp,xt_limit,xt_conntrack,xt_LOG,xt_multiport,iptable_filter,ip6t_rt,ipt_REJECT,ip6_tables,xt_addrtype,ip6t_REJECT
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
drbg                   32768  1
ansi_cprng             16384  0
algif_skcipher         20480  0
af_alg                 16384  1 algif_skcipher
dm_crypt               28672  1
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  2 hid_generic,usbhid
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
aesni_intel           167936  4
aes_x86_64             20480  1 aesni_intel
i915                 1208320  8
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
cryptd                 20480  3 aesni_intel,ablk_helper
psmouse               126976  0
i2c_algo_bit           16384  1 i915
ahci                   36864  2
drm_kms_helper        147456  1 i915
libahci                32768  1 ahci
syscopyarea            16384  1 drm_kms_helper
intel_ips              20480  0
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
e1000e                237568  0
sdhci_pci              28672  0
fb_sys_fops            16384  1 drm_kms_helper
sdhci                  45056  1 sdhci_pci
drm                   364544  5 i915,drm_kms_helper
ptp                    20480  1 e1000e
pps_core               20480  1 ptp
video                  40960  1 i915
fjes                   28672  0



```

Many thanks in advance!

ps: I've now been able to log into another wifi so perhaps the problem is compatibility with my router at home? Any advice would be greatly appreciated. Complete beginner here.

---

### Post by wildmanne39 on 2016-09-16
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. Be sure you are at the router you can not connect too when you run the script.
Thanks

---

### Post by daniel852 on 2016-09-16
Wild Man, 

Thanks for the response. I appear to have solved the issue by identifying the exact driver I needed from Intel and adding it to me drivers directory (it was not automatically installed by Ubuntu's driver search function).

Hopefully that's the end of that. If the issue resurfaces I'll try the script you linked to.

Thanks again.

---

### Post by wildmanne39 on 2016-09-16
The driver for your device does come with ubuntu and it was loaded, did you install a different updated driver?
Good Luck! and if it acts up post back.

---

### Post by daniel852 on 2016-09-16
Oh, I see. I'm really not sure why it's working now then. I'll try and run the script in case the problems come back. Thanks!

[Edit: Yes, I installed a driver I found here for the Intel® Centrino® Advanced-N 6200: [link]("http://www.intel.com/content/www/us/en/support/network-and-i-o/wireless-networking/000005511.html")]

Hi again, and sorry for continuing to update this thread after marking it as solved. I'm still having problems, including drops in connectivity and now, strangely, I'm connected again but have no graphical menu in the panel for my wireless connections. I've posted the results of your script below in case anything jumps out at you.

```


########## wireless info START ##########


Report from: 17 Sep 2016 01:11 ICT +0700


Booted last: 17 Sep 2016 00:00 ICT +0700


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.1 LTS
Release:	16.04
Codename:	xenial


##### kernel ############################


Linux 4.4.0-36-generic #55-Ubuntu SMP Thu Aug 11 18:01:55 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


MATE


##### lspci #############################


00:19.0 Ethernet controller [0200]: Intel Corporation 82577LM Gigabit Network Connection [8086:10ea] (rev 06)
	Subsystem: Matsushita Electric Industrial Co., Ltd. 82577LM Gigabit Network Connection [10f7:8338]
	Kernel driver in use: e1000e


0a:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6200 [8086:422c] (rev 35)
	Subsystem: Intel Corporation Centrino Advanced-N 6200 2x2 AGN [8086:1301]
	Kernel driver in use: iwlwifi


##### lsusb #############################


Bus 002 Device 003: ID 044e:3001 Alps Electric Co., Ltd UGTZ4 Bluetooth
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 04da:250e Panasonic (Matsushita) 
Bus 001 Device 004: ID 0424:2512 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 003: ID 0430:0530 Sun Microsystems, Inc. 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255


##### rfkill ############################


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


iwldvm                233472  0
mac80211              737280  1 iwldvm
iwlwifi               200704  1 iwldvm
cfg80211              565248  3 iwlwifi,mac80211,iwldvm


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp0s25   Link encap:Ethernet  HWaddr <MAC 'enp0s25' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:eb100000-eb120000 


wlp10s0   Link encap:Ethernet  HWaddr <MAC 'wlp10s0' [IF2]>  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlp10s0' [IF2]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:360249 errors:0 dropped:0 overruns:0 frame:0
          TX packets:238700 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:418556020 (418.5 MB)  TX bytes:42755652 (42.7 MB)


##### iwconfig ##########################


lo        no wireless extensions.


enp0s25   no wireless extensions.


wlp10s0   IEEE 802.11abgn  ESSID:"EWEPEM"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'EWEPEM' [AN3]>   
          Bit Rate=78 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:5  Invalid misc:1535   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlp10s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp10s0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp10s0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root      1028     1  0 Sep16 ?        00:00:08 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlp10s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Centrino Advanced-N 6200 (2x2 AGN)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.4.0-36-generic
GENERAL.FIRMWARE-VERSION:               9.176.4.1 build 15835
GENERAL.HWADDR:                         <MAC 'wlp10s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:0a:00.0/net/wlp10s0
GENERAL.IP-IFACE:                       wlp10s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     EWEPEM 1
GENERAL.CON-UUID:                       50afd696-c280-4a05-8fd3-fd3e8b5e5802
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/5
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     39 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3,5}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   50afd696-c280-4a05-8fd3-fd3e8b5e5802 | EWEPEM 1
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   459c0568-c800-4ef6-9ab8-27973a292e35 | LOBBY-C
IP4.ADDRESS[1]:                         192.168.1.103/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        server_name = TP-LINK
DHCP4.OPTION[5]:                        domain_name_servers = 192.168.1.1
DHCP4.OPTION[6]:                        ip_address = 192.168.1.103
DHCP4.OPTION[7]:                        requested_static_routes = 1
DHCP4.OPTION[8]:                        dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[9]:                        requested_time_offset = 1
DHCP4.OPTION[10]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       dhcp_rebinding_time = 226800
DHCP4.OPTION[13]:                       requested_domain_name_servers = 1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       requested_broadcast_address = 1
DHCP4.OPTION[16]:                       routers = 192.168.1.1
DHCP4.OPTION[17]:                       dhcp_renewal_time = 129600
DHCP4.OPTION[18]:                       requested_domain_name = 1
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1474286429
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       host_name = dhcppc3
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       next_server = 192.168.1.1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 259200
IP6.ADDRESS[1]:                         fe80::<IP6 'wlp10s0' [IF2]>/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         enp0s25
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        82577LM Gigabit Network Connection
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.12-1
GENERAL.HWADDR:                         <MAC 'enp0s25' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:19.0/net/enp0s25
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
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


SSID               BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
ASUS-MKT           <MAC 'ASUS-MKT' [AN1]>  Infra  6     2437 MHz  54 Mbit/s  72      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
ymcadondon         <MAC 'ymcadondon' [AN2]>  Infra  11    2462 MHz  54 Mbit/s  72      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
EWEPEM             <MAC 'EWEPEM' [AN3]>  Infra  1     2412 MHz  54 Mbit/s  62      &#9602;&#9604;&#9606;_  WPA2       yes     * 
LOBBY-C            <MAC 'LOBBY-C' [AN4]>  Infra  6     2437 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA1       no        
Ceil_11/5          <MAC 'Ceil_11/5' [AN5]>  Infra  8     2447 MHz  54 Mbit/s  50      &#9602;&#9604;__  WPA2       no        
Kenggy             <MAC 'Kenggy' [AN6]>  Infra  3     2422 MHz  54 Mbit/s  45      &#9602;&#9604;__  WPA1 WPA2  no        
true_home2G_C98    <MAC 'true_home2G_C98' [AN7]>  Infra  1     2412 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA1 WPA2  no        
true_home2G_585    <MAC 'true_home2G_585' [AN8]>  Infra  1     2412 MHz  54 Mbit/s  30      &#9602;___  WPA2       no        
PARWANI_SONIA      <MAC 'PARWANI_SONIA' [AN9]>  Infra  6     2437 MHz  54 Mbit/s  29      &#9602;___  WPA2       no        
--                 <MAC '--' [AN10]>  Infra  6     2437 MHz  54 Mbit/s  29      &#9602;___  --         no        
JAVIER 5GHz        <MAC 'JAVIER 5GHz' [AN11]>  Infra  60    5300 MHz  54 Mbit/s  29      &#9602;___  WPA1 WPA2  no        
true_homewifi_HUP  <MAC 'true_homewifi_HUP' [AN12]>  Infra  11    2462 MHz  54 Mbit/s  27      &#9602;___  WPA1 WPA2  no        


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


[[/etc/NetworkManager/system-connections/EWEPEM]] (600 root)
[connection] id=EWEPEM | type=wifi | permissions=user:ubuntu-mate:;
[wifi] mac-address=<MAC 'wlp10s0' [IF2]> | mac-address-blacklist= | ssid=EWEPEM
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/LOBBY-C]] (600 root)
[connection] id=LOBBY-C | type=wifi | permissions=user:dan:;
[wifi] mac-address=<MAC 'wlp10s0' [IF2]> | mac-address-blacklist= | ssid=LOBBY-C
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/_@  truemoveH]] (600 root)
[connection] id=.@  truemoveH | type=wifi | permissions=user:dan:;
[wifi] mac-address=<MAC 'wlp10s0' [IF2]> | mac-address-blacklist= | ssid=.@  truemoveH
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/   .@  TRUEWIFI]] (600 root)
[connection] id=\s\s\s.@  TRUEWIFI | type=wifi | permissions=user:dan:;
[wifi] mac-address=<MAC 'wlp10s0' [IF2]> | mac-address-blacklist= | ssid=\s\s\s.@  TRUEWIFI
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/EWEPEM 1]] (600 root)
[connection] id=EWEPEM 1 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp10s0' [IF2]> | mac-address-blacklist= | ssid=EWEPEM
[ipv4] method=auto
[ipv6] method=ignore


##### iw reg get ########################


Region: Asia/Bangkok (based on set time zone)


country TW: DFS-JP
	(2402 - 2472 @ 40), (N/A, 30), (N/A)
	(5270 - 5330 @ 40), (N/A, 17), (0 ms), DFS
	(5490 - 5590 @ 80), (N/A, 30), (0 ms), DFS
	(5650 - 5710 @ 40), (N/A, 30), (0 ms), DFS
	(5735 - 5835 @ 80), (N/A, 30), (N/A)


##### iwlist channels ###################


lo        no frequency information.


enp0s25   no frequency information.


wlp10s0   27 channels in total; available frequencies :
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
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency:2.412 GHz (Channel 1)


##### iwlist scan #######################


lo        Interface doesn't support scanning.


enp0s25   Interface doesn't support scanning.


wlp10s0   Interface doesn't support scanning : Device or resource busy


##### module infos ######################


[iwldvm]
filename:       /lib/modules/4.4.0-36-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     6A40B68AAA6792A5BDEA010
depends:        mac80211,iwlwifi,cfg80211
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 
parm:           force_cam:force continuously aware mode (no power saving at all) (bool)


[mac80211]
filename:       /lib/modules/4.4.0-36-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B10AF1CD828D26173EA0378
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename:       /lib/modules/4.4.0-36-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265D-13.ucode
firmware:       iwlwifi-7265-13.ucode
firmware:       iwlwifi-3160-13.ucode
firmware:       iwlwifi-7260-13.ucode
firmware:       iwlwifi-8000-13.ucode
srcversion:     651BF6CBF283F6F817B8F3A
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           nvm_file:NVM file name (charp)
parm:           d0i3_disable:disable d0i3 functionality (default: Y) (bool)
parm:           lar_disable:disable LAR functionality (default: N) (bool)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)


[cfg80211]
filename:       /lib/modules/4.4.0-36-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[iwldvm]
force_cam: Y


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500


[iwlwifi]
11n_disable: 0
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
d0i3_disable: Y
fw_monitor: N
fw_restart: Y
lar_disable: N
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: Y


[cfg80211]
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


[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


[/etc/pm/power.d/disable_wol] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/laptop-mode] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/pci_devices] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/pcie_aspm] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/sched-powersave] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/usb_bluetooth] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/wireless] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/xfs_buffer] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


##### udev rules ########################


##### dmesg #############################


[21593.578859] iwlwifi 0000:0a:00.0:                 CSR_GPIO_IN: 0X0000000f
[21593.578884] iwlwifi 0000:0a:00.0:                   CSR_RESET: 0X00000000
[21593.578909] iwlwifi 0000:0a:00.0:                CSR_GP_CNTRL: 0X080403c5
[21593.578934] iwlwifi 0000:0a:00.0:                  CSR_HW_REV: 0X00000074
[21593.578959] iwlwifi 0000:0a:00.0:              CSR_EEPROM_REG: 0X02010ffd
[21593.578984] iwlwifi 0000:0a:00.0:               CSR_EEPROM_GP: 0X90000001
[21593.579009] iwlwifi 0000:0a:00.0:              CSR_OTP_GP_REG: 0X00030001
[21593.579033] iwlwifi 0000:0a:00.0:                 CSR_GIO_REG: 0X00080042
[21593.579058] iwlwifi 0000:0a:00.0:            CSR_GP_UCODE_REG: 0X00001db2
[21593.579083] iwlwifi 0000:0a:00.0:           CSR_GP_DRIVER_REG: 0X00000002
[21593.579108] iwlwifi 0000:0a:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[21593.579133] iwlwifi 0000:0a:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[21593.579157] iwlwifi 0000:0a:00.0:                 CSR_LED_REG: 0X00000040
[21593.579182] iwlwifi 0000:0a:00.0:        CSR_DRAM_INT_TBL_REG: 0X880c4292
[21593.579207] iwlwifi 0000:0a:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[21593.579232] iwlwifi 0000:0a:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[21593.579257] iwlwifi 0000:0a:00.0:      CSR_MONITOR_STATUS_REG: 0X7bf7ffd7
[21593.579281] iwlwifi 0000:0a:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[21593.579306] iwlwifi 0000:0a:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[21593.579308] iwlwifi 0000:0a:00.0: FH register values:
[21593.579342] iwlwifi 0000:0a:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X2208b700
[21593.579357] iwlwifi 0000:0a:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X02208bf0
[21593.579371] iwlwifi 0000:0a:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000068
[21593.579385] iwlwifi 0000:0a:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80801114
[21593.579400] iwlwifi 0000:0a:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[21593.579413] iwlwifi 0000:0a:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[21593.579428] iwlwifi 0000:0a:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[21593.579442] iwlwifi 0000:0a:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[21593.579456] iwlwifi 0000:0a:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[21593.579459] iwlwifi 0000:0a:00.0: Loaded firmware version: 9.176.4.1 build 15835
[21593.579609] iwlwifi 0000:0a:00.0: Start IWL Error Log Dump:
[21593.579610] iwlwifi 0000:0a:00.0: Status: 0x0000004C, count: 5
[21593.579612] iwlwifi 0000:0a:00.0: 0x00000016 | NMI_INTERRUPT_TRM           
[21593.579614] iwlwifi 0000:0a:00.0: 0x000007C0 | uPc
[21593.579615] iwlwifi 0000:0a:00.0: 0x00000686 | branchlink1
[21593.579616] iwlwifi 0000:0a:00.0: 0x000007C4 | branchlink2
[21593.579617] iwlwifi 0000:0a:00.0: 0x00000996 | interruptlink1
[21593.579619] iwlwifi 0000:0a:00.0: 0x0000F836 | interruptlink2
[21593.579620] iwlwifi 0000:0a:00.0: 0x00000040 | data1
[21593.579621] iwlwifi 0000:0a:00.0: 0x07030000 | data2
[21593.579623] iwlwifi 0000:0a:00.0: 0x00011CBE | line
[21593.579624] iwlwifi 0000:0a:00.0: 0x9E816810 | beacon time
[21593.579625] iwlwifi 0000:0a:00.0: 0x90D287F0 | tsf low
[21593.579626] iwlwifi 0000:0a:00.0: 0x0000000A | tsf hi
[21593.579628] iwlwifi 0000:0a:00.0: 0x00000000 | time gp1
[21593.579629] iwlwifi 0000:0a:00.0: 0xF2C387F7 | time gp2
[21593.579630] iwlwifi 0000:0a:00.0: 0x00000000 | time gp3
[21593.579631] iwlwifi 0000:0a:00.0: 0x000109B0 | uCode version
[21593.579633] iwlwifi 0000:0a:00.0: 0x00000074 | hw version
[21593.579634] iwlwifi 0000:0a:00.0: 0x0048D704 | board version
[21593.579635] iwlwifi 0000:0a:00.0: 0xC5331D9C | hcmd
[21593.579637] iwlwifi 0000:0a:00.0: 0x27863802 | isr0
[21593.579638] iwlwifi 0000:0a:00.0: 0x1103E000 | isr1
[21593.579639] iwlwifi 0000:0a:00.0: 0x0000001F | isr2
[21593.579641] iwlwifi 0000:0a:00.0: 0x014338C3 | isr3
[21593.579642] iwlwifi 0000:0a:00.0: 0x00000000 | isr4
[21593.579643] iwlwifi 0000:0a:00.0: 0x00004110 | isr_pref
[21593.579644] iwlwifi 0000:0a:00.0: 0x00011CBE | wait_event
[21593.579646] iwlwifi 0000:0a:00.0: 0x000000D4 | l2p_control
[21593.579647] iwlwifi 0000:0a:00.0: 0x00000000 | l2p_duration
[21593.579648] iwlwifi 0000:0a:00.0: 0x00000007 | l2p_mhvalid
[21593.579650] iwlwifi 0000:0a:00.0: 0x00103042 | l2p_addr_match
[21593.579651] iwlwifi 0000:0a:00.0: 0x00000035 | lmpm_pmg_sel
[21593.579652] iwlwifi 0000:0a:00.0: 0x25090952 | timestamp
[21593.579654] iwlwifi 0000:0a:00.0: 0x00000000 | flow_handler
[21593.579734] iwlwifi 0000:0a:00.0: Start IWL Event Log Dump: display last 20 entries
[21593.579753] iwlwifi 0000:0a:00.0: EVT_LOGT:4072898240:0x00000001:0204
[21593.579785] iwlwifi 0000:0a:00.0: EVT_LOGT:4072898245:0x00000001:0219
[21593.579816] iwlwifi 0000:0a:00.0: EVT_LOGT:4072898245:0x01000110:0211
[21593.579848] iwlwifi 0000:0a:00.0: EVT_LOGT:4072898414:0x00000000:0212
[21593.579879] iwlwifi 0000:0a:00.0: EVT_LOGT:4072898462:0x00000000:0215
[21593.579910] iwlwifi 0000:0a:00.0: EVT_LOGT:4072898466:0x00000008:0220
[21593.579942] iwlwifi 0000:0a:00.0: EVT_LOGT:4072898484:0x00000000:0302
[21593.579974] iwlwifi 0000:0a:00.0: EVT_LOGT:4072898514:0x000000d4:0303
[21593.580005] iwlwifi 0000:0a:00.0: EVT_LOGT:4072898519:0x000006d9:0217
[21593.580037] iwlwifi 0000:0a:00.0: EVT_LOGT:4072898520:0x02d8001c:0217
[21593.580068] iwlwifi 0000:0a:00.0: EVT_LOGT:4072900466:0x04c4004e:0401
[21593.580100] iwlwifi 0000:0a:00.0: EVT_LOGT:4072900502:0x02d9001c:0206
[21593.580131] iwlwifi 0000:0a:00.0: EVT_LOGT:4072900503:0x00000001:0204
[21593.580163] iwlwifi 0000:0a:00.0: EVT_LOGT:4072900508:0x00000001:0219
[21593.580195] iwlwifi 0000:0a:00.0: EVT_LOGT:4072900509:0x01000110:0211
[21593.580226] iwlwifi 0000:0a:00.0: EVT_LOGT:4072900542:0x00000000:0256 (repeated 2 times)
[21593.580290] iwlwifi 0000:0a:00.0: EVT_LOGT:4072900543:0x01020084:0212
[21593.580321] iwlwifi 0000:0a:00.0: EVT_LOGT:4072900596:0x000000e1:0123
[21593.580352] iwlwifi 0000:0a:00.0: EVT_LOGT:4072900621:0x00000000:0125
[21593.580873] iwlwifi 0000:0a:00.0: L1 Enabled - LTR Disabled (repeated 2 times)
[21593.581217] iwlwifi 0000:0a:00.0: Radio type=0x1-0x3-0x1
[21593.795190] iwlwifi 0000:0a:00.0: L1 Enabled - LTR Disabled (repeated 2 times)
[21593.795510] iwlwifi 0000:0a:00.0: Radio type=0x1-0x3-0x1
[21626.392703] [UFW BLOCK] IN=wlp10s0 OUT= MAC=01:00:5e:00:00:01:<MAC 'EWEPEM' [AN3]>:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=47480 PROTO=2 
[21751.391103] [UFW BLOCK] IN=wlp10s0 OUT= MAC=01:00:5e:00:00:01:<MAC 'EWEPEM' [AN3]>:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=47556 PROTO=2 
[21876.389543] [UFW BLOCK] IN=wlp10s0 OUT= MAC=01:00:5e:00:00:01:<MAC 'EWEPEM' [AN3]>:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=47653 PROTO=2 
[22001.388059] [UFW BLOCK] IN=wlp10s0 OUT= MAC=01:00:5e:00:00:01:<MAC 'EWEPEM' [AN3]>:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=47690 PROTO=2 
[22126.386758] [UFW BLOCK] IN=wlp10s0 OUT= MAC=01:00:5e:00:00:01:<MAC 'EWEPEM' [AN3]>:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=47775 PROTO=2 
[22251.384997] [UFW BLOCK] IN=wlp10s0 OUT= MAC=01:00:5e:00:00:01:<MAC 'EWEPEM' [AN3]>:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=47832 PROTO=2 
[22376.383499] [UFW BLOCK] IN=wlp10s0 OUT= MAC=01:00:5e:00:00:01:<MAC 'EWEPEM' [AN3]>:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=47864 PROTO=2 


########## wireless info END ############

```

---

### Post by wildmanne39 on 2016-09-16
It looks like your firewall is blocking your connection turn it off and see if that helps if it does then you can set it up not to block your connection.

---

### Post by daniel852 on 2016-09-16
Awesome, thanks. I'll give that a go.

So I stopped ufw and at first the problem continued, so I rebooted and now I've managed to get back online. Could you suggest how to configure ufw for my problem?

---

### Post by wildmanne39 on 2016-09-17
You should be able to use the default settings in ufw but we should not be seeing those messages about it in the dmesg output from the wireless script and that may not be the only thing that needs changed but it should be the first.

Like I said I would leave it disable for a little while and see if that fixes your issues if not we will continue to troube shoot with it disabled so we know for a fact it is not interfering, here is a link for setting up ufw.
[https://www.linuxbabe.com/desktop-linux/getting-started-gufw-ubuntu-16-04](https://www.linuxbabe.com/desktop-linux/getting-started-gufw-ubuntu-16-04)

---

