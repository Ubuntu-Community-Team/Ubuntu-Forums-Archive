---
title: "Connection  wifi - Nothing happen"
date: 2014-05-24
forum: Networking &amp; Wireless
---

### Post by AladdinVonSane on 2014-05-24
Hello everyone, 
I just installed Lubuntu this afternoon*, and I finally succeed finding how to show the network and I have found mine but when I tap my password, nothing happen, the window close and that's all. I really don't know what can cause that, and how to fix it, does anyone have an idea ? 
Thank you in advance ! 



*In a second part on my macbook pro

---

### Post by Hadaka on 2014-05-24
hi, let's get some info and see what can be done.
please post the output of.

```
grep -v lp /etc/motd
lspci -n | egrep '0200|0280'
lsmod |egrep 'wl|b43'
cat /etc/default/crda
rfkill list all
```
thanks

---

### Post by AladdinVonSane on 2014-05-25
Thanks for your interest, here is the terminal answer to the code : 

aladdin@aladdin-MacBookPro:~$ grep -v lp /etc/motd
grep: /etc/motd: Aucun fichier ou dossier de ce type
aladdin@aladdin-MacBookPro:~$ lspci -n | egrep '0200|0280'
02:00.0 0280: 14e4:432b (rev 01)
03:00.0 0200: 14e4:1684 (rev 10)
aladdin@aladdin-MacBookPro:~$ lsmod |egrep 'wl|b43'
wl                   4207846  0 
lib80211               14381  2 wl,lib80211_crypt_tkip
cfg80211              484040  1 wl
aladdin@aladdin-MacBookPro:~$ cat /etc/default/crda
# Set REGDOMAIN to a ISO/IEC 3166-1 alpha2 country code so that iw(8) may set
# the initial regulatory domain setting for IEEE 802.11 devices which operate
# on this system.
#
# Governments assert the right to regulate usage of radio spectrum within
# their respective territories so make sure you select a ISO/IEC 3166-1 alpha2
# country code suitable for your location or you may infringe on local
# legislature. See `/usr/share/zoneinfo/zone.tab' for a table of timezone
# descriptions containing ISO/IEC 3166-1 alpha2 country codes.

REGDOMAIN=
aladdin@aladdin-MacBookPro:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by Hadaka on 2014-05-25
please open a terminal ctrl/alt/t and do.,,
To avoid typo's please COPY and paste the commands
find your country code in this list.
```
cat /usr/share/zoneinfo/zone.tab
```
**Replace XX with YOUR country code,,UPPERCASE
```
sed -i 's/^REG.*=$/&XX/' /etc/default/crda
```
BOOT <-Mandatory
```
sudo iw reg set XX
```
BOOT <-Mandatory
to verify please do and post.
```
cat /etc/default/crda
iw reg get
```
thanks.

---

### Post by AladdinVonSane on 2014-05-25
I think it didn't work, here is what happened in the terminal windows : 
```

aladdin@aladdin-MacBookPro:~$ sudo sed -i 's/^REG.*=$/&+4852+00220/' /etc/default/crda
[sudo] password for aladdin: 

aladdin@aladdin-MacBookPro:~$ sudo iw reg set +4852+00220
sudo: iw: command not found

aladdin@aladdin-MacBookPro:~$ cat /etc/default/crda
# Set REGDOMAIN to a ISO/IEC 3166-1 alpha2 country code so that iw(8) may set
# the initial regulatory domain setting for IEEE 802.11 devices which operate
# on this system.
#
# Governments assert the right to regulate usage of radio spectrum within
# their respective territories so make sure you select a ISO/IEC 3166-1 alpha2
# country code suitable for your location or you may infringe on local
# legislature. See `/usr/share/zoneinfo/zone.tab' for a table of timezone
# descriptions containing ISO/IEC 3166-1 alpha2 country codes.

REGDOMAIN=+4852+00220
aladdin@aladdin-MacBookPro:~$ iw reg get

```

Thanks to you !

---

### Post by AladdinVonSane on 2014-05-25
Did I do something wrong ? I must confess I don't understand what I was suppose to do...

---

### Post by Hadaka on 2014-05-25
hi, yes you entered incorrect data- the country code is only
2 letters.... Tell me what country you are in and i
will do the code to correct it.

---

### Post by jeremy31 on 2014-05-25
I think I see what went wrong, use FR instead of [COLOR=#000000][FONT=Ubuntu Mono]+4852+00220 for the XX[/FONT][/COLOR]

---

### Post by Hadaka on 2014-05-25
yes,but first set it to nothing for the crda file and 00 for the iw reg file
not doing so may cause issues.
*by "nothing i mean REGDOMAIN=.......NOT REGDOMAIN=nothing

---

### Post by AladdinVonSane on 2014-05-26
hi, to set it to nothing the code is 
REGDOMAIN=.......NOT REGDOMAIN
Or the same one with 00 in country code ? 
Thnaks for all, sorry I'm a Ubuntu beginner....

---

### Post by Hadaka on 2014-05-26
sudo sed -i 's/^REG.*=*/REGDOMANIN=/' /etc/default/crda
sudo iw reg set 00


Exactly like above
COPY and paste to make it easy

---

### Post by AladdinVonSane on 2014-05-26
I re-set and try again with FR, but the terminal said the iw config is not found
```

