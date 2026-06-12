---
title: "Need Intel Ac-9560 Driver for Ubuntu 18.04"
date: 2018-09-07
forum: Networking &amp; Wireless
---

### Post by CCgirl6690 on 2018-09-07
Hello everyone.  Could someone please help me find intel ac9560 driver or some alternative for it on Ubuntu 18.04?  i have issues with wifi on my new laptop.  It doesnt always connect to Wifi and when it does it shows a Question mark instead showing bars. So i thought maybe Installing a driver for the WIFI card would solve the issue.   I could be wrong.  
Btw  intel ac 9560 is what shows on windows device managar, that's how i got the Model number.
I appreciate any help. Thank you

---

### Post by chili555 on 2018-09-07
Please run and post:```
lspci -nnk | grep 0280 -A3
dmesg | grep -e wl -e iwl
umame -r
```Your device already has a driver, iwlwifi, and so connection issues are not likely the fault of the driver.

Please also run:```
sudo iwlist scan
```Please show us the network you are having trouble connection with and please redact the MAC address like this:```
Cell 03 - Address: [COLOR="#FF0000"]XXXX[/COLOR]
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"GBR1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001835bcf3fb
                    Extra: Last beacon: 3872ms ago
                    IE: Unknown: 000447425231
                    <snip>
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

```

------------------------

Note to Chili; possibly helpful: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1772467](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1772467)

---

### Post by CCgirl6690 on 2018-09-07
> **chili555 said:**
> Please run and post:```
lspci -nnk | grep 0280 -A3
dmesg | grep -e wl -e iwl
umame -r
```Your device already has a driver, iwlwifi, and so connection issues are not likely the fault of the driver.

Please also run:```
sudo iwlist scan
```Please show us the network you are having trouble connection with and please redact the MAC address like this:```
Cell 03 - Address: [COLOR=#FF0000]XXXX[/COLOR]
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"GBR1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001835bcf3fb
                    Extra: Last beacon: 3872ms ago
                    IE: Unknown: 000447425231
                    <snip>
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

```

------------------------

Note to Chili; possibly helpful: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1772467](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1772467)
Hello thank you for the reply.  here is my result.  first for the first set of commands u gave...
```
neon@neon-Predator-PH315-51:~$ lspci -nnk | grep 0280 -A3
00:14.3 Network controller [0280]: Intel Corporation Device [8086:a370] (rev 10)
    Subsystem: Intel Corporation Device [8086:0034]
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi
neon@neon-Predator-PH315-51:~$ dmesg | grep -e wl -e iwl
[    2.601660] iwlwifi 0000:00:14.3: loaded firmware version 34.0.0 op_mode iwlmvm
[    2.624788] iwlwifi 0000:00:14.3: Detected Intel(R) Dual Band Wireless AC 9560, REV=0x318
[    2.678750] iwlwifi 0000:00:14.3: base HW address: 14:4f:8a:a1:76:bf
[    2.749262] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    2.752714] iwlwifi 0000:00:14.3 wlp0s20f3: renamed from wlan0
[    4.856928] IPv6: ADDRCONF(NETDEV_UP): wlp0s20f3: link is not ready
[    5.059838] IPv6: ADDRCONF(NETDEV_UP): wlp0s20f3: link is not ready
[    5.143087] IPv6: ADDRCONF(NETDEV_UP): wlp0s20f3: link is not ready
[    8.538574] wlp0s20f3: authenticate with 00:15:6d:b0:ee:a9
[    8.545636] wlp0s20f3: send auth to 00:15:6d:b0:ee:a9 (try 1/3)
[    8.584591] wlp0s20f3: authenticated
[    8.584825] iwlwifi 0000:00:14.3 wlp0s20f3: disabling HT as WMM/QoS is not supported by the AP
[    8.584826] iwlwifi 0000:00:14.3 wlp0s20f3: disabling VHT as WMM/QoS is not supported by the AP
[    8.588149] wlp0s20f3: associate with 00:15:6d:b0:ee:a9 (try 1/3)
[    8.591365] wlp0s20f3: RX AssocResp from 00:15:6d:b0:ee:a9 (capab=0x431 status=0 aid=2)
[    8.595000] wlp0s20f3: associated
[    8.608908] iwlwifi 0000:00:14.3: Unhandled alg: 0x707
[    8.628340] IPv6: ADDRCONF(NETDEV_CHANGE): wlp0s20f3: link becomes ready
[ 6022.818989] wlp0s20f3: deauthenticating from 00:15:6d:b0:ee:a9 by local choice (Reason: 3=DEAUTH_LEAVING)
[ 6025.027117] IPv6: ADDRCONF(NETDEV_UP): wlp0s20f3: link is not ready
[ 6025.088695] IPv6: ADDRCONF(NETDEV_UP): wlp0s20f3: link is not ready
[ 6028.497650] wlp0s20f3: authenticate with 00:15:6d:b0:ee:a9
[ 6028.502275] wlp0s20f3: send auth to 00:15:6d:b0:ee:a9 (try 1/3)
[ 6028.540495] wlp0s20f3: authenticated
[ 6028.540646] iwlwifi 0000:00:14.3 wlp0s20f3: disabling HT as WMM/QoS is not supported by the AP
[ 6028.540647] iwlwifi 0000:00:14.3 wlp0s20f3: disabling VHT as WMM/QoS is not supported by the AP
[ 6028.544322] wlp0s20f3: associate with 00:15:6d:b0:ee:a9 (try 1/3)
[ 6028.547389] wlp0s20f3: RX AssocResp from 00:15:6d:b0:ee:a9 (capab=0x431 status=0 aid=2)
[ 6028.554001] wlp0s20f3: associated
[ 6028.583410] IPv6: ADDRCONF(NETDEV_CHANGE): wlp0s20f3: link becomes ready
neon@neon-Predator-PH315-51:~$ umame -r

Command 'umame' not found, did you mean:

  command 'umake' from snap ubuntu-make (master)
  command 'mame' from snap mame (mame0200)
  command 'mame' from deb mame
  command 'umake' from deb ubuntu-make
  command 'uname' from deb coreutils
 
```

