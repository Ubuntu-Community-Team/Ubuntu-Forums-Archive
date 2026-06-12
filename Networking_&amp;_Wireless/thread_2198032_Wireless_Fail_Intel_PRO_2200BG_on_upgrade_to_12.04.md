---
title: "Wireless Fail: Intel PRO 2200BG on upgrade to 12.04 for Dell Latitude D410"
date: 2014-01-06
forum: Networking &amp; Wireless
---

### Post by jhaefner2 on 2014-01-06
Hi, I'm one of many that have wireless problems after upgrading to 12.04.  My hardwired ethernet connection works.  I have a 9 year old Dell Latitude D410. The service request to restart networking failed (see the last code fragment). Based on the sticky thread on howto post wireless problems I am including the following data:

uname -a
lspci -nnk | grep -iA2 net
dmesg | grep ipw
iwconfig
lsmod
ifconfig -a
rfkill list all
sudo iwlist scan
sudo service networking restart

Thanks in advance for any help you can provide.

Jim H.

-----
```

uname -a  
Linux iris 3.2.0-58-generic #88-Ubuntu SMP Tue Dec 3 17:40:43 UTC 2013 i686 i686 i386 GNU/Linux

```
-----
```

lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)
    Subsystem: Dell Device [1028:018f]
    Kernel driver in use: tg3
--
02:03.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
    Subsystem: Intel Corporation Dell B130 laptop integrated WLAN [8086:2721]
    Kernel driver in use: ipw2200

```
-----

```

dmesg | grep ipw
[   37.651588] libipw: 802.11 data/management/control stack, git-1.1.13
[   37.651592] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   37.686388] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   37.686392] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   37.847087] ipw2200 0000:02:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   37.847116] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   38.652126] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)

```

-----
```

iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11bg  ESSID:""Hale Kulikuli""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.


```
------
```

lsmod
Module                  Size  Used by
lzo                    12525  0 
cast6                  16773  0 
cts                    12816  0 
gcm                    18768  0 
ccm                    17596  0 
geode_aes              13228  0 
cryptd                 19821  0 
aes_i586               16995  0 
xfrm_user              31159  2 
ah6                    12793  0 
ah4                    12707  0 
esp6                   12811  0 
esp4                   12806  0 
xfrm4_mode_beet        12497  0 
xfrm4_tunnel           12675  0 
tunnel4                13045  1 xfrm4_tunnel
xfrm4_mode_tunnel      12546  0 
xfrm4_mode_transport    12517  0 
xfrm6_mode_transport    12517  0 
xfrm6_mode_ro          12458  0 
xfrm6_mode_beet        12576  0 
xfrm6_mode_tunnel      12546  0 
ipcomp                 12593  0 
ipcomp6                12596  0 
xfrm_ipcomp            13282  2 ipcomp,ipcomp6
xfrm6_tunnel           13522  1 ipcomp6
tunnel6                13016  1 xfrm6_tunnel
deflate                12545  0 
zlib_deflate           26622  1 deflate
ctr                    13033  0 
twofish_generic        16579  0 
twofish_i586           12787  0 
twofish_common         20823  2 twofish_generic,twofish_i586
camellia               29212  0 
serpent                29029  0 
blowfish_generic       12474  0 
blowfish_common        16667  1 blowfish_generic
cast5                  24976  0 
des_generic            21191  0 
xcbc                   12711  0 
rmd160                 16664  0 
sha512_generic         16780  0 
crypto_null            12782  0 
af_key                 31567  0 
dm_crypt               22528  0 
parport_pc             32114  0 
ppdev                  12849  0 
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158447  8 bnep,rfcomm
binfmt_misc            17292  1 
ip6t_LOG               16846  4 
joydev                 17393  0 
xt_hl                  12465  6 
ip6t_rt                12473  3 
nf_conntrack_ipv6      13581  7 
nf_defrag_ipv6         13175  1 nf_conntrack_ipv6
ipt_REJECT             12512  1 
ipt_LOG                12783  5 
xt_limit               12541  12 
xt_tcpudp              12531  22 
snd_intel8x0           33455  0 
snd_ac97_codec        110213  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80916  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
xt_addrtype            12596  4 
pcmcia                 39826  0 
xt_state               12514  14 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
dell_laptop            17767  0 
dcdbas                 14098  1 dell_laptop
ip6table_filter        12711  1 
ip6_tables             18432  3 ip6t_LOG,ip6t_rt,ip6table_filter
nf_conntrack_netbios_ns    12585  0 
nf_conntrack_broadcast    12541  1 nf_conntrack_netbios_ns
nf_nat_ftp             12595  0 
nf_nat                 24959  1 nf_nat_ftp
nf_conntrack_ipv4      19084  9 nf_nat
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
nf_conntrack_ftp       13183  1 nf_nat_ftp
nf_conntrack           73847  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         12706  1 
ip_tables              18106  1 iptable_filter
psmouse                96744  0 
x_tables               22011  13 ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
snd                    62218  7 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ipw2200               146210  0 
libipw                 46732  1 ipw2200
cfg80211              178877  2 ipw2200,libipw
soundcore              14635  1 snd
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
lib80211               14040  2 ipw2200,libipw
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
serio_raw              13027  0 
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
i915                  428213  3 
drm_kms_helper         45466  1 i915
drm                   197641  4 i915,drm_kms_helper
tg3                   141465  0 
i2c_algo_bit           13199  1 i915
video                  19115  1 i915

```
------