aladdin@aladdin-MacBookPro:~$ sudo sed -i 's/^REG.*=$/&FR/' /etc/default/crda[sudo] password for aladdin: 
aladdin@aladdin-MacBookPro:~$ sudo iw reg set FR
sudo: iw: command not found
aladdin@aladdin-MacBookPro:~$ sudo iw reg set FR
sudo: iw: command not found

```

---

### Post by Hadaka on 2014-05-26
ok, im going to try to help you clean this up
but when i type do it EXACTLY like this, i would
expect you to do that.let's start by seeing what the files
say now. please post the output of..
```
cat /etc/default/crda
iw reg get
```
thanks.

---

### Post by AladdinVonSane on 2014-05-26
Thanks for your help, and know that I always copy and paste the code you give me (with a sudo if the terminal say I don't have the permissions).

So here is the code, I could install the iw program : 
```

aladdin@aladdin-MacBookPro:~$ cat /etc/default/crda
# Set REGDOMAIN to a ISO/IEC 3166-1 alpha2 country code so that iw(8) may set
# the initial regulatory domain setting for IEEE 802.11 devices which operate
# on this system.
#
# Governments assert the right to regulate usage of radio spectrum within
# their respective territories so make sure you select a ISO/IEC 3166-1 alpha2
# country code suitable for your location or you may infringe on local
# legislature. See `/usr/share/zoneinfo/zone.tab' for a table of timezone
# descriptions containing ISO/IEC 3166-1 alpha2 country codes.

REGDOMANIN=FR

aladdin@aladdin-MacBookPro:~$ iw reg get
Le programme 'iw' n'est pas encore installé. Vous pouvez l'installer en tapant : *#Programm 'iw' is not installed yet, you cann install tapping sudo apt-get install iw*
sudo apt-get install iw

aladdin@aladdin-MacBookPro:~$ sudo apt-get install iw
[sudo] password for aladdin: 

Construction de l'arbre des dépendances    
Lecture des informations d'état... Fait
Les paquets suivants ont été installés automatiquement et ne sont plus nécessaires :
  linux-headers-generic linux-image-generic
Veuillez utiliser « apt-get autoremove » pour les supprimer.
Les NOUVEAUX paquets suivants seront installés :
  iw
0 mis à jour, 1 nouvellement installés, 0 à enlever et 0 non mis à jour.
Il est nécessaire de prendre 51,7 ko dans les archives.
Après cette opération, 153 ko d'espace disque supplémentaires seront utilisés.
Réception de : 1 http://fr.archive.ubuntu.com/ubuntu/ trusty/main iw amd64 3.4-1 [51,7 kB]
51,7 ko réceptionnés en 0s (105 ko/s)
Sélection du paquet iw précédemment désélectionné.
(Lecture de la base de données... 115528 fichiers et répertoires déjà installés.)
Préparation du décompactage de .../archives/iw_3.4-1_amd64.deb ...
Décompactage de iw (3.4-1) ...
Traitement déclenché pour  man-db (2.6.7.1-1) ...
Paramétrage de iw (3.4-1) ...

aladdin@aladdin-MacBookPro:~$ 

```

Thanks again _

---

### Post by Hadaka on 2014-05-26
Hi, please do..
```
sudo apt-get autoremove
iw reg set FR
```
then do and post
```
cat iw reg get
cat /etc/default/crda
```
thanks

---

### Post by AladdinVonSane on 2014-05-26
I couldn't do "iw reg set FR", the operation was not permetted and elevating via sudo didn't change anything.
Here the code  you asked me to post : 

```

aladdin@aladdin-MacBookPro:~$ cat iw reg get
cat: iw: Aucun fichier ou dossier de ce type
cat: reg: Aucun fichier ou dossier de ce type
cat: get: Aucun fichier ou dossier de ce type
aladdin@aladdin-MacBookPro:~$ cat /etc/default/crda
# Set REGDOMAIN to a ISO/IEC 3166-1 alpha2 country code so that iw(8) may set
# the initial regulatory domain setting for IEEE 802.11 devices which operate
# on this system.
#
# Governments assert the right to regulate usage of radio spectrum within
# their respective territories so make sure you select a ISO/IEC 3166-1 alpha2
# country code suitable for your location or you may infringe on local
# legislature. See `/usr/share/zoneinfo/zone.tab' for a table of timezone
# descriptions containing ISO/IEC 3166-1 alpha2 country codes.

REGDOMANIN=FR

```

---

### Post by Hadaka on 2014-05-26
hi, i am sorry one of the commands i gave you was incorrect
please do
```
iw reg get
```
thanks

---

### Post by AladdinVonSane on 2014-05-26
No problem of course, here is the code : 
```

