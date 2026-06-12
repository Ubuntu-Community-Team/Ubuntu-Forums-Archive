---
title: "Asus PCE-N53 patch/driver 14.04"
date: 2014-04-19
forum: Networking &amp; Wireless
---

### Post by allinson-ryan on 2014-04-19
Hi I've recently upgraded from 13.10 to 14.04 and my network card drivers aren't working with the new kernel. Does anyone know a new patch or driver that works with the new kernel?

---

### Post by praseodym on 2014-04-19
Please show```


lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
sudo iwlist scan
```
Is it an Asus computer?

---

### Post by allinson-ryan on 2014-04-19
```
lspci -nnk | grep -iA2 net
03:00.0 Network controller [0280]: Ralink corp. RT5592 PCIe Wireless Network Adapter [1814:5592]
    Subsystem: ASUSTeK Computer Inc. Device [1043:851a]
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
    Kernel driver in use: r8169
lsusb
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 046d:c293 Logitech, Inc. WingMan Formula Force GP
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 046d:c526 Logitech, Inc. Nano Receiver
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 002: ID 046a:0021 Cherry GmbH CyMotion Expert Combo
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
lsmod
Module                  Size  Used by
nfsv3                  39326  1 
ctr                    13049  2 
ccm                    17773  2 
arc4                   12608  2 
rt2800usb              27034  0 
rt2x00usb              20742  1 rt2800usb
rt2800lib              89076  1 rt2800usb
rt2x00lib              55307  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              626489  3 rt2x00lib,rt2x00usb,rt2800lib
cfg80211              484040  2 mac80211,rt2x00lib
crc_ccitt              12707  1 rt2800lib
rpcsec_gss_krb5        35573  0 
nfsv4                 465643  0 
rfcomm                 69160  0 
bnep                   19624  2 
bluetooth             395423  10 bnep,rfcomm
snd_hda_codec_hdmi     46207  1 
nfsd                  280297  2 
binfmt_misc            17468  1 
auth_rpcgss            59338  2 nfsd,rpcsec_gss_krb5
nfs_acl                12837  2 nfsd,nfsv3
nfs                   236636  3 nfsv3,nfsv4
lockd                  93977  3 nfs,nfsd,nfsv3
sunrpc                284404  23 nfs,nfsd,rpcsec_gss_krb5,auth_rpcgss,lockd,nfsv3,nfsv4,nfs_acl
fscache                63988  2 nfs,nfsv4
kvm                   451511  0 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
snd_hda_codec_realtek    61438  1 
aesni_intel            55624  4 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hda_intel          52355  8 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
serio_raw              13462  0 
snd_seq_midi           13324  0 
snd_pcm               102099  5 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
fam15h_power           13119  0 
k10temp                13126  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
edac_core              62291  0 
edac_mce_amd           22617  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
sp5100_tco             13979  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
i2c_piix4              22155  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
snd                    69238  25 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
joydev                 17381  0 
nvidia              10675249  65 
parport_pc             32701  0 
soundcore              12680  1 snd
ppdev                  17671  0 
drm                   302817  2 nvidia
lp                     17759  0 
mac_hid                13205  0 
parport                42348  3 lp,ppdev,parport_pc
wmi                    19177  0 
hid_logitech           26709  0 
ff_memless             13573  1 hid_logitech
pata_acpi              13038  0 
hid_generic            12548  0 
usbhid                 52616  0 
hid                   106148  3 hid_generic,hid_logitech,usbhid
ahci                   25819  2 
r8169                  67581  0 
pata_atiixp            13271  0 
libahci                32168  1 ahci
mii                    13934  1 r8169

iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"BlackMesa"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: E0:3F:49:8B:99:14   
          Bit Rate=65 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: on
          Link Quality=63/70  Signal level=-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1154  Invalid misc:54   Missed beacon:0

rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

sudo iwlist scan
eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: E0:3F:49:8B:99:14
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption keyn
                    ESSID:"BlackMesa"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000045fc313c4
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 0009426C61636B4D657361
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FFFFFF00010000000000000000000000000C1846471100
                    IE: Unknown: 3D1606000600000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0504001B127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706474220010D10
          Cell 02 - Address: AC:22:0B:E8:F4:00
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key: on
                    ESSID:"BlackMesa"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000005bb711c15
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 0009426C61636B4D657361
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 0B0503001D0000
                    IE: Unknown: 2D1ABD1917FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F03010008
                    IE: Unknown: DD090010180203001C0000
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
          Cell 03 - Address: 00:62:2C:64:1E:7C
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key: on
                    ESSID:"BTHub5-N56M"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b21bbef180
                    Extra: Last beacon: 492ms ago
                    IE: Unknown: 000B4254487562352D4E35364D
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050402030000
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000008000000000000000000000
                    IE: Unknown: 3D1606000500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080100000000000040
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD2C0050F204104A00011010440001021057000100104700102FA69EB263445AD18F81AD30776DFB82103C000101
          Cell 04 - Address: 00:0C:E6:0A:77:F1
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key: on
                    ESSID:"Learning-Student"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000020d2361d346
                    Extra: Last beacon: 16408ms ago
                    IE: Unknown: 00104C6561726E696E672D53747564656E74
                    IE: Unknown: 010802040B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7D181BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1601000000000000000000000000000000000000000000
                    IE: Unknown: DD180050F202010180000353000027A4000042435E0062322F00
                    IE: Unknown: DD36000CE600042B0000000106000CE61243450404010000000504005000000908105861230D0200000A04010000000B04010000000D010A
          Cell 05 - Address: 00:0C:E6:0A:E7:36
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key: on
                    ESSID:"Learning-Staff"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000020d236365f1
                    Extra: Last beacon: 16348ms ago
                    IE: Unknown: 000E4C6561726E696E672D5374616666
                    IE: Unknown: 010802040B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7D181BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001100000000000000000000000000000000000000
                    IE: Unknown: DD180050F202010180000353000027A4000042435E0062322F00
                    IE: Unknown: DD36000CE60004050000000106000CE61244BF040401000000050400F000000908EE4D62230D0200000A04010000000B04030000000D010A
          Cell 06 - Address: 00:18:0A:21:B2:FD
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key: on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000000b8922d7
                    Extra: Last beacon: 1140ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B9618243048
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555349010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 3202606C
                    IE: Unknown: DD180050F20201010F0003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080800000000000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0D00180A0700000000010065D4D0
                    IE: Unknown: DD0A00037F04010000000000
          Cell 07 - Address: 06:18:0A:21:B2:FD
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key: on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000000b928180
                    Extra: Last beacon: 516ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B9618243048
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555349010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 3202606C
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080800000000000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0D00180A0700000000010065D4D0
                    IE: Unknown: DD0A00037F04010000000000
          Cell 08 - Address: 1A:18:0A:21:B2:FD
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key: on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000000b928180
                    Extra: Last beacon: 504ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B9618243048
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555349010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 3202606C
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080800000000000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0D00180A0700000000010065D4D0
                    IE: Unknown: DD0A00037F04010000000000
          Cell 09 - Address: 00:1F:33:05:82:32
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key: on
                    ESSID:"SKY32782"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003551f50f51
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 0008534B593332373832
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0103
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
```



My computer isn't Asus, I built it the specs are:

AMD FX-6300
Nvidia GT-640

---

### Post by praseodym on 2014-04-19
Obviously, you are connected via the stick. Deactivate the power management:
```

sudo iwconfig wlan0 power off
```

Driver for the PCI card from here:

