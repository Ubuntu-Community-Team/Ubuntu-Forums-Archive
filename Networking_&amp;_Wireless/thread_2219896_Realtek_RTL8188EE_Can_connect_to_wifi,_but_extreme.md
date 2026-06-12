---
title: "Realtek RTL8188EE: Can connect to wifi, but extremely slow."
date: 2014-04-25
forum: Networking &amp; Wireless
---

### Post by Jonathan_Law on 2014-04-25
Hi guys.

I've recently installed Ubuntu 14 LTS, Everything has gone greatly, with some tweaks here and there with the exception of the wifi. I have been able to connect, but it is incredibly slow compared to when I had Windows before this installation, and is still quick on my desktop computer.

I'm not sure what the problem is, and have tried a few suggestions which I didn't really understand, and have reversed when it was evident that it did not help.

I'm posting the output of a list of commands which another user posted and got good response from.
[B]
$ uname -r -m
```
[/B]3.13.0-24-generic x86_64[B]
```
[/B][B]
$ sudo lshw -c network
```
[/B]  *-network                      description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 07
       serial: a0:48:1c:11:fa:d5
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8106e-1_0.0.1 06/29/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:78 ioport:3000(size=256) memory:f0104000-f0104fff memory:f0100000-f0103fff memory:f0110000-f011ffff
  *-network
       description: Wireless interface
       product: RTL8188EE Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 01
       serial: 70:18:8b:38:3c:f9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8188ee driverversion=3.13.0-24-generic firmware=N/A ip=192.168.1.94 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn

       resources: irq:80 ioport:2000(size=256) memory:f0200000-f0203fff[B]
```
[/B]
[B]$ iwconfig
```
[/B]eth0      no wireless extensions.

lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"BTHub3-4HC5"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:01:3B:96:16:52   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-38 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:247   Missed beacon:0


[B]
```
[/B][B]
$ lspci -vnn | grep -i net -A 8

```
[/B]05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)	Subsystem: Hewlett-Packard Company Device [103c:2139]
	Flags: bus master, fast devsel, latency 0, IRQ 78
	I/O ports at 3000 [size=256]
	Memory at f0104000 (64-bit, prefetchable) [size=4K]
	Memory at f0100000 (64-bit, prefetchable) [size=16K]
	Expansion ROM at f0110000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
--
06:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:197d]
	Flags: bus master, fast devsel, latency 0, IRQ 80
	I/O ports at 2000 [size=256]
	Memory at f0200000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: rtl8188ee


[B]
```
[/B]
[B]$ rfkill list 