aladdin@aladdin-MacBookPro:~$ iw reg get
country FR:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5490 - 5710 @ 40), (N/A, 27), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR
aladdin@aladdin-MacBookPro:~$ cat iw reg get
cat: iw: Aucun fichier ou dossier de ce type
cat: reg: Aucun fichier ou dossier de ce type
cat: get: Aucun fichier ou dossier de ce type
aladdin@aladdin-MacBookPro:~$ cat /etc/default/crda
# Set REGDOMAIN to a ISO/IEC 3166-1 alpha2 country code so that iw(8) may set
# the initial regulatory domain setting for IEEE 802.11 devices which operate
# on this system.
#
# Governments assert the right to regulate usage of radio spectrum within
# their respective territories so make sure you select a ISO/IEC 3166-1 alpha2
# country code suitable for your location or you may infringe on local
# legislature. See `/usr/share/zoneinfo/zone.tab' for a table of timezone
# descriptions containing ISO/IEC 3166-1 alpha2 country codes.

REGDOMANIN=FR

```

---

### Post by Hadaka on 2014-05-26
yes !! looks great, please do and post
```
dmesg | grep -i -e alpha -e crda
```
thanks

---

### Post by AladdinVonSane on 2014-05-26
Cool if it's loogs great ! :-) I was just wondering, what seams to be the problem ? Is my computer  not configure with the french network system ? 
here the response to the code you gave me : 
```

aladdin@aladdin-MacBookPro:~$ dmesg | grep -i -e alpha -e crda
[   18.533928] cfg80211: Calling CRDA to update world regulatory domain

```

---

### Post by AladdinVonSane on 2014-06-03
Hello Hadaka, 

Do you still ave any idea to fix my problem ? (sorry to ask directly to you..I just don't know what to do...)

Thanks !

---

### Post by Hadaka on 2014-06-03
hi, lets give this a try, please do.
COPY and paste one command at a time
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo apt-get install linux-firmware-nonfree
sudo modpobe b43
```
 boot

---

### Post by AladdinVonSane on 2014-06-03
Thanks for the interest, that's very kind ! 
Two lines didn't work :
- ```

sudo rm /etc/modprobe.d/blacklist-bcm43.conf 
```
Because there was no such file in the directory

And : 
- ```

sudo modpobe b43 
```
The 'modpobe' command was invalid

---

### Post by Hadaka on 2014-06-03
hi, the first command that failed is a "just in case" line...not  to worrry
the second one is my fault...i am sorry...it was a typo it should read
```
sudo modprobe b43
```
try that and then boot
thanks

---

### Post by AladdinVonSane on 2014-06-03
hi, 
thanks for the code, is that normal that after asking my password, nothing happened, I immediatly can do other things on the terminal ? 

I re-boot, it still doesn't work, do I have to give you the iw config or someting else ? 

thanks

---

### Post by Hadaka on 2014-06-03
yes that is normal you will not see your password.
connect to the internet with the cable and do

```
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
sudo iwlist wlan0 scan
```
post the output please
thanks.

---

### Post by AladdinVonSane on 2014-06-03
Line by line ? 

thanks

---

### Post by AladdinVonSane on 2014-06-03
Here the output, line by line : 
- for the linux firmware : 
```
 aladdin@aladdin-MacBookPro:~$ sudo apt-get install linux-firmware-nonfree
[sudo] password for aladdin: 
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
linux-firmware-nonfree est déjà la plus récente version disponible.
Les paquets suivants ont été installés automatiquement et ne sont plus nécessaires :
  dkms gcc gcc-4.8 libasan0 libatomic1 libc-dev-bin libc6-dev libgcc-4.8-dev
  libgomp1 libitm1 libtsan0 linux-libc-dev manpages-dev
Veuillez utiliser « apt-get autoremove » pour les supprimer.
0 mis à jour, 0 nouvellement installés, 0 à enlever et 0 non mis à jour.

```

-for the modprobe, nothing came in the output