```

ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:12:3f:22:0b:fb  
          inet addr:192.168.1.145  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:3fff:fe22:bfb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:58351 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32578 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:72166927 (72.1 MB)  TX bytes:3421819 (3.4 MB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:12:f0:70:89:7f  
          inet6 addr: fe80::212:f0ff:fe70:897f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3882 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:1037130 (1.0 MB)
          Interrupt:17 Base address:0xe000 Memory:dfcff000-dfcfffff 

eth1:avahi Link encap:Ethernet  HWaddr 00:12:f0:70:89:7f  
          inet addr:169.254.7.226  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0xe000 Memory:dfcff000-dfcfffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4247 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4247 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:491246 (491.2 KB)  TX bytes:491246 (491.2 KB)


```
-----

```

rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```
-----

```

sudo iwlist scan
lo        Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 98:FC:11:50:B5:12
                    ESSID:"Hale Kulikuli"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=93/100  Signal level=-35 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 200ms ago

eth0      Interface doesn't support scanning.

```

------

```

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:3f:22:0b:fb  
          inet addr:192.168.1.145  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:3fff:fe22:bfb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:59067 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33446 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:72267175 (72.2 MB)  TX bytes:3517036 (3.5 MB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:12:f0:70:89:7f  
          inet6 addr: fe80::212:f0ff:fe70:897f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:1087911 (1.0 MB)
          Interrupt:17 Base address:0xe000 Memory:dfcff000-dfcfffff 

eth1:avahi Link encap:Ethernet  HWaddr 00:12:f0:70:89:7f  
          inet addr:169.254.7.226  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0xe000 Memory:dfcff000-dfcfffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4247 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4247 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:491246 (491.2 KB)  TX bytes:491246 (491.2 KB)

```
-----
```

sudo service networking restart
stop: Unknown instance: 
networking stop/waiting

```
-----

---

### Post by chili555 on 2014-01-06
Network Manager will try to use wired ethernet if it's available, which it is here, because it's faster and more secure. Please detach the ethernet, reboot so we have a clean slate and try again. When you click the Network Manager icon, do you see your network? I suspect so, since it scans and sees networks now. What happens when you click your network and try to connect? Does it try? Does it ask for the encryption key? 

Frankly, I see nothing to fix so far.

---

### Post by jhaefner2 on 2014-01-06
I agree that the output does not indicate a clear problem, as I have seen in other wireless threads.  I did disconnect the ethernet and reboot.  I'm not sure what you mean by the "Network Manager icon" .  I'm using "gnome classic [no enhancements]".  If you mean the network icon in the "indicator applet" at the top system tray, then no it neither shows the wired or wireless networks except as a "grey" option.  When I click on "Connection information"  I see "No valid active connections found!", and that includes the ethernet connection I am currently typing on.  I can't find any menu item called "Network Manager".

"sudo service networking restart" gives the same output as originally posted.  

With the ethernet disconnected, when I attempt to use firefox I get (something like) "Server not found".  Indicating that the wireless is trying to work, but I have a problem with the wireless DNS.  When the wireless first failed I thought it was a bad definition of my local wireless router.  I used "Network Tools" to delete and redefine the SSID, security choices, etc.  Perhaps I erred in doing this.  I had previously assigned a name to my router ("Hale Kulikuli") with a password.  Is it proper to use the name as the SSID?  Or, is it looking for a numerical identifier?  So far, I have not been prompted for authentification (password) from the router.  Cycling the power on the router had no effect.

Do you think it could be a DNS issue?

JH

---

### Post by chili555 on 2014-01-06
I doubt it is a DNS issue.

If you set up a name in the router, that is indeed the SSID. Perhaps incidentally, it is often preferrable to use an SSID without a space; i.e HaleKulikuli.Let's leave that alone for a bit and troubleshoot a bit more. First, let's see if Network Manager is running here:```
ps aux |  grep -i network
```> "sudo service networking restart" gives the same output as originally posted. Please don't do this, it isn't needed, well, ever, in my few years of experience. It gives a confusing and often misleading result and really never fixes anything.

