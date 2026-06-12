---
title: "Wireless Connection Problem"
date: 2014-04-18
forum: Networking &amp; Wireless
---

### Post by Mago Nick on 2014-04-18
Hello everybody. 
Apologies if the title is too general, let me know and I will change it. I am experiencing some wireless connection with my new desktop computer. I am running Ubuntu 12.04.4 lts.
Basically the problem is that the internet connection is not continus and even if the network manager shows that I am connected I am not able to send or receive packets. The card mounts a realtek chipset. 
Here there are some outputs:
```

mago@desktop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: Killer E2200 Gigabit Ethernet Controller
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 13
       serial: d4:3d:7e:ed:ed:3e
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
        capabilities: pm pciexpress msi msix bus_master cap_list ethernet  physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx latency=0 link=no multicast=yes port=twisted pair
       resources: irq:46 memory:f7300000-f733ffff ioport:d000(size=128)
  *-network
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 01
       serial: 00:06:4f:9b:e4:50
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
        configuration: broadcast=yes driver=rtl8192ce  driverversion=3.11.0-18-generic firmware=N/A ip=192.168.1.104 latency=0  link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 ioport:c000(size=256) memory:f7200000-f7203fff


```



```
mago@desktop:~$ rfkill list
0: phy0: Wireless LAN
   Soft blocked: no
   Hard blocked: no

```

```

mago@desktop:~$ lspci | grep Network
04:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)

```

Since from the syslog I get:

```

Apr 18 15:54:11 desktop wpa_supplicant[1096]: CTRL-EVENT-DISCONNECTED bssid=d4:d1:84:e1:63:a3 reason=4

```

I checked if the power saving was enabled but 

```

mago@desktop:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Telecom-81879965"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: D4:D1:84:E1:63:A3   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=34/70  Signal level=-76 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

could you please help me?
Thank you very much.
Andrea

---

### Post by praseodym on 2014-04-18
Hi,

try to update the driver via LAN:
```