```
[/B]0: phy0: Wireless LAN	Soft blocked: no
	Hard blocked: no


[B]
```
[/B][B]
$ nm-tool
```
[/B]NetworkManager Tool

State: connected (global)


- Device: wlan0  [BTHub3-4HC5] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8188ee
  State:             connected
  Default:           yes
  HW Address:        70:18:8B:38:3C:F9


  Capabilities:
    Speed:           72 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    BTHub3-4XNT:     Infra, 20:F3:A3:02:2F:7B, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    BTWifi-X:        Infra, 22:FE:F4:67:17:20, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2 Enterprise
    SKY09D20:        Infra, C8:CD:72:C0:9D:21, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    BTHub3-5H6T:     Infra, 88:53:D4:6E:05:99, Freq 2462 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    BTHub3-MPZM:     Infra, 00:FE:F4:67:17:20, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    BTWiFi-with-FON: Infra, 82:F3:A3:02:2F:7C, Freq 2412 MHz, Rate 54 Mb/s, Strength 80
    BTWiFi-with-FON: Infra, 12:01:3B:96:16:52, Freq 2437 MHz, Rate 54 Mb/s, Strength 100
    BTWifi-with-FON: Infra, 02:FE:F4:67:17:20, Freq 2437 MHz, Rate 54 Mb/s, Strength 64
    BTWiFi:          Infra, 02:01:3B:96:16:52, Freq 2437 MHz, Rate 54 Mb/s, Strength 100
    BTWiFi-with-FON: Infra, 3A:53:D4:6E:05:9A, Freq 2462 MHz, Rate 54 Mb/s, Strength 64
    BTWiFi-with-FON: Infra, 8A:2B:C1:6C:17:5A, Freq 2412 MHz, Rate 54 Mb/s, Strength 77
    TALKTALK-028D7A: Infra, C4:A8:1D:02:8D:7A, Freq 2462 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    BTHub3-Z38H:     Infra, 20:2B:C1:6C:17:59, Freq 2412 MHz, Rate 54 Mb/s, Strength 77 WPA WPA2
    *BTHub3-4HC5:    Infra, 00:01:3B:96:16:52, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    BTWifi-with-FON: Infra, CC:33:BB:1A:73:EF, Freq 2462 MHz, Rate 54 Mb/s, Strength 60
    RUTLAND1:        Infra, 4C:8B:EF:DF:97:F0, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2


  IPv4 Settings:
    Address:         192.168.1.94
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254


    DNS:             192.168.1.254




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        A0:48:1C:11:FA:D5


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off




[B]
```
[/B][B]
$ cat /etc/network/interfaces
```
[/B]# interfaces(5) file used by ifup(8) and ifdown(8)auto lo
iface lo inet loopback


[B]
```
[/B]
[B]$ lsmod
```
[/B]Module                  Size  Used byctr                    13049  1 
ccm                    17773  1 
rfcomm                 69160  0 
bnep                   19624  2 
bluetooth             395423  10 bnep,rfcomm
nls_iso8859_1          12713  1 
snd_hda_codec_realtek    61438  1 
snd_hda_codec_hdmi     46207  1 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
joydev                 17381  0 
videodev              134688  2 uvcvideo,videobuf2_core
hp_wmi                 14062  0 
amd_freq_sensitivity    12589  0 
sparse_keymap          13948  1 hp_wmi
snd_hda_intel          52355  5 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
kvm_amd                59987  0 
arc4                   12608  2 
radeon               1514165  3 
kvm                   451511  1 kvm_amd
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
rtl8188ee              89601  0 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
aesni_intel            55624  2 
snd_rawmidi            30144  1 snd_seq_midi
aes_x86_64             17131  1 aesni_intel
rtl_pci                26690  1 rtl8188ee
lrw                    13286  1 aesni_intel
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
gf128mul               14951  1 lrw
rtlwifi                63475  2 rtl_pci,rtl8188ee
psmouse               102222  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
glue_helper            13990  1 aesni_intel
mac80211              626489  3 rtl_pci,rtlwifi,rtl8188ee
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
cfg80211              484040  2 mac80211,rtlwifi
ttm                    85115  1 radeon
serio_raw              13462  0 
snd                    69238  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
drm_kms_helper         52758  1 radeon
drm                   302817  5 ttm,drm_kms_helper,radeon
wmi                    19177  1 hp_wmi
hp_accel               26012  0 
rtsx_pci_ms            18151  0 
soundcore              12680  1 snd
edac_core              62291  0 
fam15h_power           13119  0 
k10temp                13126  0 
lis3lv02d              20156  1 hp_accel
edac_mce_amd           22617  0 
input_polldev          13896  1 lis3lv02d
i2c_algo_bit           13413  1 radeon
memstick               16966  1 rtsx_pci_ms
i2c_piix4              22155  0 
video                  19476  0 
parport_pc             32701  0 
ppdev                  17671  0 
mac_hid                13205  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
rtsx_pci_sdmmc         23274  0 
ahci                   25819  3 
r8169                  67581  0 
libahci                32168  1 ahci
rtsx_pci               45956  2 rtsx_pci_ms,rtsx_pci_sdmmc
mii                    13934  1 r8169


[B]
```
[/B]
[B]$ lspci
```
[/B]00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Root Complex00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Kabini [Radeon HD 8330]
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device 9840
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 0
00:02.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
00:02.3 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
00:02.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 01)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 39)
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 39)
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 3a)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 02)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 5
01:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 07)
06:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter (rev 01)


[B]
```
[/B]
Thanks in advance!

---

### Post by varunendra on 2014-04-27
Welcome to the forums Jonathan_Law!

Please change the encryption type in your router/access-point to pure WPA2-PSK with AES (CCMP). Currently it is using WPA/WPA2 mixed mode with TKIP. TKIP can severely affect performance sometimes and should be avoided at all costs.

