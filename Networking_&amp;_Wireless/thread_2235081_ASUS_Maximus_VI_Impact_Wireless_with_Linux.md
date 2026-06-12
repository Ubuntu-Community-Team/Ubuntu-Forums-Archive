---
title: "ASUS Maximus VI Impact Wireless with Linux"
date: 2014-07-18
forum: Networking &amp; Wireless
---

### Post by pages on 2014-07-18
Hi all ,


Tried looking for help on the Asus forums but having no luck there so thought I might try my luck here.
Recently made a PC using the asus impact VI [motherboard]("http://www.asus.com/Motherboards/MAXIMUS_VI_IMPACT/"). It comes with a "mPCIe Combo II + Wi-Fi 802.11ac/Bluetooth 4.0"wireless adapter which I've been using. Just installed Ubuntu on the machine but it doesn't recognise the wireless . I've had this issue before and it's usually fine since i can download the drivers onto a USB but I'm having no luck in finding them 

 I'm having no luck with trying to google a solution. Unfortunately using Ethernet cable isn't an option so I'm wondering if anyone here knows where I might be able to get the correct drivers or is this a case that it's not supported and I'll have to buy an external wireless adapter

If anyone knows anything it'd be much appreciated.

Cheers !

---

### Post by chili555 on 2014-07-18
Let's start by identifying the device. Please open a terminal and run and post:```
lspci-nn | grep 0280
```Thanks.

---

### Post by pages on 2014-07-18
Hey ran that 

00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I217-V [8086:153b] (rev 05)

---

### Post by chili555 on 2014-07-18
I asked for:```
lspci-nn | grep 02[COLOR="#FF0000"][SIZE=3]8[/SIZE][/COLOR]0
```But you evidently typed 0200:```
00:19.0 Ethernet controller [[COLOR="#FF0000"]0200[/COLOR]]: Intel Corporation Ethernet Connection I217-V [8086:153b] (rev 05)
```Could you give it another try, please?

---

### Post by pages on 2014-07-18
Apologies !

$ lspci -nn | grep 0280
03:00.0 Network controller [0280]: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)

---

### Post by chili555 on 2014-07-18
> Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)Ouch!!

This is one of the toughest devices to get going in all of Ubuntu and, in fact, all of Linux. This mess will give you a slight taste of the nightmare: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1173761](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1173761)

The workaround requires many needed packages and their dependencies and the dependencies of the dependencies! It isn't as easy as downloading a driver and installing it. It involves compiling a driver from scratch and even patching it. It's sort of like buying a block of aluminum and carving away everything that isn't a Toyota!

If you had a temporary wired ethernet connection, you could probably get it going in ten minutes; without, maybe ten days if ever.

If it were my motherboard, I'd take this option:> it's not supported and I'll have to buy an external wireless adapterThere are several threads here about working USB devices. They are pretty inexpensive and will work immediately with drivers already built in to recent Ubuntu versions.

Then check back in six months or so and see if support has improved.

---

### Post by praseodym on 2014-07-19
Please try this workaround on the fly:

```
sudo modprobe -rfv wl
sudo modprobe -rfv bcma ssb
sudo modprobe -v wl
sudo ifconfig eth1 up
sudo iwconfig eth1 power off
```

---

### Post by pages on 2014-07-19
> **praseodym said:**
> Please try this workaround on the fly:

```
sudo modprobe -rfv wl
sudo modprobe -rfv bcma ssb
sudo modprobe -v wl
sudo ifconfig eth1 up
sudo iwconfig eth1 power off
```



Hey thanks for the advice , tried running those modprobe commands the but WL module isn't found. 

Looked online for help but ran these 

sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source[INDENT]*Got Error-- E: Unable to locate package bcmvl-kernal-source*[/INDENT]
sudo modprobe wl[INDENT]*Got Error-- FATAL: Module wl not found *
[/INDENT]


>  

[COLOR=#000000]This is one of the toughest devices to get going in all of Ubuntu and, in fact, all of Linux. This mess will give you a slight taste of the nightmare:[/COLOR][https://bugs.launchpad.net/ubuntu/+s...x/+bug/1173761]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1173761")

[COLOR=#000000]The workaround requires many needed packages and their dependencies and the dependencies of the dependencies! It isn't as easy as downloading a driver and installing it. It involves compiling a driver from scratch and even patching it. It's sort of like buying a block of aluminum and carving away everything that isn't a Toyota!
[/COLOR][COLOR=#000000]

I've tethered a mobile phone as a temporary option to download stuff i need but obviously this isn't something I want to be doing for life.
If i was to go that method ( sorry cause it just seems complicated ) do i just download and install these two ?
[/COLOR]

[LIST]
[*][http://people.canonical.com/~ypwong/drivers/broadcom/hybrid-v35_64-nodebug-pcoem-6_30_223_95.tar.gz](http://people.canonical.com/~ypwong/drivers/broadcom/hybrid-v35_64-nodebug-pcoem-6_30_223_95.tar.gz)
[*][http://launchpadlibrarian.net/143917424/bcmwl-kernel-source_6.30.223.30%2Bbdcom-0ubuntu3_amd64.deb](http://launchpadlibrarian.net/143917424/bcmwl-kernel-source_6.30.223.30%2Bbdcom-0ubuntu3_amd64.deb)
[/LIST]

---

### Post by chili555 on 2014-07-19
I think there is a very small chance that the bcmwl driver may work. Before we proceed, let's try it:```
sudo apt-get update
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```Any change? If not, let's try some diagnosis:```
dmesg | grep wl
```If this fails, we'll plunge into the deep waters.

---

### Post by pages on 2014-07-19
sudo apt-get install bcmwl-kernel-source

Seems to have been the key to this , ran that.


shane@shane-All-Series:~$ sudo modprobe wl
shane@shane-All-Series:~$ sudo modprobe -rfv wl
rmmod wl
rmmod cfg80211
shane@shane-All-Series:~$ sudo modprobe -rfv bcma ssb
shane@shane-All-Series:~$ sudo modprobe -v wl
insmod /lib/modules/3.13.0-24-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.13.0-24-generic/updates/dkms/wl.ko 
shane@shane-All-Series:~$ sudo ifconfig eth1 up
eth1: ERROR while getting interface flags: No such device
shane@shane-All-Series:~$ sudo ifconfig eth1 power off
power: Unknown host
ifconfig: `--help' gives usage information.
shane@shane-All-Series:~$ 




