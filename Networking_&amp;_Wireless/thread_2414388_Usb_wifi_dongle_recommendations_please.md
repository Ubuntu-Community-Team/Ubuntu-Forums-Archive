---
title: "Usb wifi dongle recommendations please"
date: 2019-03-09
forum: Networking &amp; Wireless
---

### Post by iamtheeggman2 on 2019-03-09
Hi,

I'm looking for ubuntu supported and Linux in general  usb wifi dongles... 

I've got one from netgear but it is not connecting to the new router, it can see the router but despite the password going in correctly it just tells me that the network is encrypted implying I've not got the right password.

Anyway the new router can do both 2.4 and 5ghz so if I can get a better dongle this will be OK.

Thanks in advance. 

Kind regards

I believe I need wpa2 compatible devices. Thanks

---

### Post by him610 on 2019-03-09
Recommend you read this post, [https://ubuntuforums.org/showthread.php?t=2397914]("https://ubuntuforums.org/showthread.php?t=2397914")

---

### Post by iamtheeggman2 on 2019-03-10
Thanks for this..

Upon further thinking its not necessarily the answer but I need to find out what specific cause of failure I'm getting in it refusing to connect, is there a way to find out a specific reason rather than it just say its not authenticating properly?

---

### Post by nicholasarussell on 2019-03-10
most cheap ebay dongles are realtek and tend to work, my laptop had a realtek built in and was not supported until I upgraded from 14.04 LTS to 18.04 LTS, I am now sitting on 18.10 no issues.

---

### Post by iamtheeggman2 on 2019-03-10
Hi

Luckily I have found one advertised and reviewed on amazon as working well in ubuntu so I've bought a Laptone N600 Dual band dongle and it's pretty tiny, not much bigger than the port itself!

Thanks again for the responses I'll update you on the use of it when I get it.

Just wondering if you can upgrade the encryption types these USB devices do? Eg update firmware.

Hi, I put the USB dongle in and the device supports the kernel 2.6 (and I presume upwards) mine is 4.15.0_45_generic (buildd@lyc01_amd64-021) but the computer doesn't show as having WiFi devices so what am I doing wrong?

OK well after some testing this is what has happened.

Linux ubuntu as above worked on seeing the local WiFi networks with my old adapter as did ubuntu 10.4, fedora 12 and suse however they just aren't using or seeing the new device.

When I plug it in the windows laptop it brings the new hardware menu up straight away so clearly it is being recognised.

I've even tried moving it to a different USB port and no results

OK well I found out that I needed drivers for this. I downloaded them from ogemray. Com and I now have to follow some instructions to unpack them as I got a parsing error like this.

[https://askubuntu.com/questions/801426/parsing-filters-unsupported-error-during-extraction-of-rar-file](https://askubuntu.com/questions/801426/parsing-filters-unsupported-error-during-extraction-of-rar-file)

Well anyway will try this tomorrow.

Hi I found the drivers but not sure what to do, doesn't Linux have a sort of application that can be used to search for drivers within a given directory?

Hi,

I might be onto a winner here, I found this page [https://ubuntuforums.org/showthread.php?t=1509969](https://ubuntuforums.org/showthread.php?t=1509969)

someone else had success following the instructions a poster gave

I followed these instructions:

> Go to : *Applications > Accessories > Terminal*
```
 	sudo gedit /etc/modprobe.d/blacklist.conf
``` 
The text editor gedit will open the file blacklist.conf
Add the following line to the end ot the opened file.
```
 	blacklist rt2800usb
``` 
Proofread carefully. [COLOR=Red]Save[/COLOR] and close gedit.


however it has not worked. the computer doesn't see the device when connected. they advised to put an output from the terminal if the trick didnt work, here is my output.


```
house@house:~$ lsusb
Bus 001 Device 004: ID 0e8d:7610 MediaTek Inc. 
Bus 001 Device 002: ID 0a16:1200 Trek Technology (S) PTE, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 1bcf:0005 Sunplus Innovation Technology Inc. Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
house@house:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          16384  1
snd_hda_codec_via      20480  1
snd_hda_codec_generic    69632  1 snd_hda_codec_via
ip6t_REJECT            16384  1
nf_reject_ipv6         16384  1 ip6t_REJECT
nf_log_ipv6            16384  5
xt_hl                  16384  22
ip6t_rt                16384  3
nf_conntrack_ipv6      16384  8
nf_defrag_ipv6         24576  1 nf_conntrack_ipv6
ipt_REJECT             16384  1
nf_reject_ipv4         16384  1 ipt_REJECT
nf_log_ipv4            16384  5
nf_log_common          16384  2 nf_log_ipv6,nf_log_ipv4
xt_LOG                 16384  10
snd_hda_codec_hdmi     45056  1
xt_limit               16384  13
xt_tcpudp              16384  18
xt_addrtype            16384  4
nf_conntrack_ipv4      16384  8
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_conntrack           16384  16
edac_mce_amd           28672  0
kvm_amd                73728  0
kvm                   520192  1 kvm_amd
snd_hda_intel          36864  5
snd_hda_codec         106496  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_via
snd_hda_core           65536  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_via
irqbypass              16384  1 kvm
snd_hwdep              16384  1 snd_hda_codec
snd_pcm                86016  4 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            28672  1 snd_seq_midi
snd_seq                57344  2 snd_seq_midi_event,snd_seq_midi
input_leds             16384  0
serio_raw              16384  0
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28672  2 snd_seq,snd_pcm
k10temp                16384  0
snd                    69632  21 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_pcm,snd_hda_codec_via
shpchp                 32768  0
soundcore              16384  1 snd
mac_hid                16384  0
sch_fq_codel           20480  2
ip6table_filter        16384  1
ip6_tables             24576  1 ip6table_filter
nf_conntrack_netbios_ns    16384  0
nf_conntrack_broadcast    16384  1 nf_conntrack_netbios_ns
nf_nat_ftp             16384  0
nf_nat                 28672  1 nf_nat_ftp
nf_conntrack_ftp       16384  1 nf_nat_ftp
nf_conntrack          106496  8 nf_conntrack_ipv6,nf_conntrack_ftp,nf_conntrack_ipv4,nf_conntrack_broadcast,nf_nat_ftp,nf_conntrack_netbios_ns,xt_conntrack,nf_nat
libcrc32c              16384  2 nf_conntrack,nf_nat
iptable_filter         16384  1
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                45056  3 lp,parport_pc,ppdev
ip_tables              20480  1 iptable_filter
x_tables               28672  13 xt_LOG,ipt_REJECT,ip_tables,iptable_filter,xt_tcpudp,xt_limit,ip6t_REJECT,ip6table_filter,xt_addrtype,ip6t_rt,xt_conntrack,ip6_tables,xt_hl
autofs4                40960  2
uas                    20480  0
usb_storage            53248  2 uas
hid_generic            16384  0
usbhid                 49152  0
hid                    98304  2 hid_generic,usbhid
pata_acpi              16384  0
nvidia_drm             36864  1
nvidia_modeset       1105920  8 nvidia_drm
nvidia              13250560  315 nvidia_modeset
drm_kms_helper        151552  1 nvidia_drm
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   339968  4 nvidia_drm,drm_kms_helper
ipmi_devintf           16384  0
ipmi_msghandler        49152  2 nvidia,ipmi_devintf
sata_nv                24576  1
forcedeth              61440  0
i2c_nforce2            16384  0
pata_amd               16384  0
floppy                 61440  0
house@house:~$ ~
```

---

### Post by chili555 on 2019-03-14
> 
Bus 001 Device 004: ID 0e8d:7610 MediaTek Inc. 
Please check here: [https://askubuntu.com/questions/975464/mt7610u-unable-to-install-wifi-driver/975504#975504](https://askubuntu.com/questions/975464/mt7610u-unable-to-install-wifi-driver/975504#975504)

> I might be onto a winner here, I found this page [https://ubuntuforums.org/showthread.php?t=1509969](https://ubuntuforums.org/showthread.php?t=1509969)No post from 2010 written for kernel version 2.6 (!!) is ever going to work in any modern Ubuntu version. Ever.

---

### Post by iamtheeggman2 on 2019-03-14
Hi,

Thanks for the response.  the device is advertised as working on the kernel 2.6 (and presumably onwards?)... But perhaps I was mistaken in thinking it would work on following kernels.

On another note, if it is the case that it only works on the older kernel, is it possible to use the older kernel on the computer instead of the newer one?

---

### Post by chili555 on 2019-03-14
Using kernel version 2.6 is likely impossible. I wouldn't even speculate as to how to start. It is long since end-of-life and a great number of newer devices, sound cards, video cards, etc. won't work with it as there are no matching drivers. There haven't been crucial security updates for many years. It is the kerosene latern of kernels.

> 
The device is reviewed on amazon as working for the current version of ubuntu I expect they were referring to kernel versions much earlier than 4.15 and 4.18 that we are using now.

I suspect that you may have some luck at posts #6 and following here: [https://ubuntuforums.org/showthread.php?t=2390893&highlight=mt7610u](https://ubuntuforums.org/showthread.php?t=2390893&highlight=mt7610u)

---

### Post by iamtheeggman2 on 2019-03-14
Well I am back to square one looking for a wifi device that can be used for wpa2 psk then pref one that is dual band.

Their site doesn't suggest they are old drivers 

Date is 2016

[http://www.iqs.link/mt/](http://www.iqs.link/mt/)

I have a rt2500 pci express WiFi card which is only capable of wpa psk when I need it to do wpa2 psk. Would this advice work possibly?

[https://www.linuxquestions.org/questions/slackware-14/ralink-rt2500-wireless-on-13-37-32-bit-901687/](https://www.linuxquestions.org/questions/slackware-14/ralink-rt2500-wireless-on-13-37-32-bit-901687/)

Also please would you explain what is wicd and ndiswrapper?

Hi to my surprise when I found one of my pci e wifi adapter product on their site it says it support wpa2 so I have emailed them to ask if I can get firmware update for mine which I bought over ten years ago [https://www.edimax.com/edimax/merchandise/merchandise_detail/data/edimax/global/home_legacy_wireless_adapters/ew-7128g](https://www.edimax.com/edimax/merchandise/merchandise_detail/data/edimax/global/home_legacy_wireless_adapters/ew-7128g)

Wow to my surprise they emailed me back at 7:50 am with the following response.


Please keep in mind that the EW-7128g has been phased out for a very long time, and we no longer support this model.

The EW-7128g is using the Ralink RT2561ST chipset and according to this page the card can work with WPA2.
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax)

But after Ralink was taken over by MediaTek, the old drivers were slowly removed.
Perhaps you can still find drivers on GitHub for this model that include the patch for WPA2.

---

### Post by chili555 on 2019-03-15
> **iamtheeggman2 said:**
> Wow to my surprise they emailed me back at 7:50 am with the following response.


Please keep in mind that the EW-7128g has been phased out for a very long time, and we no longer support this model.

The EW-7128g is using the Ralink RT2561ST chipset and according to this page the card can work with WPA2.
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax)

But after Ralink was taken over by MediaTek, the old drivers were slowly removed.
Perhaps you can still find drivers on GitHub for this model that include the patch for WPA2.Any card that you buy new will support WPA2. > 
 have a rt2500 pci express WiFi card which is only capable of wpa psk when I need it to do wpa2 psk. Would this advice work possibly?

[https://www.linuxquestions.org/quest...32-bit-901687/](https://www.linuxquestions.org/quest...32-bit-901687/)

Also please would you explain what is wicd and ndiswrapper?
I am not quite sure how you do it! You keep finding and referring to posts that are 100 years old in Linux years that reference kernel version 2.6! It is over, done with and dead. 

Until you insert your rt2500 card and run:```
sudo iwlist auth
```...then we are not yet confident that your card doesn't do WPA2 with a modern kernel.

Wicd and ndiswrapper are dead ends. Sorry.

---

### Post by iamtheeggman2 on 2019-03-16
OK well interesting it lists this :

Wlx0023ffc8c16 authentication capabilities

Wpa
WPA2 
Cipher-tkip
Cipher-ccmp

Lo        no authentication information 
Enp0s7     no authentication information


Thanks well I wish I could have seen that before I bought a new WiFi dongle!

OK well I think the next step is to find out EXACTLY why it is not connecting to the router, it just says "activation of network connection failed "

---

### Post by chili555 on 2019-03-16
I suggest that you give it the best possible chance to connect.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Then set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
sudo nano /etc/default/crda
```
Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save (Ctrl+o followed by Enter) and close (Ctrl+x) the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

---

### Post by iamtheeggman2 on 2019-03-16
OK but is there a way to get the exact error message making it think it is failing?

Is there anything I can look for on the Linux laptop when it is connecting properly to help us understand why that is connecting but not the pc?

A network configuration file perhaps?

---

### Post by chili555 on 2019-03-16
Check the message log for entries involving either Network Manager or your device. As you are trying and failing to connect:```
cat /var/log/syslog | grep -e etwork -e wlx
```Post the last 12-15 lines.

---

### Post by Redalien0304 on 2019-03-16
Wi-PI usb dongle works perfectly with all my Linux OS, even Raspberry PI.
like this one [https://www.amazon.com/Wi-Pi-Raspberry-802-11n-Wireless-Adapter/dp/B00BDW6D7I/ref=sr_1_2?keywords=wi-pi&qid=1552755785&s=gateway&sr=8-2](https://www.amazon.com/Wi-Pi-Raspberry-802-11n-Wireless-Adapter/dp/B00BDW6D7I/ref=sr_1_2?keywords=wi-pi&qid=1552755785&s=gateway&sr=8-2)

---

### Post by iamtheeggman2 on 2019-03-16
nning -> authenticating
Mar 16 16:44:17 house kernel: [ 4923.988094] wlx00223ffc8c16: send auth to 30:24:78:e4:46:ee (try 2/3)
Mar 16 16:44:17 house kernel: [ 4924.192098] wlx00223ffc8c16: send auth to 30:24:78:e4:46:ee (try 3/3)
Mar 16 16:44:17 house kernel: [ 4924.396081] wlx00223ffc8c16: authentication with 30:24:78:e4:46:ee timed out
Mar 16 16:44:17 house wpa_supplicant[870]: wlx00223ffc8c16: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="BTHub6-WX3G" auth_failures=1 duration=10 reason=CONN_FAILED
Mar 16 16:44:17 house NetworkManager[871]: <info>  [1552754657.8546] device (wlx00223ffc8c16): supplicant interface state: authenticating -> disconnected
Mar 16 16:44:22 house NetworkManager[871]: <info>  [1552754662.9412] device (wlx00223ffc8c16): supplicant interface state: disconnected -> scanning
Mar 16 16:44:28 house wpa_supplicant[870]: wlx00223ffc8c16: CTRL-EVENT-SSID-REENABLED id=0 ssid="BTHub6-WX3G"
Mar 16 16:44:28 house wpa_supplicant[870]: wlx00223ffc8c16: SME: Trying to authenticate with 30:24:78:e4:46:ee (SSID='BTHub6-WX3G' freq=2437 MHz)
Mar 16 16:44:28 house kernel: [ 4934.973533] wlx00223ffc8c16: authenticate with 30:24:78:e4:46:ee
Mar 16 16:44:28 house kernel: [ 4935.155393] wlx00223ffc8c16: send auth to 30:24:78:e4:46:ee (try 1/3)
Mar 16 16:44:28 house NetworkManager[871]: <info>  [1552754668.4158] device (wlx00223ffc8c16): supplicant interface state: scanning -> authenticating
Mar 16 16:44:28 house kernel: [ 4935.360066] wlx00223ffc8c16: send auth to 30:24:78:e4:46:ee (try 2/3)
Mar 16 16:44:28 house kernel: [ 4935.568055] wlx00223ffc8c16: send auth to 30:24:78:e4:46:ee (try 3/3)
Mar 16 16:44:29 house kernel: [ 4935.772068] wlx00223ffc8c16: authentication with 30:24:78:e4:46:ee timed out
Mar 16 16:44:29 house wpa_supplicant[870]: wlx00223ffc8c16: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="BTHub6-WX3G" auth_failures=2 duration=20 reason=CONN_FAILED
Mar 16 16:44:29 house NetworkManager[871]: <info>  [1552754669.2234] device (wlx00223ffc8c16): supplicant interface state: authenticating -> disconnected
Mar 16 16:44:29 house NetworkManager[871]: <warn>  [1552754669.2599] device (wlx00223ffc8c16): Activation: (wifi) association took too long, failing activation
Mar 16 16:44:29 house NetworkManager[871]: <info>  [1552754669.2600] device (wlx00223ffc8c16): state change: config -> failed (reason 'ssid-not-found', sys-iface-state: 'managed')
Mar 16 16:44:29 house NetworkManager[871]: <info>  [1552754669.2602] manager: NetworkManager state is now DISCONNECTED
Mar 16 16:44:29 house kernel: [ 4936.002527] IPv6: ADDRCONF(NETDEV_UP): wlx00223ffc8c16: link is not ready
Mar 16 16:44:29 house NetworkManager[871]: <warn>  [1552754669.2608] device (wlx00223ffc8c16): Activation: failed for connection 'BTHub6-WX3G 1'
Mar 16 16:44:29 house NetworkManager[871]: <info>  [1552754669.2615] device (wlx00223ffc8c16): state change: failed -> disconnected (reason 'none', sys-iface-state: 'managed')
Mar 16 16:44:39 house NetworkManager[871]: <info>  [1552754679.2238] device (wlx00223ffc8c16): supplicant interface state: disconnected -> inactive

Hi I have more lines to show after turning the router to just wpa and not use wpa2 - it still failed to connect.


Mar 16 19:37:59 house NetworkManager[2355]: <info>  [1552765079.5330] Config: added 'ssid' value 'BTHub6-WX3G'
Mar 16 19:37:59 house NetworkManager[2355]: <info>  [1552765079.5332] Config: added 'scan_ssid' value '1'
Mar 16 19:37:59 house NetworkManager[2355]: <info>  [1552765079.5334] Config: added 'bgscan' value 'simple:30:-80:86400'
Mar 16 19:37:59 house NetworkManager[2355]: <info>  [1552765079.5336] Config: added 'key_mgmt' value 'WPA-PSK'
Mar 16 19:37:59 house NetworkManager[2355]: <info>  [1552765079.5337] Config: added 'psk' value '<hidden>'
Mar 16 19:38:00 house NetworkManager[2355]: <info>  [1552765080.6370] device (wlx00223ffc8c16): supplicant interface state: inactive -> scanning
Mar 16 19:38:02 house wpa_supplicant[792]: wlx00223ffc8c16: SME: Trying to authenticate with 30:24:78:e4:46:ee (SSID='BTHub6-WX3G' freq=2437 MHz)
Mar 16 19:38:02 house kernel: [ 4757.605359] wlx00223ffc8c16: authenticate with 30:24:78:e4:46:ee
Mar 16 19:38:03 house kernel: [ 4757.963847] wlx00223ffc8c16: send auth to 30:24:78:e4:46:ee (try 1/3)
Mar 16 19:38:03 house NetworkManager[2355]: <info>  [1552765083.2245] device (wlx00223ffc8c16): supplicant interface state: scanning -> authenticating
Mar 16 19:38:03 house kernel: [ 4758.164025] wlx00223ffc8c16: send auth to 30:24:78:e4:46:ee (try 2/3)
Mar 16 19:38:03 house kernel: [ 4758.368077] wlx00223ffc8c16: send auth to 30:24:78:e4:46:ee (try 3/3)
Mar 16 19:38:03 house kernel: [ 4758.572063] wlx00223ffc8c16: authentication with 30:24:78:e4:46:ee timed out
Mar 16 19:38:04 house wpa_supplicant[792]: wlx00223ffc8c16: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="BTHub6-WX3G" auth_failures=1 duration=10 reason=CONN_FAILED
Mar 16 19:38:04 house NetworkManager[2355]: <info>  [1552765084.0381] device (wlx00223ffc8c16): supplicant interface state: authenticating -> disconnected
Mar 16 19:38:14 house NetworkManager[2355]: <info>  [1552765094.1216] device (wlx00223ffc8c16): supplicant interface state: disconnected -> scanning
Mar 16 19:38:16 house wpa_supplicant[792]: wlx00223ffc8c16: CTRL-EVENT-SSID-REENABLED id=0 ssid="BTHub6-WX3G"
Mar 16 19:38:16 house wpa_supplicant[792]: wlx00223ffc8c16: SME: Trying to authenticate with 30:24:78:e4:46:ee (SSID='BTHub6-WX3G' freq=2437 MHz)
Mar 16 19:38:16 house kernel: [ 4771.105529] wlx00223ffc8c16: authenticate with 30:24:78:e4:46:ee
Mar 16 19:38:16 house kernel: [ 4771.451401] wlx00223ffc8c16: send auth to 30:24:78:e4:46:ee (try 1/3)
Mar 16 19:38:16 house NetworkManager[2355]: <info>  [1552765096.7129] device (wlx00223ffc8c16): supplicant interface state: scanning -> authenticating
Mar 16 19:38:16 house kernel: [ 4771.652116] wlx00223ffc8c16: send auth to 30:24:78:e4:46:ee (try 2/3)
Mar 16 19:38:17 house kernel: [ 4771.856062] wlx00223ffc8c16: send auth to 30:24:78:e4:46:ee (try 3/3)
Mar 16 19:38:17 house kernel: [ 4772.060110] wlx00223ffc8c16: authentication with 30:24:78:e4:46:ee timed out
Mar 16 19:38:17 house wpa_supplicant[792]: wlx00223ffc8c16: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="BTHub6-WX3G" auth_failures=2 duration=20 reason=CONN_FAILED
Mar 16 19:38:17 house NetworkManager[2355]: <info>  [1552765097.5228] device (wlx00223ffc8c16): supplicant interface state: authenticating -> disconnected
Mar 16 19:38:25 house kernel: [ 4780.003122] IPv6: ADDRCONF(NETDEV_UP): wlx00223ffc8c16: link is not ready
Mar 16 19:38:25 house NetworkManager[2355]: <warn>  [1552765105.2600] device (wlx00223ffc8c16): Activation: (wifi) association took too long, failing activation
Mar 16 19:38:25 house NetworkManager[2355]: <info>  [1552765105.2601] device (wlx00223ffc8c16): state change: config -> failed (reason 'ssid-not-found', sys-iface-state: 'managed')
Mar 16 19:38:25 house NetworkManager[2355]: <info>  [1552765105.2603] manager: NetworkManager state is now DISCONNECTED
Mar 16 19:38:25 house NetworkManager[2355]: <warn>  [1552765105.2608] device (wlx00223ffc8c16): Activation: failed for connection 'BTHub6-WX3G 1'
Mar 16 19:38:25 house NetworkManager[2355]: <info>  [1552765105.2615] device (wlx00223ffc8c16): state change: failed -> disconnected (reason 'none', sys-iface-state: 'managed')
Mar 16 19:38:31 house NetworkManager[2355]: <info>  [1552765111.5283] device (wlx00223ffc8c16): supplicant interface state: disconnected -> inactive

> **Redalien0304 said:**
> Wi-PI usb dongle works perfectly with all my Linux OS, even Raspberry PI.
like this one [https://www.amazon.com/Wi-Pi-Raspberry-802-11n-Wireless-Adapter/dp/B00BDW6D7I/ref=sr_1_2?keywords=wi-pi&qid=1552755785&s=gateway&sr=8-2](https://www.amazon.com/Wi-Pi-Raspberry-802-11n-Wireless-Adapter/dp/B00BDW6D7I/ref=sr_1_2?keywords=wi-pi&qid=1552755785&s=gateway&sr=8-2)



Hi, thanks for your response, which item is this please?

---

### Post by chili555 on 2019-03-16
> after turning the router to just wpa and not use wpa2Exactly the opposite of what I recommended:> 
First, check the settings in the router. [COLOR="#FF0000"]WPA2-AES[/COLOR] is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Did you make each and every one of those changes?

---

### Post by iamtheeggman2 on 2019-03-16
It is using aes and not tkip.

I'm pretty sure you did say not to have mixed wpa and wpa2..

---

### Post by chili555 on 2019-03-16
So you made a couple of changes or most of the changes or all of the changes? Your reply is unclear.> 
CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="BTHub6-WX3G" [COLOR="#FF0000"]auth_failures=1 [/COLOR]duration=10 reason=CONN_FAILEDThat strongly suggests that the authentication; that is, password, is incorrect. Please recheck it. Make especially certain that the case is correct. For example, password is not the same as Password which is also not the same as PassWord.

Also make certain that MAC address filtering is not active and also that you are not requesting a static IP address that is not otherwise available.

---

### Post by iamtheeggman2 on 2019-03-17
Password has been checked its definitely in correctly with appropriate upper and lower cases.

I don't see any options about automatic Ip or fixed addressing

wifi 2.5ghz is on channel 6 
wpa is set to auto but from what I can see on my network scanning via the wifi dongle (I now have drivers installed for windows 8.1 laptop) it is using wpa and not  wpa2
there is no wpa/wpa2 mix mode

windows 8.1 doesn't connect vis the usb dongle - so that means on both pc and laptop, using multiple operating systems its the same result, it sees router but doesn't connect.

the router has three modes you can change to make it easier to connect but i'll have to speak to owner (dad) before I want to change it because it states all the devices connected (many) will need to be reconnected using their instruction manuals. I don't want to potentially let it forget everything and he have to spend hours reconnecting.

sadly the router log doesn't log failed login attempts. this is what it shows when the laptop successfully logs in if that is of any help:


10:14:39, 17 Mar.

BR_LAN:The DHCP options that are offered by the device (id:10): DiscoverOptions: 53,12,55 | DiscoverOption55: 1,28,2,3,15,6,119,12,44,47,26,121,42,249,33,252 | RequestOptions: 53,61,50,12,81,60,55 | RequestOption55: 1,15,3,6,44,46,47,31,33,121,249,252,43 | HostName: house | VendorId: MSFT 5.0
 
10:14:39, 17 Mar.

:DHCP Confirmation of Request
 
10:14:36, 17 Mar.

wl0:A WiFi device <00:1F:3B:6C:AE:AD> has successfully connected to SSID (Device/WiFi/SSIDs/SSID[WL_PRIV5G])

this is my usb device
[https://www.netgear.com/support/product/WG111v3.aspx](https://www.netgear.com/support/product/WG111v3.aspx)

this is the router

[https://shop.bt.com/products/bt-smart-hub-088138-C6NX.html](https://shop.bt.com/products/bt-smart-hub-088138-C6NX.html)

I found this interesting page, how do I double check th likelihood that any given chipset here is likely to be a long lasting supported item in Ubuntu or any mainstream version of Linux for that matter? luckily some of them are less than £10 on ebay

[https://www.wirelesshack.org/top-linux-compatible-usb-wireless-adapters.html](https://www.wirelesshack.org/top-linux-compatible-usb-wireless-adapters.html)

If my laptop connects and the device I nit is Dell Wireless 1395 which I can see on ebay, cant I just establish which chipset is in it and fid the pc version and install that? id assume Linux would work with that hardware on the pc when it works with it on the laptop.

ok well I have some temporary success using an edimax router extension device, its only temporary as my brother lent it to me and wants it back, however the setup I have now is that device connects to the wifi and I plug my pc into it using a small rj45 cable. 

[https://www.edimax.com/edimax/merchandise/merchandise_detail/data/edimax/uk/wireless_routers_dual-band/br-6208ac/](https://www.edimax.com/edimax/merchandise/merchandise_detail/data/edimax/uk/wireless_routers_dual-band/br-6208ac/)

so if that connects can I either find out A: how to see it working in order to copy over data into existing wifi adapter and B: if i find their product range to see what wifi dongles go with it, then that in theory would hopefully work too!

Hey,

I got a prompt response from edimax, they say the following devices work on the 18.04 kernel 4.15

EW-7811UAC
EW-7811UTC
EW-7811DAC 

now my next question is, i see ubuntu 18.04 has long term support, but do kernels change over this time? Would it be possible it would stop working after an update?

[https://ubuntuforums.org/showthread.php?t=2394421&highlight=EW-7811UTC](https://ubuntuforums.org/showthread.php?t=2394421&highlight=EW-7811UTC)
this link suggests he product doesnt work ut of the box, however the article is older, is there a way i can check for recent developments on wifi support? this page here seems old.

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax)

[https://edimax.freshdesk.com/support/solutions/articles/14000041287-how-to-install-ew-7811-ac600-ew-7822uac-in-linux-with-kernel-higher-than-v4-1](https://edimax.freshdesk.com/support/solutions/articles/14000041287-how-to-install-ew-7811-ac600-ew-7822uac-in-linux-with-kernel-higher-than-v4-1)

"
[FONT=Andale Mono]As  of November 2017, the Official Linux drivers for the above-mentioned  adapters support Linux kernel up to v4.1 only.  Any versions higher than  that are not supported.  The only workaround is to use an open source  driver from GitHub.  Here's the link for your reference.[/FONT]
[FONT=Andale Mono][https://github.com/aircrack-ng/rtl8812au](https://github.com/aircrack-ng/rtl8812au)"

now i think you have to pay for github, but i am wondering, can i easily just downgrade the kernel to one that this device supports? is it then just running out of the box?
[/FONT]

---

### Post by jeremy31 on 2019-03-18
You do not have to pay for github.  There are updated versions for rtl8812au, even rtl8812au-dkms is in the Ubuntu repos

---

### Post by iamtheeggman2 on 2019-03-18
> **jeremy31 said:**
> You do not have to pay for github.  There are updated versions for rtl8812au, even rtl8812au-dkms is in the Ubuntu repos

so if i buy this card, do all i have to do is install the rtl8812au-dkms and simply start the computer with the card attached and it will work automatically like my ol usb wifi device?

---

### Post by jeremy31 on 2019-03-18
> **iamtheeggman2 said:**
> so if i buy this card, do all i have to do is install the rtl8812au-dkms and simply start the computer with the card attached and it will work automatically like my ol usb wifi device?

If it is true that it is a rtl8812au device, there is one problem with rtl8812au-dkms, the dkms is broken but that can be fixed by editing the /usr/src/rtl8812au-4.3.8.12175.20140902+dfsg/dkms.conf file and change the line that starts with MAKE to
```
MAKE="'make' all KVER=${kernelver}"
```
If this isn't done it builds a module for a new kernel using the old kernels headers rather than the new and you may see exec format error in dmesg

---

### Post by iamtheeggman2 on 2019-03-19
> **jeremy31 said:**
> If it is true that it is a rtl8812au device, there is one problem with rtl8812au-dkms, the dkms is broken but that can be fixed by editing the /usr/src/rtl8812au-4.3.8.12175.20140902+dfsg/dkms.conf file and change the line that starts with MAKE to
```
MAKE="'make' all KVER=${kernelver}"
```
If this isn't done it builds a module for a new kernel using the old kernels headers rather than the new and you may see exec format error in dmesg

Why is it broken? Have you used it before yourself? Will these tricks work on other Linux platforms 3

OK well I spoke with the broadband provider and despite the fact that I was not the account holder they decided to send out a free WiFi to ethernet bridge in the post!

So anyway thanks so much for the responses I've had on here from all of you! I hope you know your spare time is appreciated!

OMG the devices I received to connect to the wifi router don't connect either! Not via the idiot-proof "press the wps button" or through manual search and connect, and indeed I get the exact same issue I had with the ther devices, it sees the router, tries to connect, but simply doesn't!

---

### Post by chili555 on 2019-03-22
Isn't this an ISP and router problem? Shouldn't you take it up with them?

---

### Post by iamtheeggman2 on 2019-03-22
> **chili555 said:**
> Isn't this an ISP and router problem? Shouldn't you take it up with them?

well we will have to go back to them, it doesn't make sense, my old laptop works with linux or windows, two  android phones work and at 5ghz, dads pc tablet (ipad i think) , mums laptop, but dads old laptops, my usb wifi, two pci express cards see it and dont connect, very bizarre!

Dad has incidentally asa  result f one of his laptops not connecting googled it too and he says its a POS lol.but sadly he doesn't use his laptops much if at all, he uses his pc near the router (wired so no issues) and his pc tablet (which connects) so who knows if he will demand a better one or whatever, i will have to talk to him when he gets back home.

come to think of it if my zenithink pc tablet dont connet then thats not cool either i shall check tomorrow

OK well I have some GREAT NEWS!

MY computer connecting to the router has now been SOLVED!!!

I used BTs wifi extender to link to my laptop (wifi to ethernet bridge ie putting cable into laptop and the wifiplug in the wall extender) and it had issues, it could see the router but had no internet access. It had a "fix network connections" helper which I ran and surprisingly it said although it had an IP address but there was a problem.. I had remembered there was a command you type into command prompt to get a new IP address and looked it up and it worked!

The command was

ipconfig /release

then do 

ipconfig /renew

et voila!

Also what I don't understand is why when putting the wifi adapter onto the linux machine it then connected to the router, obviously this was an IP address issue at the router end, which I had restarted this morning (though didn't make any changes to settings). The weird thing is though the router was set to auto ip addressing so I dont understand why this was ever an issue? I was able to then have not only my usb wifi device on my ubuntu box but a pci e wifi card too! However, it appeared to slow down my connection to the net to have both, just using the netgear wifi gave me 28.85dl and 9.4 ul, however the connection to the router itself is like 50, so perhaps this is a limitation of 2.4ghz? 

Anyway this is fast enough for me so I am a very happy chappy! Though I hope there are 5ghz wifi devices for linux out there.

Thank you so much to all of you for your help in this I appreciate your time and patience!

---