- for the iwlist wlan0  : ```
 aladdin@aladdin-MacBookPro:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:78:9E:77:EB:E0
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"Bbox-C54D70B1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000019827722e2
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 000D42626F782D4335344437304231
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEC0103FFFFFF00000000000000000000000000000C1846471100
                    IE: Unknown: 3D1601000400000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0501001A127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706455520010D10
                    IE: Unknown: DDA70050F204104A0001101044000102103B00010310470010CF4E96EFDEAC4AA3927A6D800044B5151021001A43656C656E6F20436F6D6D756E69636174696F6E2C20496E632E1023001743656C656E6F20576972656C65737320415020322E344710240006434C313830301042000831323334353637381054000800060050F20400011011000C43656C656E6F4150322E344710080002278C103C0001011049000600372A000120
          Cell 02 - Address: 00:78:9E:77:EB:E1
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:off
                    ESSID:"Bouygues Telecom Wi-Fi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000198275fc3a
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 0016426F7579677565732054656C65636F6D2057692D4669
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEC0103FFFFFF00000000000000000000000000000C1846471100
                    IE: Unknown: 3D1601000400000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0501001A127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706455520010D10
          Cell 03 - Address: 06:19:70:64:7D:E6
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:off
                    ESSID:"orange"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000006a53e590d
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 00066F72616E6765
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101850003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000900000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010020000000
                    IE: Unknown: 0706465220010D14
          Cell 04 - Address: 54:22:F8:0D:2D:64
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"kevreadenn"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000c310c416f1
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 000A6B657672656164656E6E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F20201018B0003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: 0706465220010D14
                    IE: Unknown: DD920050F204104A0001101044000102103B00010310470010000000000000100000005422F80D2D64102100035A54451023000F4C697665626F7820465454482076321024001A6164363833365F4144534C5F5048595F30783030303030303030104200074C4D5A313330371054000800060050F20400011011000D465446525341332E3639313631100800020086103C000101
          Cell 05 - Address: 8C:E0:81:60:79:86
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"Livebox-7986"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007e8c4e5e28
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 000C4C697665626F782D37393836
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F20201018A0003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000900000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: 0706465220010D14
                    IE: Unknown: DD920050F204104A0001101044000102103B00010310470010000000000000100000008CE081607986102100035A54451023000F4C697665626F7820465454482076321024001A6164363833365F4144534C5F5048595F30783030303030303030104200074C4D5A313230391054000800060050F20400011011000D465446525341332E3639313631100800020086103C000101
          Cell 06 - Address: 00:19:70:64:7D:E6
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"Livebox-17b4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000006a53e8a6e
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 000C4C697665626F782D31376234
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101850003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000900000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010020000000
                    IE: Unknown: 0706465220010D14
                    IE: Unknown: DD880050F204104A000110104400010210570001001041000100103B00010310470010405A9B3517B4405A9B3517B49B3517B410210005536167656D102300084C697665626F7832102400084C697665626F78321042000A414E31323232323235351054000800060050F20400011011000D4C697665626F78322D31374234100800020086103C000101
          Cell 07 - Address: 7A:A1:D7:34:3E:E5
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:off
                    ESSID:"SFR WiFi FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004b07917391
                    Extra: Last beacon: 5804ms ago
                    IE: Unknown: 000C534652205769466920464F4E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AEC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001100000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 08 - Address: 7A:A1:D7:34:3E:E7
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"SFR WiFi Mobile"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004b07918450
                    Extra: Last beacon: 5804ms ago
                    IE: Unknown: 000F5346522057694669204D6F62696C65
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AEC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001100000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 09 - Address: 5C:33:8E:CD:13:99
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"Livebox-DJEBA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000c936f51679
                    Extra: Last beacon: 6704ms ago
                    IE: Unknown: 000D4C697665626F782D444A454241
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000900000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010020000000
                    IE: Unknown: 0706465220010D14
          Cell 10 - Address: BA:A1:D7:D1:53:EF
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"SFR WiFi Mobile"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000115de0451e6
                    Extra: Last beacon: 5804ms ago
                    IE: Unknown: 000F5346522057694669204D6F62696C65
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F02C0000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 11 - Address: BA:A1:D7:D1:53:ED
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:off
                    ESSID:"SFR WiFi FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000115de0406e5
                    Extra: Last beacon: 5804ms ago
                    IE: Unknown: 000C534652205769466920464F4E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F02C0000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 12 - Address: 7A:A4:42:A7:92:34
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"ALICE_JEANYVES_WG"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000176c80a0c
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 0011414C4943455F4A45414E595645535F5747
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D160B070600000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: DD1E00904C336E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B070600000000000000000000000000000000000000
          Cell 13 - Address: 00:78:9E:77:EB:E2
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000019821d7335
                    Extra: Last beacon: 7112ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706455520010D14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEC0103FFFFFF00000000000000000000000000000C1846471100
                    IE: Unknown: 3D1601000400000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05010017127A
                    IE: Unknown: DD07000C4307000000
          Cell 14 - Address: 00:78:9E:77:EB:E3
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000019821d7a1e
                    Extra: Last beacon: 7112ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706455520010D14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEC0103FFFFFF00000000000000000000000000000C1846471100
                    IE: Unknown: 3D1601000400000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05010017127A
                    IE: Unknown: DD07000C4307000000
          Cell 15 - Address: E0:A1:D7:34:3E:E4
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"SFR_3EE0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004b03cfc105
                    Extra: Last beacon: 6700ms ago
                    IE: Unknown: 00085346525F33454530
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AEC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001500000000000000000000000000000000000000
                    IE: Unknown: DD840050F204104A0001101044000102103B00010310470010000000000000000000000000000000001021000A4E42362D4658432D72311023000A4E42362D4658432D72311024000A4E42362D4658432D72311042000C4530413144373334334545301054000800060050F2040001101100085346525F33454530100800020084103C000101
                    IE: Unknown: DD090010180201F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 16 - Address: 5C:33:8E:04:95:51
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"Maison-Close"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000067948a0d85
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 000C4D6169736F6E2D436C6F7365
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000900000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010001000000
                    IE: Unknown: 0706465220010D14
                    IE: Unknown: DD880050F204104A000110104400010210570001001041000100103B0001031047001000789EDE2E5200789EDE2E529EDE2E5210210005536167656D102300084C697665626F7832102400084C697665626F78321042000A333231333334354450351054000800060050F20400011011000D4C697665626F78322D32453532100800020086103C000101
          Cell 17 - Address: E0:A1:D7:D1:53:EC
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"NEUF_53E8"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000115de0574e7
                    Extra: Last beacon: 6256ms ago
                    IE: Unknown: 00094E4555465F35334538
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050402030100
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180201F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 18 - Address: 7A:A4:42:A7:92:36
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:off
                    ESSID:"FreeWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000176c81cd8
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 00084672656557696669
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D160B070600000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: DD1E00904C336E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B070600000000000000000000000000000000000000
          Cell 19 - Address: 7A:A4:42:A7:92:37
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"FreeWifi_secure"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000176c82687
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 000F46726565576966695F736563757265
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D160B070600000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: DD1E00904C336E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B070600000000000000000000000000000000000000
          Cell 20 - Address: 7A:A4:42:A7:92:35
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000176c7cb40
                    Extra: Last beacon: 480ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D160B070600000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0502002D127A
                    IE: Unknown: DD1E00904C336E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B070600000000000000000000000000000000000000
                    IE: Unknown: DD07000C4300000000

aladdin@aladdin-MacBookPro:~$ 

```