shane@shane-All-Series:~$ dmesg | grep wl
[ 4303.265552] wl: module license 'MIXED/Proprietary' taints kernel.
[ 4303.266479] wl: module verification failed: signature and/or  required key missing - tainting kernel
[ 4303.285098] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[ 4303.329067] wlan0: Broadcom BCM43b1 802.11 Hybrid Wireless Controller 6.30.223.141 (r415941)
[ 4452.809171] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[ 4452.851532] wlan0: Broadcom BCM43b1 802.11 Hybrid Wireless Controller 6.30.223.141 (r415941)
shane@shane-All-Series:~$ 


Can see wireless networks now 
(although can't seem to connect to them even with the password )

---

### Post by praseodym on 2014-07-19
Ok, lets check now
```

lsmod
iwconfig
ifconfig -a
rfkill list
cat /etc/resolv.conf
iwlist chan
sudo iwlist scan
```

---

### Post by pages on 2014-07-19
Prepare the eyes for spam !
```

shane@shane-All-Series:~$ lsmod
Module                  Size  Used by
wl                   4207846  0 
cfg80211              484040  1 wl
lib80211_crypt_tkip    17619  0 
lib80211               14381  2 wl,lib80211_crypt_tkip
rndis_host             14503  0 
cdc_ether              14351  1 rndis_host
usbnet                 43877  2 rndis_host,cdc_ether
mii                    13934  1 usbnet
nls_iso8859_1          12713  0 
usb_storage            62209  0 
bnep                   19624  2 
rfcomm                 69160  0 
bluetooth             395423  10 bnep,rfcomm
dm_crypt               23177  0 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
joydev                 17381  0 
videodev              134688  2 uvcvideo,videobuf2_core
eeepc_wmi              13151  0 
asus_wmi               24191  1 eeepc_wmi
sparse_keymap          13948  1 asus_wmi
snd_hda_codec_hdmi     46207  1 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm                   451511  0 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
snd_hda_codec_realtek    61438  1 
snd_seq_midi           13324  0 
aesni_intel            55624  465 
snd_seq_midi_event     14899  1 snd_seq_midi
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
snd_rawmidi            30144  1 snd_seq_midi
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
snd_hda_intel          52355  15 
cryptd                 20359  235 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
psmouse               102222  0 
snd_hwdep              13602  1 snd_hda_codec
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
mei_me                 18627  0 
serio_raw              13462  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
mei                    82274  1 mei_me
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
lpc_ich                21080  0 
snd                    69238  41 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd
mac_hid                13205  0 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 52616  0 
hid                   106148  2 hid_generic,usbhid
nouveau              1097199  5 
e1000e                254433  0 
ahci                   25819  2 
mxm_wmi                13021  1 nouveau
i2c_algo_bit           13413  1 nouveau
ptp                    18933  1 e1000e
libahci                32168  1 ahci
ttm                    85115  1 nouveau
pps_core               19382  1 ptp
drm_kms_helper         52758  1 nouveau
drm                   302817  7 ttm,drm_kms_helper,nouveau
video                  19476  2 nouveau,asus_wmi
wmi                    19177  3 mxm_wmi,nouveau,asus_wmi
shane@shane-All-Series:~$ iwconfig
usb0      no wireless extensions.

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
shane@shane-All-Series:~$ if config -a
> ^C
shane@shane-All-Series:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr e0:3f:49:7c:32:e7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:f7100000-f7120000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:823 errors:0 dropped:0 overruns:0 frame:0
          TX packets:823 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:78524 (78.5 KB)  TX bytes:78524 (78.5 KB)

usb0      Link encap:Ethernet  HWaddr 96:97:36:d5:a9:a8  
          inet addr:192.168.42.130  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::9497:36ff:fed5:a9a8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3539 (3.5 KB)  TX bytes:13271 (13.2 KB)

wlan0     Link encap:Ethernet  HWaddr 54:27:1e:86:5c:78  
          inet6 addr: fe80::5627:1eff:fe86:5c78/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:442 errors:0 dropped:0 overruns:0 frame:1146
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:49946 (49.9 KB)  TX bytes:0 (0.0 B)
          Interrupt:19 

shane@shane-All-Series:~$ rfkill list
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
shane@shane-All-Series:~$ cat /etc/resolv.conf 
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
shane@shane-All-Series:~$ iwlist chan
usb0      no frequency information.

eth0      no frequency information.

lo        no frequency information.

wlan0     26 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
shane@shane-All-Series:~$ sudo iwlist scan
[sudo] password for shane: 
usb0      Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.




```

---

### Post by chili555 on 2014-07-19
You will get a better result trying to connect with the tether detached, I suspect.

---

### Post by pages on 2014-07-19
Yeah thought it might be because of that too , tried it without the connection and still no joy.
Also tried making the phone a portable hotspot and connecting to it with no luck as well.

It seems to be not able to establish any wifi connections , but tethering via phone works.
Any ideas ?

---

### Post by chili555 on 2014-07-19
Please see praseodym's post above. We'd love to see the results.

---

### Post by pages on 2014-07-19
hey I've the output of one of his latest request in post #12 

But here's the output from his original request

```

shane@shane-All-Series:~$ sudo modprobe -rfv wl
[sudo] password for shane: 
rmmod wl
rmmod cfg80211
shane@shane-All-Series:~$ sudo modprobe -rfv bcma ssb
shane@shane-All-Series:~$ sudo modprobe -v wl
insmod /lib/modules/3.13.0-24-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.13.0-24-generic/updates/dkms/wl.ko 
shane@shane-All-Series:~$ sudo ifconfig eth1 up
eth1: ERROR while getting interface flags: No such device
shane@shane-All-Series:~$ sudo iwconfig eth1 power off
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device eth1 ; No such device.
shane@shane-All-Series:~$ 



```

---

### Post by chili555 on 2014-07-19
Let's try it a bit differently:```
sudo iwlist wlan0 scan
```We don't need to see all the results, just are there some. If not, what is the error or warning. Also:```
cat /var/log/syslog | grep -e etwork -e wlan | tail -n20
```

---

### Post by pages on 2014-07-19
> **chili555 said:**
> 
```
sudo iwlist wlan0 scan
```

Yep it's returning the Wifi's which my receiver is picking up 

> 
```
cat /var/log/syslog | grep -e etwork -e wlan | tail -n20
```

Ran this and got back 
```
 shane@shane-All-Series:~$ cat /var/log/syslog | grep -e etwork -e wlan | tail -n20
Jul 19 22:02:54 shane-All-Series NetworkManager[1048]: <info> (usb0): DHCPv4 state changed nbi -> preinit
Jul 19 22:03:00 shane-All-Series NetworkManager[1048]: <info> (usb0): DHCPv4 state changed preinit -> bound
Jul 19 22:03:00 shane-All-Series NetworkManager[1048]: <info>   address 192.168.42.138
Jul 19 22:03:00 shane-All-Series NetworkManager[1048]: <info>   prefix 24 (255.255.255.0)
Jul 19 22:03:00 shane-All-Series NetworkManager[1048]: <info>   gateway 192.168.42.129
Jul 19 22:03:00 shane-All-Series NetworkManager[1048]: <info>   hostname 'shane-All-Series'
Jul 19 22:03:00 shane-All-Series NetworkManager[1048]: <info>   nameserver '192.168.42.129'
Jul 19 22:03:00 shane-All-Series NetworkManager[1048]: <info> Activation (usb0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jul 19 22:03:00 shane-All-Series NetworkManager[1048]: <info> Activation (usb0) Stage 5 of 5 (IPv4 Commit) started...
Jul 19 22:03:01 shane-All-Series NetworkManager[1048]: <info> (usb0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Jul 19 22:03:01 shane-All-Series NetworkManager[1048]: <info> Activation (usb0) Stage 5 of 5 (IPv4 Commit) complete.
Jul 19 22:03:01 shane-All-Series NetworkManager[1048]: <info> (usb0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Jul 19 22:03:01 shane-All-Series NetworkManager[1048]: <info> NetworkManager state is now CONNECTED_GLOBAL
Jul 19 22:03:01 shane-All-Series NetworkManager[1048]: <info> Policy set 'Wired connection 2' (usb0) as default for IPv4 routing and DNS.
Jul 19 22:03:01 shane-All-Series NetworkManager[1048]: <info> Writing DNS information to /sbin/resolvconf
Jul 19 22:03:01 shane-All-Series NetworkManager[1048]: <info> Activation (usb0) successful, device activated.
Jul 19 22:03:14 shane-All-Series NetworkManager[1048]: <info> (usb0): IP6 addrconf timed out or failed.
Jul 19 22:03:14 shane-All-Series NetworkManager[1048]: <info> Activation (usb0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jul 19 22:03:14 shane-All-Series NetworkManager[1048]: <info> Activation (usb0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jul 19 22:03:14 shane-All-Series NetworkManager[1048]: <info> Activation (usb0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
shane@shane-All-Series:~$ 


```

not sure if that log has been useful to you since I've been plugging / unpluggin my phone when i go onto the machine

---

### Post by chili555 on 2014-07-19
> not sure if that log has been useful to youNot very; it shows that the USB connects perfectly. Please detach the tether and try again. Try to connect to your network, supply the WPA2 password and then capture the log:```
cat /var/log/syslog | grep -e etwork -e wlan | tail -n20  >  wifi.txt
```Find the file wifi.txt and paste it in your reply.

---

### Post by pages on 2014-07-19
here's the output  did a tail -50 just in case some  important information might have been cut from the top .
From reading it , it seems to be auth failures but you'll have to trust me when im saying that I am entering then correct password 

```
 
Jul 19 22:20:54 shane-All-Series NetworkManager[1048]: <info> Config: added 'auth_alg' value 'OPEN'
Jul 19 22:20:54 shane-All-Series NetworkManager[1048]: <info> Config: added 'psk' value '<omitted>'
Jul 19 22:20:54 shane-All-Series NetworkManager[1048]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jul 19 22:20:54 shane-All-Series NetworkManager[1048]: <info> Config: set interface ap_scan to 1
Jul 19 22:20:54 shane-All-Series NetworkManager[1048]: <info> (wlan0): supplicant interface state: inactive -> scanning
Jul 19 22:21:04 shane-All-Series wpa_supplicant[5576]: wlan0: Trying to associate with 4c:72:b9:9a:28:80 (SSID='UPC687842' freq=2437 MHz)
Jul 19 22:21:04 shane-All-Series NetworkManager[1048]: <info> (wlan0): supplicant interface state: scanning -> associating
Jul 19 22:21:14 shane-All-Series wpa_supplicant[5576]: wlan0: Authentication with 4c:72:b9:9a:28:80 timed out.
Jul 19 22:21:14 shane-All-Series wpa_supplicant[5576]: wlan0: CTRL-EVENT-DISCONNECTED bssid=4c:72:b9:9a:28:80 reason=3 locally_generated=1
Jul 19 22:21:14 shane-All-Series wpa_supplicant[5576]: wlan0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="UPC687842" auth_failures=1 duration=10
Jul 19 22:21:14 shane-All-Series NetworkManager[1048]: <warn> Connection disconnected (reason -3)
Jul 19 22:21:14 shane-All-Series NetworkManager[1048]: <info> (wlan0): supplicant interface state: associating -> disconnected
Jul 19 22:21:14 shane-All-Series NetworkManager[1048]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jul 19 22:21:19 shane-All-Series NetworkManager[1048]: <warn> Activation (wlan0/wireless): association took too long.
Jul 19 22:21:19 shane-All-Series NetworkManager[1048]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Jul 19 22:21:19 shane-All-Series NetworkManager[1048]: <warn> Activation (wlan0/wireless): asking for new secrets
Jul 19 22:21:19 shane-All-Series NetworkManager[1048]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Jul 19 22:21:19 shane-All-Series NetworkManager[1048]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Jul 19 22:21:24 shane-All-Series NetworkManager[1048]: <info> (wlan0): supplicant interface state: scanning -> inactive
Jul 19 22:21:38 shane-All-Series NetworkManager[1048]: get_secret_flags: assertion 'is_secret_prop (setting, secret_name, error)' failed
Jul 19 22:21:38 shane-All-Series NetworkManager[1048]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 19 22:21:38 shane-All-Series NetworkManager[1048]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jul 19 22:21:38 shane-All-Series NetworkManager[1048]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Jul 19 22:21:38 shane-All-Series NetworkManager[1048]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jul 19 22:21:38 shane-All-Series NetworkManager[1048]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jul 19 22:21:38 shane-All-Series NetworkManager[1048]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jul 19 22:21:38 shane-All-Series NetworkManager[1048]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jul 19 22:21:38 shane-All-Series NetworkManager[1048]: <info> Activation (wlan0/wireless): connection 'UPC687842' has security, and secrets exist.  No new secrets needed.
Jul 19 22:21:38 shane-All-Series NetworkManager[1048]: <info> Config: added 'ssid' value 'UPC687842'
Jul 19 22:21:38 shane-All-Series NetworkManager[1048]: <info> Config: added 'scan_ssid' value '1'
Jul 19 22:21:38 shane-All-Series NetworkManager[1048]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jul 19 22:21:38 shane-All-Series NetworkManager[1048]: <info> Config: added 'auth_alg' value 'OPEN'
Jul 19 22:21:38 shane-All-Series NetworkManager[1048]: <info> Config: added 'psk' value '<omitted>'
Jul 19 22:21:38 shane-All-Series NetworkManager[1048]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jul 19 22:21:38 shane-All-Series NetworkManager[1048]: <info> Config: set interface ap_scan to 1
Jul 19 22:21:38 shane-All-Series NetworkManager[1048]: <info> (wlan0): supplicant interface state: inactive -> scanning
Jul 19 22:21:48 shane-All-Series wpa_supplicant[5576]: wlan0: Trying to associate with 4c:72:b9:9a:28:80 (SSID='UPC687842' freq=2437 MHz)
Jul 19 22:21:48 shane-All-Series NetworkManager[1048]: <info> (wlan0): supplicant interface state: scanning -> associating
Jul 19 22:21:58 shane-All-Series wpa_supplicant[5576]: wlan0: Authentication with 4c:72:b9:9a:28:80 timed out.
Jul 19 22:21:58 shane-All-Series wpa_supplicant[5576]: wlan0: CTRL-EVENT-DISCONNECTED bssid=4c:72:b9:9a:28:80 reason=3 locally_generated=1
Jul 19 22:21:58 shane-All-Series wpa_supplicant[5576]: wlan0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="UPC687842" auth_failures=1 duration=10
Jul 19 22:21:58 shane-All-Series NetworkManager[1048]: <warn> Connection disconnected (reason -3)
Jul 19 22:21:58 shane-All-Series NetworkManager[1048]: <info> (wlan0): supplicant interface state: associating -> disconnected
Jul 19 22:21:58 shane-All-Series NetworkManager[1048]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jul 19 22:22:03 shane-All-Series NetworkManager[1048]: <warn> Activation (wlan0/wireless): association took too long.
Jul 19 22:22:03 shane-All-Series NetworkManager[1048]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Jul 19 22:22:03 shane-All-Series NetworkManager[1048]: <warn> Activation (wlan0/wireless): asking for new secrets
Jul 19 22:22:03 shane-All-Series NetworkManager[1048]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Jul 19 22:22:03 shane-All-Series NetworkManager[1048]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Jul 19 22:22:08 shane-All-Series NetworkManager[1048]: <info> (wlan0): supplicant interface state: scanning -> inactive


```

---

### Post by chili555 on 2014-07-19
> get_secret_flags: assertion 'is_secret_prop (setting, secret_name, error)' failedVery interesting. Is the behavior the same if you set IPv6 to 'Ignore'? That seems to be a regular finding when I Google the error. [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

---

### Post by pages on 2014-07-19
Ok , disabled ipv6 and ran that again
```

Jul 19 23:11:34 shane-All-Series NetworkManager[1048]: <info> Config: set interface ap_scan to 1
Jul 19 23:11:34 shane-All-Series NetworkManager[1048]: <info> (wlan0): supplicant interface state: inactive -> scanning
Jul 19 23:11:44 shane-All-Series wpa_supplicant[5576]: wlan0: Trying to associate with 4c:72:b9:9a:28:80 (SSID='UPC687842' freq=2437 MHz)
Jul 19 23:11:44 shane-All-Series NetworkManager[1048]: <info> (wlan0): supplicant interface state: scanning -> associating
Jul 19 23:11:54 shane-All-Series wpa_supplicant[5576]: wlan0: Authentication with 4c:72:b9:9a:28:80 timed out.
Jul 19 23:11:54 shane-All-Series wpa_supplicant[5576]: wlan0: CTRL-EVENT-DISCONNECTED bssid=4c:72:b9:9a:28:80 reason=3 locally_generated=1
Jul 19 23:11:54 shane-All-Series wpa_supplicant[5576]: wlan0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="UPC687842" auth_failures=1 duration=10
Jul 19 23:11:54 shane-All-Series NetworkManager[1048]: <warn> Connection disconnected (reason -3)
Jul 19 23:11:54 shane-All-Series NetworkManager[1048]: <info> (wlan0): supplicant interface state: associating -> disconnected
Jul 19 23:11:54 shane-All-Series NetworkManager[1048]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jul 19 23:11:59 shane-All-Series NetworkManager[1048]: <warn> Activation (wlan0/wireless): association took too long.
Jul 19 23:11:59 shane-All-Series NetworkManager[1048]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Jul 19 23:11:59 shane-All-Series NetworkManager[1048]: <warn> Activation (wlan0/wireless): asking for new secrets
Jul 19 23:11:59 shane-All-Series NetworkManager[1048]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Jul 19 23:11:59 shane-All-Series NetworkManager[1048]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Jul 19 23:12:02 shane-All-Series NetworkManager[1048]: get_secret_flags: assertion 'is_secret_prop (setting, secret_name, error)' failed
Jul 19 23:12:02 shane-All-Series NetworkManager[1048]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 19 23:12:02 shane-All-Series NetworkManager[1048]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jul 19 23:12:02 shane-All-Series NetworkManager[1048]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Jul 19 23:12:02 shane-All-Series NetworkManager[1048]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jul 19 23:12:02 shane-All-Series NetworkManager[1048]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jul 19 23:12:02 shane-All-Series NetworkManager[1048]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jul 19 23:12:02 shane-All-Series NetworkManager[1048]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jul 19 23:12:02 shane-All-Series NetworkManager[1048]: <info> Activation (wlan0/wireless): connection 'UPC687842' has security, and secrets exist.  No new secrets needed.
Jul 19 23:12:02 shane-All-Series NetworkManager[1048]: <info> Config: added 'ssid' value 'UPC687842'
Jul 19 23:12:02 shane-All-Series NetworkManager[1048]: <info> Config: added 'scan_ssid' value '1'
Jul 19 23:12:02 shane-All-Series NetworkManager[1048]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jul 19 23:12:02 shane-All-Series NetworkManager[1048]: <info> Config: added 'auth_alg' value 'OPEN'
Jul 19 23:12:02 shane-All-Series NetworkManager[1048]: <info> Config: added 'psk' value '<omitted>'
Jul 19 23:12:02 shane-All-Series NetworkManager[1048]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jul 19 23:12:02 shane-All-Series NetworkManager[1048]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Jul 19 23:12:02 shane-All-Series NetworkManager[1048]: <info> Config: set interface ap_scan to 1
Jul 19 23:12:04 shane-All-Series wpa_supplicant[5576]: wlan0: Trying to associate with 4c:72:b9:9a:28:80 (SSID='UPC687842' freq=2437 MHz)
Jul 19 23:12:04 shane-All-Series NetworkManager[1048]: <info> (wlan0): supplicant interface state: scanning -> associating
Jul 19 23:12:14 shane-All-Series wpa_supplicant[5576]: wlan0: Authentication with 4c:72:b9:9a:28:80 timed out.
Jul 19 23:12:14 shane-All-Series wpa_supplicant[5576]: wlan0: CTRL-EVENT-DISCONNECTED bssid=4c:72:b9:9a:28:80 reason=3 locally_generated=1
Jul 19 23:12:14 shane-All-Series wpa_supplicant[5576]: wlan0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="UPC687842" auth_failures=1 duration=10
Jul 19 23:12:14 shane-All-Series NetworkManager[1048]: <warn> Connection disconnected (reason -3)
Jul 19 23:12:14 shane-All-Series NetworkManager[1048]: <info> (wlan0): supplicant interface state: associating -> disconnected
Jul 19 23:12:14 shane-All-Series NetworkManager[1048]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jul 19 23:12:24 shane-All-Series wpa_supplicant[5576]: wlan0: CTRL-EVENT-SSID-REENABLED id=0 ssid="UPC687842"
Jul 19 23:12:24 shane-All-Series wpa_supplicant[5576]: wlan0: Trying to associate with 4c:72:b9:9a:28:80 (SSID='UPC687842' freq=2437 MHz)
Jul 19 23:12:24 shane-All-Series NetworkManager[1048]: <info> (wlan0): supplicant interface state: scanning -> associating
Jul 19 23:12:28 shane-All-Series NetworkManager[1048]: <warn> Activation (wlan0/wireless): association took too long.
Jul 19 23:12:28 shane-All-Series NetworkManager[1048]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Jul 19 23:12:28 shane-All-Series NetworkManager[1048]: <warn> Activation (wlan0/wireless): asking for new secrets
Jul 19 23:12:28 shane-All-Series wpa_supplicant[5576]: wlan0: CTRL-EVENT-DISCONNECTED bssid=4c:72:b9:9a:28:80 reason=3 locally_generated=1
Jul 19 23:12:28 shane-All-Series NetworkManager[1048]: <warn> Connection disconnected (reason -3)
Jul 19 23:12:28 shane-All-Series NetworkManager[1048]: <info> (wlan0): supplicant interface state: associating -> disconnected
Jul 19 23:12:28 shane-All-Series NetworkManager[1048]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.

```

---

### Post by chili555 on 2014-07-20
We are running very low on viable options. First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router.

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

The logs show that Network Manager is struggling and not the driver. If these changes don't help, I really have no other suggestions.

---

### Post by pages on 2014-07-20
You sir are a genious !

It's working now.
Just in case there are others out there who have similar issues Here's what I ran to alter stuff to help it work.

```

sudo apt-get update
sudo apt-get install bcmwl-kernel-source
sudo modprobe -rfv wl
sudo modprobe -rfv bcma ssb 
sudo modprobe -v wl 
sudo ifconfig eth1 up 
sudo iwconfig eth1 power off

```
[Disable ipv6]("http://ubuntuforums.org/showthread.php?t=87798&page=16")
```

sudo iw reg set [$COUNTRY_DOMAIN]("http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2")
sudo vi /etc/default/crda  #edit last line to country domain

```

---

### Post by chili555 on 2014-07-20
Awesome! Glad it's working.

---