And this is second command 
```
 neon@neon-Predator-PH315-51:~$ sudo iwlist scan
[sudo] password for neon: 
wlp0s20f3  Scan completed :
          Cell 01 - Address: x
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-32 dBm  
                    Encryption key:on
                    ESSID:"UBNT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002b0bd33ea
                    Extra: Last beacon: 1648ms ago
                    IE: Unknown: 000455424E54
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030106
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD26000C42000000011E0000000000660203FF0F55424E5400000000000000000000000000000000
          Cell 02 - Address: x
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"roya"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001266b8ec17c
                    Extra: Last beacon: 1948ms ago
                    IE: Unknown: 0004726F7961
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E1817FF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601050000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336E1817FF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401050000000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 03 - Address: x
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"kambiz1227"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001266a11817c
                    Extra: Last beacon: 1708ms ago
                    IE: Unknown: 000A6B616D62697A31323237
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E1817FF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A00B400C800140005001900
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336E1817FF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406000000000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 04 - Address: x
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"tara"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001266f783712
                    Extra: Last beacon: 1400ms ago
                    IE: Unknown: 000474617261
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AEE191FFFFF000000000000000000000000000000001804810000
                    IE: Unknown: 3D160B000000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A00B400C800140005001900
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33EE191FFFFF000000000000000000000000000000001804810000
                    IE: Unknown: DD1A00904C340B000000000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160
          Cell 05 - Address: x
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"KH_Access_Point"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001266fa358e7
                    Extra: Last beacon: 1396ms ago
                    IE: Unknown: 000F4B485F4163636573735F506F696E74
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0500013D7A12
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706555320010B10

enp6s0f1  Interface doesn't support scanning.

tun0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

 
```
thanks for helping i appreaciate this. 
btw this is the station i can connect to. and has internet. Problem is there is a qestion mark shown in top panel, instead showing signal bars. thr other one i cant even connect to.

---

### Post by chili555 on 2018-09-07
> Cell 01 - Address: x
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-32 dBm  
                    Encryption key:on
                    ESSID:"UBNT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002b0bd33ea
                    Extra: Last beacon: 1648ms ago
                    IE: Unknown: 000455424E54
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030106
                    IE: WPA Version 1
                        Group Cipher : [COLOR="#FF0000"]CCMP[/COLOR]
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSKIs this the one you CAN connect to? And is this the one you cannot?> Cell 04 - Address: x
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"tara"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001266f783712
                    Extra: Last beacon: 1400ms ago
                    IE: Unknown: 000474617261
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AEE191FFFFF000000000000000000000000000000001804810000
                    IE: Unknown: 3D160B000000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A00B400C800140005001900
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher :[COLOR="#FF0000"] TKIP[/COLOR]
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSKThe iwlwifi driver doesn't like TKIP!