Thank you very very much !

---

### Post by AladdinVonSane on 2014-06-03
(By the way my box correspond to the cell n°4 (ESSID "kevraedenn"))

---

### Post by Hadaka on 2014-06-03
hi, please go into your router settings and change them
to be wpa2 AES  you currenty have 
Group Cipher : TKIP

that needs to be removed.
then do ..
```
sudo apt-get-update
apt-get autoremove
```
thanks

---

### Post by AladdinVonSane on 2014-06-04
Hi
First I didn't see the type in the first line so I dit apt-get autoremove first.
 Then I look closer and saw the typo so I did sudo apt-get update, 
and after a second time apt-get autoremov

Here the output of all I did : (sorry a lot of code, tell me I you want me to translate in english)
```

aladdin@aladdin-MacBookPro:~$ sudo apt-get-update
sudo: apt-get-update: command not found

aladdin@aladdin-MacBookPro:~$ apt-get autoremove
E: Impossible d'ouvrir le fichier verrou /var/lib/dpkg/lock - open (13: Permission non accordée)
E: Impossible de verrouiller le répertoire d'administration (/var/lib/dpkg/). Avez-vous les privilèges du superutilisateur ?
aladdin@aladdin-MacBookPro:~$ sudo apt-get autoremove
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Les paquets suivants seront ENLEVÉS :
  dkms gcc gcc-4.8 libasan0 libatomic1 libc-dev-bin libc6-dev libgcc-4.8-dev
  libgomp1 libitm1 libtsan0 linux-libc-dev manpages-dev
0 mis à jour, 0 nouvellement installés, 13 à enlever et 0 non mis à jour.
Après cette opération, 41,3 Mo d'espace disque seront libérés.
Souhaitez-vous continuer ? [O/n] o
(Lecture de la base de données... 115461 fichiers et répertoires déjà installés.)
Suppression de dkms (2.2.0.3-1.1ubuntu5) ...
Suppression de gcc (4:4.8.2-1ubuntu6) ...
Suppression de gcc-4.8 (4.8.2-19ubuntu1) ...
Suppression de libgcc-4.8-dev:amd64 (4.8.2-19ubuntu1) ...
Suppression de libasan0:amd64 (4.8.2-19ubuntu1) ...
Suppression de libatomic1:amd64 (4.8.2-19ubuntu1) ...
Suppression de libc6-dev:amd64 (2.19-0ubuntu6) ...
Suppression de libc-dev-bin (2.19-0ubuntu6) ...
Suppression de libgomp1:amd64 (4.8.2-19ubuntu1) ...
Suppression de libitm1:amd64 (4.8.2-19ubuntu1) ...
Suppression de libtsan0:amd64 (4.8.2-19ubuntu1) ...
Suppression de linux-libc-dev:amd64 (3.13.0-24.47) ...
Suppression de manpages-dev (3.54-1ubuntu1) ...
Traitement déclenché pour  man-db (2.6.7.1-1) ...
Traitement déclenché pour  libc-bin (2.19-0ubuntu6) ...

aladdin@aladdin-MacBookPro:~$ sudo apt-get update
[sudo] password for aladdin: 
Ign http://security.ubuntu.com trusty-security InRelease
Ign http://fr.archive.ubuntu.com trusty InRelease                     
Ign http://extras.ubuntu.com trusty InRelease                          
Réception de : 1 http://security.ubuntu.com trusty-security Release.gpg [933 B]
Ign http://fr.archive.ubuntu.com trusty-updates InRelease                                               
Réception de : 2 http://extras.ubuntu.com trusty Release.gpg [72 B]    
Réception de : 3 http://security.ubuntu.com trusty-security Release [58,5 kB]                          
Ign http://fr.archive.ubuntu.com trusty-backports InRelease                                          
Atteint http://extras.ubuntu.com trusty Release                                                      
Atteint http://fr.archive.ubuntu.com trusty Release.gpg                                     
Réception de : 4 http://fr.archive.ubuntu.com trusty-updates Release.gpg [933 B]            
Réception de : 5 http://fr.archive.ubuntu.com trusty-backports Release.gpg [933 B]               
Atteint http://extras.ubuntu.com trusty/main Sources                                                     
Réception de : 6 http://security.ubuntu.com trusty-security/main Sources [16,6 kB]
Atteint http://fr.archive.ubuntu.com trusty Release                                                                             
Atteint http://extras.ubuntu.com trusty/main amd64 Packages                                                                                            
Réception de : 7 http://security.ubuntu.com trusty-security/restricted Sources [14 B]                                            
Réception de : 8 http://fr.archive.ubuntu.com trusty-updates Release [58,5 kB]                                                  
Atteint http://extras.ubuntu.com trusty/main i386 Packages                                                
Réception de : 9 http://security.ubuntu.com trusty-security/universe Sources [4 212 B]                
Réception de : 10 http://security.ubuntu.com trusty-security/multiverse Sources [687 B]                                      
Réception de : 11 http://security.ubuntu.com trusty-security/main amd64 Packages [53,2 kB]                                         
Réception de : 12 http://fr.archive.ubuntu.com trusty-backports Release [58,6 kB]                         
Réception de : 13 http://security.ubuntu.com trusty-security/restricted amd64 Packages [14 B]                                     
Atteint http://fr.archive.ubuntu.com trusty/main Sources                                                                          
Réception de : 14 http://security.ubuntu.com trusty-security/universe amd64 Packages [17,9 kB]            
Atteint http://fr.archive.ubuntu.com trusty/restricted Sources                                                                    
Réception de : 15 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [1 154 B]                                  
Atteint http://fr.archive.ubuntu.com trusty/universe Sources                                                                      
Réception de : 16 http://security.ubuntu.com trusty-security/main i386 Packages [50,7 kB]                 
Atteint http://fr.archive.ubuntu.com trusty/multiverse Sources                                          
Atteint http://fr.archive.ubuntu.com trusty/main amd64 Packages                                                                   
Réception de : 17 http://security.ubuntu.com trusty-security/restricted i386 Packages [14 B]                                      
Atteint http://fr.archive.ubuntu.com trusty/restricted amd64 Packages                                                             
Réception de : 18 http://security.ubuntu.com trusty-security/universe i386 Packages [17,9 kB]             
Atteint http://fr.archive.ubuntu.com trusty/universe amd64 Packages                                                               
Réception de : 19 http://security.ubuntu.com trusty-security/multiverse i386 Packages [1 404 B]                                   
Atteint http://fr.archive.ubuntu.com trusty/multiverse amd64 Packages                                      
Atteint http://fr.archive.ubuntu.com trusty/main i386 Packages                                                                    
Ign http://extras.ubuntu.com trusty/main Translation-fr_FR                                                
Atteint http://fr.archive.ubuntu.com trusty/restricted i386 Packages    
Ign http://extras.ubuntu.com trusty/main Translation-fr                 
Réception de : 20 http://security.ubuntu.com trusty-security/main Translation-en [25,2 kB]
Ign http://extras.ubuntu.com trusty/main Translation-en                                                       
Atteint http://fr.archive.ubuntu.com trusty/universe i386 Packages                                            
Atteint http://fr.archive.ubuntu.com trusty/multiverse i386 Packages    
Atteint http://fr.archive.ubuntu.com trusty/main Translation-fr
Atteint http://security.ubuntu.com trusty-security/multiverse Translation-en
Atteint http://fr.archive.ubuntu.com trusty/main Translation-en
Atteint http://fr.archive.ubuntu.com trusty/multiverse Translation-fr   
Atteint http://security.ubuntu.com trusty-security/restricted Translation-en
Atteint http://fr.archive.ubuntu.com trusty/multiverse Translation-en
Atteint http://fr.archive.ubuntu.com trusty/restricted Translation-fr   
Réception de : 21 http://security.ubuntu.com trusty-security/universe Translation-en [9 065 B]
Atteint http://fr.archive.ubuntu.com trusty/restricted Translation-en        
Atteint http://fr.archive.ubuntu.com trusty/universe Translation-fr     
Atteint http://fr.archive.ubuntu.com trusty/universe Translation-en     
Réception de : 22 http://fr.archive.ubuntu.com trusty-updates/main Sources [51,4 kB]
Réception de : 23 http://fr.archive.ubuntu.com trusty-updates/restricted Sources [14 B]        
Réception de : 24 http://fr.archive.ubuntu.com trusty-updates/universe Sources [29,3 kB]       
Réception de : 25 http://fr.archive.ubuntu.com trusty-updates/multiverse Sources [2 234 B]
Réception de : 26 http://fr.archive.ubuntu.com trusty-updates/main amd64 Packages [135 kB]     
Réception de : 27 http://fr.archive.ubuntu.com trusty-updates/restricted amd64 Packages [14 B]  
Réception de : 28 http://fr.archive.ubuntu.com trusty-updates/universe amd64 Packages [78,8 kB] 
Réception de : 29 http://fr.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [7 089 B]
Réception de : 30 http://fr.archive.ubuntu.com trusty-updates/main i386 Packages [133 kB]       
Réception de : 31 http://fr.archive.ubuntu.com trusty-updates/restricted i386 Packages [14 B]   
Réception de : 32 http://fr.archive.ubuntu.com trusty-updates/universe i386 Packages [79,2 kB]  
Réception de : 33 http://fr.archive.ubuntu.com trusty-updates/multiverse i386 Packages [7 273 B]
Ign http://security.ubuntu.com trusty-security/main Translation-fr_FR                           
Ign http://security.ubuntu.com trusty-security/main Translation-fr      
Réception de : 34 http://fr.archive.ubuntu.com trusty-updates/main Translation-en [64,5 kB]
Ign http://security.ubuntu.com trusty-security/multiverse Translation-fr_FR 
Ign http://security.ubuntu.com trusty-security/multiverse Translation-fr     
Ign http://security.ubuntu.com trusty-security/restricted Translation-fr_FR                           
Ign http://security.ubuntu.com trusty-security/restricted Translation-fr                              
Ign http://security.ubuntu.com trusty-security/universe Translation-fr_FR
Atteint http://fr.archive.ubuntu.com trusty-updates/multiverse Translation-en
Ign http://security.ubuntu.com trusty-security/universe Translation-fr
Atteint http://fr.archive.ubuntu.com trusty-updates/restricted Translation-en
Réception de : 35 http://fr.archive.ubuntu.com trusty-updates/universe Translation-en [35,7 kB]
Réception de : 36 http://fr.archive.ubuntu.com trusty-backports/main Sources [14 B]
Réception de : 37 http://fr.archive.ubuntu.com trusty-backports/restricted Sources [14 B]
Réception de : 38 http://fr.archive.ubuntu.com trusty-backports/universe Sources [5 045 B]
Réception de : 39 http://fr.archive.ubuntu.com trusty-backports/multiverse Sources [768 B]
Réception de : 40 http://fr.archive.ubuntu.com trusty-backports/main amd64 Packages [14 B]
Réception de : 41 http://fr.archive.ubuntu.com trusty-backports/restricted amd64 Packages [14 B]
Réception de : 42 http://fr.archive.ubuntu.com trusty-backports/universe amd64 Packages [5 764 B]
Réception de : 43 http://fr.archive.ubuntu.com trusty-backports/multiverse amd64 Packages [619 B]
Réception de : 44 http://fr.archive.ubuntu.com trusty-backports/main i386 Packages [14 B]
Réception de : 45 http://fr.archive.ubuntu.com trusty-backports/restricted i386 Packages [14 B]
Réception de : 46 http://fr.archive.ubuntu.com trusty-backports/universe i386 Packages [5 773 B]
Réception de : 47 http://fr.archive.ubuntu.com trusty-backports/multiverse i386 Packages [619 B]
Atteint http://fr.archive.ubuntu.com trusty-backports/main Translation-en
Atteint http://fr.archive.ubuntu.com trusty-backports/multiverse Translation-en
Atteint http://fr.archive.ubuntu.com trusty-backports/restricted Translation-en
Réception de : 48 http://fr.archive.ubuntu.com trusty-backports/universe Translation-en [3 655 B]
Ign http://fr.archive.ubuntu.com trusty/main Translation-fr_FR                                                                                              
Ign http://fr.archive.ubuntu.com trusty/multiverse Translation-fr_FR                                                                                        
Ign http://fr.archive.ubuntu.com trusty/restricted Translation-fr_FR                                                                                        
Ign http://fr.archive.ubuntu.com trusty/universe Translation-fr_FR                                                                                          
Ign http://fr.archive.ubuntu.com trusty-updates/main Translation-fr_FR                                                                                      
Ign http://fr.archive.ubuntu.com trusty-updates/main Translation-fr                                                                                         
Ign http://fr.archive.ubuntu.com trusty-updates/multiverse Translation-fr_FR                                                                                
Ign http://fr.archive.ubuntu.com trusty-updates/multiverse Translation-fr                                                                                   
Ign http://fr.archive.ubuntu.com trusty-updates/restricted Translation-fr_FR                                                                                
Ign http://fr.archive.ubuntu.com trusty-updates/restricted Translation-fr                                                                                   
Ign http://fr.archive.ubuntu.com trusty-updates/universe Translation-fr_FR                                                                                  
Ign http://fr.archive.ubuntu.com trusty-updates/universe Translation-fr                                                                                     
Ign http://fr.archive.ubuntu.com trusty-backports/main Translation-fr_FR                                                                                    
Ign http://fr.archive.ubuntu.com trusty-backports/main Translation-fr                                                                                       
Ign http://fr.archive.ubuntu.com trusty-backports/multiverse Translation-fr_FR                                                                              
Ign http://fr.archive.ubuntu.com trusty-backports/multiverse Translation-fr                                                                                 
Ign http://fr.archive.ubuntu.com trusty-backports/restricted Translation-fr_FR                                                                              
Ign http://fr.archive.ubuntu.com trusty-backports/restricted Translation-fr                                                                                 
Ign http://fr.archive.ubuntu.com trusty-backports/universe Translation-fr_FR                                                                                
Ign http://fr.archive.ubuntu.com trusty-backports/universe Translation-fr                                                                                   
1 022 ko réceptionnés en 8s (118 ko/s)                                                                                                                      
Lecture des listes de paquets... Fait

aladdin@aladdin-MacBookPro:~$ sudo apt-get autoremove
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
0 mis à jour, 0 nouvellement installés, 0 à enlever et 29 non mis à jour.

```

