---
title: "help with wifi on acer switch notebook/tablet"
date: 2015-05-02
forum: Networking &amp; Wireless
---

### Post by miatawnt2b on 2015-05-02
Hoping you folks can help. I just installed 15.04 on my acer switch. Problem is wifi does not work and I can't seem to get any method for broadcom working (I'm assuming it's a broadcom but I'm actually unsure.

It looks like my wifi card is the broadcom since my device ID says 0x4324 in the mmc1:0001:1/data file however, the vendor id in the same directory is 0x02d0 which as far as I can tell is not standard broadcom. probably why none of the standard drivers does not work. lspci does not show any broadcom device at all.

Anyone have ideas on getting this working?

---

### Post by wildmanne39 on 2015-05-02
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

### Post by miatawnt2b on 2015-05-03
Thanks so much Wild Man, I posted the output to pastebin.

[http://paste.ubuntu.com/10977951/](http://paste.ubuntu.com/10977951/)

-J

---

### Post by miatawnt2b on 2015-05-03
Here is another output after I cleaned some things up that I was messing with.

[http://paste.ubuntu.com/10980502/](http://paste.ubuntu.com/10980502/)

-J

---

### Post by wildmanne39 on 2015-05-03
In this thread they got wifi to work.
[http://ubuntuforums.org/showthread.php?t=2249936](http://ubuntuforums.org/showthread.php?t=2249936)

---

### Post by chili555 on 2015-05-03
So far, we see no wireless device at all! Let's dig deeper. Please run and post:```
lspci -nn
sudo lshw -C network
```

---

### Post by miatawnt2b on 2015-05-03
Yea, I'm not convinced it's a realtek chipset. I had installed the rtl8723bs driver and it didn't work. I never uninstalled it but I realized from Acer's support page they offer two drivers for windows. A broadcom and a realtek. I'm thinking it's a broadcom since the device ID in the mmc1:0001:1/data file says 0x4324 which is a broadcom ID. So I uninstalled the broadcom stuff and the realtek stuff and rebooted then ran the script again. That's the second pastebin link. I'll run the other commands for chilli555 in a min.
-J

---

### Post by miatawnt2b on 2015-05-03
```

root@switch:~# lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Atom Processor Z36xxx/Z37xxx Series SoC Transaction Register [8086:0f00] (rev 0f)
00:02.0 VGA compatible controller [0300]: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Graphics & Display [8086:0f31] (rev 0f)
00:14.0 USB controller [0c03]: Intel Corporation Atom Processor Z36xxx/Z37xxx Series USB xHCI [8086:0f35] (rev 0f)
00:1a.0 Encryption controller [1080]: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Trusted Execution Engine [8086:0f18] (rev 0f)
00:1f.0 ISA bridge [0601]: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Power Control Unit [8086:0f1c] (rev 0f)
root@switch:~# sudo lshw -C network
  *-network               
       description: Ethernet interface
       physical id: 1
       logical name: eth0
       serial: 00:80:c8:38:7d:71
       size: 100Mbit/s
       capacity: 100Mbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=asix driverversion=22-Dec-2011 duplex=full firmware=ASIX AX88772 USB 2.0 Ethernet ip=192.168.1.141 link=yes multicast=yes port=MII speed=100Mbit/s
root@switch:~# 

```

It does seem strange ubuntu sees nothing. It definitely works in windows, though I don't have the windows install on it anymore to see exactly what driver it's using (well I do, but I'd have to restore the whole maching from USB stick wiping my ubuntu load.)

---

### Post by chili555 on 2015-05-03
Grasping at straws a bit here, but may I see:```
ls /sys/bus/sdio/devices/
```I am running out of ideas.

---

### Post by miatawnt2b on 2015-05-03
```

root@switch:~# ls /sys/bus/sdio/devices/
mmc1:0001:1  mmc1:0001:2

```

---

### Post by miatawnt2b on 2015-05-04
I think I'm getting closer.

```

########## wireless info START ##########

Report from: 04 May 2015 07:18 MST -0700

Booted last: 04 May 2015 00:16 MST -0700

Script from: 30 Apr 2015 17:23 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 15.04
Release:	15.04
Codename:	vivid

##### kernel ############################

Linux 3.19.0-15-generic #15-Ubuntu SMP Thu Apr 16 23:32:37 UTC 2015 x86_64 x86_6
4 x86_64 GNU/Linux

Parameters: 

##### desktop ###########################

Ubuntu (from ~/.dmrc)

##### lspci #############################

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 06cb:2968 Synaptics, Inc. 
Bus 001 Device 003: ID 3538:0901 Power Quotient International Co., Ltd 
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: acer-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

brcmfmac              278528  0 
brcmutil               16384  1 brcmfmac
cfg80211              540672  1 brcmfmac
snd_soc_sst_byt_rt5640_mach    16384  0 
acer_wmi               20480  0 
sparse_keymap          16384  1 acer_wmi
snd_soc_rt5640         94208  1 snd_soc_sst_byt_rt5640_mach
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          196608  4 snd_soc_rt5640,snd_soc_sst_baytrail_pcm,snd_soc_
sst_byt_rt5640_mach,snd_soc_sst_mfld_platform
snd_pcm               106496  5 snd_soc_rt5640,snd_soc_core,snd_soc_sst_baytrail
_pcm,snd_soc_sst_mfld_platform,snd_pcm_dmaengine
wmi                    20480  1 acer_wmi
video                  20480  2 i915,acer_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

##### iwconfig ##########################

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### NetworkManager info ###############

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

##### iw reg get ########################

Region: America/Phoenix (based on set time zone)

country 00: DFS-UNSET
	(2402 - 2472 @ 40), (3, 20), (N/A)
	(2457 - 2482 @ 40), (3, 20), (N/A), NO-IR
	(2474 - 2494 @ 20), (3, 20), (N/A), NO-OFDM, NO-IR
	(5170 - 5250 @ 40), (3, 20), (N/A), NO-IR
	(5735 - 5835 @ 40), (3, 20), (N/A), NO-IR

##### iwlist channels ###################

lo        no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

##### module infos ######################

[brcmfmac]
filename:       /lib/modules/3.19.0-15-generic/kernel/drivers/net/wireless/brcm8
0211/brcmfmac/brcmfmac.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11 wireless LAN fullmac driver.
author:         Broadcom Corporation
firmware:       brcm/brcmfmac4354-sdio.txt
firmware:       brcm/brcmfmac4354-sdio.bin
firmware:       brcm/brcmfmac4339-sdio.txt
firmware:       brcm/brcmfmac4339-sdio.bin
firmware:       brcm/brcmfmac43362-sdio.txt
firmware:       brcm/brcmfmac43362-sdio.bin
firmware:       brcm/brcmfmac4335-sdio.txt
firmware:       brcm/brcmfmac4335-sdio.bin
firmware:       brcm/brcmfmac4334-sdio.txt
firmware:       brcm/brcmfmac4334-sdio.bin
firmware:       brcm/brcmfmac4330-sdio.txt
firmware:       brcm/brcmfmac4330-sdio.bin
firmware:       brcm/brcmfmac4329-sdio.txt
firmware:       brcm/brcmfmac4329-sdio.bin
firmware:       brcm/brcmfmac43241b4-sdio.txt
firmware:       brcm/brcmfmac43241b4-sdio.bin
firmware:       brcm/brcmfmac43241b0-sdio.txt
firmware:       brcm/brcmfmac43241b0-sdio.bin
firmware:       brcm/brcmfmac43143-sdio.txt
firmware:       brcm/brcmfmac43143-sdio.bin
firmware:       brcm/brcmfmac43569.bin
firmware:       brcm/brcmfmac43242a.bin
firmware:       brcm/brcmfmac43236b.bin
firmware:       brcm/brcmfmac43143.bin
firmware:       brcm/brcmfmac43570-pcie.txt
firmware:       brcm/brcmfmac43570-pcie.bin
firmware:       brcm/brcmfmac4354-pcie.txt
firmware:       brcm/brcmfmac4354-pcie.bin
firmware:       brcm/brcmfmac43602-pcie.txt
firmware:       brcm/brcmfmac43602-pcie.bin
srcversion:     EF8DB74BE0DC2CF3B4D9D7E
depends:        brcmutil,cfg80211
intree:         Y
vermagic:       3.19.0-15-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        9E:64:80:70:92:F3:A6:A8:F6:6F:3B:7E:A4:CB:37:67:FD:FA:E0:8A
sig_hashalgo:   sha512
parm:           txglomsz:maximum tx packet chain size [SDIO] (int)
parm:           firmware_path:string
parm:           debug:level of debug output (int)
parm:           fcmode:mode of firmware signalled flow control (int)
parm:           roamoff:do not use internal roaming engine (int)

[brcmutil]
filename:       /lib/modules/3.19.0-15-generic/kernel/drivers/net/wireless/brcm8
0211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     A2434DDD5B2051715F2E908
depends:        
intree:         Y
vermagic:       3.19.0-15-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        9E:64:80:70:92:F3:A6:A8:F6:6F:3B:7E:A4:CB:37:67:FD:FA:E0:8A
sig_hashalgo:   sha512

[cfg80211]
filename:       /lib/modules/3.19.0-15-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     268045EBCFAFDADD136DCF6
depends:        
intree:         Y
vermagic:       3.19.0-15-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        9E:64:80:70:92:F3:A6:A8:F6:6F:3B:7E:A4:CB:37:67:FD:FA:E0:8A
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz
 band (bool)

##### module parameters #################

[brcmfmac]
debug: 0
fcmode: 0
roamoff: 0

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

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# USB device 0x:0x (asix)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", 
ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[    6.879716] byt-rt5640 byt-rt5640: ASoC: CPU DAI baytrail-pcm-audio not regis
tered
[    6.882208] platform byt-rt5640: Driver byt-rt5640 requests probe deferral
[    6.882264] byt-rt5640 byt-rt5640: ASoC: CPU DAI baytrail-pcm-audio not regis
tered
[    6.885830] platform byt-rt5640: Driver byt-rt5640 requests probe deferral
[    6.911017] byt-rt5640 byt-rt5640: ASoC: CPU DAI baytrail-pcm-audio not regis
tered
[    6.913357] platform byt-rt5640: Driver byt-rt5640 requests probe deferral
[    7.120935] byt-rt5640 byt-rt5640: ASoC: CPU DAI baytrail-pcm-audio not regis
tered
[    7.123226] platform byt-rt5640: Driver byt-rt5640 requests probe deferral
[   23.045911] byt-rt5640 byt-rt5640: ASoC: CPU DAI baytrail-pcm-audio not regis
tered
[   23.048877] platform byt-rt5640: Driver byt-rt5640 requests probe deferral
[   23.210962] byt-rt5640 byt-rt5640: ASoC: CPU DAI baytrail-pcm-audio not regis
tered
[   23.210983] platform byt-rt5640: Driver byt-rt5640 requests probe deferral
[   23.217632] brcmf_sdio_drivestrengthinit: No SDIO Drive strength init done fo
r chip 4324 rev 5 pmurev 17
[   23.218088] byt-rt5640 byt-rt5640: ASoC: CPU DAI baytrail-pcm-audio not regis
tered
[   23.218107] platform byt-rt5640: Driver byt-rt5640 requests probe deferral
[   23.233782] brcmfmac_sdio mmc1:0001:1: firmware, attempted to load /lib/firmw
are/brcm/brcmfmac43241b4-sdio.txt, but failed with error -22
[   23.233786] brcmfmac_sdio mmc1:0001:1: Direct firmware load for brcm/brcmfmac
43241b4-sdio.txt failed with error -22
[   24.249845] brcmf_sdio_htclk: HT Avail timeout (1000000): clkctl 0x50 (repeat
ed 2 times)

########## wireless info END ############

```

---

### Post by chili555 on 2015-05-04
> I think I'm getting closer.Indeed you are! We see a fixable problem! We shall apply a fix and it may work or it may then bring up a further error; we'll see.> brcmfmac_sdio mmc1:0001:1: firmware, attempted to load /lib/firmware/brcm/brcmfmac43241b4-sdio.txt, but failed with error -22I found this: [https://github.com/jfwells/linux-asus-t100ta/blob/master/nvram/lib/firmware/brcm/brcmfmac43241b4-sdio.txt](https://github.com/jfwells/linux-asus-t100ta/blob/master/nvram/lib/firmware/brcm/brcmfmac43241b4-sdio.txt)

Notice it is a text file. Examining it we see, in part:> #Sample variables file for BCM94324A1 iPA+iLNA FCBGA REF board
# NV VER: 0.2.3.0.XV1
# 20130829 Change Note:
# Enable Out of band GPIO for connected standby
# 20130809 Change Note:
# REMOVE 2x2 BTC effect BIT
# Change CCODE to XV/1
# 20130816 Change Note:
# Change PA parameters for TSSI 
# 20130830 Change Note:
# Change Power-per-rate settings
# 20130903 Change Note:
# Change Power-per-rate settings
<snip>There follows a list of variables that are evidently user-variable. What any of these do or mean is unknown to me. I suggest you load the file into /lib/firmware/brcm and see if the wireless works or if dmesg tells us more we can go on.

If you have internet access by ethernet or otherwise, then do:```
cd /lib/firmware/brcm
sudo wget https://github.com/jfwells/linux-asus-t100ta/blob/master/nvram/lib/firmware/brcm/brcmfmac43241b4-sdio.txt
sudo modprobe -r brcmfmac  &&  sudo modprobe brcmfmac
```If you haven't any internet access, download the file on any other computer, transfer it on a USB key or similar to the desktop and then:```
sudo cp ~/Desktop/brcmfmac43241b4-sdio.txt  /lib/firmware/brcm
sudo modprobe -r brcmfmac  &&  sudo modprobe brcmfmac
```If the wireless doesn't spring to life, look for and post any clues:```
dmesg | grep brcm
```

---

### Post by miatawnt2b on 2015-05-04
Getting closer. Thanks for your help so far. Problem is now that I can't see any ssid's.

[http://paste.ubuntu.com/10988058/](http://paste.ubuntu.com/10988058/)

-J

---

### Post by chili555 on 2015-05-05
I notice this:> wlan0     11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          <snip>
          Channel 11 : 2.462 GHzMay I assume that at least one of the SSIDs you are seeking is on one of those channels? Is there any change if you set the regulatory domain? Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. If it helps, we'll set it permanently.

Now test:```
sudo iwlist wlan0 scan
```

Are there any clues here?```
cat /var/log/syslog | grep -e wlan -e brcm | tail -n20
```[http://paste.ubuntu.com](http://paste.ubuntu.com) if you please.

---

### Post by miatawnt2b on 2015-05-05
thank you chili555! I think that might have been the issue. It was set for 00. I changed it to US country code and I am able to see SSID's at the library where I am working. I'm betting when I get home it will work as expected. Just need to set it permanently. I'll do some searching to see if I can figure it out.

-J

---

### Post by miatawnt2b on 2015-05-05
hummm... so I can see the library ssid's but I can't connect. I also turned on my hotspot and I cannot see it's ssid at all. I am seeing brcmf_escan_timeout: timer expired messages in the syslog.

---

### Post by miatawnt2b on 2015-05-05
I killed networkmanager and nmapplet and installed wicd. I can now see and connect to all SSID's.  Any thoughts?

---

### Post by chili555 on 2015-05-05
> **miatawnt2b said:**
> I killed networkmanager and nmapplet and installed wicd. I can now see and connect to all SSID's.  Any thoughts?Any thoughts? LOL! I'd remove NM entirely, set your reg domain permanently and call it solved!

```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Of course, substitute your country code if not Iceland. Proofread carefully, save and close the text editor.

---

### Post by miatawnt2b on 2015-05-05
That's exactly what I did... install wicd and uninstall nm. 

So now onto performance. I get probably 10-15% packet loss with this thing.  I've disabled power management temporarily with 'iwconfig wlan0 power off'
That helped a little. Now I'm at 6% packet loss.  I seem to remember with my old mac that had a broadcom chip I had to disable wireless n and I got much better performance. How can I do that with the brcmfmac driver? and make it and the power off permanent?

---

### Post by chili555 on 2015-05-06
I think a mistake has been made with the .txt file we downloaded. Please do:```
cat /lib/firmware/brcm/brcmfmac43241b4-sdio.txt  | head -n5
```Do you see this?> 


<!DOCTYPE html>
<html lang="en" class="">If so, a mistake has been made; I apologize. Please do:```
sudo rm /lib/firmware/brcm/brcmfmac43241b4-sdio.txt 
cd /lib/firmware/brcm
wget https://github.com/jfwells/linux-asus-t100ta/raw/master/nvram/lib/firmware/brcm/brcmfmac43241b4-sdio.txt
```Now we edit the raw file:```
sudo gedit /lib/firmware/brcm/brcmfmac43241b4-sdio.txt 
```Use nano or kate or leafpad if you don't have the text editor gedit. Remove the first several characters such that the very first line now reads:```
#Sample variables file for BCM94324A1 iPA+iLNA FCBGA REF board
```Proofread carefully, save and close the text editor. Reload the module so it now sees the proper file:```
sudo modprobe -r brcmfmac  &&  sudo modprobe brcmfmac
```Any change in the performance?

---

### Post by miatawnt2b on 2015-05-06
I ran through your steps and this is what I get:
```

root@switch:/lib/firmware/brcm# cat /lib/firmware/brcm/brcmfmac43241b4-sdio.txt  | head -n5
#Sample variables file for BCM94324A1 iPA+iLNA FCBGA REF board
# NV VER: 0.2.3.0.XV1
# 20130829 Change Note:
# Enable Out of band GPIO for connected standby
# 20130809 Change Note:

```

same 10% packet loss as before.

---

### Post by chili555 on 2015-05-06
> I ran through your steps and this is what I get:
Code:

root@switch:/lib/firmware/brcm# cat /lib/firmware/brcm/brcmfmac43241b4-sdio.txt  | head -n5
#Sample variables file for BCM94324A1 iPA+iLNA FCBGA REF board
# NV VER: 0.2.3.0.XV1
# 20130829 Change Note:
# Enable Out of band GPIO for connected standby
# 20130809 Change Note:

Excellent.

The first step is to examine syslog to see if we see why there is packet loss:```
cat /var/log/syslog | grep -e brcm -e wlan | tail -n20
```Next, we'll see if there is a relevant parameter to manipulate in either the .txt file or the driver itself:```
parm:           txglomsz:maximum tx packet chain size [SDIO] (int)
parm:           firmware_path:string
parm:           debug:level of debug output (int)
parm:           fcmode:mode of firmware signalled flow control (int)
parm:           roamoff:do not use internal roaming engine (int)

```By the way, this is the first successful use of brcmfmac I have seen and also the first successful SDIO device. What we're doing here is educated guesswork and, probably, trial and error.

---

### Post by miatawnt2b on 2015-05-06
I really appreciate the help!

```

root@switch:/# cat /var/log/syslog | grep -e brcm -e wlan | tail -n20
May  6 13:24:45 switch avahi-daemon[687]: Interface wlan0.IPv6 no longer relevant for mDNS.
May  6 13:24:45 switch avahi-daemon[687]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::aed1:b8ff:fe33:375.
May  6 13:24:45 switch avahi-daemon[687]: Withdrawing address record for fe80::aed1:b8ff:fe33:375 on wlan0.
May  6 13:24:45 switch dhclient: Listening on LPF/wlan0/ac:d1:b8:33:03:75
May  6 13:24:45 switch dhclient: Sending on   LPF/wlan0/ac:d1:b8:33:03:75
May  6 13:24:45 switch dhclient: DHCPRELEASE on wlan0 to 192.168.43.1 port 67 (xid=0x1abd8ca6)
May  6 13:24:47 switch avahi-daemon[687]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::aed1:b8ff:fe33:375.
May  6 13:24:47 switch avahi-daemon[687]: New relevant interface wlan0.IPv6 for mDNS.
May  6 13:24:47 switch avahi-daemon[687]: Registering new address record for fe80::aed1:b8ff:fe33:375 on wlan0.*.
May  6 13:24:48 switch kernel: [ 3403.989750] Modules linked in: brcmfmac brcmutil cfg80211 nls_iso8859_1 intel_rapl snd_soc_sst_baytrail_pcm intel_soc_dts_thermal intel_powerclamp snd_soc_sst_dsp joydev gpio_keys coretemp snd_soc_sst_byt_rt5640_mach kvm_intel kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd snd_soc_rt5640 snd_soc_rl6231 snd_intel_sst_acpi snd_intel_sst_core snd_soc_sst_mfld_platform hid_acer(OE) hid_multitouch snd_seq_midi snd_soc_core snd_seq_midi_event snd_compress snd_pcm_dmaengine snd_rawmidi snd_seq snd_pcm snd_seq_device snd_timer mei_txe mei iosf_mbi dw_dmac ak8975 snd lpc_ich dw_dmac_core i2c_hid soundcore industrialio mac_hid 8250_fintek soc_button_array spi_pxa2xx_platform int3400_thermal 8250_dw snd_soc_sst_acpi acpi_pad processor_thermal_device acpi_thermal_rel int3403_thermal int3402_thermal i2c_designware_platform i2c_designware_core parport_pc ppdev lp parport autofs4 hid_generic usbhid hid mmc_block i915 i2c_algo_bit drm_kms_helper drm wmi video sdhci_acpi sdhci [last unloaded: brcmutil]
May  6 13:24:48 switch kernel: [ 3404.011177] Modules linked in: brcmfmac brcmutil cfg80211 nls_iso8859_1 intel_rapl snd_soc_sst_baytrail_pcm intel_soc_dts_thermal intel_powerclamp snd_soc_sst_dsp joydev gpio_keys coretemp snd_soc_sst_byt_rt5640_mach kvm_intel kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd snd_soc_rt5640 snd_soc_rl6231 snd_intel_sst_acpi snd_intel_sst_core snd_soc_sst_mfld_platform hid_acer(OE) hid_multitouch snd_seq_midi snd_soc_core snd_seq_midi_event snd_compress snd_pcm_dmaengine snd_rawmidi snd_seq snd_pcm snd_seq_device snd_timer mei_txe mei iosf_mbi dw_dmac ak8975 snd lpc_ich dw_dmac_core i2c_hid soundcore industrialio mac_hid 8250_fintek soc_button_array spi_pxa2xx_platform int3400_thermal 8250_dw snd_soc_sst_acpi acpi_pad processor_thermal_device acpi_thermal_rel int3403_thermal int3402_thermal i2c_designware_platform i2c_designware_core parport_pc ppdev lp parport autofs4 hid_generic usbhid hid mmc_block i915 i2c_algo_bit drm_kms_helper drm wmi video sdhci_acpi sdhci [last unloaded: brcmutil]
May  6 13:24:48 switch kernel: [ 3404.032621] brcmf_cfg80211_escan: Connecting: status (3)
May  6 13:24:48 switch kernel: [ 3404.032639] brcmf_cfg80211_scan: scan error (-11)
May  6 13:24:49 switch dhclient: Listening on LPF/wlan0/ac:d1:b8:33:03:75
May  6 13:24:49 switch dhclient: Sending on   LPF/wlan0/ac:d1:b8:33:03:75
May  6 13:24:49 switch dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 (xid=0x7a716458)
May  6 13:24:49 switch dhclient: DHCPREQUEST of 192.168.43.209 on wlan0 to 255.255.255.255 port 67 (xid=0x7a716458)
May  6 13:24:49 switch avahi-daemon[687]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.43.209.
May  6 13:24:49 switch avahi-daemon[687]: New relevant interface wlan0.IPv4 for mDNS.
May  6 13:24:49 switch avahi-daemon[687]: Registering new address record for 192.168.43.209 on wlan0.IPv4.
root@switch:/# 

```

not sure what what your second code field is... (the param: stuff)
Thanks!

---

### Post by chili555 on 2015-05-06
> brcmf_cfg80211_scan: scan error (-11)That's about the only thing I see that's suspicious. I Googled it and found: [https://bugzilla.kernel.org/show_bug.cgi?id=88061](https://bugzilla.kernel.org/show_bug.cgi?id=88061)> Actually this was enough:

---
bus/platform/drivers/sdhci-acpi/INT33BB:00/power/control = on
---What does your file say?```
cat /bus/platform/drivers/sdhci-acpi/INT33BB:00/power/control
```You might have to look around:```
ls /bus/platform/drivers/
```And keep drilling down until you find power/control. My hope is that if control is set to off and we change it to on, we fix or at least help your issue.> not sure what what your second code field is... (the param: stuff)Those are the parameters that are manipulable in the driver brcmfmac. You can see them with:```
modinfo brcmfmac
```

---

### Post by miatawnt2b on 2015-05-06
ok, here are the modinfo params
```

parm:           txglomsz:maximum tx packet chain size [SDIO] (int)
parm:           firmware_path:string
parm:           debug:level of debug output (int)
parm:           fcmode:mode of firmware signalled flow control (int)
parm:           roamoff:do not use internal roaming engine (int)
root@switch:/# 

```

and
```

root@switch:/# cat sys/bus/platform/drivers/sdhci-acpi/INT33BB:00/power/control
auto

```

i'll set the power control to on and see what happens

---

### Post by chili555 on 2015-05-06
> root@switch:/# cat sys/bus/platform/drivers/sdhci-acpi/INT33BB:00/power/control
autoAre you certain it wasn't:```
cat [COLOR="#FF0000"]**/**[/COLOR]sys/bus/platform/drivers/sdhci-acpi/INT33BB:00/power/control
auto
```> i'll set the power control to on and see what happens How? I have an idea or two but I'm interested in your method.

---

### Post by miatawnt2b on 2015-05-06
So... Interesting things with that sysfsutils edit. 

My packet loss is still the same. but my rtt significantly decreased from 400-1200ms down to 100-200ms. 

install sysfsutils and edit the /etc/sysfs.conf file with the following

bus/platform/drivers/sdhci-acpi/80860F14:00/power/control = on
bus/platform/drivers/sdhci-acpi/80860F14:01/power/control = on
bus/platform/drivers/sdhci-acpi/INT33BB:00/power/control = on

it was set to auto by default. I also tried 'off' for grins and giggles. same experience as auto

---

### Post by chili555 on 2015-05-06
Ah, I see. Very well done.> bus/platform/drivers/sdhci-acpi/[COLOR="#FF0000"]INT33BB:00[/COLOR]/power/control = on
As far as I can read, this is the wireless; I doubt there is any reason to change the others. As well, I doubt that the others impact wireless either way.

Let's check again now:```
cat /var/log/syslog | grep wlan | tail -n20
cat /var/log/syslog | grep brcm | tail -n20
```Since this is now 40 lines, let's save some clutter and put them here: [http://paste.ubuntu.com](http://paste.ubuntu.com)

---

### Post by miatawnt2b on 2015-05-07
Here's the latest output.

[http://paste.ubuntu.com/11010045/](http://paste.ubuntu.com/11010045/)

---

### Post by chili555 on 2015-05-07
I am still Googling, but I see one thing we might adjust. Please run:```
ifconfig
```Please make note of the HWADDR, known otherwise as the MAC address. Now we edit the famous text file. The copy I downloaded includes:> macaddr=00:90:4c:cc:11:33Please do:```
gksudo gedit /lib/firmware/brcm/brcmfmac43241b4-sdio.txt
```Change the macaddr= to the address you found in ifconfig. Proofread carefully, save and close the text editor. Unload and reload the driver:```
sudo modprobe -r brcmfmac  &&  sudo modprobe brcmfmac
```I will continue my studies, but this may be helpful.

I also see this:> devid=0x4374I wonder if yours is that. Please check:```
dmesg | grep -e devid -e 14e4
```

---

### Post by miatawnt2b on 2015-05-07
changed the mac address in the HW file. No change.

also nothing matching the devid in dmesg

```

root@switch:~# dmesg | grep -e devid -e 14e4
root@switch:~# dmesg | grep -e 4374
root@switch:~# dmesg | grep -e devid
root@switch:~# dmesg | grep -e 14e4

```

---

### Post by chili555 on 2015-05-07
Would you please reboot so we have a clean slate and do:```
dmesg > wifi.txt
```Find the file wifi.txt in your user directory and paste it. Maybe I can see something that confirms the device id. [http://paste.ubuntu.com](http://paste.ubuntu.com)

I am quickly running out of ideas/mojo/talent.

---

### Post by miatawnt2b on 2015-05-08
thanks for taking a look.

[http://paste.ubuntu.com/11030248/](http://paste.ubuntu.com/11030248/)

---

### Post by miatawnt2b on 2015-05-09
Fixed the packet loss issue by disabling ipv6. Who needs it anyway?!

---

### Post by chili555 on 2015-05-09
Wow! Great job.

So, are you all set? If so, it will be helpful to the searchers out there to use Thread Tools at the top to mark Solved.

---