I have a theory with regard to the Intel 9000 series and it requires a bit of experimentation and may take a few steps.

Please clarify my scan question before we proceed.

---

### Post by CCgirl6690 on 2018-09-07
> **chili555 said:**
> Is this the one you CAN connect to? And is this the one you cannot?The iwlwifi driver doesn't like TKIP!

I have a theory with regard to the Intel 9000 series and it requires a bit of experimentation and may take a few steps.

Please clarify my scan question before we proceed.

This is the one i can connect always to. But it shows question mark instead showing signal bars, Otherwise everything else works fine and fast. 
the other one which is a 4g modem it sometimes connects sometimes dont.  For exmapled i disconnected from that one u seen results for and could connect to the other one.( question mark is always there tho )  then i had to restart my laptop after i restarted i tried to connect again then it says connecting... And after 15 20 seconds it says failed to connect. 
thanks  
Edit: Im going to sleep now so i will reply back tomorrow ok.

---

### Post by chili555 on 2018-09-07
Let's try to address the ??s first. Let's see:```
cat /etc/NetworkManager/NetworkManager.conf
cat /etc/network/interfaces
```

---

### Post by CCgirl6690 on 2018-09-08
> **chili555 said:**
> Let's try to address the ??s first. Let's see:```
cat /etc/NetworkManager/NetworkManager.conf
cat /etc/network/interfaces
```

Hello chilli. Thhanks for helping me.  Here is the resuls ......  BTW im connected to the station that sometimes i cant connect to....
```
neon@neon-Predator-PH315-51:~$ cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

[device]
wifi.scan-rand-mac-address=no
neon@neon-Predator-PH315-51:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
neon@neon-Predator-PH315-51:~$ 
 
```

---

### Post by chili555 on 2018-09-08
That's really *bad *news; it's bad news because it is perfect and offers no clue whatever as to the origin of:> But it shows question mark instead showing signal bars,Please try:```
sudo apt install --reinstall network-manager
```After it finishes, please run:```
sudo service network-manager restart
```Then tell us if the ??? issue is resolved.

