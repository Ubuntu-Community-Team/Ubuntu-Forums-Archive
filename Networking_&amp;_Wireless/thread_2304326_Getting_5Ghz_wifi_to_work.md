---
title: "Getting 5Ghz wifi to work"
date: 2015-11-25
forum: Networking &amp; Wireless
---

### Post by Spency on 2015-11-25
I have a dual-band wifi pci adapter for 2 of my computers. The adapter is advertised as dual-band but when I run 
```
iwlist enp3s0 freq
```
It only lists frequencies within the 2.4-2.5Ghz range - which according to [this]("http://unix.stackexchange.com/questions/137894/how-do-i-find-out-if-my-wireless-card-supports-5ghz") demonstrates my card does not support 5ghz. But this network adapter SHOULD see 5Ghz frequencies. 
This is the [card]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833320161") I have.

The drivers I am using are modified ASUS drivers designed for the card. Details [here]("http://ubuntuforums.org/showthread.php?t=2300692").

---

### Post by Bucky Ball on 2015-11-26
Is your router capable of those speeds? Is it set up to serve those speeds? Also, that is an odd name for the wireless. Generally they are 'wlan0' or 'wlan1' or similar. Have you done anything to change the default or that is what you were given? ... :)

---

### Post by chili555 on 2015-11-26
> **Bucky Ball said:**
> Is your router capable of those speeds? Is it set up to serve those speeds? Also, that is an odd name for the wireless. Generally they are 'wlan0' or 'wlan1' or similar. Have you done anything to change the default or that is what you were given? ... :)Please see: [http://askubuntu.com/questions/689070/network-interface-name-changes-after-update-to-15-10-udev-changes](http://askubuntu.com/questions/689070/network-interface-name-changes-after-update-to-15-10-udev-changes)

---

### Post by chili555 on 2015-11-26
> **Spency said:**
> I have a dual-band wifi pci adapter for 2 of my computers. The adapter is advertised as dual-band but when I run 
```
iwlist enp3s0 freq
```
It only lists frequencies within the 2.4-2.5Ghz range - which according to [this]("http://unix.stackexchange.com/questions/137894/how-do-i-find-out-if-my-wireless-card-supports-5ghz") demonstrates my card does not support 5ghz. But this network adapter SHOULD see 5Ghz frequencies. 
This is the [card]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833320161") I have.

The drivers I am using are modified ASUS drivers designed for the card. Details [here]("http://ubuntuforums.org/showthread.php?t=2300692").May we see: ```
ifconfig
iwconfig
```On my 15.10 machine, enpXX is my ethernet interface and my wireless is wlpXX. Color me confused.

I suspect this is a driver issue, not a hardware issue.

---

### Post by Bucky Ball on 2015-11-26
> **chili555 said:**
> Please see: [http://askubuntu.com/questions/689070/network-interface-name-changes-after-update-to-15-10-udev-changes](http://askubuntu.com/questions/689070/network-interface-name-changes-after-update-to-15-10-udev-changes)

Tnx for that chili555. Hadaka also PMed me re. that info. Explains everything. :)

---

### Post by Spency on 2015-11-26
> **Bucky Ball said:**
> Is your router capable of those speeds? Is it set up to serve those speeds? 

As a matter of fact it is - but that doesn't matter at this point. This is what I see when I run the command off of my iMac:
```
root@Silverback:~# iwlist wlan0 freqwlan0     19 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Current Frequency:2.437 GHz (Channel 6)
``` 

vs. one of my two computers using the asus card.

```
root@blackbox:~$ iwlist enp3s0 freqenp3s0    11 channels in total; available frequencies :
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
          Current Frequency:2.437 GHz (Channel 6)

```

@Chili555

ifconfig:
```
enp3s0    Link encap:Ethernet  HWaddr 10:c3:7b:c8:a5:6b            inet addr:10.0.1.4  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::12c3:7bff:fec8:a56b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1280  Metric:1
          RX packets:12415048 errors:203 dropped:1 overruns:0 frame:0
          TX packets:7693836 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8437692565 (8.4 GB)  TX bytes:5934043459 (5.9 GB)
          Interrupt:17 


enp5s0    Link encap:Ethernet  HWaddr 30:85:a9:3a:bb:73  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:44724 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44724 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4622411 (4.6 MB)  TX bytes:4622411 (4.6 MB)

```

iwconfig
```
enp3s0    Ralink STA  ESSID:"Plato's Cave"  Nickname:"RT2860STA"          Mode:Managed  Frequency=2.437 GHz  Access Point: 5C:96:9D:6A:16:E9   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-60 dBm  Noise level:-75 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


enp5s0    no wireless extensions.


lo        no wireless extensions.

```

---

### Post by chili555 on 2015-11-26
My next thought is that the hacked..er, uh, patched rt5592sta doesn't provide 5gHz capability. 

Did you have to copy over the RT2860STA.dat file? It might be in /etc/Wireless/RT2860(or some such)/RT2860STA.dat. There are a couple of settings that look suspicious:> CountryRegion=5
CountryRegionABand=7
CountryCode=
ChannelGeography=1Is this the only workable driver that you could find and compile?

---

### Post by Spency on 2015-11-26
[COLOR=#000000]RT2860STA.dat file in /etc/wireless is identical to the one in the makefile directory. [/COLOR]

[COLOR=#000000]It is odd looking... 
```
[/COLOR]SSID=Dennis2860AP
```

---

### Post by chili555 on 2015-11-26
That's it?? We could try to tweak it but I wonder if it is actually used, given that it contains nothing useful.

Was rt5592sta the only workable, compilable driver you could find? I hope we are not stuck.

---

### Post by Spency on 2015-11-26
No that's just one line.
```
#The word of "Default" must not be removed
Default
CountryRegion=5
CountryRegionABand=7
CountryCode=
ChannelGeography=1
SSID=Dennis2860AP
NetworkType=Infra
WirelessMode=5
Channel=0
BeaconPeriod=100
TxPower=100
BGProtection=0
TxPreamble=0
RTSThreshold=2347
FragThreshold=2346
TxBurst=1
PktAggregate=0
WmmCapable=1
AckPolicy=0;0;0;0
AuthMode=OPEN
EncrypType=NONE
WPAPSK=
DefaultKeyID=1
Key1Type=0
Key1Str=
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
PSMode=CAM
AutoRoaming=0
RoamThreshold=70
APSDCapable=0
APSDAC=0;0;0;0
HT_RDG=1
HT_EXTCHA=0
HT_OpMode=0
HT_MpduDensity=4
HT_BW=1
HT_AutoBA=1
HT_BADecline=0
HT_AMSDU=0
HT_BAWinSize=64
HT_GI=1
HT_MCS=33
HT_MIMOPSMode=3
HT_DisallowTKIP=1
HT_STBC=0
EthConvertMode=
EthCloneMac=
IEEE80211H=0
TGnWifiTest=0
WirelessEvent=0
MeshId=MESH
MeshAutoLink=1
MeshAuthMode=OPEN
MeshEncrypType=NONE
MeshWPAKEY=
MeshDefaultkey=1
MeshWEPKEY=
CarrierDetect=0
AntDiversity=0
BeaconLostTime=4
FtSupport=0
Wapiifname=ra0
WapiPsk=
WapiPskType=
WapiUserCertPath=
WapiAsCertPath=
PSP_XLINK_MODE=0
WscManufacturer=
WscModelName=
WscDeviceName=
WscModelNumber=
WscSerialNumber=
RadioOn=1
WIDIEnable=1
P2P_L2SD_SCAN_TOGGLE=3
Wsc4digitPinCode=0
P2P_WIDIEnable=0
PMFMFPC=0
PMFMFPR=0
PMFSHA256=0

```


That is the only work around for my card I discovered, and I had to dig for a little while to find it. 

Would changing the wireless mode have any effect?
```

WirelessMode=5
{0: legacy 11b/g mixed}
{1: legacy 11b only}
{2: legacy 11a only}
{3: legacy 11a/b/g mixed}
{4: legacy 11g only}
{5: 11a/b/g/n mixed}
{6: 11n only}
{7: 11g/n mixed}
{8: 11a/n mixed}
{9: 11b/g/n mixed}
{10: 11a/g/n mixed}

```

[http://www.techknow.one/forum/index.php?topic=428.0"]Source]("http://[/COLOR)

---

### Post by chili555 on 2015-11-26
> Would changing the wireless mode have any effect?Perhaps. We don't know if the file is actually referred to by the driver or not. Back in the day, it was.

It seems to me that the wireless mode is already at the ideal setting.

Your [COLOR="#FF0000"]Source[/COLOR] doesn't open anything for me.

I suggest you tinker with any and all of the likely settings to see if they help.

Also, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

I am almost of the thinking that the best we can do is 2.4 gHz and we ought to be grateful we found *any* driver!

---

### Post by Spency on 2015-11-27
```
 
:~$ sudo iw reg get
country US: DFS-FCC
	(2402 - 2472 @ 40), (N/A, 30), (N/A)
	(5170 - 5250 @ 80), (N/A, 17), (N/A)
	(5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS
	(5735 - 5835 @ 80), (N/A, 30), (N/A)
	(57240 - 63720 @ 2160), (N/A, 40), (N/A)

```

```

:~$ sudo gedit /etc/default/crda
```
```

# Set REGDOMAIN to a ISO/IEC 3166-1 alpha2 country code so that iw(8) may set
# the initial regulatory domain setting for IEEE 802.11 devices which operate
# on this system.
#
# Governments assert the right to regulate usage of radio spectrum within
# their respective territories so make sure you select a ISO/IEC 3166-1 alpha2
# country code suitable for your location or you may infringe on local
# legislature. See `/usr/share/zoneinfo/zone.tab' for a table of timezone
# descriptions containing ISO/IEC 3166-1 alpha2 country codes.


REGDOMAIN=US

```

Now let's reboot....

```

:~$ iwlist enp3s0 freq; 
enp3s0    11 channels in total; available frequencies :
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
          Current Frequency:2.437 GHz (Channel 6)

```

No dice.

Don't get me wrong, after a few hours of searching and then stumbling on an archlinux forum post with a very specific driver patch, I was like Phweew! 

If I can enable 5gz on these cards that would be great, but yeah, I mean they do work nonetheless.

---

### Post by chili555 on 2015-11-29
Sorry, I haven't any other suggestions.

---