---

### Post by AladdinVonSane on 2014-06-04
But I could configure my router as a WPA2/AES
Here the correspondig router in the iw list
```


     Cell 05 - Address: 54:22:F8:0D:2D:64
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:"kevreadenn"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000004d329d49
                    Extra: Last beacon: 68ms ago
                    IE: Unknown: 000A6B657672656164656E6E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: 0706465220010D14
                    IE: Unknown: DD920050F204104A0001101044000102103B00010310470010000000000000100000005422F80D2D64102100035A54451023000F4C697665626F7820465454482076321024001A6164363833365F4144534C5F5048595F30783030303030303030104200074C4D5A313330371054000800060050F20400011011000D465446525341332E3639313631100800020086103C000101

```

Thanks you very much again !

---

### Post by Hadaka on 2014-06-04
Hi, your wifi should be working...lets try some diagnostics
and see what might be the issue, please read and follow the
instructions carefully...[http://ubuntuforums.org/showthread.php?t=2224209&p=13024222#post13024222](http://ubuntuforums.org/showthread.php?t=2224209&p=13024222#post13024222)
post the results
thanks,

---

### Post by AladdinVonSane on 2014-06-04
Hi, 
So I use that code : 
```

wget -N -t 5 -T 10 https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script && chmod +x wireless_script && ./wireless_script 
```

And here the result : 
```

|:443&#8230; connecté.
requête HTTP transmise, en attente de la réponse&#8230; 200 OK
Taille : 15521 (15K) [text/plain]
Enregistre : «wireless_script»

100%[======================================>] 15 521      --.-K/s   ds 0s      

En-tête de dernière modification manquant &#8212; horodatage arrêté.
2014-06-05 00:41:22 (96,3 MB/s) - «wireless_script» enregistré [15521/15521]



        **** PLEASE WAIT WHILE THE SCRIPT GENERATES THE REPORT ****
  
  If this takes more than 1 minute, you may abort the script by pressing
  "Ctrl+Z" on your keyboard.
  
  (Type your Login Password when asked, then press 'Enter')

[sudo] password for aladdin: 


    ########################################################################

    DONE! All results saved in -

		 File Name: 	"wireless-info.tar.gz" 
		 Directory: 	"/home/aladdin"

    Please upload the above file or its contents where you are seeking help.

    ------------------------------------------------------------------------
    NOTE: Although we have taken full precaution to filter out all sensitive
          information, it is recommended to take a look at the file yourself
          to be double sure that it contains no sensitive data.
    ------------------------------------------------------------------------

    ########################################################################


```

I think I have to upload a file but I thought I did it via the codes you gave me, is there any other problem occur on my computer ? 

thanks !

---

### Post by Hadaka on 2014-06-04
please do,'
```
wget -N -t 5 -T 10 https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script && chmod +x wireless_script && ./wireless_script
```
then READ the instructions...you should have a info.txt file in your home directory...that is the one to paste'''' \\\
,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,READ THE INSTRUCTIONS

---

### Post by AladdinVonSane on 2014-06-25
Hi, 
Sorry for the time without answer, I moved, so I could do anything. 
So  I try to upload the file like the instruction said, but I just don't  succeed finding the upload command, I tried 'put', 'mput', or 'upgrade', but the command still unfound... I also tried to lunch directly the script 'wireless_script', but I don't see the difference, how can I update? 

Thanks a lot in advance _

---

### Post by AladdinVonSane on 2014-06-25
C*** I have a problem with my disks on my macbook pro, so I have to delete my lubuntu part, and install it again, but I will read again your instruction since the beggining of this topic ! (And maybe install ubuntu and not lubuntu, once I installed ubuntu and I didn't have this problem)

Thanks again for all !

---

