---
title: "Ubuntu 18.04 wifi unstable"
date: 2018-11-30
forum: Networking &amp; Wireless
---

### Post by Liis on 2018-11-30
Hello

Everything works just fine before I install Ubuntu 18.04 (before i had 16.04). Wifi is stable abut 10-15 min then disconnect and after a while connects itself again. What should I do, please help! :(

---

### Post by chili555 on 2018-12-01
Please provide the wireless diagnostics from here: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

### Post by jeremy31 on 2018-12-01
Moved to Networking and wireless

---

### Post by cam17 on 2018-12-02
I have a similar problem where the wifi starts up after a few minutes by itself and it only started about a month ago. Did you find a solution?

---

### Post by chili555 on 2018-12-02
> **cam17 said:**
> I have a similar problem where the wifi starts up after a few minutes by itself and it only started about a month ago. Did you find a solution?Please start your own new thread. It is very doubtful that you have the same issue and, most particularly, the same wireless device as the original poster.

---

### Post by Liis on 2018-12-17
Sorry, but it didn't helped me. Same problem..also i can't connect with wired internet.

---

### Post by chili555 on 2018-12-17
> **Liis said:**
> Sorry, but it didn't helped me. Same problem..also i can't connect with wired internet.I asked that you provide the diagnostic report so we can try to see what the problem is; merely running the report isn’t designed to fix anything.

---

### Post by Liis on 2018-12-17
```
liis@liis-Inspiron-3521:~$ sudo apt update
[sudo] password for liis: 
Sorry, try again.
[sudo] password for liis: 
Hit:1 [http://ppa.launchpad.net/linrunner/tlp/ubuntu](http://ppa.launchpad.net/linrunner/tlp/ubuntu) bionic InRelease
Hit:2 [https://installer.id.ee/media/ubuntu](https://installer.id.ee/media/ubuntu) bionic InRelease                    
Hit:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic InRelease                     
Hit:4 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic InRelease               
Hit:6 [http://archive.canonical.com](http://archive.canonical.com) bionic InRelease                      
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates InRelease [88.7 kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports InRelease [74.6 kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-security InRelease [83.2 kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe Sources [121 kB]
Get:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 DEP-11 Metadata [245 kB]
Get:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main DEP-11 48x48 Icons [55.7 kB]
Get:12 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main DEP-11 64x64 Icons [109 kB]
Get:13 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe amd64 Packages [705 kB]
Get:14 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe i386 Packages [698 kB]
Get:15 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe Translation-en [171 kB]
Get:16 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe amd64 DEP-11 Metadata [199 kB]
Get:17 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe DEP-11 48x48 Icons [174 kB]
Get:18 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe DEP-11 64x64 Icons [329 kB]
Get:19 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/multiverse amd64 DEP-11 Metadata [2,468 B]
Get:20 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports/universe amd64 DEP-11 Metadata [5,816 B]
Get:21 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-security/main amd64 DEP-11 Metadata [204 B]
Get:22 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-security/universe amd64 DEP-11 Metadata [14.8 kB]
Get:23 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-security/universe DEP-11 48x48 Icons [9,088 B]
Get:24 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-security/universe DEP-11 64x64 Icons [39.8 kB]
Fetched 3,005 kB in 10s (310 kB/s)                                             
sudo apt install pastebinit
Reading package lists... Done
Building dependency tree       
Reading state information... Done
3 packages can be upgraded. Run 'apt list --upgradable' to see them.
liis@liis-Inspiron-3521:~$ sudo apt install pastebinit
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pastebinit is already the newest version (1.5-2).
The following packages were automatically installed and are no longer required:
  libxerces-c3.1 libxml-security-c17v5
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
liis@liis-Inspiron-3521:~$ wget -N -t 5 -T 10 [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info) && \
> chmod +x wireless-info && \
> ./wireless-info
--2018-12-17 16:05:06--  [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info)
Resolving github.com (github.com)... 140.82.118.3, 140.82.118.4
Connecting to github.com (github.com)|140.82.118.3|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: [https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info](https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info) [following]
--2018-12-17 16:05:08--  [https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info](https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info)
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 151.101.84.133
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|151.101.84.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 17452 (17K) [text/plain]
Saving to: &#8216;wireless-info&#8217;


wireless-info       100%[===================>]  17.04K  --.-KB/s    in 0.03s   


Last-modified header missing -- time-stamps turned off.
2018-12-17 16:05:09 (631 KB/s) - &#8216;wireless-info&#8217; saved [17452/17452]




Results saved in "/home/liis/wireless-info.txt".


Results also archived in "/home/liis/wireless-info.tar.gz", as they exceed the 19.5 kB size limit for ".txt" attachments on the Ubuntu Forums.


Do you also want to post them to your default 'pastebinit' provider? [Y/n]: y


Pastebin successful:


[http://paste.ubuntu.com/p/P3S9rmnVjh/](http://paste.ubuntu.com/p/P3S9rmnVjh/)
```


Sorry, this was the result!?

---

### Post by chili555 on 2018-12-17
> Pastebin successful:


[http://paste.ubuntu.com/p/P3S9rmnVjh/](http://paste.ubuntu.com/p/P3S9rmnVjh/)Yes, indeed!

We notice this in your results:

```
ath9k                 151552  0
ath9k_common           36864  1 ath9k
ath9k_hw              471040  2 ath9k_common,ath9k
ath                    28672  3 ath9k_common,ath9k,ath9k_hw
dell_smbios            24576  2 dell_wmi,dell_laptop
mac80211              778240  1 ath9k
dell_wmi_descriptor    16384  2 dell_wmi,dell_smbios
wmi_bmof               16384  0
cfg80211              622592  5 wl,ath9k_common,ath9k,ath,mac80211
```wl is a driver for Broadcom devices and won't help your Atheros at all. Let's remove it.```
sudo apt-get purge bcmwl-kernel-source
```We also see:

```
[/etc/network/interfaces]
auto lo
iface lo inet loopback
[COLOR="#B22222"]auto eth0
iface eth0 inet dhcp[/COLOR]
```The eth0 entries mean that Network Manager will no longer manage the ethernet. I doubt that that is what you intend. Please carefully edit the file to remove the lines I've highlighted.

We also see:> 
Cell 01 - Address: <MAC 'Thomson1AB4DF' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"Thomson1AB4DF"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002d1fea4677
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/[COLOR="#B22222"]WPA2 [/COLOR]Version 1
                        Group Cipher : [COLOR="#B22222"]TKIP[/COLOR]
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: [COLOR="#B22222"]WPA[/COLOR] Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSKMany Linux wireless drivers hate hate hate TKIP. Old Chili hates it because it's rather insecure.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:

   ```
 sudo iw reg get
```

If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:

    ```
sudo iw reg set IS
```

Of course, substitute your country code if not Iceland. Set it permanently:

    ```
sudo nano /etc/default/crda
```

Change the last line to read:

    ```
REGDOMAIN=IS
```

Proofread carefully, save and close the text editor.

Reboot and let us hear your report.

---

### Post by Liis on 2018-12-17
liis@liis-Inspiron-3521:~$ sudo apt update
[sudo] password for liis: 
Sorry, try again.
[sudo] password for liis: 
Hit:1 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic InRelease
Hit:2 [http://ppa.launchpad.net/linrunner/tlp/ubuntu](http://ppa.launchpad.net/linrunner/tlp/ubuntu) bionic InRelease           
Hit:3 [https://installer.id.ee/media/ubuntu](https://installer.id.ee/media/ubuntu) bionic InRelease                    
Hit:4 [http://archive.canonical.com](http://archive.canonical.com) bionic InRelease                            
Hit:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic InRelease               
Get:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates InRelease [88.7 kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports InRelease [74.6 kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-security InRelease [83.2 kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 DEP-11 Metadata [245 kB]
Get:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main DEP-11 48x48 Icons [54.0 kB]
Get:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main DEP-11 64x64 Icons [105 kB]
Get:12 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe i386 Packages [698 kB]
Get:13 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe amd64 Packages [706 kB]
Get:14 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe amd64 DEP-11 Metadata [200 kB]
Get:15 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe DEP-11 48x48 Icons [178 kB]
Get:16 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe DEP-11 64x64 Icons [337 kB]
Get:17 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/multiverse amd64 DEP-11 Metadata [2,468 B]
Get:18 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports/universe amd64 DEP-11 Metadata [5,812 B]
Get:19 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-security/main amd64 DEP-11 Metadata [204 B]
Get:20 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-security/universe amd64 DEP-11 Metadata [14.9 kB]
Get:21 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-security/universe DEP-11 48x48 Icons [9,088 B]
Get:22 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-security/universe DEP-11 64x64 Icons [39.7 kB]
Fetched 2,841 kB in 7s (436 kB/s)                                              
Reading package lists... Done
Building dependency tree       
Reading state information... Done
3 packages can be upgraded. Run 'apt list --upgradable' to see them.
liis@liis-Inspiron-3521:~$ 
liis@liis-Inspiron-3521:~$ sudo apt install pastebinit
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pastebinit is already the newest version (1.5-2).
The following packages were automatically installed and are no longer required:
  libxerces-c3.1 libxml-security-c17v5
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
liis@liis-Inspiron-3521:~$ #!/bin/bash
liis@liis-Inspiron-3521:~$ #
liis@liis-Inspiron-3521:~$ # Copyright (c) 2012
liis@liis-Inspiron-3521:~$ #
liis@liis-Inspiron-3521:~$ # Authors: Wild Man, Krytarik
liis@liis-Inspiron-3521:~$ # Helpers: chili555
liis@liis-Inspiron-3521:~$ #
liis@liis-Inspiron-3521:~$ # This script gathers the infos necessary for troubleshooting a wireless
liis@liis-Inspiron-3521:~$ # connection and saves them in a text file, wrapping it in an archive if it
liis@liis-Inspiron-3521:~$ # exceeds the 19.5 kB size limit for ".txt" attachments on the Ubuntu Forums.
liis@liis-Inspiron-3521:~$ #
liis@liis-Inspiron-3521:~$ ##############################################################################
liis@liis-Inspiron-3521:~$ #
liis@liis-Inspiron-3521:~$ # This program is free software: you can redistribute it and/or modify
liis@liis-Inspiron-3521:~$ # it under the terms of the GNU General Public License as published by
liis@liis-Inspiron-3521:~$ # the Free Software Foundation, either version 3 of the License, or
liis@liis-Inspiron-3521:~$ # (at your option) any later version.
liis@liis-Inspiron-3521:~$ #
liis@liis-Inspiron-3521:~$ # This program is distributed in the hope that it will be useful,
liis@liis-Inspiron-3521:~$ # but WITHOUT ANY WARRANTY; without even the implied warranty of
liis@liis-Inspiron-3521:~$ # MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
liis@liis-Inspiron-3521:~$ # GNU General Public License for more details.
liis@liis-Inspiron-3521:~$ #
liis@liis-Inspiron-3521:~$ # You should have received a copy of the GNU General Public License
liis@liis-Inspiron-3521:~$ # along with this program.  If not, see <http://www.gnu.org/licenses/>.
liis@liis-Inspiron-3521:~$ #
liis@liis-Inspiron-3521:~$ 
liis@liis-Inspiron-3521:~$ SCRIPTDATE="2018-10-22 05:34 +0200"
liis@liis-Inspiron-3521:~$ FILEBASE="wireless-info"
liis@liis-Inspiron-3521:~$ OUTPUTDIR="$PWD"
liis@liis-Inspiron-3521:~$ OUTPUTDIRFB="/tmp"
liis@liis-Inspiron-3521:~$ 
liis@liis-Inspiron-3521:~$ MODMATCHES="(air|ar5|at7|ath[^3]?|b43|bcma|brcm|carl|ipw|iwl|ndis|r(818|8192[eu]|871|92su)|8(188|189|192|723|812)[acde][esu]|rt[23567]|rtl|ssb|wl|(cfg|mac)80211)"
liis@liis-Inspiron-3521:~$ LSMODMATCHES="(wmi|(dell|ideapad)[-_]laptop)"
liis@liis-Inspiron-3521:~$ IFACEMATCHES="(wlan[0-9]|eth[0-9])"
liis@liis-Inspiron-3521:~$ DMESGMATCHES="(firmware|[nN]etwork|sdio|SDIO)"
liis@liis-Inspiron-3521:~$ NMPROFMATCHES="\(\[connection\]\|id=\|type=\|permissions=\|autoconnect=\|\[802-11-wireless\]\|\[wifi\]\|ssid=\|bssid=\|mac-address\(-blacklist\)\?=\|mtu=\|\[802-1x\]\|[[:graph:]]*ca-certs\?=\|\[ipv[46]\]\|method=\)"
liis@liis-Inspiron-3521:~$ 
liis@liis-Inspiron-3521:~$ DMESGEXCL="apparmor|(cfg|mac)80211"
liis@liis-Inspiron-3521:~$ MODINFOEXCL="alias"
liis@liis-Inspiron-3521:~$ MODPROBEXCL="(alsa-base|blacklist-(firewire|framebuffer|modem|oss|watchdog)|fglrx|nvidia|fbdev|bumblebee)"
liis@liis-Inspiron-3521:~$ PMUTILSEXCL="/etc/pm/(power.d/(95hdparm-apm|intel-audio-powersave|sata_alpm)|sleep.d/(10_grub-common|10_unattended-upgrades.*|novatel_3g.*))"
liis@liis-Inspiron-3521:~$ 
liis@liis-Inspiron-3521:~$ NETMGRNAMES=("NetworkManager" "Wicd" "ConnMan")
liis@liis-Inspiron-3521:~$ NETMGRPATHS=("/usr/sbin/NetworkManager" "/usr/sbin/wicd" "/usr/sbin/connmand")
liis@liis-Inspiron-3521:~$ DEC2BI=({0..1}{0..1}{0..1}{0..1}{0..1}{0..1}{0..1}{0..1})
liis@liis-Inspiron-3521:~$ DEC2HEX=($(printf "%02x " {0..255}))
liis@liis-Inspiron-3521:~$ 
liis@liis-Inspiron-3521:~$ export LANG="en_US.UTF-8"
liis@liis-Inspiron-3521:~$ export LANGUAGE="en_US:en"
liis@liis-Inspiron-3521:~$ export LC_ALL="en_US.UTF-8"
liis@liis-Inspiron-3521:~$ 
liis@liis-Inspiron-3521:~$ if [ -t 0 ]; then
>     DIALOGAPP="terminal"
>     DIALOGBREAK=" "
>     TERMOUT="yes"
> elif [ -x /usr/bin/zenity ]; then
>     DIALOGAPP="zenity"
>     DIALOGBREAK="\n"
> elif [ -x /usr/bin/kdialog ]; then
>     DIALOGAPP="kdialog"
ESFILE" "$IFACESFLCNT"
    fi
done


printf "\n##### ifconfi>     DIALOGBREAK="\n"
> else
>     exit 1
> fi
liis@liis-Inspiron-3521:~$ 
liis@liis-Inspiron-3521:~$ if [ -t 0 ]; then
>     SUDO="sudo"
> elif [ -x /usr/bin/pkexec ]; then
>     SUDO="pkexec"
> elif [ -x /usr/bin/gksudo ]; then
>     SUDO="gksudo"
>     GKSUDO="yes"
> elif [ -x /usr/bin/kdesudo ]; then
>     SUDO="kdesudo"
>     KDESUDO="yes"
>     KDESUDOCMT=" needs administrative privileges. Please enter your password."
> fi
liis@liis-Inspiron-3521:~$ 
liis@liis-Inspiron-3521:~$ dialog_info () {
>     case $DIALOGAPP in
> terminal)
>     printf "%b\n" "$1"
>     ;;
> zenity)
>     zenity --info --text="$1"
>     ;;
> kdialog)
>     kdialog --msgbox "$1"
>     ;;
>     esac
> }
MAliis@liis-Inspiron-3521:~$ 
Tliis@liis-Inspiron-3521:~$ dialog_error () {
>     case $DIALOGAPP in
> terminal)
>     printf "%b\n" "$1" >&2
>     ;;
> zenity)
>     zenity --error --text="$1"
>     ;;
> kdialog)
>     kdialog --error "$1"
>     ;;
>     esac
> }
ouliis@liis-Inspiron-3521:~$ 
tliis@liis-Inspiron-3521:~$ dialog_question () {
>     case $DIALOGAPP in
> terminal)
>     local INPUT
>     read -r -p "$1 [Y/n]: " INPUT
>     echo "${INPUT,,}"
>     ;;
> zenity)
>     zenity --question --text="$1" || echo "no"
>     ;;
> kdialog)
>     kdialog --yesno "$1" || echo "no"
>     ;;
>     esac
> }
agliis@liis-Inspiron-3521:~$ 
liis@liis-Inspiron-3521:~$ ip6-mac () {
>     for MAC in "$@"; do
> OCT1BI=${DEC2BI[0x${MAC:0:2}]}
> OCT1BI7=$((${OCT1BI:6:1} - 1))
> OCT1BIM="${OCT1BI:0:6}${OCT1BI7#-}${OCT1BI:7}"
> IP6S+=${IP6S:+$'\n'}"${DEC2HEX[2#$OCT1BIM]}${MAC:3:2}:${MAC:6:2}ff:fe${MAC:9:2}:${MAC:12:2}${MAC:15:2}"
>     done
>     sed 's/\(^\|:\)0\+\([[:alnum:]]\)/\1\2/g;s/^\([0:]\+\)/\\(::\\|\1\\)/' <<< "$IP6S"
> }
liis@liis-Inspiron-3521:~$ 
liis@liis-Inspiron-3521:~$ exec 3>&1 4>&2
liis@liis-Inspiron-3521:~$ exec 1> "$OUTPUTDIR/$FILEBASE.txt" || {
>     dialog_error "${TERMOUT+\n}Cannot write output file in \"$OUTPUTDIR\",${DIALOGBREAK}trying in \"$OUTPUTDIRFB\" instead.${TERMOUT+\n}"
>     OUTPUTDIR="$OUTPUTDIRFB"
>     exec 1> "$OUTPUTDIR/$FILEBASE.txt" || {
> dialog_error "${TERMOUT+\n}Cannot write output file in \"$OUTPUTDIR\" either, aborting.${TERMOUT+\n}"
> exit 1
>     }
> }
liis@liis-Inspiron-3521:~$ exec 2>&1
\F\Eliis@liis-Inspiron-3521:~$ exec 1>&3 3>&-
liis@liis-Inspiron-3521:~$ 
liis@liis-Inspiron-3521:~$ ##### MAC address masking #####
liis@liis-Inspiron-3521:~$ 
liis@liis-Inspiron-3521:~$ RESULTS=$(cat -s "$OUTPUTDIR/$FILEBASE.txt")$'\n'
liis@liis-Inspiron-3521:~$ 
liis@liis-Inspiron-3521:~$ ORIGIFS="$IFS"
liis@liis-Inspiron-3521:~$ IFS=$'\n'
liis@liis-Inspiron-3521:~$ 
liis@liis-Inspiron-3521:~$ IFACESIDS=($(sed -n "/\([[:alnum:]]\{2\}:\)\{5\}[[:alnum:]]\{2\}/ {/\(00:\)\{5\}00/! {s/^[0-9]\+: \([^ :]\+\):.*/'\1'/p; s/^\([^ :]\+\):\? .*/'\1'/p}}" <<< "$IFCONFIG"))
liis@liis-Inspiron-3521:~$ IFACESMACS=($(sed -n '/\(00:\)\{5\}00/! s#.*\(HWaddr\|link/[^ ]\+\|ether\) \(\([[:alnum:]]\{2\}:\)\{5\}[[:alnum:]]\{2\}\).*#\2#p' <<< "$IFCONFIG"))
liis@liis-Inspiron-3521:~$ IFACESIP6S=($(ip6-mac "${IFACESMACS[@]}"))
liis@liis-Inspiron-3521:~$ 
liis@liis-Inspiron-3521:~$ WLAPSIWLIDS=($(sed -n "/^[ ]*Cell [0-9]\+/,/^[ ]*ESSID:/ {/^[ ]*Cell [0-9]\+/h; /^[ ]*ESSID:/ {H;g;s/^[ ]*Cell 0\?\([0-9]\+\).*ESSID:\"\(.*\)\"$/'\2' [AC\1]/p}}" <<< "$IWLISTSCAN"))
liis@liis-Inspiron-3521:~$ WLAPSIWLMACS=($(sed -n 's/^[ ]*Cell [0-9]\+.*Address: \([^ ]\+\)/\1/p' <<< "$IWLISTSCAN"))
liis@liis-Inspiron-3521:~$ WLAPSIWLIP6S=($(ip6-mac "${WLAPSIWLMACS[@]}"))
liis@liis-Inspiron-3521:~$ 
liis@liis-Inspiron-3521:~$ WLAPSNMRAW=$(sed -n '/^##### NetworkManager info #####/,/^##### / {/^[ ]*Wireless Access Points/,/^$/ {/Wireless Access Points/d;s/^[ ]\+\*\?//;s/:[ ]\+/\t/;p}; /^SSID[ ]\+BSSID[ ]\+/,/^$/ {/^SSID[ ]\{2,\}BSSID[ ]\{2,\}/d;s/[ ]\{2,\}/\t/;p}}' <<< "$RESULTS")
liis@liis-Inspiron-3521:~$ WLAPSNMIDS=($(awk -F '\t' '{print "'\''" $1 "'\''"}' <<< "$WLAPSNMRAW"))
liis@liis-Inspiron-3521:~$ WLAPSNMMACS=($(grep -o '\([[:alnum:]]\{2\}:\)\{5\}[[:alnum:]]\{2\}' <<< "$WLAPSNMRAW"))
liis@liis-Inspiron-3521:~$ WLAPSNMIP6S=($(ip6-mac "${WLAPSNMMACS[@]}"))
liis@liis-Inspiron-3521:~$ 
liis@liis-Inspiron-3521:~$ IFS="$ORIGIFS"
liis@liis-Inspiron-3521:~$ 
liis@liis-Inspiron-3521:~$ for IFACENR in "${!IFACESMACS[@]}"; do
>     MACMASKSED+="s;${IFACESMACS[$IFACENR]};<MAC ${IFACESIDS[$IFACENR]} [IF$(($IFACENR + 1))]>;I;"
>     MACMASKSED+=" /${IFACESIP6S[$IFACENR]}/ s;${IFACESIP6S[$IFACENR]/#\\(::/\(};<IP6 ${IFACESIDS[$IFACENR]} [IF$(($IFACENR + 1))]>;I;"
>     IFACEMACC=${IFACESMACS[$IFACENR]//:/}
>     if [[ ${IFACESIDS[$IFACENR],,} =~ ${IFACEMACC,,} ]]; then
> MACMASKSED+="s;\(${IFACESIDS[$IFACENR]:1:3}\)$IFACEMACC;\1<IF from MAC [IF$(($IFACENR + 1))]>;Ig;"
>     fi
> done
liis@liis-Inspiron-3521:~$ 
liis@liis-Inspiron-3521:~$ for WLAPIWLNR in "${!WLAPSIWLMACS[@]}"; do
>     MACMASKSED+="s;${WLAPSIWLMACS[$WLAPIWLNR]};<MAC ${WLAPSIWLIDS[$WLAPIWLNR]}>;I;"
>     MACMASKSED+=" /${WLAPSIWLIP6S[$WLAPIWLNR]}/ s;${WLAPSIWLIP6S[$WLAPIWLNR]/#\\(::/\(};<IP6 ${WLAPSIWLIDS[$WLAPIWLNR]}>;I;"
> done
liis@liis-Inspiron-3521:~$ 
liis@liis-Inspiron-3521:~$ for WLAPNMNR in "${!WLAPSNMMACS[@]}"; do
>     MACMASKSED+="s;${WLAPSNMMACS[$WLAPNMNR]};<MAC ${WLAPSNMIDS[$WLAPNMNR]} [AN$(($WLAPNMNR + 1))]>;I;"
>     MACMASKSED+=" /${WLAPSNMIP6S[$WLAPNMNR]}/ s;${WLAPSNMIP6S[$WLAPNMNR]/#\\(::/\(};<IP6 ${WLAPSNMIDS[$WLAPNMNR]} [AN$(($WLAPNMNR + 1))]>;I;"
> done
liis@liis-Inspiron-3521:~$ 
liis@liis-Inspiron-3521:~$ sed "$MACMASKSED /\([[:alnum:]]\{2\}:\)\{6,\}/! s/\([[:alnum:]]\{2\}:\)\{5\}[[:alnum:]]\{2\}/<MAC address>/g" <<< "$RESULTS" > "$OUTPUTDIR/$FILEBASE.txt"
liis@liis-Inspiron-3521:~$ 
liis@liis-Inspiron-3521:~$ ##### The End #####
liis@liis-Inspiron-3521:~$ 
liis@liis-Inspiron-3521:~$ dialog_info "${TERMOUT+\n}Results saved in \"$OUTPUTDIR/$FILEBASE.txt\".${TERMOUT+\n}"


Results saved in "/home/liis/wireless-info.txt".


liis@liis-Inspiron-3521:~$ 
liis@liis-Inspiron-3521:~$ if (( $(stat -c %s "$OUTPUTDIR/$FILEBASE.txt") > 19968 )); then
>     tar -czf "$OUTPUTDIR/$FILEBASE.tar.gz" -C "$OUTPUTDIR" "$FILEBASE.txt" && \
> dialog_info "Results also archived in \"$OUTPUTDIR/$FILEBASE.tar.gz\",${DIALOGBREAK}as they exceed the 19.5 kB size limit for \".txt\" attachments${DIALOGBREAK}on the Ubuntu Forums.${TERMOUT+\n}" || \
> dialog_error "Results exceed the 19.5 kB size limit for \".txt\" attachments${DIALOGBREAK}on the Ubuntu Forums, but archive could not be created.${TERMOUT+\n}"
> fi
Results also archived in "/home/liis/wireless-info.tar.gz", as they exceed the 19.5 kB size limit for ".txt" attachments on the Ubuntu Forums.


liis@liis-Inspiron-3521:~$ 
liis@liis-Inspiron-3521:~$ if [ -x /usr/bin/pastebinit ] && ping -nc 3 -w 6 -i 0.2 paste.ubuntu.com > /dev/null 2>&1; then
>     PASTEBIN=$(dialog_question "Do you also want to post them${DIALOGBREAK}to your default 'pastebinit' provider?")
>     if [[ ! $PASTEBIN =~ ^no?$ ]]; then
> PASTERESULT=$(pastebinit -i "$OUTPUTDIR/$FILEBASE.txt" -f text 2>&1) && PASTESUCCESS="yes"
> if [ "$PASTESUCCESS" = "yes" ]; then
>     dialog_info "${TERMOUT+\n}Pastebin successful:\n\n${PASTERESULT}${TERMOUT+\n}"
> else
>     if [ -n "$PASTERESULT" ]; then
> 
Display all 3455 possibilities? (y or n)
:
!
./
[
[[
]]
{
}
2to3-2.7
411toppm
7z
7za
7zr
a11y-profile-manager-indicator
aa-enabled
aa-exec
aa-remove-unknown
aa-status
accept
accessdb
aclocal
aclocal-1.15
aconnect
> }Pastebin failed, error message is:\n\n${PASTERESULT}${TERMOUT+\n}"
>     else
> 
Display all 232 possibilities? (y or n)
123/                                  .goutputstream-JR8ADX
.:60-fakexinerama                     .goutputstream-JR9NLX
.adobe/                               .goutputstream-JWJ9DX
.AMD/                                 .goutputstream-KAXOFX
.apport-ignore.xml                    .goutputstream-KJFATX
.avidemux/                            .goutputstream-LCT4DX
.bash_history                         .goutputstream-LDHBHX
.bash_logout                          .goutputstream-LGEZDX
.bashrc                               .goutputstream-LPI1SX
.cache/                               .goutputstream-M36HDX
.clamtk/                              .goutputstream-M4C0HY
compat-wireless-3.6.6-1-snpc/         .goutputstream-MC47PX
compat-wireless-3.6.6-1-snpc.tar.bz2  .goutputstream-MR5BEX
.compiz/                              .goutputstream-N55MRY
.compiz-1/                            .goutputstream-NA3N1X
.config/                              .goutputstream-NDUTYX
.dbus/                                .goutputstream-NK95QX
desktop/                              .goutputstream-NSFBIY
.digidocpp/                           .goutputstream-O82QHX
.dmrc                                 .goutputstream-OA5YAY
Downloads/                            .goutputstream-OPTWLX
.fakexinerama                         .goutputstream-ORYBRY
.fctsslvpnhistory                     .goutputstream-P37MEY
> }Pastebin failed, no error message given.${TERMOUT+\n}"
>     fi
> fi
>     else
> echo
>     fi
> fi
Do you also want to post them to your default 'pastebinit' provider? [Y/n]: wget -N -t 5 -T 10 [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info) && \
chmod +x wireless-info && \
./wireless-info
Pastebin successful:


[http://paste.ubuntu.com/p/SvkhqdmtKp/](http://paste.ubuntu.com/p/SvkhqdmtKp/)


liis@liis-Inspiron-3521:~$ chmod +x wireless-info && \
> ./wireless-info


I hope I did it right.

---

### Post by chili555 on 2018-12-17
> liis@liis-Inspiron-3521:~$ sudo apt update
[sudo] password for liis: 
Sorry, try again.
[sudo] password for liis: 
Hit:1 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic InRelease
Hit:2 [http://ppa.launchpad.net/linrunner/tlp/ubuntu](http://ppa.launchpad.net/linrunner/tlp/ubuntu) bionic InRelease 
Hit:3 [https://installer.id.ee/media/ubuntu](https://installer.id.ee/media/ubuntu) bionic InRelease 
Hit:4 [http://archive.canonical.com](http://archive.canonical.com) bionic InRelease 
Hit:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic InRelease 
Get:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates InRelease [88.7 kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports InRelease [74.6 kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-security InRelease [83.2 kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 DEP-11 Metadata [245 kB]
Get:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main DEP-11 48x48 Icons [54.0 kB]
<snip>You posted the script itself but not the resultt of running the script.

You posted the result of running the script two posts above. 

Do you have new information to tell us?

---