I'd also love to see:```
ls /etc/netplan
cat /etc/netplan/*.yaml
```

---

### Post by CCgirl6690 on 2018-09-08
> **chili555 said:**
> That's really *bad *news; it's bad news because it is perfect and offers no clue whatever as to the origin of:Please try:```
sudo apt install --reinstall network-manager
```After it finishes, please run:```
sudo service network-manager restart
```Then tell us if the ??? issue is resolved.

I'd also love to see:```
ls /etc/netplan
cat /etc/netplan/*.yaml
```

Hi the commands didnt help... 
And here is the resuls/...
```
 neon@neon-Predator-PH315-51:~$ ls /etc/netplan
01-network-manager-all.yaml
neon@neon-Predator-PH315-51:~$ cat /etc/netplan/*.yaml
# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager
neon@neon-Predator-PH315-51:~$ 


```

---

### Post by jeremy31 on 2018-09-08
Lets try the newest from Intel
```
sudo apt install git build-essential
git clone https://git.kernel.org/pub/scm/linux/kernel/git/iwlwifi/backport-iwlwifi.git
cd backport-iwlwifi
make defconfig-iwlwifi-public
sed -i 's/CPTCFG_IWLMVM_VENDOR_CMDS=y/# CPTCFG_IWLMVM_VENDOR_CMDS is not set/' .config
make -j4
sudo make install
cd /lib/firmware
sudo wget https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/iwlwifi-9000-pu-b0-jf-b0-38.ucode
sudo wget https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/iwlwifi-9260-th-b0-jf-b0-38.ucode
```
Reboot

---

### Post by CCgirl6690 on 2018-09-08
> **jeremy31 said:**
> Lets try the newest from Intel
```
sudo apt install git build-essential
git clone https://git.kernel.org/pub/scm/linux/kernel/git/iwlwifi/backport-iwlwifi.git
cd backport-iwlwifi
make defconfig-iwlwifi-public
sed -i 's/CPTCFG_IWLMVM_VENDOR_CMDS=y/# CPTCFG_IWLMVM_VENDOR_CMDS is not set/' .config
make -j4
sudo make install
cd /lib/firmware
sudo wget https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/iwlwifi-9000-pu-b0-jf-b0-38.ucode
sudo wget https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/iwlwifi-9260-th-b0-jf-b0-38.ucode
```
Reboot

Hello jeremy thanks for the help. Are these all one command or i put them line by line? Cuz i copy pasted all in one command and it only installed git build essential?
Thanks

---

### Post by jeremy31 on 2018-09-08
One line at a time

---

### Post by CCgirl6690 on 2018-09-08
> **jeremy31 said:**
> One line at a time

i did it all but i see no change. question mark is still there instead signal bars and i couldnt connect to this station when i rebooted. However if this helpes... When i reboot the modem it can connect to this sepecific modem. Looks like it doesnt disconnect when i reboot or switch APs. so it keeps trying to connect till it fails untill i reboot the AP. however it connects to my main AP everytime. so maybe could be the that modem's fault. even tho i dont never had such issue with my other laptop which runs ubuntu 14.   Its not a killer issue. But the question mark is on the nerves. If only could be a fix for that.
Thank you so much again for the helping

---

### Post by jeremy31 on 2018-09-08
There were these errors from your logs ```
[    8.584825] iwlwifi 0000:00:14.3 wlp0s20f3: disabling HT as WMM/QoS is not supported by the AP
[    8.584826] iwlwifi 0000:00:14.3 wlp0s20f3: disabling VHT as WMM/QoS is not supported by the AP
```
It may have an issue with an older router or possibly the encryption is not WPA2-PSK/AES only

---

### Post by chili555 on 2018-09-08
> **jeremy31 said:**
> There were these errors from your logs ```
[    8.584825] iwlwifi 0000:00:14.3 wlp0s20f3: disabling HT as WMM/QoS is not supported by the AP
[    8.584826] iwlwifi 0000:00:14.3 wlp0s20f3: disabling VHT as WMM/QoS is not supported by the AP
```
It may have an issue with an older router or possibly the encryption is not WPA2-PSK/AES onlyIndeed!

Please check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Your driver, iwlwifi, hates hates hates TKIP.

---

### Post by CCgirl6690 on 2018-09-08
Thanks for the help . This is a 3g modem. Pw is wpa2 aes .  i juct changed channel to 5 and type to AES and Tkip mixed. so hope it does the trick. but im still curious about the question mark instead signal bars. Is it an ubuntu 18 bug??  thanks

---

### Post by chili555 on 2018-09-08
>  i juct changed channel to 5 and type to AES and Tkip mixed. This is not recommended. Channel 1, 6 or 11 fixed and WPA2-AES *only.*

---

### Post by CCgirl6690 on 2018-09-08
> **chili555 said:**
> This is not recommended. Channel 1, 6 or 11 fixed and WPA2-AES *only.*

done. Not sure whats the difference tho. but i did it anyway. In fact my other AP is tkip and it always connects to it with no problem. 
Thanks for the help tho guys.

---

### Post by jeremy31 on 2018-09-08
I have a 4G Dlink router and I do see the question mark for a couple seconds after opening the laptop but the normal wifi symbol shows up quickly.
I just posted what I did because of some issues a person had with the same chipset that I chatted with on IRC, he installed the newer firmware and a much newer kernel to fix the issues.  I think it is better to use a supported kernel and backports when needed

---

### Post by CCgirl6690 on 2018-09-08
> **jeremy31 said:**
> I have a 4G Dlink router and I do see the question mark for a couple seconds after opening the laptop but the normal wifi symbol shows up quickly.
I just posted what I did because of some issues a person had with the same chipset that I chatted with on IRC, he installed the newer firmware and a much newer kernel to fix the issues.  I think it is better to use a supported kernel and backports when needed

Thank you. Mine is dlink too.  soo am i good now? with the new drivers?  or need to uninstall intels newest drivers? I guess i leave them be the way you guiled me .
Thanks anyway for ur help.

---

### Post by jeremy31 on 2018-09-08
I would leave them be and see what happens in the next kernel.  If the next kernel makes things really bad, we can reinstall what we did

---

### Post by CCgirl6690 on 2018-09-08
Okay thanks.

---

### Post by mikelebike on 2019-03-09
Hey chilli thanks! I had the exact same problem but for me this solved the ??-mark issue and no problem connecting :D

It's people like you guys who make the internet my favorite place <3

---

