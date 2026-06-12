---
title: "Wireless adaptor driver"
date: 2014-06-02
forum: Networking &amp; Wireless
---

### Post by mmuresanpaul on 2014-06-02
Hello, i am really new to Ubuntu, I have just installed it yesterday. When I opened it I came to the surprise that the wireless adapter is not working anymore and since I am 3 rooms away from the closest internet connection today I have bought a 10m internet cable. xD but still this can't be a permanent solution so i searched for a driver. I found some on the site but I couldn't really install it. If anyone can help me I would greatly apreciate it :D 

Here is some info about the adapter:

Name: D-link GO-USB- N150
H/W Ver: B1 
F/W ver: 2.00

Here's some info about my PC (if it is of any help): 

OS: ubuntu 14.04 LTS
Memory: 7.7 GiB
Processor: Intel® Core™ i5-3570K CPU @ 3.40GHz × 4 
Graphics: Gallium 0.4 on NVE6
OS type: 64-bit
Disk: 976,0 GB

---

### Post by stalkingwolf on 2014-06-02
try going to  system > preferences >additional drivers.  then just click search. if there is a driver it will bring up a list. select the recommended driver and click activate or install . i dont remember which it is.
If that doesnt work under system > administration there is a tool for using windows drivers.

---

### Post by Rob Sayer on 2014-06-02
Don't use preferences>additional drivers unless you're sure it'll work.  I stopped using it some time ago.  There are times ... I've seen this myself ... when it'll install the wrong driver for the system, generally meaning the proprietary driver works LESS well than the open source one.

In other words, the linux drivers some manufacturers come up with aren't done properly or are not up to date.

Using windows drivers can be done with ndiswrapper BUT it is a last ditch approach for cases where there simply is no linux driver available.

If that were the case, personally I'd just go out and buy a USB wireless dongle that actually is supported in linux.

Besides, if using the windows wireless driver was reliable ... and it isn't ... wouldn't everyone be using them?  I would have done it myself by now.

Here's a link to a good answer ....