[http://wireless.kernel.org/en/users/Drivers/rt2800pci](http://wireless.kernel.org/en/users/Drivers/rt2800pci)

does not compile against kernel 3.8 (here), it is for kernel 2.6.

Try to add the device ID to the native driver **[B]rt2800pci**[/B]:

```
echo 'install rt2800pci modprobe --ignore-install rt2800pci ; /bin/echo "1814 5592" > [COLOR="#FF0000"]/sys/bus/pci/drivers/rt2800pci/[/COLOR]new_id' | sudo tee /etc/modprobe.d/rt2800pci.conf
```

This is one line, you better copy/paste it. Check the path in red first! If its ok, load the driver after unplugging the stick:

```
sudo modprobe -v rt2800pci
dmesg | grep rt2
iwconfig
cat /etc/udev/rules.d/70-persistent-net.rules
sudo iwlist scan
iwlist chan
```

---

### Post by chili555 on 2014-04-19
I don't believe the new_id technique works for PCI devices; only USB.

---

### Post by allinson-ryan on 2014-04-19
Does this mean my card won't work with 14.04?

---

### Post by praseodym on 2014-04-19
Did you try it?

---

### Post by allinson-ryan on 2014-04-19
Yes, I tried it  but it didn't work.

---

### Post by praseodym on 2014-04-19
Please show the outputs.

---

### Post by allinson-ryan on 2014-04-21
```
echo 'install rt2800pci modprobe --ignore-install rt2800pci ; /bin/echo "1814 5592" > /sys/bus/pci/drivers/rt2800pci/new_id' | sudo tee /etc/modprobe.d/rt2800pci.confinstall rt2800pci modprobe --ignore-install rt2800pci ; /bin/echo "1814 5592" > /sys/bus/pci/drivers/rt2800pci/new_id
ryan@Skyblade:~$ sudo modprobe -v rt2800pci
insmod /lib/modules/3.13.0-24-generic/kernel/drivers/misc/eeprom/eeprom_93cx6.ko 
insmod /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko 
insmod /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko 
insmod /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rt2x00/rt2800mmio.ko 
install modprobe --ignore-install rt2800pci ; /bin/echo "1814 5592" > /sys/bus/pci/drivers/rt2800pci/new_id 
insmod /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko 
ryan@Skyblade:~$ dmesg | grep rt2
[    6.665088] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 5390, rev 0502 detected
[    6.695123] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 5370 detected
[    6.700696] usbcore: registered new interface driver rt2800usb
[    7.295113] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[    7.300431] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[   97.109187] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[   97.109223] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[   97.109229] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[   97.109279] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[   97.109285] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[   97.113320] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[   97.187170] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[   97.187353] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  165.221276] ieee80211 phy1: rt2x00_set_rt: Info - RT chipset 5592, rev 0222 detected
[  165.224670] ieee80211 phy1: rt2x00_set_rf: Info - RF chipset 000f detected
[  165.229976] ieee80211 phy1: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2860.bin'
[  165.231110] ieee80211 phy1: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.34
[  165.305348] ieee80211 phy1: rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840
[  165.326129] ieee80211 phy1: rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840
[  165.326787] ieee80211 phy1: rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840
[  165.327270] ieee80211 phy1: rt2x00lib_rxdone_read_signal: Warning - Frame received with unrecognized signal, mode=0x0000, signal=0x0074, type=4
[  165.636111] ieee80211 phy1: rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840
[  165.641831] ieee80211 phy1: rt2x00lib_rxdone: Error - Wrong frame size 4095 max 3840
[  165.689945] ieee80211 phy1: rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840


iwconfig
wlan1     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"BlackMesa"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: AC:22:0B:E8:F4:00   
          Bit Rate=11 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=39/70  Signal level=-71 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:133  Invalid misc:159   Missed beacon:0
cat /etc/udev/rules.d/70-persistent-net.rules
# This file was automatically generated by the /lib/udev/write_net_rules
# program, run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single
# line, and change only the value of the NAME= key.


# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="90:2b:34:a5:b3:19", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="7c:dd:90:31:a5:2c", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# PCI device 0x1814:0x5592 (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="50:46:5d:ae:0a:45", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

sudo iwlist scan
wlan1     No scan results


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: AC:22:0B:E8:F4:00
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"BlackMesa"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002a949f3618
                    Extra: Last beacon: 60ms ago
                    IE: Unknown: 0009426C61636B4D657361
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 0B0506000F0000
                    IE: Unknown: 2D1ABD1917FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F03010008
                    IE: Unknown: DD090010180206001C0000
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
          Cell 02 - Address: 12:62:2C:64:1E:7C
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000d6f4cb93f8
                    Extra: Last beacon: 60ms ago
                    IE: Unknown: 000F4254576946692D776974682D464F4E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000008000000000000000000000
                    IE: Unknown: 3D1606000100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080100000000000040
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 03 - Address: 00:62:2C:64:1E:7C
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"BTHub5-N56M"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000d6f4e80180
                    Extra: Last beacon: 284ms ago
                    IE: Unknown: 000B4254487562352D4E35364D
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050401030000
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000008000000000000000000000
                    IE: Unknown: 3D1606000100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080100000000000040
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD2C0050F204104A00011010440001021057000100104700102FA69EB263445AD18F81AD30776DFB82103C000101
          Cell 04 - Address: 00:1F:33:05:82:32
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"SKY32782"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000008574fce02
                    Extra: Last beacon: 64ms ago
                    IE: Unknown: 0008534B593332373832
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
iwlist chan
wlan1     29 channels in total; available frequencies :
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
          Channel 151 : 5.755 GHz
          Channel 153 : 5.765 GHz
          Channel 155 : 5.775 GHz
          Channel 157 : 5.785 GHz
          Channel 159 : 5.795 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
eth0      no frequency information.


lo        no frequency information.


wlan0     14 channels in total; available frequencies :
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
          Current Frequency:2.437 GHz (Channel 6)




```

---

### Post by praseodym on 2014-04-21
Please show these outputs after unplugging the stick and creating a new profile using wlan1 as interface:
```

iwconfig wlan1
iwlist wlan1 chan
sudo iwlist wklan1 scan
ifconfig wlan1
dmesg | grep rt2
```

---

### Post by allinson-ryan on 2014-04-21
Outputs after I unplugged the usb wifi dongle.

```
iwconfig wlan1wlan1     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


iwconfig wlan1
wlan1     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlan1     IEEE 802.11abgn  ESSID:off/any  
wlan1: command not found
         Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
Mode:Managed: command not found
           Retry  long limit:7   RTS thr:off   Fragment thr:off
Retry: command not found




sudo iwlist wklan1 scan
[sudo] password for ryan: 
wklan1    Interface doesn't support scanning.


ifconfig wlan1
wlan1     Link encap:Ethernet  HWaddr 50:46:5d:ae:0a:45  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
ifconfig wlan1
wlan1     Link encap:Ethernet  HWaddr 50:46:5d:ae:0a:45  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


:~$ dmesg | grep rt2
[    6.665088] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 5390, rev 0502 detected
[    6.695123] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 5370 detected
[    6.700696] usbcore: registered new interface driver rt2800usb
[    7.295113] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[    7.300431] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[   97.109187] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[   97.109223] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[   97.109229] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[   97.109279] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[   97.109285] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[   97.113320] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[   97.187170] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[   97.187353] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  165.221276] ieee80211 phy1: rt2x00_set_rt: Info - RT chipset 5592, rev 0222 detected
[  165.224670] ieee80211 phy1: rt2x00_set_rf: Info - RF chipset 000f detected
[  165.229976] ieee80211 phy1: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2860.bin'
[  165.231110] ieee80211 phy1: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.34
[  165.305348] ieee80211 phy1: rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840
[  165.326129] ieee80211 phy1: rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840
[  165.326787] ieee80211 phy1: rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840
[  165.327270] ieee80211 phy1: rt2x00lib_rxdone_read_signal: Warning - Frame received with unrecognized signal, mode=0x0000, signal=0x0074, type=4
[  165.636111] ieee80211 phy1: rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840
[  165.641831] ieee80211 phy1: rt2x00lib_rxdone: Error - Wrong frame size 4095 max 3840
[  165.689945] ieee80211 phy1: rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840
[  515.689512] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 2
[  515.689537] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 2
[  515.689567] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 2
[  515.689594] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[  515.689617] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 7 in queue 2
[  515.689637] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
[  515.689657] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 2
[  515.708478] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  515.708596] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  515.708718] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  515.708845] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  515.708969] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  515.713981] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  515.714101] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  954.880770] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 2
[  954.880797] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 2
[  954.880856] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 2
[  954.880881] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 2
[  954.880901] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[  954.880922] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 7 in queue 2
[  954.880942] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
[  954.880967] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 2
[  954.880989] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 2
[  954.881010] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 2
[  954.884967] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  954.885089] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  954.885213] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  954.885339] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  954.885460] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  954.885590] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  954.885714] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  954.885838] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  954.885963] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  954.886088] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 5657.637920] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 0
[ 5657.637958] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 0
[ 5657.637977] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 0
[ 5657.974956] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[ 6160.212095] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 0
[ 6160.212139] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 0
[ 6160.212152] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 0
[ 6160.212173] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 2
[ 6160.286827] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[ 6160.287052] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 6162.410767] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 0
[ 6162.410812] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 0
[ 6162.410821] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 0
[ 6162.458523] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 2
[ 6162.458538] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 2
[ 6162.458542] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 2
[ 6162.610466] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[ 6162.610510] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[ 6162.610519] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[ 6162.610553] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 0
[ 6162.610574] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 2
[ 6162.761901] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 6162.762020] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 6162.762271] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[ 6162.762411] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[ 6162.779664] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[ 6165.563042] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 0
[ 6165.563075] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 0
[ 6165.563084] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 0
[ 6165.594432] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[ 6228.837661] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 0
[ 6228.837696] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 0
[ 6228.837702] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 0
[ 6228.943922] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[ 6235.907379] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 0
[ 6235.907416] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 0
[ 6235.907435] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 0
[ 6237.315087] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[16843.613940] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 2
[16843.614285] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[19267.398117] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[19267.398164] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[19267.398170] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[19267.398214] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 2
[19267.401744] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 2
[19267.401778] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 2
[19267.401784] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 2
[19267.521770] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[19267.521889] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[19267.635526] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[23414.577706] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[23414.577726] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[23414.577732] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[23414.577761] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[23414.577774] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[23414.577786] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[23414.577799] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[23414.577825] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 2
[23414.577843] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 2
[23414.931252] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[23414.931373] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[23414.931519] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[23414.931633] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[23414.931751] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[23414.931873] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[23414.939888] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[29144.527408] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]



```

---

### Post by praseodym on 2014-04-21
Please check if a MAC-address filter is on in your router, check the manual. Additionally:
[LIST]
[*]
[*]Do not hide the network
[*]fixed channel, e.g. "1"
[*]bandwidth to 20MHz instead of 20/40MHz
[*]router firmware is up to date?
[/LIST]

---

### Post by praseodym on 2014-04-21
Can you please start with a 13.10 Live-CD and show the outputs of
```

lspci -nnk | grep -iA2 net
lsmod
dmesg | grep rt2
```
from there?

---

### Post by praseodym on 2014-04-22
One of my German supporter collegues (known here as **flash63**) adapted the source code of the **rt5592sta** driver, please try this one:

```
sudo apt-get install linux-headers-$(uname -r) linux-headers-generic build-essential
wget http://www.elektronenblitz63.de/downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326_patched.tar.gz
tar xvf DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326_patched.tar.gz
cd DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326_patched/
sudo make
sudo make install
```
Load the new driver:
```

sudo modprobe -rfv rt2800pci
sudo modprobe -v rt5592sta
sudo service network-manager restart
```
Check:
```

iwconfig
iwlist chan
sudo iwlist scan
dmesg | egrep 'rt2|rt5'
```
Which country do you live? Maybe we need to adjust one more file.

---

### Post by allinson-ryan on 2014-04-25
Thanks, I'm downloading the drivers now, I live in the UK. Sorry about the long wait for a reply I haven't been able to get on my computer so much in the last couple of days.

---

### Post by allinson-ryan on 2014-04-25
The wifi card now works however once the desktop loads either my computer freezes or there is no input from my keyboard or mouse. This happened after running this command: ```
[COLOR=#000000][FONT=Ubuntu Mono]sudo service network-manager restart[/FONT][/COLOR]
``` I'm not sure if it was this part of the code that caused this. Is there anything I can run in  command line before logging into the desktop, for this to be fixed or do I need a fresh install? This is from my laptop. I'm away the weekend so I can't try anything until Sunday.

Thanks

---

### Post by praseodym on 2014-04-25
Did you blacklist the rt2800pci?
```

echo "blacklist rt2800pci" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot and check:
```

iwconfig
lsmod
```

---

### Post by markallinson on 2014-04-25
Hi, I'm Ryans dad. He's away this weekend so I thought I'd try to help him out with this.

I ran the commands above,



mark@Skyblade:~$ iwconfig
ra0       Ralink STA  
          
eth0      no wireless extensions.

lo        no wireless extensions.

mark@Skyblade:~$ lsmod
Module                  Size  Used by
cfg80211              484040  0 
rpcsec_gss_krb5        35573  0 
nfsv4                 465643  0 
rfcomm                 69160  0 
bnep                   19624  2 
bluetooth             395423  10 bnep,rfcomm
snd_hda_codec_hdmi     46207  1 
nfsd                  280297  2 
auth_rpcgss            59338  2 nfsd,rpcsec_gss_krb5
nfs_acl                12837  1 nfsd
nfs                   236636  1 nfsv4
binfmt_misc            17468  1 
lockd                  93977  2 nfs,nfsd
sunrpc                284404  8 nfs,nfsd,rpcsec_gss_krb5,auth_rpcgss,lockd,nfsv4,nfs_acl
fscache                63988  2 nfs,nfsv4
kvm                   451511  0 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
joydev                 17381  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
snd_hda_codec_realtek    61438  1 
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_hda_intel          52355  5 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
serio_raw              13462  0 
snd_hwdep              13602  1 snd_hda_codec
nvidia              10675249  41 
fam15h_power           13119  0 
k10temp                13126  0 
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
edac_core              62291  0 
edac_mce_amd           22617  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
sp5100_tco             13979  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
drm                   302817  2 nvidia
i2c_piix4              22155  0 
snd                    69238  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd
parport_pc             32701  0 
wmi                    19177  0 
ppdev                  17671  0 
mac_hid                13205  0 
rt5592sta            1172345  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
pata_acpi              13038  0 
hid_generic            12548  0 
hid_logitech           26709  0 
ff_memless             13573  1 hid_logitech
usbhid                 52616  0 
hid                   106148  3 hid_generic,hid_logitech,usbhid
ahci                   25819  2 
pata_atiixp            13271  0 
libahci                32168  1 ahci
r8169                  67581  0 
mii                    13934  1 r8169
mark@Skyblade:~$ ^C
mark@Skyblade:~$ iwconfig
ra0       Ralink STA  ESSID:"BlackMesa"  Nickname:"RT2860STA"
          Mode:Managed  Frequency=2.437 GHz  Access Point: AC:22:0B:E8:F4:00   
          Bit Rate=19.5 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=58/100  Signal level:-81 dBm  Noise level:-94 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

lo        no wireless extensions.

mark@Skyblade:~$ lsmod
Module                  Size  Used by
nfsv3                  39326  1 
cfg80211              484040  0 
rpcsec_gss_krb5        35573  0 
nfsv4                 465643  0 
rfcomm                 69160  0 
bnep                   19624  2 
bluetooth             395423  10 bnep,rfcomm
snd_hda_codec_hdmi     46207  1 
nfsd                  280297  2 
auth_rpcgss            59338  2 nfsd,rpcsec_gss_krb5
nfs_acl                12837  2 nfsd,nfsv3
nfs                   236636  3 nfsv3,nfsv4
binfmt_misc            17468  1 
lockd                  93977  3 nfs,nfsd,nfsv3
sunrpc                284404  23 nfs,nfsd,rpcsec_gss_krb5,auth_rpcgss,lockd,nfsv3,nfsv4,nfs_acl
fscache                63988  2 nfs,nfsv4
kvm                   451511  0 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
joydev                 17381  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
snd_hda_codec_realtek    61438  1 
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_hda_intel          52355  5 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
serio_raw              13462  0 
snd_hwdep              13602  1 snd_hda_codec
nvidia              10675249  41 
fam15h_power           13119  0 
k10temp                13126  0 
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
edac_core              62291  0 
edac_mce_amd           22617  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
sp5100_tco             13979  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
drm                   302817  2 nvidia
i2c_piix4              22155  0 
snd                    69238  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd
parport_pc             32701  0 
wmi                    19177  0 
ppdev                  17671  0 
mac_hid                13205  0 
rt5592sta            1172345  1 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
pata_acpi              13038  0 
hid_generic            12548  0 
hid_logitech           26709  0 
ff_memless             13573  1 hid_logitech
usbhid                 52616  0 
hid                   106148  3 hid_generic,hid_logitech,usbhid
ahci                   25819  2 
pata_atiixp            13271  0 
libahci                32168  1 ahci
r8169                  67581  0 
mii                    13934  1 r8169
mark@Skyblade:~$

---

### Post by markallinson on 2014-04-25
I have tried to use the computer, it loads up ok but as soon as I open a web page, it locks up. Chrome does it, just tried Firefox and it does it too. Seemed to be ok until a web browser was opened....

---

### Post by praseodym on 2014-04-25
Try reinstalling the browser and the NM from terminal:
```

sudo apt-get install --reinstall firefox network-manager network-manager-gnome
```

---

### Post by markallinson on 2014-04-26
Hi, just tried the above. It's still the same I'm afraid. The PC runs ok if I disable the WiFi, I can run Firefox or Chrome (but not get online of course). Libre Office all good, edit files etc etc. when I enable WiFi still ok, but as soon as the PC uses the WiFi, ie to load a webpage or look for updates with software updater, the PC freezes.

---

### Post by praseodym on 2014-04-26
Sounds like a VGA problem?! Lets check
```

lspci -nnk | grep -iA2 VGA
lsmod
cat /etc/X11/xorg.conf
```

---

### Post by markallinson on 2014-04-27
Did as requested above, 

mark@Skyblade:~$ lspci -nnk  grep -iA2 VGA
Usage: lspci [<switches>]

Basic display modes:
-mm		Produce machine-readable output (single -m for an obsolete format)
-t		Show bus tree

Display options:
-v		Be verbose (-vv for very verbose)
-k		Show kernel drivers handling each device
-x		Show hex-dump of the standard part of the config space
-xxx		Show hex-dump of the whole config space (dangerous; root only)
-xxxx		Show hex-dump of the 4096-byte extended config space (root only)
-b		Bus-centric view (addresses and IRQ's as seen by the bus)
-D		Always show domain numbers

Resolving of device ID's to names:
-n		Show numeric ID's
-nn		Show both textual and numeric ID's (names & numbers)
-q		Query the PCI ID database for unknown ID's via DNS
-qq		As above, but re-query locally cached entries
-Q		Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]	Show only devices in selected slots
-d [<vendor>]:[<device>]			Show only devices with specified ID's

Other options:
-i <file>	Use specified ID database instead of A2
-p <file>	Look up kernel modules in a given file instead of default modules.pcimap
-M		Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>	Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>	Set PCI access parameter (see `-O help' for a list)
-G		Enable PCI access debugging
-H <mode>	Use direct hardware access (<mode> = 1 or 2)
-F <file>	Read PCI configuration dump from a given file
mark@Skyblade:~$ lsmod
Module                  Size  Used by
nfsv3                  39326  1 
cfg80211              484040  0 
rpcsec_gss_krb5        35573  0 
nfsv4                 465643  0 
bnep                   19624  2 
rfcomm                 69160  0 
bluetooth             395423  10 bnep,rfcomm
snd_hda_codec_hdmi     46207  1 
nvidia              10675249  41 
nfsd                  280297  2 
snd_hda_codec_realtek    61438  1 
auth_rpcgss            59338  2 nfsd,rpcsec_gss_krb5
nfs_acl                12837  2 nfsd,nfsv3
kvm                   451511  0 
snd_hda_intel          52355  5 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
joydev                 17381  0 
nfs                   236636  3 nfsv3,nfsv4
snd_hwdep              13602  1 snd_hda_codec
crct10dif_pclmul       14289  0 
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
lockd                  93977  3 nfs,nfsd,nfsv3
crc32_pclmul           13113  0 
sunrpc                284404  23 nfs,nfsd,rpcsec_gss_krb5,auth_rpcgss,lockd,nfsv3,nfsv4,nfs_acl
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
ghash_clmulni_intel    13259  0 
binfmt_misc            17468  1 
snd_seq_midi           13324  0 
aesni_intel            55624  0 
fscache                63988  2 nfs,nfsv4
snd_seq_midi_event     14899  1 snd_seq_midi
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
snd_rawmidi            30144  1 snd_seq_midi
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
ablk_helper            13597  1 aesni_intel
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_timer              29482  2 snd_pcm,snd_seq
rt5592sta            1172345  0 
serio_raw              13462  0 
edac_core              62291  0 
snd                    69238  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
fam15h_power           13119  0 
edac_mce_amd           22617  0 
k10temp                13126  0 
soundcore              12680  1 snd
sp5100_tco             13979  0 
drm                   302817  2 nvidia
i2c_piix4              22155  0 
wmi                    19177  0 
mac_hid                13205  0 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
pata_acpi              13038  0 
hid_generic            12548  0 
hid_logitech           26709  0 
ff_memless             13573  1 hid_logitech
usbhid                 52616  0 
hid                   106148  3 hid_generic,hid_logitech,usbhid
pata_atiixp            13271  0 
ahci                   25819  2 
r8169                  67581  0 
libahci                32168  1 ahci
mii                    13934  1 r8169
mark@Skyblade:~$ cat /etc/X11/xorg.conf
cat: /etc/X11/xorg.conf: No such file or directory
mark@Skyblade:~$

---

### Post by praseodym on 2014-04-27
```
lspci -nnk | grep -iA2 VGA
```
This is one line, you better copy/paste it. The "pipe" | is necessary, alternatively, show
```

lspci -nnk

```
completely.

---

### Post by markallinson on 2014-04-27
Oops, missed the pipe.... Try again,

mark@Skyblade:~$ lspci -nnk | grep -iA2 VGA
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK107 [GeForce GT 640] [10de:0fc1] (rev a1)
	Subsystem: Gigabyte Technology Co., Ltd Device [1458:353e]
	Kernel driver in use: nvidia
mark@Skyblade:~$ lsmod
Module                  Size  Used by
nfsv3                  39326  1 
cfg80211              484040  0 
rpcsec_gss_krb5        35573  0 
nfsv4                 465643  0 
rfcomm                 69160  0 
bnep                   19624  2 
bluetooth             395423  10 bnep,rfcomm
binfmt_misc            17468  1 
nfsd                  280297  2 
auth_rpcgss            59338  2 nfsd,rpcsec_gss_krb5
nfs_acl                12837  2 nfsd,nfsv3
nfs                   236636  3 nfsv3,nfsv4
lockd                  93977  3 nfs,nfsd,nfsv3
sunrpc                284404  23 nfs,nfsd,rpcsec_gss_krb5,auth_rpcgss,lockd,nfsv3,nfsv4,nfs_acl
fscache                63988  2 nfs,nfsv4
snd_hda_codec_hdmi     46207  1 
kvm                   451511  0 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
serio_raw              13462  0 
k10temp                13126  0 
fam15h_power           13119  0 
snd_hda_codec_realtek    61438  1 
edac_core              62291  0 
edac_mce_amd           22617  0 
snd_hda_intel          52355  5 
sp5100_tco             13979  0 
i2c_piix4              22155  0 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
joydev                 17381  0 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
rt5592sta            1172345  0 
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
parport_pc             32701  0 
nvidia              10675249  41 
snd                    69238  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
ppdev                  17671  0 
soundcore              12680  1 snd
mac_hid                13205  0 
wmi                    19177  0 
drm                   302817  2 nvidia
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
pata_acpi              13038  0 
hid_generic            12548  0 
hid_logitech           26709  0 
ff_memless             13573  1 hid_logitech
usbhid                 52616  0 
hid                   106148  3 hid_generic,hid_logitech,usbhid
ahci                   25819  2 
r8169                  67581  0 
pata_atiixp            13271  0 
libahci                32168  1 ahci
mii                    13934  1 r8169
mark@Skyblade:~$ cat /etc/X11/xorg.conf
cat: /etc/X11/xorg.conf: No such file or directory
mark@Skyblade:~$

---

### Post by praseodym on 2014-04-27
So, lets create a xorg.conf file:

Change with CTRL+ALT+F1 to the first console, login there and run:
```

sudo service lightdm stop
sudo nvidia-xconfig --composite
sudo service lightdm start
```
Check:
```

modinfo nvidia
cat /etc/X11/xorg.conf
```

---

### Post by markallinson on 2014-04-27
OK, just tried that,

mark@Skyblade:~$ modinfo nvidia
modinfo: ERROR: Module nvidia not found.
mark@Skyblade:~$ cat /etc/X11/xorg.conf
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 331.38  (buildmeister@swio-display-x64-rhel04-15)  Wed Jan  8 19:53:14 PST 2014

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

mark@Skyblade:~$

---

### Post by cj2008 on 2014-05-18
Did you manage to fix this in the end?

Just built a brand new machine, loaded 14.04 on and tried to set up wifi using my PCE-N53 network card.

I immediately ran into exactly the problem reported here - the card can see and connect to a network, but then as soon as you try to connect to the internet everything simply freezes up. What's worse is that this patch appears to be doing something strange to ALL connectivity; I can't even plug an Ethernet cable in as that doesn't connect either. :-(

Can anybody help either with instructions on how to back this patch out so that I can at least get wired connectivity back, and/or ideas what might be going wrong here?

---

### Post by cj2008 on 2014-05-18
I don't know if this helps or is related in any way (but given that this is a completely clean install and this is the first "job" I've tackled, it's too coincidental to ignore...)

Just had an Ubuntu crash report flash up (abridged details below):

ExecutablePath:  /usr/bin/compiz
Title: compix crashed with SIGSEGV in FT_Load_Glyph()
SegvReason: writing NULL VMA
UnreportableReason: 
You have some obsolete package versions installed. Please upgrade [...]
compiz, compiz-core, compiz-gnome, compiz-plugins-default, libcompizconfig0, libdecoration0

---

### Post by chili555 on 2014-05-20
> **cj2008 said:**
> I don't know if this helps or is related in any way (but given that this is a completely clean install and this is the first "job" I've tackled, it's too coincidental to ignore...)

Just had an Ubuntu crash report flash up (abridged details below):

ExecutablePath:  /usr/bin/compiz
Title: compix crashed with SIGSEGV in FT_Load_Glyph()
SegvReason: writing NULL VMA
UnreportableReason: 
You have some obsolete package versions installed. Please upgrade [...]
compiz, compiz-core, compiz-gnome, compiz-plugins-default, libcompizconfig0, libdecoration0It is certainly worth solving, however, it shows no signs to me of being in any way related to your wireless driver.

---

### Post by WinEunuchs2Unix on 2014-06-09
There are years of discussion on the RT2x000lib / RT2800 driver issue.  This thread: [https://dev.openwrt.org/ticket/13523](https://dev.openwrt.org/ticket/13523) has programmers discussing various ways of correcting it.  At the bottom of the thread are two lines of code to swap out of the module and two lines to swap in.  Basically the fix moves the messages out of the dmesg output and back into some debug area where it used to be a long time ago.  The debug area was something I gleamed from an entirely different thread I read in Ubuntu I think and may be subject to a better description.

--- EDIT Below -----

OK the above was to answer the annoying message appearing in dmesg which brought me to this thread:
   "ieee80211 phy1: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping"

However upon reading more of the thread I see I was directed here via too much google of the message details and not enough of the header.  I tried to delete the message quickly but no delete key ](*,)

---

### Post by Dmitry_T on 2014-06-14
Hi!

I have the same freeze problem with my PCE N53 with 14.04. I used the drivers patched by rt5592sta_fix_64bit_3.8.patch for 13.04, but they stopped compiling for the new version, so I applied DPO_GPL_RT5592STAQ_LinuxSTA_v2.6.0.0_20120326_patched.tar.gz as recommended here, and the device started connecting to the hotspot only to freeze momentarily.

Has anyone overcome this yet?

---

### Post by atisou on 2014-08-19
Hello,

We are 19th August, and I have exactly the same problem with my PCE-N53 card and Ubuntu 14.04 (freshly built computer). Is there anybody out there who managed to make the PCE-N53 work with Ubuntu 14.04 (kernel 3.13.0-generic or any kernel > 2.6)???
Which wi-fi card (PCI, not USB please since I'm limited with my mb usb connections for now) 100% compatible with Ubuntu 14.04 (kernel 3.13.0-generic) is recommended if there is no hope for PCE-N53?
Thanks.

---

### Post by praseodym on 2014-08-19
[http://ubuntuforums.org/showthread.php?t=2217996&page=2&p=12997915#post12997915](http://ubuntuforums.org/showthread.php?t=2217996&page=2&p=12997915#post12997915)

Have you tried it?

---

### Post by pcvonz on 2014-08-22
> **chili555 said:**
> It is certainly worth solving, however, it shows no signs to me of being in any way related to your wireless driver.

I think you should reconsider that thought, my computer also froze a couple seconds after connecting to the wireless after installing that patch. I'm pretty bummed since I can't return this card :(

---

### Post by chili555 on 2014-08-22
> **pcvonz said:**
> I think you should reconsider that thought, my computer also froze a couple seconds after connecting to the wireless after installing that patch. I'm pretty bummed since I can't return this card :(OK, I just reconsidered it and I still don't think the previously reported crash has the slightest to do with wireless:> ExecutablePath: /usr/bin/[COLOR="#FF0000"]compiz[/COLOR]
Title: compix crashed with SIGSEGV in FT_Load_Glyph()
SegvReason: writing NULL VMA
UnreportableReason: 
[COLOR="#FF0000"]You have some obsolete package versions installed. Please upgrade [...]
compiz, compiz-core, compiz-gnome, compiz-plugins-default, libcompizconfig0, libdecoration0[/COLOR]If yours is different, please post the details which you may find in /var/log/syslog.

At this moment, I know of no reliable way to get the 1814:5592 device going in later kernels such as 3.13.0-xx used in Ubuntu 14.04. I have googled some information that it was to be included in rt2800pci, but, as of 3.16.1, it isn't there yet.

I wish I had better news.

---

### Post by pcvonz on 2014-08-23
Here is what /var/log/syslog had:

```
Aug 23 18:44:37 paul-minty udisksd[1778]: mounted-fs entry {'', @a{sv} {}} is invalid: no block-device key/value pair
Aug 23 18:44:37 paul-minty udisksd[1778]: Cleaning up mount point  (device 0:0 no longer exist)
Aug 23 18:44:37 paul-minty kernel: [   40.909006] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 420
Aug 23 18:44:37 paul-minty NetworkManager[1047]: <info> (ra0): supplicant interface state: scanning -> inactive
Aug 23 18:44:39 paul-minty kernel: [   42.891059] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 614
Aug 23 18:44:40 paul-minty dbus[706]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
Aug 23 18:44:40 paul-minty colord: Using config file /etc/colord.conf
Aug 23 18:44:40 paul-minty colord: Using mapping database file /var/lib/colord/mapping.db
Aug 23 18:44:40 paul-minty colord: Using device database file /var/lib/colord/storage.db
Aug 23 18:44:40 paul-minty colord: plugin /usr/lib/x86_64-linux-gnu/colord-plugins/libcd_plugin_sane.so not loaded: plugin refused to load
Aug 23 18:44:40 paul-minty colord: loaded plugin libcd_plugin_camera.so
Aug 23 18:44:40 paul-minty colord: loaded plugin libcd_plugin_scanner.so
Aug 23 18:44:40 paul-minty colord: Daemon ready for requests
Aug 23 18:44:40 paul-minty dbus[706]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Aug 23 18:44:40 paul-minty colord: Profile added: icc-93aeab1e18c3195a8c5474d8c43a0792
Aug 23 18:44:40 paul-minty colord: Profile added: icc-14c5ddbb0abd000deb198c68bb185dc3
Aug 23 18:44:40 paul-minty colord: Profile added: icc-e729b445abc89051fe8ba7c6d8e9b127
Aug 23 18:44:40 paul-minty colord: Profile added: icc-781f6f71344167d3526631689139f109
Aug 23 18:44:40 paul-minty colord: Profile added: icc-7fb30d688bf82d32a0e748daf3dba95d
Aug 23 18:44:40 paul-minty colord: Profile added: icc-ea421e3a65cfa796e2732ce36086e327
Aug 23 18:44:40 paul-minty colord: Profile added: icc-526fbc9bdf0d7156c553998d47a3b5fc
Aug 23 18:44:40 paul-minty colord: Profile added: icc-df7c0067b1eb9bcc9fc9b33bc3a797eb
Aug 23 18:44:40 paul-minty colord: Profile added: icc-353a6bcabda00f04b6988f89126ce6f5
Aug 23 18:44:40 paul-minty colord: Profile added: icc-a10be98be58460669fcdc6946939b7cf
Aug 23 18:44:40 paul-minty colord: Profile added: icc-3bd2261b1125a0fd9ebf827a2d1bed84
Aug 23 18:44:40 paul-minty colord: Profile added: icc-57f0d896250f6f98f77ca1b0d19019c0
Aug 23 18:44:40 paul-minty colord: Profile added: icc-2f1f11ecd613fe5551420fcaf5b11ff8
Aug 23 18:44:40 paul-minty colord: Profile added: icc-d6490883a866e4059370e1de1d840283
Aug 23 18:44:40 paul-minty colord: Profile added: icc-3a34aa6c3d1fb1ef63ff41e04ee00979
Aug 23 18:44:40 paul-minty colord: Profile added: icc-d4a7a2bd8ddaacf10e275e3db31d72b8
Aug 23 18:44:40 paul-minty colord: Profile added: icc-0383c34650771ce95ef93fe916867725
Aug 23 18:44:40 paul-minty colord: Profile added: icc-6a245ab2d8892e2e56232af93cd48b81
Aug 23 18:44:40 paul-minty colord: Profile added: icc-fb0ac62618f016ed9b92ce239258efa8
Aug 23 18:44:40 paul-minty colord: Profile added: icc-6ad6d63767ce0393245528ada92f1cb2
Aug 23 18:44:40 paul-minty colord: Profile added: icc-c227f46f246694ba9971f270cb61a0c1
Aug 23 18:44:40 paul-minty colord: Profile added: icc-72f5b1cba915b68ea75cc843e270df5a
Aug 23 18:44:40 paul-minty colord: Profile added: icc-523e494bc2f53c53d51d0758b07f4879
Aug 23 18:44:40 paul-minty colord: Profile added: icc-b0701c2ccf059287d0b067464df8bda9
Aug 23 18:44:40 paul-minty colord: Profile added: icc-f64a1f19ce07290b35a752b00217b684
Aug 23 18:44:40 paul-minty colord: Profile added: icc-0720e7cdbc792b77c0740c39f325ef9e
Aug 23 18:44:40 paul-minty colord: Profile added: icc-c3e6382fa9b2d31b01b736f6f97aac3a
Aug 23 18:44:40 paul-minty colord: Profile added: icc-a1d13bd5309e0f06ceda6f0d75367823
Aug 23 18:44:40 paul-minty colord: Profile added: icc-654b99c87e67edb1c1cfb0dcb7fa9d04
Aug 23 18:44:40 paul-minty colord: Profile added: icc-c90203802db7875c010cf0875c3ecac1
Aug 23 18:44:40 paul-minty colord: Profile added: icc-186b88621ed8da652865e3e84836f85b
Aug 23 18:44:40 paul-minty colord: Profile added: icc-1a00a956a836388ae20968e84f57d211
Aug 23 18:44:40 paul-minty colord: Profile added: icc-07000710072007300740075007600770
Aug 23 18:44:40 paul-minty colord: Profile added: icc-7cfad1a392b1ed7aaf7bd4cb60faaae4
Aug 23 18:44:40 paul-minty colord: Profile added: icc-d0f2748c6e21eee954827c71e1e81c12
Aug 23 18:44:40 paul-minty colord: Profile added: icc-10080b14e236a5c33088e1d3404db83c
Aug 23 18:44:40 paul-minty colord: Profile added: icc-79e56e42bf930a269bb6a0421eb80753
Aug 23 18:44:40 paul-minty colord: Profile added: icc-b0ddeb99aea00b3e6527017fe5b73803
Aug 23 18:44:40 paul-minty colord: Profile added: icc-a71f743c68b0bf74d37a601835ca05cf
Aug 23 18:44:40 paul-minty colord: Profile added: icc-296f10aadb0eba217aa824dc712c8a07
Aug 23 18:44:40 paul-minty colord: Profile added: icc-40e2a2d10e23e2777853990e7c80dbd6
Aug 23 18:44:40 paul-minty colord: Profile added: icc-a392a74919c54455cf25f7400b2319ac
Aug 23 18:44:40 paul-minty colord: Profile added: icc-f3e0aad931efae878c9eba9125dc758f
Aug 23 18:44:41 paul-minty colord: Profile added: icc-aaafa3414484eb7d6a63b27b9d77223c
Aug 23 18:44:41 paul-minty colord: Profile added: icc-71190e50549b40fd8fd2c1b6d407f0a9
Aug 23 18:44:41 paul-minty colord: Profile added: icc-983c94c0717adbe432182cb7732e986c
Aug 23 18:44:41 paul-minty colord: Device added: xrandr-DELL 1908FP-FP18281QGDRJ
Aug 23 18:44:41 paul-minty colord: Device added: xrandr-HD2201-M2J8B70R0222
Aug 23 18:44:41 paul-minty dbus[706]: [system] Activating service name='org.kde.powerdevil.backlighthelper' (using servicehelper)
Aug 23 18:44:41 paul-minty org.kde.powerdevil.backlighthelper: QDBusConnection: system D-Bus connection created before QCoreApplication. Application may misbehave.
Aug 23 18:44:41 paul-minty dbus[706]: [system] Successfully activated service 'org.kde.powerdevil.backlighthelper'
Aug 23 18:44:41 paul-minty NetworkManager[1047]: <info> (eth0): IP6 addrconf timed out or failed.
Aug 23 18:44:41 paul-minty NetworkManager[1047]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Aug 23 18:44:41 paul-minty NetworkManager[1047]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Aug 23 18:44:41 paul-minty NetworkManager[1047]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Aug 23 18:44:41 paul-minty dbus[706]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Aug 23 18:44:42 paul-minty dbus[706]: [system] Successfully activated service 'org.freedesktop.systemd1'
Aug 23 18:44:42 paul-minty kernel: [   45.821894] audit_printk_skb: 132 callbacks suppressed
Aug 23 18:44:42 paul-minty kernel: [   45.821898] type=1400 audit(1408844682.582:56): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1877 comm="apparmor_parser"
Aug 23 18:44:42 paul-minty kernel: [   45.821904] type=1400 audit(1408844682.582:57): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1877 comm="apparmor_parser"
Aug 23 18:44:42 paul-minty kernel: [   45.822313] type=1400 audit(1408844682.586:58): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1877 comm="apparmor_parser"
Aug 23 18:44:42 paul-minty dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15 (xid=0x39a245c2)
Aug 23 18:44:44 paul-minty NetworkManager[1047]: <info> Auto-activating connection 'BEEF_STROKINOFF'.
Aug 23 18:44:44 paul-minty NetworkManager[1047]: <info> Activation (ra0) starting connection 'BEEF_STROKINOFF'
Aug 23 18:44:44 paul-minty NetworkManager[1047]: <info> (ra0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Aug 23 18:44:44 paul-minty NetworkManager[1047]: <info> Activation (ra0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 23 18:44:44 paul-minty NetworkManager[1047]: <info> Activation (ra0) Stage 1 of 5 (Device Prepare) started...
Aug 23 18:44:44 paul-minty NetworkManager[1047]: <info> Activation (ra0) Stage 2 of 5 (Device Configure) scheduled...
Aug 23 18:44:44 paul-minty NetworkManager[1047]: <info> Activation (ra0) Stage 1 of 5 (Device Prepare) complete.
Aug 23 18:44:44 paul-minty NetworkManager[1047]: <info> Activation (ra0) Stage 2 of 5 (Device Configure) starting...
Aug 23 18:44:44 paul-minty NetworkManager[1047]: <info> (ra0): device state change: prepare -> config (reason 'none') [40 50 0]
Aug 23 18:44:44 paul-minty NetworkManager[1047]: <info> Activation (ra0/wireless): access point 'BEEF_STROKINOFF' has security, but secrets are required.
Aug 23 18:44:44 paul-minty NetworkManager[1047]: <info> (ra0): device state change: config -> need-auth (reason 'none') [50 60 0]
Aug 23 18:44:44 paul-minty NetworkManager[1047]: <info> Activation (ra0) Stage 2 of 5 (Device Configure) complete.
Aug 23 18:44:45 paul-minty NetworkManager[1047]: get_secret_flags: assertion 'is_secret_prop (setting, secret_name, error)' failed
Aug 23 18:44:45 paul-minty NetworkManager[1047]: <info> Activation (ra0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 23 18:44:45 paul-minty NetworkManager[1047]: <info> Activation (ra0) Stage 1 of 5 (Device Prepare) started...
Aug 23 18:44:45 paul-minty NetworkManager[1047]: <info> (ra0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Aug 23 18:44:45 paul-minty NetworkManager[1047]: <info> Activation (ra0) Stage 2 of 5 (Device Configure) scheduled...
Aug 23 18:44:45 paul-minty NetworkManager[1047]: <info> Activation (ra0) Stage 1 of 5 (Device Prepare) complete.
Aug 23 18:44:45 paul-minty NetworkManager[1047]: <info> Activation (ra0) Stage 2 of 5 (Device Configure) starting...
Aug 23 18:44:45 paul-minty NetworkManager[1047]: <info> (ra0): device state change: prepare -> config (reason 'none') [40 50 0]
Aug 23 18:44:45 paul-minty NetworkManager[1047]: <info> Activation (ra0/wireless): connection 'BEEF_STROKINOFF' has security, and secrets exist.  No new secrets needed.
Aug 23 18:44:45 paul-minty NetworkManager[1047]: <info> Config: added 'ssid' value 'BEEF_STROKINOFF'
Aug 23 18:44:45 paul-minty NetworkManager[1047]: <info> Config: added 'scan_ssid' value '1'
Aug 23 18:44:45 paul-minty NetworkManager[1047]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Aug 23 18:44:45 paul-minty NetworkManager[1047]: <info> Config: added 'auth_alg' value 'OPEN'
Aug 23 18:44:45 paul-minty NetworkManager[1047]: <info> Config: added 'psk' value '<omitted>'
Aug 23 18:44:45 paul-minty NetworkManager[1047]: <info> Activation (ra0) Stage 2 of 5 (Device Configure) complete.
Aug 23 18:44:45 paul-minty NetworkManager[1047]: <info> Config: set interface ap_scan to 1
Aug 23 18:44:45 paul-minty NetworkManager[1047]: <info> (ra0): supplicant interface state: inactive -> scanning
Aug 23 18:44:38 paul-minty wpa_supplicant[1155]: ra0: Reject scan trigger since one is already pending
Aug 23 18:44:47 paul-minty wpa_supplicant[1155]: ra0: Trying to associate with 00:1d:0f:d2:88:64 (SSID='BEEF_STROKINOFF' freq=2412 MHz)
Aug 23 18:44:47 paul-minty kernel: [   50.603474] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 808
Aug 23 18:44:47 paul-minty kernel: [   50.603717] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=1)
Aug 23 18:44:47 paul-minty wpa_supplicant[1155]: ra0: Association request to the driver failed
Aug 23 18:44:47 paul-minty NetworkManager[1047]: <info> (ra0): supplicant interface state: scanning -> associating
Aug 23 18:44:47 paul-minty wpa_supplicant[1155]: ra0: Associated with 00:1d:0f:d2:88:64
Aug 23 18:44:47 paul-minty NetworkManager[1047]: <info> (ra0): supplicant interface state: associating -> 4-way handshake
Aug 23 18:44:47 paul-minty wpa_supplicant[1155]: ra0: WPA: Key negotiation completed with 00:1d:0f:d2:88:64 [PTK=CCMP GTK=CCMP]
Aug 23 18:44:47 paul-minty wpa_supplicant[1155]: ra0: CTRL-EVENT-CONNECTED - Connection to 00:1d:0f:d2:88:64 completed [id=0 id_str=]
Aug 23 18:44:47 paul-minty NetworkManager[1047]: <info> (ra0): supplicant interface state: 4-way handshake -> completed
Aug 23 18:44:47 paul-minty NetworkManager[1047]: <info> Activation (ra0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'BEEF_STROKINOFF'.
Aug 23 18:44:47 paul-minty NetworkManager[1047]: <info> Activation (ra0) Stage 3 of 5 (IP Configure Start) scheduled.
Aug 23 18:44:47 paul-minty NetworkManager[1047]: <info> Activation (ra0) Stage 3 of 5 (IP Configure Start) started...
Aug 23 18:44:47 paul-minty NetworkManager[1047]: <info> (ra0): device state change: config -> ip-config (reason 'none') [50 70 0]
Aug 23 18:44:47 paul-minty NetworkManager[1047]: <info> Activation (ra0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Aug 23 18:44:47 paul-minty NetworkManager[1047]: <info> dhclient started with pid 1905
Aug 23 18:44:47 paul-minty NetworkManager[1047]: <info> Activation (ra0) Beginning IP6 addrconf.
Aug 23 18:44:47 paul-minty NetworkManager[1047]: <info> Activation (ra0) Stage 3 of 5 (IP Configure Start) complete.
Aug 23 18:44:47 paul-minty avahi-daemon[803]: Withdrawing address record for fe80::da50:e6ff:fef4:ba81 on ra0.
Aug 23 18:44:47 paul-minty avahi-daemon[803]: Leaving mDNS multicast group on interface ra0.IPv6 with address fe80::da50:e6ff:fef4:ba81.
Aug 23 18:44:47 paul-minty avahi-daemon[803]: Interface ra0.IPv6 no longer relevant for mDNS.
Aug 23 18:44:47 paul-minty dhclient: Internet Systems Consortium DHCP Client 4.2.4
Aug 23 18:44:47 paul-minty dhclient: Copyright 2004-2012 Internet Systems Consortium.
Aug 23 18:44:47 paul-minty dhclient: All rights reserved.
Aug 23 18:44:47 paul-minty dhclient: For info, please visit https://www.isc.org/software/dhcp/
Aug 23 18:44:47 paul-minty dhclient: 
Aug 23 18:44:47 paul-minty NetworkManager[1047]: <info> (ra0): DHCPv4 state changed nbi -> preinit
Aug 23 18:44:47 paul-minty kernel: [   51.133001] RTMP_TimerListAdd: add timer obj ffffc900112b4da0!
Aug 23 18:44:47 paul-minty dhclient: Listening on LPF/ra0/d8:50:e6:f4:ba:81
Aug 23 18:44:47 paul-minty dhclient: Sending on   LPF/ra0/d8:50:e6:f4:ba:81
Aug 23 18:44:47 paul-minty dhclient: Sending on   Socket/fallback
Aug 23 18:44:47 paul-minty dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 3 (xid=0x5ce603d2)
Aug 23 18:44:47 paul-minty dhclient: DHCPREQUEST of 192.168.1.217 on ra0 to 255.255.255.255 port 67 (xid=0x5ce603d2)
Aug 23 18:44:47 paul-minty dhclient: DHCPOFFER of 192.168.1.217 from 192.168.1.1
Aug 23 18:44:47 paul-minty dhclient: DHCPACK of 192.168.1.217 from 192.168.1.1
Aug 23 18:44:47 paul-minty dhclient: bound to 192.168.1.217 -- renewal in 17747 seconds.
Aug 23 18:44:47 paul-minty NetworkManager[1047]: <info> (ra0): DHCPv4 state changed preinit -> bound
Aug 23 18:44:47 paul-minty NetworkManager[1047]: <info>   address 192.168.1.217
Aug 23 18:44:47 paul-minty NetworkManager[1047]: <info>   prefix 24 (255.255.255.0)
Aug 23 18:44:47 paul-minty NetworkManager[1047]: <info>   gateway 192.168.1.1
Aug 23 18:44:47 paul-minty NetworkManager[1047]: <info>   hostname 'paul-minty'
Aug 23 18:44:47 paul-minty NetworkManager[1047]: <info>   nameserver '192.168.1.1'
Aug 23 18:44:47 paul-minty NetworkManager[1047]: <info>   domain name 'lan'
Aug 23 18:44:47 paul-minty NetworkManager[1047]: <info> Activation (ra0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Aug 23 18:44:47 paul-minty NetworkManager[1047]: <info> Activation (ra0) Stage 5 of 5 (IPv4 Commit) started...
Aug 23 18:44:47 paul-minty avahi-daemon[803]: Joining mDNS multicast group on interface ra0.IPv4 with address 192.168.1.217.
Aug 23 18:44:47 paul-minty avahi-daemon[803]: New relevant interface ra0.IPv4 for mDNS.
Aug 23 18:44:47 paul-minty avahi-daemon[803]: Registering new address record for 192.168.1.217 on ra0.IPv4.
Aug 23 18:44:47 paul-minty kernel: [   51.188881] RTMP_TimerListAdd: add timer obj ffffc900112b4e28!
Aug 23 18:44:48 paul-minty NetworkManager[1047]: <info> (ra0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Aug 23 18:44:48 paul-minty NetworkManager[1047]: <info> Activation (ra0) Stage 5 of 5 (IPv4 Commit) complete.
Aug 23 18:44:48 paul-minty NetworkManager[1047]: <info> (ra0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Aug 23 18:44:48 paul-minty NetworkManager[1047]: <info> NetworkManager state is now CONNECTED_GLOBAL
Aug 23 18:44:48 paul-minty NetworkManager[1047]: <info> Policy set 'BEEF_STROKINOFF' (ra0) as default for IPv4 routing and DNS.
Aug 23 18:44:48 paul-minty NetworkManager[1047]: <info> DNS: starting dnsmasq...
Aug 23 18:44:49 paul-minty NetworkManager[1047]: <warn> dnsmasq not available on the bus, can't update servers.
Aug 23 18:44:49 paul-minty NetworkManager[1047]: <error> [1408844689.16875] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Aug 23 18:44:49 paul-minty NetworkManager[1047]: <warn> DNS: plugin dnsmasq update failed
Aug 23 18:44:49 paul-minty NetworkManager[1047]: <info> Writing DNS information to /sbin/resolvconf
Aug 23 18:44:49 paul-minty dnsmasq[1909]: started, version 2.68 cache disabled
Aug 23 18:44:49 paul-minty dnsmasq[1909]: compile time options: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack ipset auth
Aug 23 18:44:49 paul-minty dnsmasq[1909]: DBus support enabled: connected to system bus
Aug 23 18:44:49 paul-minty dnsmasq[1909]: warning: no upstream servers configured
Aug 23 18:44:49 paul-minty kernel: [   52.524915] Rcv Wcid(1) AddBAReq
Aug 23 18:44:49 paul-minty kernel: [   52.524924] Start Seq = 00000003
Aug 23 18:44:49 paul-minty kernel: [   52.524927] RTMP_TimerListAdd: add timer obj ffffc900112b91c0!
Aug 23 18:44:49 paul-minty NetworkManager[1047]: <info> Activation (ra0) successful, device activated.
Aug 23 18:44:49 paul-minty NetworkManager[1047]: <warn> dnsmasq appeared on DBus: :1.44
Aug 23 18:44:49 paul-minty dbus[706]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Aug 23 18:44:49 paul-minty NetworkManager[1047]: <info> Writing DNS information to /sbin/resolvconf
Aug 23 18:44:49 paul-minty dnsmasq[1909]: setting upstream servers from DBus
Aug 23 18:44:49 paul-minty dnsmasq[1909]: using nameserver 192.168.1.1#53
Aug 23 18:44:49 paul-minty dbus[706]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Aug 23 18:44:49 paul-minty avahi-daemon[803]: Joining mDNS multicast group on interface ra0.IPv6 with address fe80::da50:e6ff:fef4:ba81.
Aug 23 18:44:49 paul-minty avahi-daemon[803]: New relevant interface ra0.IPv6 for mDNS.
Aug 23 18:44:49 paul-minty avahi-daemon[803]: Registering new address record for fe80::da50:e6ff:fef4:ba81 on ra0.*.
Aug 23 18:44:49 paul-minty kernel: [   52.844160] RTMP_TimerListAdd: add timer obj ffffc900112b4eb0!
Aug 23 18:44:49 paul-minty kernel: [   52.848385] Rcv Wcid(1) AddBAReq
Aug 23 18:44:49 paul-minty kernel: [   52.848392] Start Seq = 00000001
Aug 23 18:44:49 paul-minty kernel: [   52.848394] RTMP_TimerListAdd: add timer obj ffffc900112b9270!
Aug 23 18:44:49 paul-minty whoopsie[1086]: message repeated 2 times: [ offline]
Aug 23 18:44:49 paul-minty whoopsie[1086]: online
Aug 23 18:44:52 paul-minty dbus[706]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Aug 23 18:44:52 paul-minty dbus[706]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Aug 23 18:44:52 paul-minty rtkit-daemon[2089]: Successfully called chroot.
Aug 23 18:44:52 paul-minty rtkit-daemon[2089]: Successfully dropped privileges.
Aug 23 18:44:52 paul-minty rtkit-daemon[2089]: Successfully limited resources.
Aug 23 18:44:52 paul-minty rtkit-daemon[2089]: Running.
Aug 23 18:44:52 paul-minty rtkit-daemon[2089]: Watchdog thread running.
Aug 23 18:44:52 paul-minty rtkit-daemon[2089]: Canary thread running.
Aug 23 18:44:52 paul-minty rtkit-daemon[2089]: Successfully made thread 2087 of process 2087 (n/a) owned by '1000' high priority at nice level -11.
Aug 23 18:44:52 paul-minty rtkit-daemon[2089]: Supervising 1 threads of 1 processes of 1 users.
Aug 23 18:44:53 paul-minty rtkit-daemon[2089]: Successfully made thread 2100 of process 2087 (n/a) owned by '1000' RT at priority 5.
Aug 23 18:44:53 paul-minty rtkit-daemon[2089]: Supervising 2 threads of 1 processes of 1 users.
Aug 23 18:44:53 paul-minty rtkit-daemon[2089]: Successfully made thread 2101 of process 2087 (n/a) owned by '1000' RT at priority 5.
Aug 23 18:44:53 paul-minty rtkit-daemon[2089]: Supervising 3 threads of 1 processes of 1 users.
Aug 23 18:44:54 paul-minty rtkit-daemon[2089]: Successfully made thread 2107 of process 2087 (n/a) owned by '1000' RT at priority 5.
Aug 23 18:44:54 paul-minty rtkit-daemon[2089]: Supervising 4 threads of 1 processes of 1 users.
Aug 23 18:44:54 paul-minty rtkit-daemon[2089]: Successfully made thread 2108 of process 2087 (n/a) owned by '1000' RT at priority 5.
Aug 23 18:44:54 paul-minty rtkit-daemon[2089]: Supervising 5 threads of 1 processes of 1 users.
Aug 23 18:44:59 paul-minty ntpdate[2046]: step time server 91.189.94.4 offset 3.436935 sec
Aug 23 18:45:01 paul-minty dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9 (xid=0x39a245c2)
Aug 23 18:45:07 paul-minty kernel: [   67.527598] Rcv Wcid(1) AddBAReq
Aug 23 18:45:07 paul-minty kernel: [   67.527606] Start Seq = 0000000e
Aug 23 18:45:08 paul-minty kernel: [   68.278133] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 808
Aug 23 18:45:10 paul-minty NetworkManager[1047]: <warn> (eth0): DHCPv4 request timed out.
Aug 23 18:45:10 paul-minty NetworkManager[1047]: <info> (eth0): canceled DHCP transaction, DHCP client pid 1163
Aug 23 18:45:10 paul-minty NetworkManager[1047]: <info> Activation (eth0) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Aug 23 18:45:10 paul-minty NetworkManager[1047]: <info> Activation (eth0) Stage 4 of 5 (IPv4 Configure Timeout) started...
Aug 23 18:45:10 paul-minty NetworkManager[1047]: <info> (eth0): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Aug 23 18:45:10 paul-minty NetworkManager[1047]: <warn> Activation (eth0) failed for connection 'Wired connection 1'
Aug 23 18:45:10 paul-minty NetworkManager[1047]: <info> Activation (eth0) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Aug 23 18:45:10 paul-minty NetworkManager[1047]: <info> (eth0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Aug 23 18:45:10 paul-minty NetworkManager[1047]: <info> (eth0): deactivating device (reason 'none') [0]
Aug 23 18:45:10 paul-minty avahi-daemon[803]: Withdrawing address record for fe80::62a4:4cff:feae:4e22 on eth0.
Aug 23 18:45:10 paul-minty avahi-daemon[803]: Leaving mDNS multicast group on interface eth0.IPv6 with address fe80::62a4:4cff:feae:4e22.
Aug 23 18:45:10 paul-minty avahi-daemon[803]: Interface eth0.IPv6 no longer relevant for mDNS.
Aug 23 18:45:11 paul-minty NetworkManager[1047]: <info> (ra0): IP6 addrconf timed out or failed.
Aug 23 18:45:11 paul-minty NetworkManager[1047]: <info> Activation (ra0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Aug 23 18:45:11 paul-minty NetworkManager[1047]: <info> Activation (ra0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Aug 23 18:45:11 paul-minty NetworkManager[1047]: <info> Activation (ra0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Aug 23 18:45:12 paul-minty avahi-daemon[803]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::62a4:4cff:feae:4e22.
Aug 23 18:45:12 paul-minty avahi-daemon[803]: New relevant interface eth0.IPv6 for mDNS.
Aug 23 18:45:12 paul-minty avahi-daemon[803]: Registering new address record for fe80::62a4:4cff:feae:4e22 on eth0.*.
Aug 23 18:45:13 paul-minty NetworkManager[1047]: <info> Auto-activating connection 'Wired connection 1'.
Aug 23 18:45:13 paul-minty NetworkManager[1047]: <info> Activation (eth0) starting connection 'Wired connection 1'
Aug 23 18:45:13 paul-minty NetworkManager[1047]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Aug 23 18:45:13 paul-minty NetworkManager[1047]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 23 18:45:13 paul-minty NetworkManager[1047]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Aug 23 18:45:13 paul-minty NetworkManager[1047]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Aug 23 18:45:13 paul-minty NetworkManager[1047]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Aug 23 18:45:13 paul-minty NetworkManager[1047]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Aug 23 18:45:13 paul-minty NetworkManager[1047]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Aug 23 18:45:13 paul-minty NetworkManager[1047]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Aug 23 18:45:13 paul-minty NetworkManager[1047]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Aug 23 18:45:13 paul-minty NetworkManager[1047]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Aug 23 18:45:13 paul-minty NetworkManager[1047]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Aug 23 18:45:13 paul-minty NetworkManager[1047]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Aug 23 18:45:13 paul-minty NetworkManager[1047]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Aug 23 18:45:13 paul-minty NetworkManager[1047]: <info> dhclient started with pid 2193
Aug 23 18:45:13 paul-minty NetworkManager[1047]: <info> Activation (eth0) Beginning IP6 addrconf.
Aug 23 18:45:13 paul-minty NetworkManager[1047]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Aug 23 18:45:13 paul-minty avahi-daemon[803]: Withdrawing address record for fe80::62a4:4cff:feae:4e22 on eth0.
Aug 23 18:45:13 paul-minty avahi-daemon[803]: Leaving mDNS multicast group on interface eth0.IPv6 with address fe80::62a4:4cff:feae:4e22.
Aug 23 18:45:13 paul-minty avahi-daemon[803]: Interface eth0.IPv6 no longer relevant for mDNS.
Aug 23 18:45:13 paul-minty dhclient: Internet Systems Consortium DHCP Client 4.2.4
Aug 23 18:45:13 paul-minty dhclient: Copyright 2004-2012 Internet Systems Consortium.
Aug 23 18:45:13 paul-minty dhclient: All rights reserved.
Aug 23 18:45:13 paul-minty dhclient: For info, please visit https://www.isc.org/software/dhcp/
Aug 23 18:45:13 paul-minty dhclient: 
Aug 23 18:45:13 paul-minty NetworkManager[1047]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Aug 23 18:45:13 paul-minty dhclient: Listening on LPF/eth0/60:a4:4c:ae:4e:22
Aug 23 18:45:13 paul-minty dhclient: Sending on   LPF/eth0/60:a4:4c:ae:4e:22
Aug 23 18:45:13 paul-minty dhclient: Sending on   Socket/fallback
Aug 23 18:45:13 paul-minty dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 (xid=0x1b1b53b0)
Aug 23 18:45:15 paul-minty avahi-daemon[803]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::62a4:4cff:feae:4e22.
Aug 23 18:45:15 paul-minty avahi-daemon[803]: New relevant interface eth0.IPv6 for mDNS.
Aug 23 18:45:15 paul-minty avahi-daemon[803]: Registering new address record for fe80::62a4:4cff:feae:4e22 on eth0.*.
Aug 23 18:45:16 paul-minty NetworkManager[1047]: <info> (ra0): device state change: activated -> unavailable (reason 'none') [100 20 0]
Aug 23 18:45:16 paul-minty NetworkManager[1047]: <info> (ra0): deactivating device (reason 'none') [0]
Aug 23 18:45:16 paul-minty NetworkManager[1047]: <info> (ra0): canceled DHCP transaction, DHCP client pid 1905
Aug 23 18:45:16 paul-minty avahi-daemon[803]: Withdrawing address record for fe80::da50:e6ff:fef4:ba81 on ra0.
Aug 23 18:45:16 paul-minty avahi-daemon[803]: Leaving mDNS multicast group on interface ra0.IPv6 with address fe80::da50:e6ff:fef4:ba81.
Aug 23 18:45:16 paul-minty avahi-daemon[803]: Interface ra0.IPv6 no longer relevant for mDNS.
Aug 23 18:45:16 paul-minty NetworkManager[1047]: <info> (ra0): taking down device.
Aug 23 18:45:16 paul-minty avahi-daemon[803]: Interface ra0.IPv4 no longer relevant for mDNS.
Aug 23 18:45:16 paul-minty avahi-daemon[803]: Leaving mDNS multicast group on interface ra0.IPv4 with address 192.168.1.217.
Aug 23 18:45:16 paul-minty NetworkManager[1047]: <warn> (ra0): failed to change interface MAC address
Aug 23 18:45:16 paul-minty NetworkManager[1047]: <warn> (ra0): failed to reset MAC address to 00:00:00:00:00:00
Aug 23 18:45:16 paul-minty wpa_supplicant[1155]: ra0: CTRL-EVENT-DISCONNECTED bssid=00:1d:0f:d2:88:64 reason=3 locally_generated=1
Aug 23 18:45:16 paul-minty NetworkManager[1047]: <warn> (ra0): error 100 getting card mode
Aug 23 18:45:16 paul-minty NetworkManager[1047]: <warn> (ra0): error 100 getting card mode
Aug 23 18:45:16 paul-minty NetworkManager[1047]: <error> [1408844716.320428] [wifi-utils-wext.c:160] wifi_wext_set_mode(): (ra0): error setting mode 2
Aug 23 18:45:16 paul-minty NetworkManager[1047]: <info> (ra0): bringing up device.
Aug 23 18:45:16 paul-minty whoopsie[1086]: message repeated 10 times: [ online]
Aug 23 18:45:16 paul-minty whoopsie[1086]: offline
Aug 23 18:45:16 paul-minty avahi-daemon[803]: Withdrawing address record for 192.168.1.217 on ra0.
Aug 23 18:45:16 paul-minty NetworkManager[1047]: <warn> DNS: plugin dnsmasq update failed
Aug 23 18:45:16 paul-minty NetworkManager[1047]: <info> Removing DNS information from /sbin/resolvconf
Aug 23 18:45:16 paul-minty dnsmasq[1909]: setting upstream servers from DBus
Aug 23 18:45:16 paul-minty NetworkManager[1047]: <info> NetworkManager state is now CONNECTING
Aug 23 18:45:16 paul-minty NetworkManager[1047]: <info> WiFi hardware radio set disabled
Aug 23 18:45:16 paul-minty dbus[706]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Aug 23 18:45:16 paul-minty dbus[706]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Aug 23 18:45:16 paul-minty dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 (xid=0x1b1b53b0)
Aug 23 18:45:19 paul-minty dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4 (xid=0x1b1b53b0)
Aug 23 18:45:23 paul-minty dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8 (xid=0x1b1b53b0)
Aug 23 18:45:31 paul-minty dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16 (xid=0x1b1b53b0)
Aug 23 18:45:33 paul-minty NetworkManager[1047]: <info> (eth0): IP6 addrconf timed out or failed.
Aug 23 18:45:33 paul-minty NetworkManager[1047]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Aug 23 18:45:33 paul-minty NetworkManager[1047]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Aug 23 18:45:33 paul-minty NetworkManager[1047]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.


```

Note: I am running Kubuntu 14.04

---

### Post by pcvonz on 2014-08-23
I am so excited. Ok, I was searching for a fix again and stumbled upon an arch Linux post about the card. This thread has a patch: [https://bbs.archlinux.org/viewtopic.php?id=152960&p=3](https://bbs.archlinux.org/viewtopic.php?id=152960&p=3)

However, the latest update to the patch is for linux kernel 3.15.x. So, what you have to do is upgrade your kernel and then apply the patch! Let me just quote the post I followed so you don't have to dig around the thread ;) 

>  FROM: bgladx64
OK, I just compiled this driver under kernel 3.15.8. The wireless  card works great now. For anyone else trying to do the same, here's the  steps I took:
1. Download and extract driver src from Asus's website
2. Download jcrews's 3.15.8 patch
3. cd to driver src root directory
4. run "patch -p1 < /path/to/patch/file"
5. make
6. make install
7. modprobe rt5592sta



---

### Post by rac9876 on 2014-08-27
> **praseodym said:**
> One of my German supporter collegues (known here as **flash63**) adapted the source code of the **rt5592sta** driver, please try this one:

```
sudo apt-get install linux-headers-$(uname -r) linux-headers-generic build-essential
wget http://www.elektronenblitz63.de/downloads/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326_patched.tar.gz
tar xvf DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326_patched.tar.gz
cd DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326_patched/
sudo make
sudo make install
```
Load the new driver:
```

sudo modprobe -rfv rt2800pci
sudo modprobe -v rt5592sta
sudo service network-manager restart
```
Check:
```

iwconfig
iwlist chan
sudo iwlist scan
dmesg | egrep 'rt2|rt5'
```
Which country do you live? Maybe we need to adjust one more file.

Thank you. This version of the driver seems to have fixed my issue with the Asus PCE-N53 after upgrading to the 3.11.0-26-generic kernel. A computer with no network connection is not much use these days!

Edit: Erk! I spoke too soon. The computer has just frozen a second or two after starting the Software Updater. I will investigate to see whether this keeps happening.

Edit again: I rebooted and it froze again. I have to suspect there's something wrong with the driver.

---

### Post by pcvonz on 2014-09-01
> **rac9876 said:**
> Thank you. This version of the driver seems to  have fixed my issue with the Asus PCE-N53 after upgrading to the  3.11.0-26-generic kernel. A computer with no network connection is not  much use these days!

Edit: Erk! I spoke too soon. The computer has just frozen a second or  two after starting the Software Updater. I will investigate to see  whether this keeps happening.

Edit again: I rebooted and it froze again. I have to suspect there's something wrong with the driver.


Everybody who has tried that driver has had that issue. My previous post explains a solution I used to solve the issue.

---

