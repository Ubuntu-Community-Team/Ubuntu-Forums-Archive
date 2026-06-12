---
title: "Unable to connect to WPA2 Personal wireless network in Kubuntu 12.04"
date: 2013-11-02
forum: Networking &amp; Wireless
---

### Post by Karmovorotin on 2013-11-02
Hello ladies and gentlemen.

I have just installed Kubuntu 12.04 LTS on my old desktop (32-bit architecture). I have tried to connect to my home network using the default Network Manager but in the security options I cannot choose the kind of encription that it uses. I have tried to install wicd but since the only way to connect to the internet on my desktop is through that very same wifi, I have had to download the packages on a USB drive using my laptop following the advice on [this thread]("http://ubuntuforums.org/showthread.php?t=1524810") (no sudo apt-get install wicd for me!) and it failed to install. My wifi adaptor is a D-Link DWL-122. I doubt it's a driver problem since my PC recognises all nearby networks, it just fails to connect to mine! As I explain in the title, it's a WPA2 Personal network using AES encryption.

I am a pretty new and inexperienced user so I would appreciate all your comments and advice. Thank you!

---

### Post by praseodym on 2013-11-02
Hi,

please show the terminal outputs of these commands:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by Karmovorotin on 2013-11-02
Thanks, here are the outputs:

> sobremesa@sobremesa-P4X266E-8233A:~$lspci -nnk | grep -iA2 netsobremesa@sobremesa-P4X266E-8233A:~$lsusb
Bus 001 Device 001: ID 1d6b:0001 LinuxFoundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 LinuxFoundation 1.1 root hub
Bus 001 Device 002: ID 2001:3700 D-LinkCorp. DWL-122 802.11b [Intersil Prism 3]
sobremesa@sobremesa-P4X266E-8233A:~$lsmod
Module                  Size  Used by
snd_wavefront          34737  0 
snd_via82xx            24718  2 
snd_cs4236             29294  0 
snd_ac97_codec        106082  1snd_via82xx
ac97_bus               12642  1snd_ac97_codec
snd_wss_lib            30063  2snd_wavefront,snd_cs4236
snd_opl3_lib           18863  2snd_wavefront,snd_cs4236
snd_hwdep              13276  2snd_wavefront,snd_opl3_lib
snd_pcm                80845  4snd_via82xx,snd_cs4236,snd_ac97_codec,snd_wss_lib
prism2_usb            167518  0 
cfg80211              178679  1prism2_usb
snd_page_alloc         14108  3snd_via82xx,snd_wss_lib,snd_pcm
snd_mpu401             13847  0 
snd_mpu401_uart        13865  4snd_wavefront,snd_via82xx,snd_cs4236,snd_mpu401
snd_seq_midi           13132  0 
psmouse                72846  0 
serio_raw              13027  0 
snd_rawmidi            25424  3snd_wavefront,snd_mpu401_uart,snd_seq_midi
i2c_viapro             12969  0 
via_ircc               26781  0 
irda                  185517  1via_ircc
snd_seq_midi_event     14475  1snd_seq_midi
snd_seq                51567  2snd_seq_midi,snd_seq_midi_event
crc_ccitt              12595  1 irda
snd_timer              28931  4snd_wss_lib,snd_opl3_lib,snd_pcm,snd_seq
snd_seq_device         14172  4snd_opl3_lib,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  18snd_wavefront,snd_via82xx,snd_cs4236,snd_ac97_codec,snd_wss_lib,snd_opl3_lib,snd_hwdep,snd_pcm,snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10rfcomm,bnep
ppdev                  12849  0 
ns558                  12654  0 
gameport               15060  3snd_via82xx,ns558
soundcore              14635  1 snd
parport_pc             32114  1 
shpchp                 32325  0 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3ppdev,parport_pc,lp
nouveau               712294  3 
ttm                    65344  1 nouveau
drm_kms_helper         45466  1 nouveau
drm                   197692  5nouveau,ttm,drm_kms_helper
pata_via               13428  2 
i2c_algo_bit           13199  1 nouveau
mxm_wmi                12859  1 nouveau
wmi                    18744  1 mxm_wmi
video                  19068  1 nouveau
floppy                 60310  0 
sobremesa@sobremesa-P4X266E-8233A:~$iwconfig
lo        no wireless extensions.


wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Access Point:Not-Associated   Tx-Power=18 dBm   
          Retry  long limit:7   RTSthr:off   Fragment thr:off
          Power Management:on
          
sobremesa@sobremesa-P4X266E-8233A:~$rfkill list
0: phy0: Wireless LAN
        Soft blocked: no
Hard blocked: no

---

### Post by tgalati4 on 2013-11-02
You have an old card:  **802.11b**.  Perhaps the router is set up as "G-Mode" only.  Look in the wireless settings and verify that it is set to "B+G" mode.  B-mode only allows up to 11 Mbps bandwidth and may be too slow for WPA2 in crowded networks.  Try WPA instead.  Understand that operating a slow "B" transmitter can slow the entire wireless network down.

---