> I used "Network Tools" to delete and redefine the SSID, security choices, etc. Perhaps I erred in doing this.Please tell us what all the current settings are. Did you complete any settings for WPA2 encryption?

May I see:```
cat /etc/network/interfaces
```

---

### Post by jhaefner2 on 2014-01-07
```

ps aux | grep -i net
root        11  0.0  0.0      0     0 ?        S<   18:26   0:00 [netns]
root      1081  0.0  0.5  23200  5508 ?        Ssl  18:28   0:00 NetworkManager
root      1627  0.0  0.0   3792   860 ?        Ss   18:28   0:00 /usr/sbin/netdaemon

```

```

cat /etc/network/interfaces
auto lo
iface lo inet loopback

iface eth0 inet dhcp

iface eth1 inet dhcp
wireless-essid "Hale Kulikuli"
auto eth1

iface pan0 inet dhcp
auto eth0

```

===============================
My summary of the Network Tools and Network Connections screens

Network Tools screen:
IPv4 Address:  0.0.0.0
IPv4 Netmask:  0.0.0.0

Network Connections

SSID: Hale Kulikuli
Mode: Infrastructure
Device MAC Address:   00:12:F0:70:89:7F (eth1)
Cloned MAC address:  edmpty
MTU: Automatic
-----
IpV4:
Method: Automatic (DHCP)
All other input widgets on screen:  empty
IpV6:
Method: Automatic
All other widgets: empty
Security:
Security: WPA & WPA2 (personal)
Password:  (as it should be)

=====================================

A windows machine that connects to the router has specific addresses for the IPv4 address and netmask.

I have a very simple firewall operating.  Here are the few rules, but I doubt this is the problem.

```

sudo ufw status numbered
Status: active

     To                         Action      From
     --                         ------      ----
[ 1] Anywhere                   ALLOW IN    129.123.16.123/tcp
[ 2] Anywhere                   ALLOW IN    192.168.0.0/16/tcp
[ 3] 22                         DENY IN     Anywhere
[ 4] 49458/tcp                  ALLOW IN    Anywhere
[ 5] 21/tcp                     DENY IN     Anywhere

```

---

### Post by chili555 on 2014-01-07
> cat /etc/network/interfaces
auto lo
iface lo inet loopback

iface eth0 inet dhcp

iface eth1 inet dhcp
wireless-essid "Hale Kulikuli"
auto eth1

iface pan0 inet dhcp
auto eth0When you fill in the file /etc/network/interfaces with anything more than the loopback stanzas, Network Manager relinquishes control and your manual settings take precedence. That's why ethernet doesn't show up in the NM applet and yet you are using it. 

Each method has its advantages and disadvantages, but you ought to select one and stick with it. For the time being, let's tweak /etc/network/interfaces and see if we can fix it.

The first thing I notice is that you include both auto eth0 and auto eth1, telling the system that you want *both* ethernet and wireless to start automatically on boot. I suspect you really only want wireless.

Second, although you have specified the network you want to connect to, you haven't supplied an encryption key. Your network is clearly encrypted:> Cell 01 - Address: 98:FC:11:50:B5:12
                    ESSID:"Hale Kulikuli"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=93/100  Signal level=-35 dBm  
                    IE: [COLOR="#FF0000"]WPA Version 1[/COLOR]
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: [COLOR="#FF0000"]IEEE 802.11i/WPA2 Version 1[/COLOR]
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSKI suggest you re-arrange the file like this:```
auto lo
iface lo inet loopback

#auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wpa-ssid "Hale Kulikuli"
wpa-psk your_secret_key

iface pan0 inet dhcp

```I suggest you then reboot and see if you aren't connected as expected.

We could certainly revise the file to instead use Network Manager entirely, if you wish.

---

### Post by jhaefner2 on 2014-01-07
Okay, that was brilliant.  Wireless network now works.  But I think I really want NetworkManager to be in charge, so can I keep your attention just long enough to tell me how to change interfaces so that happens?

thanks.
-jh

---

### Post by chili555 on 2014-01-07
Certainly. Comment out or remove everything but the loopback stanzas:```
auto lo
iface lo inet loopback

```Reboot and you should be all set. NM should be back in charge. You can remove all the details you added there and let NM offer you several networks, pick yours and supply the WPA key and enjoy. 

I'll be around for a while, so if you want to try it, I'll be here to help. If you want to keep these details as backup, simply comment out the lines you want NM to ignore:```
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp
#wpa-ssid "Hale Kulikuli"
#wpa-psk your_secret_key

#iface pan0 inet dhcp
```

---

### Post by jhaefner2 on 2014-01-07
That all worked as advertised.  Many thanks for your good work.  I'll close out this thread as sloved.
-jh

---

### Post by chili555 on 2014-01-07
Awesome! Glad it's working.

---