sudo apt-get install --reinstall linux-headers-generic-lts-saucy linux-headers-$(uname -r) build-essential dkms git
git clone https://github.com/FreedomBen/rtl8188ce-linux-driver
cd rtl8188ce-linux-driver
make
sudo make install
sudo cp -r firmware/* /lib/firmware
```

---

### Post by Mago Nick on 2014-04-18
Done, but it seems that the problem is still there

---

### Post by praseodym on 2014-04-18
Did you reboot?

---

### Post by Mago Nick on 2014-04-18
Yes, as you said

---

### Post by praseodym on 2014-04-18
Ok, lets check:
```

lsmod
ifconfig -a
cat /etc/resolv.conf
route -n
iwlist chan
sudo iwlist scan
```

---

### Post by Mago Nick on 2014-04-19
Here are the outputs:
```

mago@desktop:~$ lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     41773  1 
joydev                 17613  0 
hid_logitech_dj        18767  0 
hid_generic            12548  0 
usbhid                 53329  0 
hid                   106315  3 hid_logitech_dj,hid_generic,usbhid
bnep                   24107  2 
rfcomm                 74718  0 
arc4                   12573  2 
bluetooth             391726  10 bnep,rfcomm
nvidia              10619255  40 
parport_pc             32866  0 
ppdev                  17711  0 
snd_hda_codec_realtek    57219  1 
rtl8192ce             141806  0 
rtlwifi               114188  1 rtl8192ce
snd_hda_intel          57134  5 
snd_hda_codec         194817  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13613  1 snd_hda_codec
mac80211              623607  2 rtl8192ce,rtlwifi
snd_pcm               107140  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
mxm_wmi                13021  0 
snd_seq_midi           13324  0 
snd_rawmidi            30416  1 snd_seq_midi
psmouse               104093  0 
snd_seq_midi_event     14899  1 snd_seq_midi
serio_raw              13413  0 
snd_seq                66061  2 snd_seq_midi,snd_seq_midi_event
cfg80211              499466  2 rtlwifi,mac80211
snd_timer              29989  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    73753  21 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lpc_ich                21163  0 
soundcore              12680  1 snd
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
drm                   306660  2 nvidia
wmi                    19256  1 mxm_wmi
video                  19574  0 
mei_me                 18418  0 
mei                    78537  1 mei_me
binfmt_misc            17508  1 
mac_hid                13253  0 
nls_iso8859_1          12713  1 
coretemp               17728  0 
lp                     17799  0 
parport                42466  3 parport_pc,ppdev,lp
alx                    32936  0 
mdio                   13807  1 alx
ahci                   30063  4 
libahci                32118  1 ahci

```

```

mago@desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr d4:3d:7e:ed:ed:3e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1908 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1908 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:195563 (195.5 KB)  TX bytes:195563 (195.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:06:4f:9b:e4:50  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::206:4fff:fe9b:e450/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:312672 errors:0 dropped:0 overruns:0 frame:0
          TX packets:190971 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:404568333 (404.5 MB)  TX bytes:38246118 (38.2 MB)



```


```

mago@desktop:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
search homenet.telecomitalia.it


```

```

mago@desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0


```

```

mago@desktop:~$ iwlist chan
eth0      no frequency information.

lo        no frequency information.

wlan0     13 channels in total; available frequencies :
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
          Current Frequency:2.437 GHz (Channel 6)


```


```

mago@desktop:~$ sudo iwlist scan

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: D4:D1:84:E1:63:A3
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"Telecom-81879965"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000de3dc3c1d3
                    Extra: Last beacon: 52ms ago
                    IE: Unknown: 001054656C65636F6D2D3831383739393635
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081500000000000000000000000000000000000000
                    IE: Unknown: DD780050F204104A00011010440001021041000100103B00010310470010CA54190EE689484587F329063827114310210003414442102300074147574946494E1024000630303030303110420004303030311054000800060050F20400011011000D41472042617369632057694669100800020088103C000101
                    IE: Unknown: DD090010180203F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: E0:91:53:5A:BB:33
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-6 dBm  
                    Encryption key:on
                    ESSID:"MyFASTWlan"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000017d06e15d8
                    Extra: Last beacon: 52ms ago
                    IE: Unknown: 000A4D7946415354576C616E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 200100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101060003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010020FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: 0706495420010D14
                    IE: Unknown: DD8C0050F204104A00011010440001021057000100103B000103104700103E9A55EB83EDD9B5BAAD341AFF56150F1021000D456C736167446174616D6174001023000E4152474F20506C6174666F726D00102400084152474F35352B001042000D303036303342314545303436001054000800060050F2040001101100054172676F0010080002008C103C000101
          Cell 03 - Address: 00:0C:F6:78:50:13
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-22 dBm  
                    Encryption key:on
                    ESSID:"Sitecom785013"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002fc3e20d6cd
                    Extra: Last beacon: 52ms ago
                    IE: Unknown: 000D53697465636F6D373835303133
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160B070600000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD790050F204104A00011010440001021041000100103B0001031047001000000000000000011000000CF67850121021000753697465636F6D10230006574C2D3334371024000576312E30301042000A4A3030353032383131381054000800060050F20400011011000B574C2D3334372857464129100800020004
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD1E00904C33EE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C340B070600000000000000000000000000000000000000



```

---

### Post by praseodym on 2014-04-19
Change the channel to fixed "1" and the encryption mode to pure WPA2-AES (CCMP) instead of mixed mode WPA/WPA2. Check the router manual.

---

### Post by Mago Nick on 2014-04-19
Done, but things did not change

---

### Post by praseodym on 2014-04-19
Try these module parameters:
```

echo "options rtl8192ce swlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8192ce.conf
sudo modprobe -rfv rtl8192ce
sudo modprobe -v rtl8192ce
```
Deactivate IPv6 in the network-manager profile

---

### Post by Mago Nick on 2014-04-19
nothing...

---

### Post by Mago Nick on 2014-04-19
NOthing... Still the same...

EDIT: sorry for the repost, connection problems

---

### Post by praseodym on 2014-04-19
Lets see:
```

egrep -i 'net|eth|wlan|firm|reason' /var/log/syslog 
dmesg | egrep 'net|eth|sky|sis|via|3c3|3c5|e100|8139|8169|acx|air|ath|atl|ar9|carl|atme|at7|herm|iwl|ipw|rtl8|r81|rt2|rt3|rt6|rt7|tg3|ssb|wl|b43|b44|ori|pri|p5|zd|ndis|wmi|ns8|FW' 
```

---

### Post by Mago Nick on 2014-04-19
Attached a tar of the output of the two commands. They are way too big to be posted directly

EDIT: i forgot... thank you!

---

### Post by praseodym on 2014-04-19
```
Apr 19 17:00:26 desktop NetworkManager[1012]: <info> (wlan0): supplicant interface state: associating -> associated
Apr 19 17:00:26 desktop NetworkManager[1012]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Apr 19 17:00:26 desktop NetworkManager[1012]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Apr 19 17:00:30 desktop NetworkManager[1012]: <info> (wlan0): roamed from BSSID (none) ((none)) to D4:D1:84:E1:63:A3 (Telecom-81879965)
Apr 19 17:01:22 desktop kernel: [ 6009.101993] wlan0: Connection to AP d4:d1:84:e1:63:a3 lost
```
Handshake (passphrase) works, but its losing the connection:
```
Apr 19 17:03:19 desktop kernel: [ 6125.481421] wlan0: deauthenticating from d4:d1:84:e1:63:a3 by local choice (reason=3)
```

Try to add the ID of you AP d4:d1:84:e1:63:a3 to the "BSSID" field in your profile. "(reason=3)" normally is a network-manager problem. Maybe we can try Wicd in the next step.

---

### Post by Mago Nick on 2014-04-19
I switched to WICD, let's see how it goes

---

### Post by Mago Nick on 2014-04-19
Now I am experiencing continuous disconnections. Probably the same problem as before, but now wicd notifies me (it is still an improvement)

---

### Post by praseodym on 2014-04-19
Lets check this:
```

sudo service network-manager stop
sudo killall wpa_supplicant
sudo service wicd restart
```
Did you choose **wlan0** as interface name and **wext** as driver in Wicd?

---

### Post by Mago Nick on 2014-04-19
Here are the outputs

```

mago@desktop:~$ sudo service network-manager stop
network-manager: unrecognized service

```

```

mago@desktop:~$ sudo killall wpa_supplicant
wpa_supplicant: no process found

```

```

mago@desktop:~$ sudo service wicd restart
 * Restarting Network connection manager wicd                            [ OK ] 

```

And for what regards the configurations yes. I am using wlan0 and wext as driver.

If it can be useful, it takes a while to obtain the IP

---

### Post by praseodym on 2014-04-19
Check this Add-on for Wicd:

```

wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon01441.tar.gz
tar xvf wicd-1.6.x_addon01441.tar.gz
cd wicd-1.6.x_addon01441
sudo ./install_wicd_addon
sudo service wicd restart
```
It bring a lot of templates for different kinds of connection.

---

### Post by Mago Nick on 2014-04-19
Done,  what should I do, now?

---

### Post by praseodym on 2014-04-19
Now try to re-connect using the template for WPA2. Is the network "hidden"?

---

### Post by Mago Nick on 2014-04-19
Nope, the network is not hidden

---

### Post by praseodym on 2014-04-19
So, lets check
```

ifconfig -a
cat /etc/network/interfaces
cat /etc/resolv.conf
iwconfig
lsmod
```
I don't know if its getting better, because the driver from Realtek is not up to date. Which driver version is it now?
```

modinfo rtl8188ee
locate rtl8192cfw.bin | grep lib
dmesg | egrep 'firm|rtl8'
```

---

### Post by Mago Nick on 2014-04-19
Hi, I had to reinstall Network Manager and remove Wicd because the connection was highly unstable, almost unusable.
here the outputs of the commands

```

mago@desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr d4:3d:7e:ed:ed:3e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:140 errors:0 dropped:0 overruns:0 frame:0
          TX packets:140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12155 (12.1 KB)  TX bytes:12155 (12.1 KB)

usb0      Link encap:Ethernet  HWaddr 02:04:61:6e:35:66  
          inet addr:192.168.42.115  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::4:61ff:fe6e:3566/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:84299 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47852 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:103553916 (103.5 MB)  TX bytes:5994811 (5.9 MB)

wlan0     Link encap:Ethernet  HWaddr 00:06:4f:9b:e4:50  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::206:4fff:fe9b:e450/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1901 errors:0 dropped:0 overruns:0 frame:0
          TX packets:731 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:234994 (234.9 KB)  TX bytes:78951 (78.9 KB)


```

```

auto lo
iface lo inet loopback



```


```

mago@desktop:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 192.168.1.1
nameserver 127.0.0.1
search homenet.telecomitalia.it


```


```

mago@desktop:~$ iwconfig
usb0      no wireless extensions.

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Telecom-81879965"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: D4:D1:84:E1:63:A3   
          Bit Rate=300 Mb/s   Tx-Power=33 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=18 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:13   Missed beacon:0


```

```

mago@desktop:~$ lsmod
Module                  Size  Used by
joydev                 17613  0 
hid_logitech_dj        18767  0 
hid_generic            12548  0 
usbhid                 53329  0 
usb_storage            66567  1 
rndis_host             14503  0 
hid                   106315  3 hid_logitech_dj,hid_generic,usbhid
cdc_ether              14400  1 rndis_host
usbnet                 39575  2 rndis_host,cdc_ether
mii                    13981  1 usbnet
snd_hda_codec_hdmi     41773  1 
nvidia              10619255  40 
arc4                   12573  2 
bnep                   24107  2 
rfcomm                 74718  0 
bluetooth             391726  10 bnep,rfcomm
parport_pc             32866  0 
snd_hda_codec_realtek    57219  1 
ppdev                  17711  0 
rtl8192ce             141806  0 
rtlwifi               114188  1 rtl8192ce
snd_hda_intel          57134  5 
snd_hda_codec         194817  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
psmouse               104093  0 
mac80211              623607  2 rtl8192ce,rtlwifi
snd_hwdep              13613  1 snd_hda_codec
mxm_wmi                13021  0 
snd_pcm               107140  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
serio_raw              13413  0 
snd_seq_midi           13324  0 
snd_rawmidi            30416  1 snd_seq_midi
cfg80211              499466  2 rtlwifi,mac80211
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                66061  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29989  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
lpc_ich                21163  0 
video                  19574  0 
snd                    73753  21 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    19256  1 mxm_wmi
mei_me                 18418  0 
soundcore              12680  1 snd
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
mei                    78537  1 mei_me
drm                   306660  2 nvidia
mac_hid                13253  0 
binfmt_misc            17508  1 
nls_iso8859_1          12713  1 
coretemp               17728  0 
lp                     17799  0 
parport                42466  3 parport_pc,ppdev,lp
ahci                   30063  4 
alx                    32936  0 
libahci                32118  1 ahci
mdio                   13807  1 alx


```

The drivers info

```

mago@desktop:~$ modinfo rtl8188ee
filename:       /lib/modules/3.11.0-19-generic/kernel/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.ko
firmware:       rtlwifi/rtl8188efw.bin
description:    Realtek 8188E 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         zhiyuan_yang    <zhiyuan_yang@realsil.com.cn>
srcversion:     C64D6079A9AFD1703A3DE05
alias:          pci:v000010ECd00008179sv*sd*bc*sc*i*
depends:        rtlwifi,mac80211
vermagic:       3.11.0-19-generic SMP mod_unload modversions 
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)


```

```

mago@desktop:~$ locate rtl8192cfw.bin | grep lib
/lib/firmware/rtlwifi/rtl8192cfw.bin
/lib/firmware/rtlwifi/rtl8192cfw.bin.bak


```

```


mago@desktop:~$ dmesg | egrep 'firm|rtl8'
[    1.567493] rtl8192ce 0000:04:00.0: enabling device (0000 -> 0003)


```

Thank you very much!

---

### Post by praseodym on 2014-04-19
Did you deactivate IPv6 ("Ignore") in the network-manager? Also add the mtu-value of your ISP (mostly 1500) as number instead of "automatic" in your profile.

Edit:

> ```
firmware:       rtlwifi/rtl8188efw.bin
```
Please check
```

locate rtl8188efw.bin | grep lib
```

---

### Post by Mago Nick on 2014-04-19
Ipv6 is set to ignore and I adjusted the mtu as you have indicated. Lets see what happens

---