### Post by Karmovorotin on 2013-11-02
My router is set up in 802.11b/g/n, so that should not be an issue. Gonna try with WPA. Problem is: on my network manager I can't choose WPA security.

---

### Post by praseodym on 2013-11-02
Did you install the package "linux-firmware-nonfree"?

[http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb)

---

### Post by Karmovorotin on 2013-11-02
No, gonna try it now. Let's see if I get the procedure right: copy the package to a USB drive, open terminal and write:

> sudo apt-get install linux-firmware-nonfree

Is that right?

Sorry if I ask stupid questions, I am a quite unskilled newbie.

EDIT: Obviously It's not right: I tried writing:

> sudo apt-get install linux-firmware-nonfree*.deb

The package could not be located, although I'm operating Konsole from the USB stick.

---

### Post by praseodym on 2013-11-02
Double-click the *.deb file and install it with the software-center

---

### Post by Karmovorotin on 2013-11-02
Can't do it, when I double-click it the package installer prompts but the "Install package" button appears greyed out.

[ATTACH=CONFIG]247498[/ATTACH]

---

### Post by praseodym on 2013-11-02
Save it in "Downloads" and install via
```

sudo dpkg -i ~/Downloads/*.deb
```

---

### Post by Karmovorotin on 2013-11-02
Done. Rebooted the system only to see the same: when adding a network connection I can't choose WPA, just LEAP, dynamic WEP (802.1x) and WEP.

---

### Post by praseodym on 2013-11-02
Maybe the driver doesnt support WPA/WPA2?! Check
```

nm-tool
```

---

### Post by Karmovorotin on 2013-11-02
Checked. These are the results:

> sobremesa@sobremesa-P4X266E-8233A:~$nm-tool

NetworkManager Tool


State: disconnected


- Device: wlan0----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            prism2_usb
  State:             disconnected
  Default:           no
  HW Address:        00:11:95:91:D6:81


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes


  Wireless Access Points 
    LemonPremium:    Infra,00:03:7F:C0:60:05, Freq 2442 MHz, Rate 0 Mb/s, Strength 42 WEP
    Jazztel_72:      Infra,BC:76:70:C6:D4:E8, Freq 2437 MHz, Rate 0 Mb/s, Strength 19 WEP
    ONOB2A1:         Infra,30:46:9A:7C:B2:A1, Freq 2412 MHz, Rate 0 Mb/s, Strength 34 WEP
    MIGUEL:          Infra,00:19:15:D6:DF:B1, Freq 2437 MHz, Rate 0 Mb/s, Strength 22 WEP
    WLAN_BA:         Infra,00:02:CF:B5:25:01, Freq 2462 MHz, Rate 0 Mb/s, Strength 25 WEP
    WLAN_78:         Infra,E0:91:53:23:D7:7C, Freq 2457 MHz, Rate 0 Mb/s, Strength 17 WEP
WLAN_591C:       Infra,C8:6C:87:4D:59:1D, Freq 2447 MHz, Rate 0 Mb/s, Strength 19 WEP

My network is Jazztel_72.

---

### Post by praseodym on 2013-11-02
> ```
Capabilities:


Wireless Properties
WEP Encryption: yes
```
Try connecting with WEP. After that install ndiswrapper via:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms ndisgtk ndiswrapper-dkms unzip
```
and try the Windows XP driver:
```

wget ftp://ftp.dlink.com/Wireless/dwl122/Driver/dwl122_driver_102.zip
unzip dwl122_driver_102.zip
cd Drivers/WinXP/
sudo ndiswrapper -i NETPRISM.inf
sudo modprobe -rfv prism2_usb
sudo modprobe -v ndiswrapper
sudo ndisrapper -ma
sudo service network-manager restart
```
Check:```

nm-tool
ndiswrapper -l
iwconfig
sudo iwlist scan
```
Afaik it works also only with WPA

---

### Post by Karmovorotin on 2013-11-02
Doesn't recognise command the option "k" on command line from -dkms. Any alternative course of action?

---

### Post by praseodym on 2013-11-02
**ndiswrapper-dkms**
is "one" word

---

### Post by Karmovorotin on 2013-11-02
Oh thank you! Silly me. But anyway couldn't locate packages:

> linux-headers-generic
build-essential
dkms
ndisgtk
ndiswrapper-dkms

It seems my computer doesn't want to connect to the internet, that's all. We have to give it the ndiswrapper or the wicd through other means.

---

### Post by praseodym on 2013-11-02
This will be too complicated. I strongly recommend buying a new stick which is supported, and which supports WPA2!

---

### Post by Karmovorotin on 2013-11-02
I see. Thank you very much for your help, I am learning a lot!

---

### Post by Karmovorotin on 2013-11-23
Hi, I am giving a bump to this thread since I managed to connect to my network by changing its encryption to WEP. Thing is, now it doesn't even connect to that one! I have changed the encryption to WEP with 128-bit encryption key and key index 1.

Please help!

---

### Post by praseodym on 2013-11-23
Lets see:
```

