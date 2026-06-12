---
title: "TL-WDN3200 - cannot connect to security wifi network :("
date: 2014-09-22
forum: Networking &amp; Wireless
---

### Post by quocdatbk on 2014-09-22
i have a usb wifi modem TL-WDN3200 and compile drive according to [http://www.blackmoreops.com/2014/01/02/tp-link-tl-wdn3200-n600-wireless-dual-band-usb-adapter-in-linux/](http://www.blackmoreops.com/2014/01/02/tp-link-tl-wdn3200-n600-wireless-dual-band-usb-adapter-in-linux/)
driver compile and insmod ok, but it only connected succesfull to open network. with securitt network , it authencate succesfull but cannot get ip from modem wifi :

```
root@ptt:~# ./wpa_supplicant -Dwext -ira0 -c ./wpa_supplicant.conf
Trying to associate with 4c:e6:76:c2:32:0e (SSID='OpenWrt' freq=2462 MHz)
Associated with 4c:e6:76:c2:32:0e
WPA: Key negotiation completed with 4c:e6:76:c2:32:0e [PTK=CCMP GTK=CCMP]
CTRL-EVENT-CONNECTED - Connection to 4c:e6:76:c2:32:0e completed (auth) [id=0 id_str=]
```

```
root@ptt:~# iwconfig ra0
ra0       Ralink STA  ESSID:"OpenWrt"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 4C:E6:76:C2:32:0E
          Bit Rate=78 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:E390-A18B-E6B8-7899-A2D2-5B97-3173-DD94 [2]   Security mode:open
          Link Quality=65/100  Signal level:-72 dBm  Noise level:-77 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

```
root@ptt:~# udhcpc -i ra0 -qn
udhcpc (v1.18.5) started
Sending discover...
Sending discover...
Sending discover...
/usr/share/udhcpc/default.script: Lease failed:
No lease, failing
```

```
root@ptt:~# dmesg -c
[20584.852032] usb 1-7: new high-speed USB device number 5 using ehci-pci
[20585.000024] usb 1-7: New USB device found, idVendor=148f, idProduct=5572
[20585.000033] usb 1-7: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[20585.000039] usb 1-7: Product: 802.11 n WLAN
[20585.000046] usb 1-7: Manufacturer: Ralink
[20585.000050] usb 1-7: SerialNumber: 1.0
[20585.001916]
[20585.001916]
[20585.001916] === pAd = f9345000, size = 565808 ===
[20585.001916]
[20585.001999] <-- RTMPAllocAdapterBlock, Status=0
[20585.002270] NVM is EFUSE
[20592.055506] NICLoadFirmware: We need to load firmware
[20592.153526] <-- RTMPAllocTxRxRingMemory, Status=0
[20592.153697] RTMP_TimerListAdd: add timer obj f938d560!
[20592.153702] RTMP_TimerListAdd: add timer obj f938d5a8!
[20592.153705] RTMP_TimerListAdd: add timer obj f938d5f0!
[20592.153709] RTMP_TimerListAdd: add timer obj f938d518!
[20592.153713] RTMP_TimerListAdd: add timer obj f938d440!
[20592.153716] RTMP_TimerListAdd: add timer obj f938d488!
[20592.153720] RTMP_TimerListAdd: add timer obj f9357c18!
[20592.153723] RTMP_TimerListAdd: add timer obj f93471a8!
[20592.153726] RTMP_TimerListAdd: add timer obj f93471f4!
[20592.153729] RTMP_TimerListAdd: add timer obj f9357d04!
[20592.153733] RTMP_TimerListAdd: add timer obj f9357b88!
[20592.153737] RTMP_TimerListAdd: add timer obj f9357cb8!
[20592.154575] -->RTUSBVenderReset
[20592.154621] <--RTUSBVenderReset
[20592.264748] BBP_R254 = 80
[20592.351901] Key1Str is Invalid key length(0) or Type(0)
[20592.351942] Key2Str is Invalid key length(0) or Type(0)
[20592.351981] Key3Str is Invalid key length(0) or Type(0)
[20592.352039] Key4Str is Invalid key length(0) or Type(0)
[20592.352759] 1. Phy Mode = 5
[20592.352762] 2. Phy Mode = 5
[20592.352766] NVM is Efuse and its size =3c[3c0-3fb]
[20592.366686] Power = f0f
[20592.366693] Power2 = f0f
[20592.367252] Power = f0f
[20592.367255] Power2 = f0f
[20592.367934] Power = f0f
[20592.367937] Power2 = f0f
[20592.368522] Power = f0f
[20592.368526] Power2 = f0f
[20592.369172] Power = 100f
[20592.369175] Power2 = f0f
[20592.369750] Power = 1010
[20592.369753] Power2 = f0f
[20592.397435] 3. Phy Mode = 5
[20592.398634] \x1b[mAntCfgInit: primary/secondary ant 0/1
[20592.398634] \x1b[mbAutoTxAgcG = 0
[20592.411770] ---> InitFrequencyCalibration
[20592.412755] InitFrequencyCalibration: frequency offset in the EEPROM = 37
[20592.412762] <--- InitFrequencyCalibration
[20592.412783] RTMPSetPhyMode: channel is out of range, use first channel=1
[20592.414432] MCS Set = ff ff 00 00 01
[20592.424668] <==== rt28xx_init, Status=0
[20592.425389] 0x1300 = 00064300
[20595.939359] ===>rt_ioctl_giwscan. 19(19) BSS returned, data->length = 2997
[20595.939576] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=11)
[20596.094968] RTMP_TimerListAdd: add timer obj f93c71d4!
```

please, help me!!

---

### Post by dave131 on 2014-09-22
Did you ever just modprobe rt2800usb?   Please follow the link below for downloading a script and running it, then post the output here in code tags:

[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by slickymaster on 2014-09-22
Hi quocdatbk, welcome to the forums.

I've edited your post, adding code tags to it.
Outputed code posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand. The [use of code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") makes the post clean, compact and more appealing, thus getting more attention from readers.

---

### Post by quocdatbk on 2014-09-22
i trying modprobe rt2800usb and ```
Module                  Size  Used by
rt2800usb              22525  0
rt2800lib              61785  1 rt2800usb
crc_ccitt              12627  1 rt2800lib
rt2x00usb              20099  1 rt2800usb
rt2x00lib              49131  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              546103  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              454468  2 rt2x00lib,mac80211
rt5572sta             747942  1
bnep                   17919  2
rfcomm                 38400  0


```
but my pc cannot get ip from route wifi modem 
```
udhcpc -i ra0
udhcpc (v1.18.5) started
Sending discover...
Sending discover...
Sending discover...
/usr/share/udhcpc/default.script: Lease failed:
Sending discover...
Sending discover...
Sending discover...
/usr/share/udhcpc/default.script: Lease failed:


```
i want to portting usb wifi to my device therefor i don't want use network-manager to connect network. my PC use mips-linux
log of wireless_script [ATTACH]256617[/ATTACH]

---

### Post by quocdatbk on 2014-09-22
thanks [ 						 							[IMG]http://ubuntuforums.org/customavatars/avatar1753126_5.gif[/IMG] 						 					]("http://ubuntuforums.org/member.php?u=1753126") 				 				 					 						 	[**[COLOR=#C61919][B]slickymaster**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1753126") very much :)

---

### Post by dave131 on 2014-09-23
You're going to need someone with more knowledge than I have - I was hoping running the wireless script would draw some in.  I did notice it does show your wireless connected:

ra0       Ralink STA  ESSID:"OpenWrt"

Then I see all of those "Cell" things, each with their own ESSID's, and I don't have a clue what those are.  Perhaps it would help if you explained what exactly was the physcial setup when you created that report - things like PC and type, trying to connect to "X" which is a "y" device, to connect to the internet.  It probably makes sense for someone else but I just don't see anything like that from any of our PC's connecting wirelessly.

---