[http://askubuntu.com/questions/315145/will-the-d-link-go-usb-n150-wireless-n-150-easy-usb-adapter-work-without-problem](http://askubuntu.com/questions/315145/will-the-d-link-go-usb-n150-wireless-n-150-easy-usb-adapter-work-without-problem)

... though the info may not be relevant to your ubuntu version.

Try putting this in terminal ....

sudo lshw -C network

and entering the password.  It'll tell you what adapter you actually have .... which may not be descibed by the model name ... and which driver you're using.

---

### Post by deadflowr on 2014-06-02
I've moved this thread over to where the pros are, in **Networking and Wireless**

---

### Post by praseodym on 2014-06-02
Hi,

please show the terminal outputs of these commands:
```

uname -a
lsusb
lsmod
iwconfig
cat /etc/resolv.conf
```

---

### Post by mmuresanpaul on 2014-06-03
paul@paul:~$ uname -a


Linux paul 3.13.0-27-generic #50-Ubuntu SMP Thu May 15 18:06:16 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```
paul@paul:~$ lsusb
Bus 002 Device 003: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 002 Device 004: ID 2001:3311 D-Link Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 1ea7:2002  
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```


```
paul@paul:~$ lsmod
Module                  Size  Used by
bnep                   19624  2 
rfcomm                 69160  0 
bluetooth             395423  10 bnep,rfcomm
nls_iso8859_1          12713  1 
snd_hda_codec_hdmi     46207  1 
joydev                 17381  0 
intel_rapl             18773  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm                   451511  0 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
snd_hda_codec_realtek    61438  1 
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hda_intel          52355  5 
psmouse               102222  0 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
serio_raw              13462  0 
snd_hwdep              13602  1 snd_hda_codec
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
lpc_ich                21080  0 
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
mei_me                 18627  0 
mei                    82274  1 mei_me
snd_rawmidi            30144  1 snd_seq_midi
nouveau              1097199  4 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
mxm_wmi                13021  1 nouveau
wmi                    19177  2 mxm_wmi,nouveau
snd                    69238  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
ttm                    85115  1 nouveau
drm_kms_helper         52758  1 nouveau
video                  19476  1 nouveau
drm                   302817  6 ttm,drm_kms_helper,nouveau
i2c_algo_bit           13413  1 nouveau
soundcore              12680  1 snd
parport_pc             32701  1 
mac_hid                13205  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 52570  0 
hid                   106148  2 hid_generic,usbhid
r8169                  67581  0 
mii                    13934  1 r8169
```


```
paul@paul:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.

```

paul@paul:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1


paul@paul:~$

---

### Post by mmuresanpaul on 2014-06-03
Here's what it showed up :

*-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: 94:de:80:b7:7b:db
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.2.109 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:d000(size=256) memory:f2104000-f2104fff memory:f2100000-f2103fff

---

### Post by chili555 on 2014-06-03
> **stalkingwolf said:**
> try going to  system > preferences >additional drivers.  then just click search. if there is a driver it will bring up a list. select the recommended driver and click activate or install . i dont remember which it is.
If that doesnt work under system > administration there is a tool for using windows drivers.As far as I know, Additional Drivers only supports Broadcom PCI devices; this is, under the hood, a Realtek USB. Additional Drivers is no help.

Perhaps the new_id technique on top of r8188eu will help my colleague praseodym.

---

### Post by praseodym on 2014-06-03
Devices with similar IDs run with the "cu" driver, but the ID needs to be added. Lets try:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git 
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.8
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
echo 'install 8192cu modprobe --ignore-install 8192cu ; /bin/echo "2001 3311" > /sys/bus/usb/drivers/rtl8192cu/new_id' | sudo tee /etc/modprobe.d/8192cu.conf
```
You'd better copy/paste these lines, especially the last one.

Reboot after that

---

### Post by mmuresanpaul on 2014-06-06
I tried what you said, and it didn't do anything. Am I doing anything wrong or should the wireless adaptor just work by itself?

---

### Post by praseodym on 2014-06-06
Please check now
```

iwconfig
ifconfig -a
lsmod
dmesg | grep 8192
cat /etc/resolv.conf
route -n
```

---

### Post by mmuresanpaul on 2014-06-08
paul@paul:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.



paul@paul:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 94:de:80:b7:7b:db  
          inet addr:192.168.2.109  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::96de:80ff:feb7:7bdb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:324730 errors:0 dropped:0 overruns:0 frame:0
          TX packets:195285 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:453734010 (453.7 MB)  TX bytes:18534725 (18.5 MB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1962 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1962 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:351345 (351.3 KB)  TX bytes:351345 (351.3 KB)


paul@paul:~$ lsmod
Module                  Size  Used by
joydev                 17381  0 
rfcomm                 69160  0 
bnep                   19624  2 
bluetooth             395423  10 bnep,rfcomm
binfmt_misc            17468  1 
nls_iso8859_1          12713  1 
snd_hda_codec_hdmi     46207  1 
hid_generic            12548  0 
usbhid                 52570  0 
hid                   106148  2 hid_generic,usbhid
intel_rapl             18773  0 
snd_hda_codec_realtek    61438  1 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm                   451511  0 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hda_intel          52355  5 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
nouveau              1097199  4 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
mxm_wmi                13021  1 nouveau
mac_hid                13205  0 
wmi                    19177  2 mxm_wmi,nouveau
video                  19476  1 nouveau
parport_pc             32701  1 
ttm                    85115  1 nouveau
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_timer              29482  2 snd_pcm,snd_seq
drm_kms_helper         52758  1 nouveau
snd                    69238  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
psmouse               102222  0 
drm                   302817  6 ttm,drm_kms_helper,nouveau
serio_raw              13462  0 
ppdev                  17671  0 
mei_me                 18627  0 
i2c_algo_bit           13413  1 nouveau
soundcore              12680  1 snd
mei                    82274  1 mei_me
lpc_ich                21080  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
r8169                  67581  0 
mii                    13934  1 r8169
paul@paul:~$ dmesg | grep 8192
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88021dc00000 s86336 r8192 d24256 u524288
[    0.000000] pcpu-alloc: s86336 r8192 d24256 u524288 alloc=1*2097152
paul@paul:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
paul@paul:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
paul@paul:~$

---

### Post by praseodym on 2014-06-08
The driver is not loaded. Lets check
```

sudo modprobe -v 8192cu
dmesg | grep 8192
iwconfig
sudo iwlist scan
```

---

### Post by mmuresanpaul on 2014-06-08
paul@paul:~$ sudo modprobe -v 8192cu
[sudo] password for paul: 


install modprobe --ignore-install 8192cu ; /bin/echo "2001 3311" > /sys/bus/usb/drivers/rtl8192cu/new_id 
insmod /lib/modules/3.13.0-27-generic/updates/dkms/8192cu.ko 
paul@paul:~$ dmesg | grep 8192
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88021dc00000 s86336 r8192 d24256 u524288
[    0.000000] pcpu-alloc: s86336 r8192 d24256 u524288 alloc=1*2097152
[ 1801.896391] 8192cu: module verification failed: signature and/or  required key missing - tainting kernel
[ 1801.899035] rtl8192cu driver version=v4.0.2_9000.20130911
[ 1801.899063] usbcore: registered new interface driver rtl8192cu
[ 1801.914923] CHIP TYPE: RTL8188C_8192C
[ 1801.915108] ====> ReadAdapterInfo8192C
[ 1801.963294] readAdapterInfo_8192CU(): REPLACEMENT = 1
[ 1801.963296] <==== ReadAdapterInfo8192C in 48 ms
[ 1805.017189] rtl8192cu_hal_init in 2916ms
paul@paul:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


paul@paul:~$ sudo iwlist scan
eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     No scan results

---

### Post by praseodym on 2014-06-08
Ok, the interface is there:
```

ifconfig -a
cat /etc/network/interfaces
cat /etc/resolv.conf
route -n
iwlist chan
ping -c 2 $(route -n | grep UG | awk {'print $2'})
ping -c 2 www.ubuntuusers.de
ping -c 2 213.95.41.11 
```
Router firmware is up to date?

---

### Post by mmuresanpaul on 2014-06-08
paul@paul:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 94:de:80:b7:7b:db  
          inet addr:192.168.2.109  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::96de:80ff:feb7:7bdb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:175086 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100250 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:238299741 (238.2 MB)  TX bytes:10073882 (10.0 MB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:871 errors:0 dropped:0 overruns:0 frame:0
          TX packets:871 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:146407 (146.4 KB)  TX bytes:146407 (146.4 KB)


paul@paul:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
paul@paul:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
paul@paul:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
paul@paul:~$ iwlist chan
eth0      no frequency information.


lo        no frequency information.


paul@paul:~$ ping -c 2 $(route -n | grep UG | awk {'print $2'})
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
64 bytes from 192.168.2.1: icmp_seq=1 ttl=64 time=0.833 ms
64 bytes from 192.168.2.1: icmp_seq=2 ttl=64 time=0.465 ms


--- 192.168.2.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 0.465/0.649/0.833/0.184 ms
paul@paul:~$ ping -c 2 [www.ubuntuusers.de](www.ubuntuusers.de)
PING ubuntuusers.de (213.95.41.4) 56(84) bytes of data.
64 bytes from 213.95.41.4: icmp_seq=1 ttl=55 time=28.2 ms
64 bytes from 213.95.41.4: icmp_seq=2 ttl=55 time=28.0 ms


--- ubuntuusers.de ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 2090ms
rtt min/avg/max/mdev = 28.081/28.185/28.290/0.197 ms
paul@paul:~$ ping -c 2 213.95.41.11^C

I don't know wheter it is or not

---

### Post by praseodym on 2014-06-08
Lets check
```

sudo ifup wlan0
```

---