ndiswrapper -l
lsmod
iwconfig
sudo iwlist scan
dmesg | grep ndis
```

---

### Post by Karmovorotin on 2013-11-23
I have formatted and reinstalled Kubuntu to start from a clean slate since I don't know what the **** was I doing. Hope that makes things easier to you.

> sobremesa@sobremesa:~$ sudo ndiswrapper-lsudo: ndiswrapper: orden no encontrada
sobremesa@sobremesa:~$ lsmod
Module                  Size  Used by
bnep                   17830  2 
bluetooth             158438  7 bnep
snd_wavefront          34737  0 
snd_cs4236             29294  0 
snd_wss_lib            30063  2snd_wavefront,snd_cs4236
snd_opl3_lib           18863  2snd_wavefront,snd_cs4236
snd_via82xx            24718  2 
snd_ac97_codec        106082  1snd_via82xx
ac97_bus               12642  1snd_ac97_codec
snd_hwdep              13276  2snd_wavefront,snd_opl3_lib
snd_pcm                80845  4snd_cs4236,snd_wss_lib,snd_via82xx,snd_ac97_codec
snd_page_alloc         14108  3snd_wss_lib,snd_via82xx,snd_pcm
ppdev                  12849  0 
snd_mpu401             13847  0 
snd_mpu401_uart        13865  4snd_wavefront,snd_cs4236,snd_via82xx,snd_mpu401
snd_seq_midi           13132  0 
snd_rawmidi            25424  3snd_wavefront,snd_mpu401_uart,snd_seq_midi
prism2_usb            167518  0 
snd_seq_midi_event     14475  1snd_seq_midi
snd_seq                51567  2snd_seq_midi,snd_seq_midi_event
snd_timer              28931  4snd_wss_lib,snd_opl3_lib,snd_pcm,snd_seq
snd_seq_device         14172  4snd_opl3_lib,snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              178679  1prism2_usb
i2c_viapro             12969  0 
via_ircc               26781  0 
irda                  185517  1via_ircc
psmouse                72846  0 
shpchp                 32325  0 
snd                    62064  18snd_wavefront,snd_cs4236,snd_wss_lib,snd_opl3_lib,snd_via82xx,snd_ac97_codec,snd_hwdep,snd_pcm,snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13027  0 
ns558                  12654  0 
gameport               15060  3snd_via82xx,ns558
parport_pc             32114  1 
soundcore              14635  1 snd
crc_ccitt              12595  1 irda
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3ppdev,parport_pc,lp
nouveau               712294  3 
ttm                    65344  1 nouveau
drm_kms_helper         45466  1 nouveau
drm                   197692  5nouveau,ttm,drm_kms_helper
pata_via               13428  2 
i2c_algo_bit           13199  1 nouveau
mxm_wmi                12859  1 nouveau
wmi                    18744  1 mxm_wmi
video                  19068  1 nouveau
floppy                 60310  0 
sobremesa@sobremesa:~$ iwconfig
lo        no wireless extensions.


wlan0     IEEE 802.11b ESSID:"Jazztel_72"  
          Mode:Managed  Frequency:2.437GHz  Access Point: BC:76:70:C6:D4:E8   
          Bit Rate=0 kb/s   Tx-Power=18dBm   
          Retry  long limit:7   RTSthr:off   Fragment thr:off
          Power Management:on
          Link Quality=39/70  Signallevel=-71 dBm  
          Rx invalid nwid:0  Rx invalidcrypt:0  Rx invalid frag:0
          Tx excessive retries:0 Invalid misc:0   Missed beacon:0


sobremesa@sobremesa:~$ sudo iwlist scan
lo        Interface doesn't supportscanning.


wlan0     Scan completed :
          Cell 01 - Address:BC:76:70:C6:D4:E8
                    Channel:6
                    Frequency:2.437 GHz(Channel 6)
                    Quality=38/70 Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"Jazztel_72"
                    Mode:Master
                   Extra:tsf=00000000000267aa
                    Extra: Last beacon:252ms ago
                    IE: Unknown:000A4A617A7A74656C5F3732
          Cell 02 - Address:00:02:CF:B5:25:01
                    Channel:11
                    Frequency:2.462 GHz(Channel 11)
                    Quality=28/70 Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"WLAN_BA"
                    Mode:Master
                   Extra:tsf=00000000000267aa
                    Extra: Last beacon:252ms ago
                    IE: Unknown:0007574C414E5F4241


sobremesa@sobremesa:~$ dmesg | grepndis

---

### Post by praseodym on 2013-11-23
Install the package linux-firmware-nonfree again. Reboot and
```

iwlist chan
cat /etc/resolv.conf
route -n
ifconfig -a
```

---

### Post by Karmovorotin on 2013-11-23
The package couldn't be located.

---

### Post by praseodym on 2013-11-23
Link on page 1 ;-)

---

### Post by Karmovorotin on 2013-11-24
Asks me for a password, and it isn't my own user password since it must be 5 characters long.

I am starting to grow very tired of Linux, to be honest.

---

### Post by praseodym on 2013-11-24
WPA2 passwords need at least 8 characters. Check the PW in the router interface. Any strange characters in your PW?

---

### Post by Karmovorotin on 2013-11-24
No, all caps and digits. Nothing weird. Just an old USB dongle and a crappy driver repository.

---