Apart from that change in the router, if required, please try some driver parameters available for your driver. Please follow the instructions in this post to try them : [http://ubuntuforums.org/showpost.php?p=12815912](http://ubuntuforums.org/showpost.php?p=12815912) (replace "rtl8192ce" with "rtl8188ee" in the commands).

If these changes don't seem to help, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

### Post by Jonathan_Law on 2014-04-27
Hi Varun! Thanks for the help so far, but no luck unforunately.

I changed the encryption type on my router to WPA2 only, although this did not seem to help.
I then tried the modprobe commands in the other thread as suggested; this made the problem worse as I could no longer connect to my Wifi at all.
I restarted my machine to revert the changes, then ran the Wireless Script, which generated a tar.gz file, which is attached below.

[ATTACH]252586[/ATTACH]

---

### Post by SLaCK3r on 2014-04-27
Hi I had the same problem with the same wireless card. I recommend you downgrade your kernel like me and a few others have done. It has solved our WiFi problems.

**Read First:** [http://askubuntu.com/questions/45172...-14-04-realtek](http://askubuntu.com/questions/45172...-14-04-realtek)

**Read Second:** [http://askubuntu.com/questions/11908...distro-upgrade](http://askubuntu.com/questions/11908...distro-upgrade)

Out of the many things that I tried, this was the only solution that worked for me (and it was simple!). I encourage you to give it a shot,

---

### Post by Jonathan_Law on 2014-04-27
Any recommendation of which version to downgrade to?

---

### Post by SLaCK3r on 2014-04-27
Sorry use this link: [http://askubuntu.com/questions/119080/how-to-update-kernel-to-the-latest-mainline-version-without-any-distro-upgrade](http://askubuntu.com/questions/119080/how-to-update-kernel-to-the-latest-mainline-version-without-any-distro-upgrade)

And 3.14.1 I can guarantee that this will make your wireless card work properly. That's the kernel I'm using with my 14.04 install.

---

### Post by Jonathan_Law on 2014-04-27
Thanks for the advice Slacker, but still no luck. Still getting patchy and slow wifi coverage.

---

### Post by SLaCK3r on 2014-04-28
I'm sorry to hear that it didn't work! That's a disappointment! 

Is this a fresh 14.04 installation, or did you try multiple fixes on this current installation?

---

### Post by varunendra on 2014-04-28
> **Jonathan_Law said:**
> I changed the encryption type on my router to WPA2 only, although this did not seem to help.
The wireless_script report you attached still shows WPA/WPA2 mixed mode (or the dreaded "TKIP" with WPA2; you have to change "TKIP" to "AES" too). Did you revert the encryption before running the script? If so, please run it after applying the changes and post back a fresh report showing current status WITH the recommended changes applied.

> **Jonathan_Law said:**
> I then tried the modprobe commands in the other thread as suggested; this made the problem worse as I could no longer connect to my Wifi at all.
Did you run both commands? The first one (modprobe -**r**v...) removes the driver, so it will obviously disconnect you from wireless network. The second one (modprobe ... without the "-**r**") reloads it with the given parameter(s), which is supposed (but not guaranteed) to help connectivity.

---

### Post by Jonathan_Law on 2014-04-28
Hi Slacker,

It's as good as fresh. Any fixes I have tried, I have then reverted. 

---

Hi Varun,

Attached is a screen grab of my router encryption settings.
Originally it was WPA & WPA 2 (Recommended), but I then switched to WPA2. These are the settings I have used, and am still currently using when I ran the script. I am unsure of how else to set the encryption type on my router.
[ATTACH=CONFIG]252600[/ATTACH]

In regards to the modprobe commands, I ran both commands at each step, eventually using that 'blind guess' command, but could not connect to wifi after running them.

---

### Post by varunendra on 2014-04-28
You have chosen the correct encryption type, but the encryption algorithm MUST be AES with WPA2, not TKIP. The "iwlist scan" part of the report you posted clearly shows "TKIP" with WPA2, which is a non-standard combination and shouldn't be allowed at all. But I have seen plenty of crappy routers which somehow deliberately fail to follow the standards.

Anyway, either the router should allow manually setting the encryption algorithm (TKIP or AES), or should automatically do that itself in the background, depending on the chosen encryption 'Type' (WPA, or WPA2). If it can't do it automatically, and doesn't provide a way to manually change it either, such a router should be in a trash can, not in a real network.

Could you find and give us a link to your router's user manual? I am curious to see what options it provides regarding wireless security.

---

### Post by Jonathan_Law on 2014-04-30
Sorry for the late reply. Been incredibly busy lately!

I've had a dig around in the router's setting for a bit and judging from my findings, I think it belongs in the trash can.

I couldn't even find any useful guides for the router. I'm using the BT Home Hub 3, which I hear is a pretty bad router anyway. Here's a link to a set of pretty unhelpful documentation: 
[http://bt.custhelp.com/app/answers/detail/a_id/32813/~/bt-home-hub-3](http://bt.custhelp.com/app/answers/detail/a_id/32813/~/bt-home-hub-3)

If possible, I shall see if a friend has a router which will allow me to try out WPA2 with AES, and see if that alleviates the problem. If so, I guess I'll get a new router.

---

### Post by John_Maurizio on 2015-02-17
I'm sure some of you may know this but I've been going nuts for almost two weeks because my brand new HP Pavilion Laptop 17-f136ds Wi Fi sucked even after I dumped McAfee and disabled all add-ons. 
 
I read everywhere to fix the limited Wi Fi signal strength just reset the TCP/IP stack using the elevated command netsh interface ipv4 reset but I got: Resetting, Failed / Access is Denied / Resetting, OK / Restart the computer to complete this action..... but even after reboot nothing was being reset until I ended up on this page and this registry fix seems to have done the trick. (I hope, or it's back to my Gateway Windows 7 laptop) 
 
[_[COLOR=#0000aa]http://www.kapilarya.com/limited-wifi-problem-in-w&#8203;indows-8[/COLOR]_]("http://www.kapilarya.com/limited-wifi-problem-in-windows-8")

---

