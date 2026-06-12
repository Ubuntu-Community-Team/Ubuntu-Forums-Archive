---
title: "Bcm4318 wpa woes"
date: 2006-12-02
forum: Networking &amp; Wireless
---

### Post by Ethos on 2006-12-02
Hello I have been working on getting my bcm4318 working on my dell laptop. I did many searches on the forum and found everything very helpful. This is my situation now. I have gotten my wifi light on my laptop to turn on, ndiswrapper is working correctly. I now need some help getting it to work with wpa2 tkip....Can someone please help me? Also my computer isnt finding any networks around nor is it finding my own...that may be part of the problem?

---

### Post by Ethos on 2006-12-02
I have a update...I installed wifi-radar and I can see all the networks around me now!, but im having trouble connecting to wpa tkip+aes, which is how my network is setup, any suggestions?

---

### Post by Ethos on 2006-12-02
Another problem I have found now is that if i uninstall wifi-radar im not able to find any networks at all when i run iwconfig, or scan of networks....My wifi light is on so I dont know what to do now...

---

### Post by wieman01 on 2006-12-03
If you need a guide on WPA... This is one:

[http://www.ubuntuforums.org/showthread.php?t=202834]("http://www.ubuntuforums.org/showthread.php?t=202834")

Covers both WPA1 (TKIP) and WPA2 (AES). Not sure if the native Linux driver for "bcm4318" supports WPA2 (AES) though. I doubt it.

---

### Post by Ethos on 2006-12-03
wieman01 I saw your tutorial when searching, and it looked very good, but i was hesitent to try it. I am using ndiswrapper with wifi-radar, from what I saw your tutorial is designed for using network manager? i was following it and im not able to get the card working under network manager, only wifi radar...Im able to connect to unsecured networks so i know that the card is working...So im not sure where to go from here...could you help me with getting the card working with network manager correctly?

---

### Post by wieman01 on 2006-12-03
Actually, this approach makes use of neither NetworkManager nor Wifi-Radar. This is a manual solution. Not sure if that's what you want owning a laptop, but I could guide you through it... Let me know.

---

### Post by Ethos on 2006-12-03
I see, well when I do the scan that is in your approach my card does not pick up any surrounding wifi networks, nor does the manager...Should I just proceed? I didn't want to do all that editing and put alot of time into it if I had something wrong in the first place you know?...Thanks


ps: iwlist scan is what i was talking about, and no networks show up..

---

### Post by Ethos on 2006-12-04
```
bill@laptop:~$ uname -a
Linux laptop 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686 GNU/Linux

bill@laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:209 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1284 (1.2 KiB)  TX bytes:1284 (1.2 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:201 Memory:dfcfe000-dfd00000

bill@laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
bill@laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

bill@laptop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1284 (1.2 KiB)  TX bytes:1284 (1.2 KiB)

wlan0     Link encap:Ethernet  HWaddr  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:201 Memory:dfcfe000-dfd00000 

bill@laptop:~$ lsmod
Module                  Size  Used by
nls_utf8                3200  1 
nls_cp437               6912  1 
vfat                   14720  1 
fat                    56348  1 vfat
usb_storage            75072  1 
libusual               17040  1 usb_storage
ipv6                  272288  8 
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
radeon                118816  2 
drm                    74644  3 radeon
speedstep_centrino      9760  1 
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  1 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sony_acpi               6412  0 
sbs                    16804  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
i2c_core               23424  1 i2c_ec
hotkey                 11556  0 
dev_acpi               12292  0 
container               5632  0 
button                  7952  0 
battery                11652  0 
asus_acpi              17688  0 
ac                      6788  0 
af_packet              24584  4 
ndiswrapper           199828  0 
sbp2                   24584  0 
parport_pc             37796  0 
lp                     12964  0 
parport                39496  2 parport_pc,lp
pcmcia                 40380  0 
sg                     37404  0 
joydev                 11200  0 
tsdev                   9152  0 
sdhci                  20108  0 
usbhid                 45152  0 
yenta_socket           28812  1 
rsrc_nonstatic         15360  1 yenta_socket
pcmcia_core            43924  3 pcmcia,yenta_socket,rsrc_nonstatic
b44                    26764  0 
mii                     6912  1 b44
mmc_core               32392  1 sdhci
evdev                  11392  2 
pcspkr                  4352  0 
serio_raw               8452  0 
psmouse                41352  0 
snd_intel8x0           34844  1 
snd_ac97_codec         97696  1 snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
snd                    58372  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
intel_agp              26012  1 
agpgart                34888  2 drm,intel_agp
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
ext3                  142728  1 
jbd                    62228  1 ext3
ehci_hcd               34696  0 
ohci1394               37040  0 
ieee1394              306104  2 sbp2,ohci1394
uhci_hcd               24968  0 
usbcore               134912  7 usb_storage,libusual,ndiswrapper,usbhid,ehci_hcd,uhci_hcd
ide_generic             2432  0 
sr_mod                 18212  0 
cdrom                  38944  1 sr_mod
sd_mod                 22656  4 
generic                 5764  0 
ata_piix               11780  2 
ahci                   20228  0 
libata                 74892  2 ata_piix,ahci
scsi_mod              144648  7 usb_storage,sbp2,sg,sr_mod,sd_mod,ahci,libata
thermal                15624  0 
processor              31560  2 speedstep_centrino,thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability

bill@laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 
                    ESSID:"Myssid"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:57/100  Signal level:-59 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK  
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK  

sit0      Interface doesn't support scanning.

bill@laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid Myssid
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk passphrasewashere


bill@laptop:~$ cat /etc/modprobe.d/ndiswrapper 
alias wlan0 ndiswrapper
bill@laptop:~$ cat /etc/resolv.conf
cat: /etc/resolv.conf: No such file or directory
```





Hope this helps...I have the card working! it just doesnt connect :/..

---

### Post by wieman01 on 2006-12-04
Looks good actually. 

Would the card connect with encryption turned off? Is DHCP enabled (router)? And please set both group & pairwise cypher to CCMP (= AES):
>  IE: IEEE 802.11i/WPA2 Version 1
                        [COLOR="Red"]Group Cipher : TKIP [/COLOR]
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK  
                    IE: WPA Version 1
                        [COLOR="Red"]Group Cipher : TKIP [/COLOR]
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK  
How did you generate the wpa_passphrase?

---

### Post by wieman01 on 2006-12-04
By the way... Please also test TKIP while you are at it. The reason being that your card may not support WPA2 (AES).

---

### Post by Ethos on 2006-12-04
DHCP is enabled on the router, I was able to connect w/o encryption . When I was using the laptop with windows I was able to use the current setup that is on the router. And the way I generated the passphrase is I googled a generator, and put in the hex key then generated a passphrase...I was not able to get linux to generate me a passphrase :/...How do I test tkip?   Thanks Bill

---

### Post by wieman01 on 2006-12-04
As for WPA-PSK key generation, type the following command in a terminal ([COLOR="Red"]"" [/COLOR]quotes required):
> wpa_passphrase [COLOR="Red"]"[/COLOR]your_essid[COLOR="Red"]"[/COLOR] [COLOR="Red"]"[/COLOR]your_ascii_key[COLOR="Red"]"[/COLOR]
Resulting in an output like...
> network={
ssid="test"
#psk="12345678"
psk=fe727aa8b64ac9b3f54c72432da14faed933ea511ecab15bbc6c52e7522f709a
}
Copy the "hex_key" (next to "psk=...") and replace [COLOR="Blue"]your_wpa_passphrase[/COLOR] in the "interfaces" files with it. 

Then test TKIP first:
> auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid Myssid
wpa-ap-scan 1
wpa-proto [COLOR="Red"]WPA[/COLOR]
wpa-pairwise [COLOR="Red"]TKIP[/COLOR]
wpa-group [COLOR="Red"]TKIP[/COLOR]
wpa-key-mgmt WPA-PSK
wpa-psk [COLOR="Blue"]your_wpa_passphrase[/COLOR]
Save the file and restart your network:
> sudo /etc/init.d/networking restart

---

### Post by wieman01 on 2006-12-04
Forgot to mention: You definitely need to uninstall Wifi-Radar... Otherwise my solution won't work & will be overwritten by it. Have you installed "wpa-supplicant"?

---

### Post by Ethos on 2006-12-04
I have installed wpa_supplicant. This is a fresh install w/o ever having installed radar, however I did have network manager-gnome installed, but I have removed the package...Could that effect anything?...when i try and generate a key I get a error that says key needs to be between 8 and 64 characters, am I entering it wrong? should the ssid or plain text key be in < > or " ", or nothing at all? when im trying to generate passphrase?

---

### Post by wieman01 on 2006-12-04
> wpa_passphrase "Myssid" "your_ascii_key"
Open a terminal & simply type "wpa_passphrase" followed by "Myessid" (plus use quotes and your normal "ascii password". Then hit enter. This command should generate your passphrase which will become part of your "interfaces" file.
[U][B]
EDIT:[/B][/U]
Yes, both NetworkManager & Wifi-Radar need to be removed. They will interfere.

---

### Post by Ethos on 2006-12-04
I would like to say that I am happily connected to my wpa2 tkip+aes network for one reason only, and that was all your great instruction wieman...I am very very thankful for your help and cant be happier :)

---

### Post by ericesque on 2006-12-04
holy crap.  nice job guys.  I connected with WPA in dapper (same wireless as Ethos) and was quite happy until I upgraded to Edgy and the same solution no longer worked.  Right now I'm plenty happy with MAC filtering and WEP encryption.  It keeps the peoples off my wifi--for as often as I run Ubuntu anymore :(

---

### Post by Ethos on 2006-12-04
ericesque its very easy to break wep, and mac filtering doesnt do much because you can spoof macs...I would use wpa if I were you..

---

### Post by wieman01 on 2006-12-04
Yes, forget about WEP... Really, it's a fairly weak & outdated algorithm. Try WPA instead. This is a full guide on it:

[http://www.ubuntuforums.org/showthread.php?t=202834]("http://www.ubuntuforums.org/showthread.php?t=202834")

---

### Post by wieman01 on 2006-12-04
> **Ethos said:**
> I would like to say that I am happily connected to my wpa2 tkip+aes network for one reason only, and that was all your great instruction wieman...I am very very thankful for your help and cant be happier :)
You are welcome. Just disable **TKIP** if possible and use **AES** instead. **TKIP** is part of the **WPA1** framework which happends to be **WEP** based. So it is not secure either. I reckon **AES** should work with your card. Not sure though.

---

