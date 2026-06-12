---
title: "Internal Error After Trying to Install D-Link DWA-525 Drivers"
date: 2014-09-15
forum: Networking &amp; Wireless
---

### Post by vermox on 2014-09-15
I have recently installed the D-Link DWA-525 internal wireless card which works for the Windows XP partition but not Ubuntu. Every five minutes or so while using Ubuntu I would be prompted for a password for the card which was driving me insane so I followed the instructions on [http://steveswinsburg.wordpress.com/2011/03/12/how-to-install-a-d-link-dwa-525-wireless-network-card-in-ubuntu-10-04/](http://steveswinsburg.wordpress.com/2011/03/12/how-to-install-a-d-link-dwa-525-wireless-network-card-in-ubuntu-10-04/). This didn't work but it did stop the password prompt from appearing. The problem is that now when I start the computer I am told that it has experienced an internal error and after about fifteen minutes the whole thing freezes and I have to reboot. I went back and undid all the changes I had made but it hasn't made a difference and it still freezes and occasionally the USB wireless card which I use for Ubuntu doesn't connect either. Does anyone have any idea what I might have done and how I could go about fixing it?

---

### Post by praseodym on 2014-09-15
Please show the terminal outputs of:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
cat /etc/resolv.conf
ifconfig -a
```
Does LAN work? What kind of computer is it?

---

### Post by vermox on 2014-09-17
```

lspci -nnk | grep -iA2 net

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:0df2]
    Kernel driver in use: r8169
04:02.0 Network controller [0280]: Ralink corp. RT5360 Wireless 802.11n 1T/1R [1814:5360]
    Subsystem: D-Link System Inc DWA-525 Wireless N 150 Desktop Adapter (rev.A2) [1186:3c05]

lsusb

Bus 001 Device 002: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter
Bus 005 Device 002: ID 15d9:0a4d Trust International B.V. Optical Mouse
Bus 005 Device 003: ID 0518:0001 EzKEY Corp. USB to PS2 Adaptor v1.09
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


lsmod

Module                  Size  Used by
nls_utf8               12557  1 
udf                    89374  1 
crc_itu_t              12707  1 udf
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             23479  0 
vboxdrv               320372  3 vboxnetadp,vboxnetflt,vboxpci
parport_pc             28152  0 
ppdev                  17073  0 
bnep                   18036  2 
rfcomm                 42641  0 
bluetooth             228808  10 bnep,rfcomm
binfmt_misc            17500  1 
r8712u                187938  0 
joydev                 17377  0 
adt7475                31316  0 
hwmon_vid              12783  1 adt7475
snd_hda_codec_realtek    78445  1 
snd_hda_intel          39619  3 
snd_hda_codec         136498  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
nouveau               943184  3 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
coretemp               13355  0 
mxm_wmi                13021  1 nouveau
wmi                    19070  2 mxm_wmi,nouveau
video                  19390  1 nouveau
ttm                    83187  1 nouveau
mac_hid                13205  0 
snd                    68876  15 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
lpc_ich                17061  0 
drm_kms_helper         49394  1 nouveau
drm                   286028  5 ttm,drm_kms_helper,nouveau
i2c_algo_bit           13413  1 nouveau
psmouse                95905  0 
lp                     17759  0 
soundcore              12680  1 snd
microcode              22881  0 
parport                46345  3 lp,ppdev,parport_pc
serio_raw              13215  0 
hid_generic            12540  0 
usbhid                 47074  0 
hid                   101289  2 hid_generic,usbhid
floppy                 69449  0 
r8169                  67466  0 


iwconfig

wlan2     IEEE 802.11bgn  ESSID:"The Round Table"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 4C:60:DE:80:BF:33   
          Bit Rate:72 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=71/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

lo        no wireless extensions.


rfkill list

**no output**


cat /etc/resolv.conf

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1


ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:22:68:3e:57:5b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:421 errors:0 dropped:0 overruns:0 frame:0
          TX packets:421 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:39176 (39.1 KB)  TX bytes:39176 (39.1 KB)

wlan2     Link encap:Ethernet  HWaddr 00:0d:81:aa:ba:bc  
          inet addr:192.168.0.17  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:81ff:feaa:babc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3311 errors:0 dropped:978 overruns:0 frame:0
          TX packets:2449 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2585294 (2.5 MB)  TX bytes:487251 (487.2 KB)




```

I don't have an ethernet cable handy to test LAN unfortunately. It's a Pentium Dual Core 2gb RAM.

---

### Post by praseodym on 2014-09-17
This device is supported by the Ralink rt3290sta driver. However, afaik it can not be compiled with the new kernels. Lets try:

```
sudo apt-get install linux-headers-$(uname -r) linux-headers-generic build-essential dkms 
wget http://media.cdn.ubuntu-de.org/forum/attachments/29/20/5641297-Ralink_3290sta-2.6.0.0_dkms.tar.gz
sudo tar xvf 5641297-Ralink_3290sta-2.6.0.0_dkms.tar.gz -C /usr/src/
sudo dkms add -m Ralink_3290sta -v 2.6.0.0
sudo dkms build -m Ralink_3290sta -v 2.6.0.0
sudo dkms install -m Ralink_3290sta -v 2.6.0.0 
sudo cp /usr/src/Ralink_3290sta/src/common/rt3290.bin /lib/firmware 
echo "blacklist rt2800pci" | sudo tee -a /etc/modprobe.d/blacklist-rt2800pci.conf  
```
Reboot. If it doesn't work uninstall it:
```
sudo dkms remove -m Ralink_3290sta -v 2.6.0.0 --all
sudo rm -r /usr/src/Ralink_3290sta-2.6.0.0
sudo rm /etc/modprobe.d/blacklist-rt2800pci.conf  
```

Edit: The native driver can be tested first:

```
sudo modprobe -v rt2800pci
dmesg | grep rt2
```
> 
```
modprobe -c | grep -i "1814.*5360"
alias pci:v00001814d00005360sv*sd*bc*sc*i* rt2800pci
```

---

