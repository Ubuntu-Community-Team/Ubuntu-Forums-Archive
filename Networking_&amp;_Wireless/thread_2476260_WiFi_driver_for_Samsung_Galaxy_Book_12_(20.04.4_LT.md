---
title: "WiFi driver for Samsung Galaxy Book 12 (20.04.4 LTS)"
date: 2022-06-21
forum: Networking &amp; Wireless
---

### Post by mistermeseeks on 2022-06-21
So I have read the previous post [https://ubuntuforums.org/showthread.php?t=2384640](https://ubuntuforums.org/showthread.php?t=2384640) about a VERY similar issue, but my issue fails on the current version(s) of Linux. I have tried Ubuntu 20.04.4 LTS and I have tried Xubuntu 22.04 AND I have tried Kali 2022.2. All fail with the same:

Output of: dmesg | grep ath

```
[  277.827172] ath10k_pci 0000:01:00.0: enabling device (0000 -> 0002)
[  277.829061] ath10k_pci 0000:01:00.0: pci irq msi oper_irq_mode 2 irq_mode 0 reset_mode 0
[  279.127016] ath10k_pci 0000:01:00.0: qca6174 hw3.2 target 0x05030000 chip_id 0x00340aff sub 144d:c14f
[  279.127022] ath10k_pci 0000:01:00.0: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[  279.127442] ath10k_pci 0000:01:00.0: firmware ver WLAN.RM.4.4.1-00140-QCARMSWPZ-1 api 6 features wowlan,ignore-otp,mfp crc32 29eb8ca1
[  279.318796] ath10k_pci 0000:01:00.0: board_file api 2 bmi_id N/A crc32 4ac0889b
[  279.409720] ath10k_pci 0000:01:00.0: htt-ver 3.60 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1
[  279.487519] ath: EEPROM regdomain: 0x5f
[  279.487523] ath: EEPROM indicates we should expect a direct regpair map
[  279.487524] ath: invalid regulatory domain/country code 0x5f
[  279.487524] ath: Invalid EEPROM contents
[  279.487528] ath10k_pci 0000:01:00.0: failed to initialise regulatory: -22
[  279.487531] ath10k_pci 0000:01:00.0: could not register to mac80211 (-22)

```

[COLOR=#232629][FONT=-apple-system]Output of : lspci -nnk | grep -iA2 net

[/FONT][/COLOR]```
01:00.0 Network Controller [0280]: Qualcomm Atheros QCA 802.11ac Wireless Network Adapter [168c:003e] (rev32)
     Subsystem: Samsung Electronics Co Ltd QCA6174 802.11ac Wireless Network Adapter [144d:c14f]
     Kernel driver in use: ath10k_pci
     Kernel modules: ath10kpci
```


rfkill list all
```

0: hci: Bluetooth
     Soft blocked: no
     Hard blocked: no

```

(bluetooth does work)

I tried following [COLOR=#DD4814]chili555'[/COLOR]s recommendations to bring the .bin files from Windows over to Ubuntu, and I get the exact same output.

My first failure in following the post is here where [COLOR=#C61919]jeremy31 [/COLOR]suggested to do the following:

```
sudo apt install git build-essential
git clone [https://github.com/jeremyb31/backports-4.14.git](https://github.com/jeremyb31/backports-4.14.git)
cd backports-4.14
make defconfig-wifi
make
sudo make install
```

I get the output:

```
~/backports-4.14$ make defconfig-wifi
Generating local configuration database from kernel ...Kernel version parse failed!
make: *** [Makefile:42: defconfig-wifi] Error 1

```

obviously this solution was for a different build of Ubuntu and subsequently other versions of linux... and now going forward and probably with every future release some manual method needs to apply. But Ill end my rant here...

Can I get assistance on getting this wifi to work on BOTH Ubuntu 20.04.4 AND Xubuntu 22.04? [I](ill also attempt to get it work on Kali with the same instructions but I am not as hopeful)


p.s. is there an easier way to transfer files from Ubuntu than "Settings -> Bluetooth -> Click on Device -> Click Send Files... ->"  ????
p.s.s.
 Kali Kernel version[/I] 5.16.0-kali7-amd64[I]
Xubuntu Kernel version [/I]5.15.0-39-generic 
*Ubuntu Kernel version *5.13.0-30-generic





EDIT: I continued to read the post and found another "solution" _**it made a difference, I can see access points but [COLOR=#ff0000]cannot connect to them [/COLOR][COLOR=#000000]Actually, I CAN now connect to 5G wifi now. But cannot connect to 2g [/COLOR]**_

[COLOR=#000000]Deleting board.bin and board-2.bin and copied the `eeprom_ar6320_3p0_TX8_clpc.bin` file to `lib/firmware/ath10k/QCA6174/hw3.0/board.bin[/COLOR]

heres the output:
```

[  286.142849] ath10k_pci 0000:01:00.0: enabling device (0000 -> 0002)
[  286.144890] ath10k_pci 0000:01:00.0: pci irq msi oper_irq_mode 2 irq_mode 0 reset_mode 0
[  286.610362] ath10k_pci 0000:01:00.0: qca6174 hw3.2 target 0x05030000 chip_id 0x00340aff sub 144d:c14f
[  286.610370] ath10k_pci 0000:01:00.0: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[  286.610800] ath10k_pci 0000:01:00.0: firmware ver WLAN.RM.4.4.1-00140-QCARMSWPZ-1 api 6 features wowlan,ignore-otp,mfp crc32 29eb8ca1
[  286.687266] ath10k_pci 0000:01:00.0: board_file api 1 bmi_id N/A crc32 c8f42334
[  286.778460] ath10k_pci 0000:01:00.0: htt-ver 3.60 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1
[  286.864880] ath: EEPROM regdomain sanitized
[  286.864885] ath: EEPROM regdomain: 0x64
[  286.864887] ath: EEPROM indicates we should expect a direct regpair map
[  286.864890] ath: Country alpha2 being used: 00
[  286.864891] ath: Regpair used: 0x64
[  286.875374] ath10k_pci 0000:01:00.0 wlp1s0: renamed from wlan0
```

rfkill list all

```

0: hci: Bluetooth
     Soft blocked: no
     Hard blocked: no

1: phy0: Wireless LAN
     Soft blocked: no
     Hard blocked: no

```

(bluetooth still works and wireless card seems detected now, but will not connect with message "Connection failed Activation of network connection failed"

perhaps I am close...

UPDATE:  [https://paste.ubuntu.com/p/98TPqNWfzf/](https://paste.ubuntu.com/p/98TPqNWfzf/)

---

### Post by chili555 on 2022-06-21
I have studied this issue extensively because I saw it in Ask Ubuntu: [https://askubuntu.com/questions/1414928/qualcomm-atheros-qca6174-on-samsung-galaxy-book-12-no-wifi](https://askubuntu.com/questions/1414928/qualcomm-atheros-qca6174-on-samsung-galaxy-book-12-no-wifi) As well, the ath10k_pci devices are a particular friend/enemy of mine. When I saw your post at AU, I read quite a bit and studied and found no useful clues or directions. Therefore, at AU, I did nothing.

I would like, however, to experiment a bit. I notice these interesting lines in dmesg:

```
[  279.487519] ath: EEPROM [COLOR="#FF0000"]regdomain[/COLOR]: 0x5f
[  279.487523] ath: EEPROM indicates we should expect a direct regpair map
[  279.487524] ath: [COLOR="#FF0000"]invalid regulatory domain[/COLOR]/country code 0x5f
[  279.487524] ath: Invalid EEPROM contents
[  279.487528] ath10k_pci 0000:01:00.0: failed to initialise regulatory: -22
[  279.487531] ath10k_pci 0000:01:00.0: could not register to mac80211 (-22)
```Let's see if we can extinguish this and see if it helps. Please find your country code here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Next, do:

```
sudo -i
echo "options cfg80211 ieee80211_regdom=IS"  >  /etc/modprobe.d/cfg80211.conf
exit
```

Of course, substitute your country code if not Iceland.

Reboot and show us:

```
sudo dmesg | grep ath
```

---

### Post by mistermeseeks on 2022-06-21
I forgot to mention that I did that too... with no help.

I updated my original post with the following:

[COLOR=#000000] continued to read the post and found another "solution" [/COLOR]_**but it also failed**_

> [COLOR=#000000][I][COLOR=#000000]I can confirm that this solution has worked for me.[/COLOR]

[COLOR=#000000]I had deleted the original `board-2.bin` and copied the `eeprom_ar6320_3p0_TX8_clpc.bin` file to `lib/firmware/ath10k/QCA6174/hw3.0/board.bin`[/COLOR]
[/I]
[/COLOR]

[COLOR=#000000]**heres the output:**
[/COLOR]
[COLOR=#000000]```

[  286.142849] ath10k_pci 0000:01:00.0: enabling device (0000 -> 0002)
[  286.144890] ath10k_pci 0000:01:00.0: pci irq msi oper_irq_mode 2 irq_mode 0 reset_mode 0
[  286.610362] ath10k_pci 0000:01:00.0: qca6174 hw3.2 target 0x05030000 chip_id 0x00340aff sub 144d:c14f
[  286.610370] ath10k_pci 0000:01:00.0: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[  286.610800] ath10k_pci 0000:01:00.0: firmware ver WLAN.RM.4.4.1-00140-QCARMSWPZ-1 api 6 features wowlan,ignore-otp,mfp crc32 29eb8ca1
[  286.687266] ath10k_pci 0000:01:00.0: board_file api 1 bmi_id N/A crc32 c8f42334
[  286.778460] ath10k_pci 0000:01:00.0: htt-ver 3.60 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1
[  286.864880] ath: EEPROM regdomain sanitized
[  286.864885] ath: EEPROM regdomain: 0x64
[  286.864887] ath: EEPROM indicates we should expect a direct regpair map
[  286.864890] ath: Country alpha2 being used: 00
[  286.864891] ath: Regpair used: 0x64
[  286.875374] ath10k_pci 0000:01:00.0 wlp1s0: renamed from wlan0

```[/COLOR]
**[COLOR=#000000]rfkill list all[/COLOR]**

```
[COLOR=#000000]
0: hci: Bluetooth
     Soft blocked: no
     Hard blocked: no

1: phy0: Wireless LAN
     Soft blocked: no
     Hard blocked: no

[/COLOR]
```
[COLOR=#000000](bluetooth still works and wireless card seems detected now, but will not connect with message "Connection failed Activation of network connection failed"[/COLOR]

[COLOR=#000000]perhaps I am close...

edit.. I tried the exact same thing with Kali just for giggles and the output is oddly ... different...  I have it here just for giggles. Perhaps we have more information with this.

```

[/COLOR]&#9484;&#9472;&#9472;(kali&#12927;kali)-[~]
&#9492;&#9472;$ sudo dmesg | grep ath   
[   19.224348] systemd[1]: Kernel Module supporting RPCSEC_GSS was skipped because of a failed condition check (ConditionPathExists=/etc/krb5.keytab).
[   23.210986] ath10k_pci 0000:01:00.0: enabling device (0000 -> 0002)
[   23.212672] ath10k_pci 0000:01:00.0: pci irq msi oper_irq_mode 2 irq_mode 0 reset_mode 0
[   23.485589] ath10k_pci 0000:01:00.0: firmware: failed to load ath10k/pre-cal-pci-0000:01:00.0.bin (-2)
[   23.485622] ath10k_pci 0000:01:00.0: firmware: failed to load ath10k/cal-pci-0000:01:00.0.bin (-2)
[   23.523031] ath10k_pci 0000:01:00.0: firmware: direct-loading firmware ath10k/QCA6174/hw3.0/firmware-6.bin
[   23.523042] ath10k_pci 0000:01:00.0: qca6174 hw3.2 target 0x05030000 chip_id 0x00340aff sub 144d:c14f
[   23.523046] ath10k_pci 0000:01:00.0: kconfig debug 0 debugfs 0 tracing 0 dfs 0 testmode 0
[   23.523530] ath10k_pci 0000:01:00.0: firmware ver WLAN.RM.4.4-00022-QCARMSWPZ-2 api 6 features wowlan,ignore-otp crc32 4d458559
[   23.586464] ath10k_pci 0000:01:00.0: firmware: failed to load ath10k/QCA6174/hw3.0/board-2.bin (-2)
[   23.587780] ath10k_pci 0000:01:00.0: firmware: direct-loading firmware ath10k/QCA6174/hw3.0/board.bin
[   23.587795] ath10k_pci 0000:01:00.0: board_file api 1 bmi_id N/A crc32 c8f42334
[   23.678955] ath10k_pci 0000:01:00.0: htt-ver 3.32 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1
[   23.762973] ath: EEPROM regdomain: 0x0
[   23.762977] ath: EEPROM indicates default country code should be used
[   23.762978] ath: doing EEPROM country->regdmn map search
[   23.762979] ath: country maps to regdmn code: 0x3a
[   23.762980] ath: Country alpha2 being used: US
[   23.762980] ath: Regpair used: 0x3a

```

---

### Post by chili555 on 2022-06-21
> ath10k_pci 0000:01:00.0 wlp1s0: renamed from wlan0You are very close!

Let's see what we can see about the access point(s) you are trying to join:

```
nmcli device wifi list
```Of course, redact all of the MAC addresses with xxxx.

Let's also see:

```
sudo dmesg | grep -e wlp -e etwork
```

---

### Post by mistermeseeks on 2022-06-22
```

sudo dmesg | grep -e wlp -e etwork
[    0.623266] drop_monitor: Initializing network drop monitor service
[  282.957866] ath10k_pci 0000:01:00.0 wlp1s0: renamed from wlan0
[ 2002.092200] wlp1s0: authenticate with KMCNV
[ 2002.150080] wlp1s0: send auth to KMCNV (try 1/3)
[ 2002.154846] wlp1s0: send auth to KMCNV (try 2/3)
[ 2002.161120] wlp1s0: send auth to KMCNV (try 3/3)
[ 2002.165991] wlp1s0: authentication with KMCNV timed out
[ 2004.995857] wlp1s0: authenticate with KMCNV
[ 2005.050283] wlp1s0: send auth to KMCNV (try 1/3)
[ 2005.061067] wlp1s0: send auth to KMCNV (try 2/3)
[ 2005.077005] wlp1s0: send auth to KMCNV (try 3/3)
[ 2005.087338] wlp1s0: authentication with KMCNV timed out
[ 2008.334769] wlp1s0: authenticate with KMCNV
[ 2008.389044] wlp1s0: send auth to KMCNV (try 1/3)
[ 2008.393829] wlp1s0: send auth to KMCNV (try 2/3)
[ 2008.398584] wlp1s0: send auth to KMCNV (try 3/3)
[ 2008.403344] wlp1s0: authentication with KMCNV timed out
[ 2012.155088] wlp1s0: authenticate with KMCNV
[ 2012.209105] wlp1s0: send auth to KMCNV (try 1/3)
[ 2012.220731] wlp1s0: send auth to KMCNV (try 2/3)
[ 2012.225387] wlp1s0: send auth to KMCNV (try 3/3)
[ 2012.230124] wlp1s0: authentication with KMCNV timed out


```

```

IN-USE  BSSID              SSID                             MODE   CHAN  RATE        SIGNAL  BARS  SECURITY  
          SSID_87_7B_63                    Infra  161   405 Mbit/s  85      &#9602;&#9604;&#9606;&#9608;  --        
          KMCNV                            Infra  6     195 Mbit/s  84      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2 
          SSID_87_7A_59                    Infra  6     195 Mbit/s  84      &#9602;&#9604;&#9606;&#9608;  --        
          SSID_87_7A_5A                    Infra  6     195 Mbit/s  84      &#9602;&#9604;&#9606;&#9608;  --        
          SSID_87_7A_5C                    Infra  6     195 Mbit/s  84      &#9602;&#9604;&#9606;&#9608;  --        
          SSID_87_7A_5E                    Infra  6     195 Mbit/s  84      &#9602;&#9604;&#9606;&#9608;  --        
          SSID_87_7A_5D                    Infra  6     195 Mbit/s  84      &#9602;&#9604;&#9606;&#9608;  --        
          SSID_87_7A_5B                    Infra  6     195 Mbit/s  84      &#9602;&#9604;&#9606;&#9608;  --        
          KMCNV 5G                         Infra  161   405 Mbit/s  84      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2 
          SSID_87_7B_61                    Infra  161   405 Mbit/s  84      &#9602;&#9604;&#9606;&#9608;  --        
          SSID_87_7B_62                    Infra  161   405 Mbit/s  84      &#9602;&#9604;&#9606;&#9608;  --        
          SSID_87_7B_65                    Infra  161   405 Mbit/s  84      &#9602;&#9604;&#9606;&#9608;  --        
          SSID_87_7B_66                    Infra  161   405 Mbit/s  84      &#9602;&#9604;&#9606;&#9608;  --        
          SSID_87_7B_64                    Infra  161   405 Mbit/s  84      &#9602;&#9604;&#9606;&#9608;  --        
          SSID_87_7B_67                    Infra  161   405 Mbit/s  84      &#9602;&#9604;&#9606;&#9608;  --        
          SSID_87_7A_5F                    Infra  6     195 Mbit/s  82      &#9602;&#9604;&#9606;&#9608;  --        
          ASUS                             Infra  6     130 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA2      
          Westcom                          Infra  2     195 Mbit/s  57      &#9602;&#9604;&#9606;_  WPA2      
          Westcom                          Infra  153   405 Mbit/s  40      &#9602;&#9604;__  WPA2      
          DIRECT-22-HP OfficeJet Pro 7740  Infra  6     65 Mbit/s   30      &#9602;___  WPA2      
          CenturyLink5092                  Infra  1     195 Mbit/s  25      &#9602;___  WPA1 WPA2 
          CenturyLink1052                  Infra  6     130 Mbit/s  25      &#9602;___  WPA1 WPA2 
          YC SIGNS LLC                     Infra  5     195 Mbit/s  22      &#9602;___  WPA1 WPA2 
          tle2ba50                         Infra  1     130 Mbit/s  19      &#9602;___  WPA2      
~



```

I have also found out how to run the wireless-info script.

here's that:

[https://paste.ubuntu.com/p/98TPqNWfzf/](https://paste.ubuntu.com/p/98TPqNWfzf/)

[SIZE=5][U][B][COLOR=#000000]Actually, I CAN now connect to 5G wifi. But cannot connect to 2g

[/COLOR][/B][/U][/SIZE]```
sudo dmesg | grep -e wlp -e network
[    0.621894] drop_monitor: Initializing network drop monitor service
[   56.020255] ath10k_pci 0000:01:00.0 wlp1s0: renamed from wlan0
[  129.541652] wlp1s0: authenticate with KMCNV 5G
[  129.595421] wlp1s0: send auth to KMCNV 5G (try 1/3)
[  129.597097] wlp1s0: authenticated
[  129.599201] wlp1s0: associate with KMCNV 5G (try 1/3)
[  129.600324] wlp1s0: RX AssocResp from KMCNV 5G (capab=0x1011 status=0 aid=3)
[  129.602880] wlp1s0: associated
[  129.715874] IPv6: ADDRCONF(NETDEV_CHANGE): wlp1s0: link becomes ready
```

---

### Post by chili555 on 2022-06-22
Frankly, with this historically tricky and stubborn device and driver combination, I'd be very happy to connect to 5 gHz. It is faster and your device was designed to take full advantage of it.

---

### Post by mistermeseeks on 2022-06-22
Normally I would be ok with that as well, but this device is not always in an area with 5G wifi. (I operate within a mobile business). 

Perhaps now we just need to try other firmware bin files. I may be using the wrong firmware-6.bin and obviously changing which board.bin I am using makes a difference as well. 

certainly irritating but there has to be a way to find the right combo.

Perhaps there is a way to see which bin file is in use in windows and move THAT one?

p.s. the audio also does not work. (sigh) more problems to fix

---

### Post by chili555 on 2022-06-22
> Perhaps there is a way to see which bin file is in use in windows and move THAT one?Didn't you already try that? Earlier, you said: > I tried following chili555's recommendations to bring the .bin files from Windows over to Ubuntu, and I get the exact same output.And..> Deleting board.bin and board-2.bin and copied the `eeprom_ar6320_3p0_TX8_clpc.bin` file to `lib/firmware/ath10k/QCA6174/hw3.0/board.binI suggest that you restore the backed up board.bin and board-2.bin files and see if it helps. I hope that you backed them up and didn't actually delete them entirely.

If they are deleted, please restore them from here: [https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/tree/ath10k/QCA6174/hw3.0](https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/tree/ath10k/QCA6174/hw3.0) After restoring the default bin files, can you connect to the 2.4 gHz access point? Are there any clues in dmesg?

---

### Post by mistermeseeks on 2022-06-24
The backed up board.bin and board-2 bin file do not even allow the wireless device to be recognized.

The "[COLOR=#000000]*eeprom_ar6320_3p0_TX8_clpc.bin"  *[/COLOR][COLOR=#000000]file was just a "random guess" as to which file is actually being used. I was only following what others did and did not come to the conclusion that, that specific file was the one being used. 

Sorry for the confusion. 

[/COLOR][COLOR=#000000]eeprom_ar6320_3p0_SS_620.bin[/COLOR]
[COLOR=#000000]eeprom_ar6320_3p0_SS_620_K.bin
[/COLOR][COLOR=#000000]eeprom_ar6320_3p0_SS_720.bin[/COLOR]
[COLOR=#000000]eeprom_ar6320_3p0_SS_720_K.bin 

these bin files also did not work and the other bin file was suggested by someone within another post on a different forum somewhere... I can't even remember where I got the idea to use THAT file.[/COLOR]

---

### Post by chili555 on 2022-06-25
I regret that after many hours of searching and study, I have no other suggestions. Sorry.

---

### Post by mistermeseeks on 2022-06-27
I will try to look into the variances between these bin files. When I did a search for the *[I]TX8_clpc.bin file, there were SEVERAL others to choose from. Something is pointing to the correct file. The possible combinations between the board.bin board-2.bin and the firmware-X.bin's is daunting, and maybe someday I will attempt all of the possibilities until I get the correct one. But as of now, I think I will give up being that even the audio does not work and getting it to work is in itself, a daunting task. Add to that, the brightness is not adjustable either. 

Samsung Galaxy book 12 = Not a good device for Linux.[/I]

---

### Post by uninstallable on 2022-08-22
Hi Guys,

Was gonna reply with a long message but found the actual patch:  [https://bugzilla.kernel.org/show_bug.cgi?id=206567](https://bugzilla.kernel.org/show_bug.cgi?id=206567) , it's this project: [https://backports.wiki.kernel.org/index.php/Main_Page](https://backports.wiki.kernel.org/index.php/Main_Page)

Thank me later.

---

### Post by uninstallable on 2022-08-23
Update: i have the device trying to accomplish the same task....

I'm a developer myself, so i "make install" the above, in default ath10k, nothing, i tried answering all the questions as best as i could, still nothing, i tried to delete /lib/firmware/ath10k as that's where the faulty modules are.

After i do the make install all the ath10k logging disapears from dmesg, so i can only image backports installs and functions but running ip link show or whatever doesn't display any additional network interfaces.

If you have any other idea's love to try them out? Any chance i can get a linux master to tell me what to try next?

Thanks

EDIT: this is resolved by this [https://github.com/RrOoSsSsOo/QCA6174-samsung-galaxy-book-12-w720](https://github.com/RrOoSsSsOo/QCA6174-samsung-galaxy-book-12-w720), tried it myself.

---

