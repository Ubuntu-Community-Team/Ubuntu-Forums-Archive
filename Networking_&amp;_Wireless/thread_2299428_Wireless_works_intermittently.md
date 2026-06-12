---
title: "Wireless works intermittently"
date: 2015-10-18
forum: Networking &amp; Wireless
---

### Post by SUPERFITTER on 2015-10-18
Every time I boot I have to find my router and click on it and then wait for a connection. If I have a few websites on, or reading email and I go to another site I get the spinning arrow buffer and then I get timed out. Ubuntu 14.04 shows that I still am connect to the internet. Sometimes it just keeps searching for the site or the next email, document etc. and nothing happens.   I then have to reboot and start over.  This computer is home build and a duel boot with Windows 7 64 bit.  This is the first time with a problem since build two years ago. If I unplug the Dongle for my wireless and replug it into the USB port I can with a little patience get the wireless working again with out rebooting.  This only works for a short time and then I have no connection again even though Ubuntu14.04 shows that I have a connection.

Thank you

```
dennis@dennis1:~$ wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
> chmod +x wireless-info && \
> ./wireless-info
--2015-10-18 11:06:22--  https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info
Resolving github.com (github.com)... 192.30.252.128
Connecting to github.com (github.com)|192.30.252.128|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info [following]
--2015-10-18 11:06:23--  https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 23.235.44.133
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|23.235.44.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 15868 (15K) [text/plain]
Saving to: &#8216;wireless-info&#8217;

100%[======================================>] 15,868      --.-K/s   in 0s      

Last-modified header missing -- time-stamps turned off.
2015-10-18 11:06:23 (182 MB/s) - &#8216;wireless-info&#8217; saved [15868/15868]


Results saved in "/home/dennis/wireless-info.txt".

Results also archived in "/home/dennis/wireless-info.tar.gz", as they exceed the 19.5 kB size limit for ".txt" attachments on the Ubuntu Forums.

dennis@dennis1:~$ 
```

---

### Post by ian-weisser on 2015-10-21
It's nice that you ran the wireless-info script.
Seeing those results would be most helpful.

---

### Post by SUPERFITTER on 2015-10-21
```
dennis@dennis1:~$ **sudo apt-get update**
Ign http://us.archive.ubuntu.com trusty InRelease
Get:1 http://us.archive.ubuntu.com trusty-updates InRelease [64.4 kB]          
Get:2 http://security.ubuntu.com trusty-security InRelease [64.4 kB]           
Ign http://archive.canonical.com trusty InRelease                              
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://archive.canonical.com quantal InRelease                             
Hit http://ppa.launchpad.net trusty InRelease                                  
Ign http://extras.ubuntu.com trusty InRelease                                  
Ign http://archive.canonical.com trusty InRelease                              
Get:3 http://us.archive.ubuntu.com trusty-backports InRelease [64.5 kB]        
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://archive.canonical.com trusty Release.gpg                            
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://archive.canonical.com quantal/partner amd64 Packages                
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://archive.canonical.com quantal/partner i386 Packages                 
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Get:4 http://us.archive.ubuntu.com trusty-updates/main Sources [240 kB]        
Get:5 http://security.ubuntu.com trusty-security/main Sources [97.6 kB]        
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://archive.canonical.com trusty Release.gpg                            
Hit http://archive.canonical.com trusty Release                                
Get:6 http://us.archive.ubuntu.com trusty-updates/restricted Sources [4,722 B] 
Get:7 http://us.archive.ubuntu.com trusty-updates/universe Sources [140 kB]    
Get:8 http://security.ubuntu.com trusty-security/restricted Sources [3,357 B]  
Hit http://archive.canonical.com trusty Release                                
Get:9 http://security.ubuntu.com trusty-security/universe Sources [31.0 kB]    
Hit http://archive.canonical.com trusty/partner Sources                        
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Get:10 http://us.archive.ubuntu.com trusty-updates/multiverse Sources [5,145 B]
Get:11 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [635 kB]
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Ign http://ppa.launchpad.net trusty/main Translation-en_US                     
Get:12 http://security.ubuntu.com trusty-security/multiverse Sources [2,346 B] 
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Hit http://archive.canonical.com trusty/partner Translation-en                 
Get:13 http://security.ubuntu.com trusty-security/main amd64 Packages [356 kB] 
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://archive.canonical.com trusty/partner Translation-en                 
Ign http://archive.canonical.com quantal/partner Translation-en_US             
Ign http://archive.canonical.com quantal/partner Translation-en                
Get:14 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [15.4 kB]
Get:15 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [323 kB]
Get:16 http://security.ubuntu.com trusty-security/restricted amd64 Packages [12.4 kB]
Get:17 http://security.ubuntu.com trusty-security/universe amd64 Packages [117 kB]
Get:18 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [3,688 B]
Get:19 http://security.ubuntu.com trusty-security/main i386 Packages [338 kB]  
Get:20 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [12.0 kB]
Get:21 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [615 kB] 
Get:22 http://security.ubuntu.com trusty-security/restricted i386 Packages [12.2 kB]
Get:23 http://security.ubuntu.com trusty-security/universe i386 Packages [117 kB]
Get:24 http://security.ubuntu.com trusty-security/multiverse i386 Packages [3,846 B]
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Get:25 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [15.1 kB]
Get:26 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [324 kB]
Get:27 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [12.1 kB]
Get:28 http://us.archive.ubuntu.com trusty-updates/main Translation-en [308 kB]
Get:29 http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en [6,148 B]
Get:30 http://us.archive.ubuntu.com trusty-updates/restricted Translation-en [3,569 B]
Get:31 http://us.archive.ubuntu.com trusty-updates/universe Translation-en [170 kB]
Get:32 http://us.archive.ubuntu.com trusty-backports/main Sources [6,687 B]    
Get:33 http://us.archive.ubuntu.com trusty-backports/restricted Sources [28 B] 
Get:34 http://us.archive.ubuntu.com trusty-backports/universe Sources [30.4 kB]
Get:35 http://us.archive.ubuntu.com trusty-backports/multiverse Sources [1,898 B]
Get:36 http://us.archive.ubuntu.com trusty-backports/main amd64 Packages [6,643 B]
Get:37 http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages [28 B]
Get:38 http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages [36.2 kB]
Get:39 http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages [1,571 B]
Get:40 http://us.archive.ubuntu.com trusty-backports/main i386 Packages [6,645 B]
Get:41 http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages [28 B]
Get:42 http://us.archive.ubuntu.com trusty-backports/universe i386 Packages [36.3 kB]
Get:43 http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages [1,552 B]
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en          
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en      
Hit http://us.archive.ubuntu.com trusty Release                                
Hit http://us.archive.ubuntu.com trusty/main Sources                           
Hit http://us.archive.ubuntu.com trusty/restricted Sources                     
Hit http://us.archive.ubuntu.com trusty/universe Sources                       
Hit http://us.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages              
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages                
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages              
Hit http://us.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://us.archive.ubuntu.com trusty/main Translation-en                    
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://us.archive.ubuntu.com trusty/universe Translation-en                
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US             
Fetched 4,245 kB in 19s (221 kB/s)                                             
Reading package lists... Done
dennis@dennis1:~$ **sudo apt-get dist-upgrade**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  indicator-session libnm-gtk-common libnm-gtk0 libpython3.4
  libpython3.4-minimal libpython3.4-stdlib network-manager-gnome
  python-urllib3 python3-urllib3 python3.4 python3.4-minimal
11 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 5,715 kB of archives.
After this operation, 15.4 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main python3-urllib3 all 1.7.1-1ubuntu4 [39.6 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main python3.4 amd64 3.4.3-1ubuntu1~14.04.3 [177 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main python3.4-minimal amd64 3.4.3-1ubuntu1~14.04.3 [1,223 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libpython3.4 amd64 3.4.3-1ubuntu1~14.04.3 [1,308 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libpython3.4-stdlib amd64 3.4.3-1ubuntu1~14.04.3 [1,986 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libpython3.4-minimal amd64 3.4.3-1ubuntu1~14.04.3 [461 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main indicator-session amd64 12.10.5+14.04.20151008-0ubuntu1 [104 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main network-manager-gnome amd64 0.9.8.8-0ubuntu4.4 [312 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libnm-gtk0 amd64 0.9.8.8-0ubuntu4.4 [59.9 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libnm-gtk-common all 0.9.8.8-0ubuntu4.4 [4,320 B]
Get:11 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main python-urllib3 all 1.7.1-1ubuntu4 [39.5 kB]
Fetched 5,715 kB in 5s (1,041 kB/s)       
(Reading database ... 923561 files and directories currently installed.)
Preparing to unpack .../python3-urllib3_1.7.1-1ubuntu4_all.deb ...
Unpacking python3-urllib3 (1.7.1-1ubuntu4) over (1.7.1-1ubuntu3) ...
Preparing to unpack .../python3.4_3.4.3-1ubuntu1~14.04.3_amd64.deb ...
Unpacking python3.4 (3.4.3-1ubuntu1~14.04.3) over (3.4.3-1ubuntu1~14.04.1) ...
Preparing to unpack .../python3.4-minimal_3.4.3-1ubuntu1~14.04.3_amd64.deb ...
Unpacking python3.4-minimal (3.4.3-1ubuntu1~14.04.3) over (3.4.3-1ubuntu1~14.04.1) ...
Preparing to unpack .../libpython3.4_3.4.3-1ubuntu1~14.04.3_amd64.deb ...
Unpacking libpython3.4:amd64 (3.4.3-1ubuntu1~14.04.3) over (3.4.3-1ubuntu1~14.04.1) ...
Preparing to unpack .../libpython3.4-stdlib_3.4.3-1ubuntu1~14.04.3_amd64.deb ...
Unpacking libpython3.4-stdlib:amd64 (3.4.3-1ubuntu1~14.04.3) over (3.4.3-1ubuntu1~14.04.1) ...
Preparing to unpack .../libpython3.4-minimal_3.4.3-1ubuntu1~14.04.3_amd64.deb ...
Unpacking libpython3.4-minimal:amd64 (3.4.3-1ubuntu1~14.04.3) over (3.4.3-1ubuntu1~14.04.1) ...
Preparing to unpack .../indicator-session_12.10.5+14.04.20151008-0ubuntu1_amd64.deb ...
Unpacking indicator-session (12.10.5+14.04.20151008-0ubuntu1) over (12.10.5+14.04.20150404-0ubuntu1) ...
Preparing to unpack .../network-manager-gnome_0.9.8.8-0ubuntu4.4_amd64.deb ...
Unpacking network-manager-gnome (0.9.8.8-0ubuntu4.4) over (0.9.8.8-0ubuntu4.3) ...
Preparing to unpack .../libnm-gtk0_0.9.8.8-0ubuntu4.4_amd64.deb ...
Unpacking libnm-gtk0 (0.9.8.8-0ubuntu4.4) over (0.9.8.8-0ubuntu4.3) ...
Preparing to unpack .../libnm-gtk-common_0.9.8.8-0ubuntu4.4_all.deb ...
Unpacking libnm-gtk-common (0.9.8.8-0ubuntu4.4) over (0.9.8.8-0ubuntu4.3) ...
Preparing to unpack .../python-urllib3_1.7.1-1ubuntu4_all.deb ...
Unpacking python-urllib3 (1.7.1-1ubuntu4) over (1.7.1-1ubuntu3) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for libglib2.0-0:amd64 (2.40.2-0ubuntu1) ...
Processing triggers for libglib2.0-0:i386 (2.40.2-0ubuntu1) ...
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Setting up python3-urllib3 (1.7.1-1ubuntu4) ...
Setting up libpython3.4-minimal:amd64 (3.4.3-1ubuntu1~14.04.3) ...
Setting up python3.4-minimal (3.4.3-1ubuntu1~14.04.3) ...
Setting up libpython3.4-stdlib:amd64 (3.4.3-1ubuntu1~14.04.3) ...
Setting up python3.4 (3.4.3-1ubuntu1~14.04.3) ...
Setting up libpython3.4:amd64 (3.4.3-1ubuntu1~14.04.3) ...
Setting up indicator-session (12.10.5+14.04.20151008-0ubuntu1) ...
Setting up libnm-gtk-common (0.9.8.8-0ubuntu4.4) ...
Setting up libnm-gtk0 (0.9.8.8-0ubuntu4.4) ...
Setting up network-manager-gnome (0.9.8.8-0ubuntu4.4) ...
Setting up python-urllib3 (1.7.1-1ubuntu4) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
dennis@dennis1:~$ [B]wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
> chmod +x wireless-info && \
> ./wireless-info[/B]
--2015-10-21 14:36:15--  https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info
Resolving github.com (github.com)... 192.30.252.130
Connecting to github.com (github.com)|192.30.252.130|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info [following]
--2015-10-21 14:36:16--  https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 199.27.76.133
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|199.27.76.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 15868 (15K) [text/plain]
Last-modified header missing -- time-stamps turned off.
--2015-10-21 14:36:16--  https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info
Reusing existing connection to raw.githubusercontent.com:443.
HTTP request sent, awaiting response... 200 OK
Length: 15868 (15K) [text/plain]
Saving to: &#8216;wireless-info&#8217;

100%[==============================================================================================================================================================================================>] 15,868      --.-K/s   in 0s      

2015-10-21 14:36:16 (372 MB/s) - &#8216;wireless-info&#8217; saved [15868/15868]


Results saved in "/home/dennis/wireless-info.txt".

Results also archived in "/home/dennis/wireless-info.tar.gz", as they exceed the 19.5 kB size limit for ".txt" attachments on the Ubuntu Forums.

dennis@denni 
```

---

### Post by SUPERFITTER on 2015-10-21
Sorry I did not know about this and had to find the file.

```
#!/bin/bash
#
# Copyright (c) 2012
#
# Authors: Wild Man, Krytarik
# Helpers: chili555
#
# This script gathers the infos necessary for troubleshooting a wireless
# connection and saves them in a text file, wrapping it in an archive if it
# exceeds the 19.5 kB size limit for ".txt" attachments on the Ubuntu Forums.
#
##############################################################################
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.
#

SCRIPTDATE="2015-09-27 02:34 +0200"
FILEBASE="wireless-info"
OUTPUTDIR="$PWD"
OUTPUTDIRFB="/tmp"

MODMATCHES="(air|ar5|at7|ath[^3]?|b43|bcma|brcm|carl|ipw|iwl|ndis|r(818|8192[eu]|871|92su)|rt[23567]|rtl|ssb|wl|(cfg|mac)80211)"
LSMODMATCHES="(wmi|(dell|ideapad)[-_]laptop)"
IFACEMATCHES="(wlan[0-9]|eth[0-9])"
DMESGMATCHES="(firmware|[nN]etwork)"
NMPROFMATCHES="\(\[connection\]\|id=\|type=\|permissions=\|autoconnect=\|\[802-11-wireless\]\|\[wifi\]\|ssid=\|bssid=\|mac-address\(-blacklist\)\?=\|mtu=\|\[802-1x\]\|[[:graph:]]*ca-certs\?=\|\[ipv[46]\]\|method=\)"

DMESGEXCL="apparmor|(cfg|mac)80211"
MODINFOEXCL="alias"
MODPROBEXCL="(alsa-base|blacklist-(firewire|framebuffer|modem|oss|watchdog)|fglrx|nvidia|fbdev|bumblebee)"
PMUTILSEXCL="/etc/pm/(power.d/(95hdparm-apm|intel-audio-powersave|sata_alpm)|sleep.d/(10_grub-common|10_unattended-upgrades.*|novatel_3g.*))"

NETMGRNAMES=("NetworkManager" "Wicd" "ConnMan")
NETMGRPATHS=("/usr/sbin/NetworkManager" "/usr/sbin/wicd" "/usr/sbin/connmand")
DEC2BI=({0..1}{0..1}{0..1}{0..1}{0..1}{0..1}{0..1}{0..1})
DEC2HEX=($(printf "%02x " {0..255}))

export LANG="en_US.UTF-8"
export LANGUAGE="en_US:en"
export LC_ALL="en_US.UTF-8"

if [ -t 0 ]; then
    DIALOGAPP="terminal"
    DIALOGBREAK=" "
    TERMOUT="yes"
elif [ -x /usr/bin/zenity ]; then
    DIALOGAPP="zenity"
    DIALOGBREAK="\n"
elif [ -x /usr/bin/kdialog ]; then
    DIALOGAPP="kdialog"
    DIALOGBREAK="\n"
else
    exit 1
fi

if [ -t 0 ]; then
    SUDO="sudo"
elif [ -x /usr/bin/pkexec ]; then
    SUDO="pkexec"
elif [ -x /usr/bin/gksudo ]; then
    SUDO="gksudo"
    GKSUDO="yes"
elif [ -x /usr/bin/kdesudo ]; then
    SUDO="kdesudo"
    KDESUDO="yes"
    KDESUDOCMT=" needs administrative privileges. Please enter your password."
fi

dialog_info () {
    case $DIALOGAPP in
    terminal)
        printf "%b\n" "$1"
        ;;
    zenity)
        zenity --info --text="$1"
        ;;
    kdialog)
        kdialog --msgbox "$1"
        ;;
    esac
}

dialog_error () {
    case $DIALOGAPP in
    terminal)
        printf "%b\n" "$1" >&2
        ;;
    zenity)
        zenity --error --text="$1"
        ;;
    kdialog)
        kdialog --error "$1"
        ;;
    esac
}

dialog_question () {
    case $DIALOGAPP in
    terminal)
        local INPUT
        read -r -p "$1 [Y/n]: " INPUT
        echo "${INPUT,,}"
        ;;
    zenity)
        zenity --question --text="$1" || echo "no"
        ;;
    kdialog)
        kdialog --yesno "$1" || echo "no"
        ;;
    esac
}

ip6-mac () {
    for MAC in "$@"; do
    OCT1BI=${DEC2BI[0x${MAC:0:2}]}
    OCT1BI7=$((${OCT1BI:6:1} - 1))
    OCT1BIM="${OCT1BI:0:6}${OCT1BI7#-}${OCT1BI:7}"
    IP6S+=${IP6S:+$'\n'}"${DEC2HEX[2#$OCT1BIM]}${MAC:3:2}:${MAC:6:2}ff:fe${MAC:9:2}:${MAC:12:2}${MAC:15:2}"
    done
    sed 's/\(^\|:\)0\+\([[:alnum:]]\)/\1\2/g;s/^\([0:]\+\)/\\(::\\|\1\\)/' <<< "$IP6S"
}

exec 3>&1 4>&2
exec 1> "$OUTPUTDIR/$FILEBASE.txt" || {
    dialog_error "${TERMOUT+\n}Cannot write output file in \"$OUTPUTDIR\",${DIALOGBREAK}trying in \"$OUTPUTDIRFB\" instead.${TERMOUT+\n}"
    OUTPUTDIR="$OUTPUTDIRFB"
    exec 1> "$OUTPUTDIR/$FILEBASE.txt" || {
    dialog_error "${TERMOUT+\n}Cannot write output file in \"$OUTPUTDIR\" either, aborting.${TERMOUT+\n}"
    exit 1
    }
}
exec 2>&1

printf "\n########## wireless info START ##########\n\n"
REPORTDATE=$(date +"%d %b %Y %H:%M %Z %z")
SCRIPTDATE=$(date -u -d "$SCRIPTDATE" +"%d %b %Y %H:%M %Z %z")
LASTBOOTDT=$(last -FRn 1 reboot | sed -n 's/.*system boot[ ]\+\(.\+\) - .*$/\1/p')
LASTBOOTDT=$(date -d "$LASTBOOTDT" +"%d %b %Y %H:%M %Z %z")
printf "Report from: %s\n\n" "$REPORTDATE"
printf "Booted last: %s\n\n" "$LASTBOOTDT"
printf "Script from: %s\n" "$SCRIPTDATE"

printf "\n##### release ###########################\n\n"
lsb_release -idrc

printf "\n##### kernel ############################\n\n"
uname -srvmpio
echo
sed 's/root=[^ ]*//;s/[ ]\+/, /g;s/^BOOT_IMAGE=[^ ]*/Parameters:/' /proc/cmdline

printf "\n##### desktop ###########################\n\n"
if [ -n "$DESKTOP_SESSION" ]; then
    DESKTOP="$DESKTOP_SESSION"
else
    DESKTOP=$(sed -n 's/^Session=\(.\+\)$/\1/p' "$HOME/.dmrc")
    DESKDMRC=" (from ~/.dmrc)"
fi
if [ -n "$DESKTOP" ]; then
    if [ -f "/usr/share/xsessions/$DESKTOP.desktop" ]; then
    DESKTOP=$(sed -n 's/^Name=\(.\+\)$/\1/p' "/usr/share/xsessions/$DESKTOP.desktop")
    fi
    echo "${DESKTOP/ Session/}${DESKDMRC}"
else
    printf "\nCould not be determined.\n"
fi

printf "\n##### lspci #############################\n\n"
lspci -nnk | grep -iA 2 '^[^[:space:]].*net' | sed '/^--$/d; /^[^[:space:]]/ i\\'

printf "\n##### lsusb #############################\n\n"
lsusb

printf "\n##### PCMCIA card info ##################\n\n"
if [ -x /sbin/pccardctl ]; then
    pccardctl info
else
    echo "'pccardctl' is not installed (package \"pcmciautils\")."
fi

printf "\n##### rfkill ############################\n\n"
rfkill list all

printf "\n##### lsmod #############################\n\n"
LSMOD=$(lsmod | egrep "(^|[[:punct:] ])($MODMATCHES|$LSMODMATCHES)[^[:punct:] ]*([[:punct:] ]|$)")
echo "$LSMOD"

printf "\n##### interfaces ########################\n\n"
sed '/^#/d;s/^wpa-psk [[:graph:]]\+/wpa-psk <WPA key removed>/' /etc/network/interfaces

printf "\n##### ifconfig ##########################\n\n"
IFCONFIG=$(ifconfig -a)
sed '/^lo /,/^$/d' <<< "$IFCONFIG"
IFACESETH=($(sed -n 's/^\([^ ]\+\)[ ]\+Link encap:Ethernet.*/\1/p' <<< "$IFCONFIG"))
if (( ${#IFACESETH[@]} > 0 )); then
    IFETHMATCHES=${IFACESETH[@]}
    IFACEMATCHES="($IFACEMATCHES|(${IFETHMATCHES// /|}))"
fi

printf "\n##### iwconfig ##########################\n\n"
iwconfig

printf "\n##### route #############################\n\n"
route -n

printf "\n##### resolv.conf #######################\n\n"
grep -v '^#' /etc/resolv.conf

printf "\n##### network managers ##################\n\n"
printf "Installed:\n\n"
for NETMGRNR in "${!NETMGRPATHS[@]}"; do
    if [ -f "${NETMGRPATHS[$NETMGRNR]}" ]; then
    NETMGRINST+=("${NETMGRNAMES[$NETMGRNR]}")
    fi
done
printf "\t%s\n" "${NETMGRINST[@]:-None found.}"
NETMGRMATCHES=${NETMGRPATHS[@]/#*\//|}
NETMGRMATCHES=${NETMGRMATCHES// |/|}
NETMGRMATCHES="(${NETMGRMATCHES#|})"
printf "\nRunning:\n\n"
ps -ef | egrep "( |/)$NETMGRMATCHES($| )" || printf "\tNone found.\n"

printf "\n##### NetworkManager info ###############\n\n"
if [ -x /usr/bin/nm-tool ]; then
    nm-tool
elif [ -x /usr/bin/nmcli ]; then
    nmcli -f all device show | sed '/^GENERAL.DEVICE:[ ]\+lo$/,/^$/d; /^AP\[[0-9]\+\]\./d'
    echo
    nmcli -f SSID,BSSID,MODE,CHAN,FREQ,RATE,SIGNAL,BARS,SECURITY,ACTIVE,IN-USE device wifi list
else
    echo "NetworkManager is not installed (package \"network-manager\")."
fi

printf "\n##### NetworkManager.state ##############\n\n"
cat -s /var/lib/NetworkManager/NetworkManager.state

printf "\n##### NetworkManager.conf ###############\n\n"
grep -v '^#' /etc/NetworkManager/NetworkManager.conf
if [ -f /etc/NetworkManager/nm-system-settings.conf ]; then
    printf "\nnm-system-settings.conf (used up to Ubuntu 10.04):\n\n"
    grep -v '^#' /etc/NetworkManager/nm-system-settings.conf
fi

printf "\n##### NetworkManager profiles ###########\n\n"
if [ -d /etc/NetworkManager/system-connections ]; then
    if [ -n "$SUDO" ]; then
    trap "" 2 3
    NMPROFILES=$(find /etc/NetworkManager/system-connections -maxdepth 1 -type f -exec $SUDO${GKSUDO+ -D grep --}${KDESUDO+ -d --comment "<b>grep</b>$KDESUDOCMT" --} grep -vH '^$' {} +) && SUDOSUCCESS="yes" || SUDOSUCCESS="no"
    trap 2 3
    if [ "$SUDOSUCCESS" = "yes" ]; then
        ORIGIFS="$IFS"
        IFS=$'\n'
        for NMWLPRFFILE in $(sed -n 's/^\(.\+\):type=\(802-11-wireless\|wifi\).*$/\1/p' <<< "$NMPROFILES"); do
        NMWLPRFFLPERMS=$(stat -c "%a %U" "$NMWLPRFFILE")
        NMWLPROFILE=($(sed -n "s;^$NMWLPRFFILE:\($NMPROFMATCHES.*\)$;\1 |;p" <<< "$NMPROFILES"))
        NMWLPROFSOUT+="[[$NMWLPRFFILE]] ($NMWLPRFFLPERMS)"$'\n'"${NMWLPROFILE[@]}"$'\n\n'
        done
        IFS="$ORIGIFS"
        sed 's# | \[#\n\[#g;s#\] |#\]#g;s/ |$//' <<< "$NMWLPROFSOUT" | sed '/^\[[^]]*\]$/d'
    else
        printf "\nAcquisition of admin privileges failed.\n"
    fi
    else
    echo "No way to acquire admin privileges found."
    fi
else
    echo "No NetworkManager profiles found."
fi

printf "\n##### iw reg get ########################\n\n"
if [ -x /sbin/iw ]; then
    if IWREGGET=$(iw reg get 2>&1) && [ -f /etc/timezone ]; then
    REGION=$(cat /etc/timezone)
    printf "Region: %s (based on set time zone)\n\n" "$REGION"
    fi
    echo "$IWREGGET"
else
    echo "'iw' is not installed (package \"iw\")."
fi

printf "\n##### iwlist channels ###################\n\n"
if [ -x /sbin/iwlist ]; then
    iwlist chan
else
    echo "'iwlist' is not installed (package \"wireless-tools\")."
fi

printf "\n##### iwlist scan #######################\n\n"
if [ -x /sbin/iwlist ]; then
    if [ -n "$SUDO" ]; then
    trap "" 2 3
    IWLISTSCAN=$($SUDO${KDESUDO+ -d} iwlist scan) && SUDOSUCCESS="yes" || SUDOSUCCESS="no"
    trap 2 3
    if [ "$SUDOSUCCESS" = "yes" ]; then
        if [[ $IWLISTSCAN = *Frequency:* ]]; then
        printf "Channel occupancy:\n\n"
        grep '^[ ]*Frequency:' <<< "$IWLISTSCAN" | sort | uniq -c | sed 's/^[ ]\+\([ ][0-9]\+\)[ ]\+/     \1   APs on   /'
        echo
        fi
        grep -v '^[ ]*IE: Unknown:' <<< "$IWLISTSCAN"
    else
        printf "\nAcquisition of admin privileges failed.\n"
    fi
    else
    echo "No way to acquire admin privileges found."
    fi
else
    echo "'iwlist' is not installed (package \"wireless-tools\")."
fi

printf "\n##### module infos ######################\n\n"
MODULES=$(egrep -o "^$MODMATCHES[^ ]*" <<< "$LSMOD")
for MODULE in $MODULES; do
    MODINFO=$(modinfo $MODULE | egrep -v "^$MODINFOEXCL:")
    printf "[%s]\n%s\n\n" "$MODULE" "$MODINFO"
done

printf "\n##### module parameters #################\n\n"
for MODULE in $MODULES; do
    if [ -d /sys/module/$MODULE/parameters ]; then
    MODPARAMS=$(grep -H '^[[:graph:]]' /sys/module/$MODULE/parameters/* | sed 's#^.*/##;s/:/: /')
    printf "[%s]\n%s\n\n" "$MODULE" "$MODPARAMS"
    fi
done

printf "\n##### /etc/modules ######################\n\n"
grep -v '^#' /etc/modules

printf "\n##### modprobe options ##################\n\n"
for MODPROBEFILE in $(find /etc/modprobe.{conf,d} -name "*.conf" -regextype posix-egrep -not -regex ".*$MODPROBEXCL.*" 2> /dev/null | sort); do
    MODPROBEOPTS=$(egrep -v '^(#|$)' $MODPROBEFILE)
    if [ -n "$MODPROBEOPTS" ]; then
    printf "[%s]\n%s\n\n" "$MODPROBEFILE" "$MODPROBEOPTS"
    fi
done

printf "\n##### rc.local ##########################\n\n"
grep -v '^#' /etc/rc.local

printf "\n##### pm-utils ##########################\n\n"
for PMUTILSFILE in $(find /etc/pm/*.d \( -type f -o -type l \) -regextype posix-egrep -not -regex "$PMUTILSEXCL" | sort); do
    PMUTFLCONT=$(egrep -v '^(#|$)' $PMUTILSFILE)
    if [ -n "$PMUTFLCONT" ]; then
    PMUTFLPERMS=$(stat -c "%a %U" $PMUTILSFILE)
    printf "[%s] (%s)\n%s\n\n" "$PMUTILSFILE" "$PMUTFLPERMS" "$PMUTFLCONT"
    fi
done

printf "\n##### udev rules ########################\n\n"
for UDEVRLFILE in /etc/udev/rules.d/*net*.rules; do
    UDEVRULES=$(grep -B1 '^[^#]' $UDEVRLFILE | egrep -v '^(--)?$')
    if [ -n "$UDEVRULES" ]; then
    printf "[%s]\n%s\n\n" "$UDEVRLFILE" "$UDEVRULES"
    fi
done

printf "\n##### dmesg #############################\n\n"
dmesg | tail -n 100 | egrep "[[:punct:] ]($MODMATCHES|$IFACEMATCHES|$DMESGMATCHES)[^[:punct:] ]*[[:punct:] ]" | egrep -v "$DMESGEXCL" | uniq -cf 2 | sed 's/^[ ]\+1[ ]\+//;s/^[ ]\+\([0-9]\+\)[ ]\+\(.\+\)$/\2 (repeated \1 times)/'

printf "\n########## wireless info END ############\n\n"

exec 2>&4 4>&-
exec 1>&3 3>&-

##### MAC address masking #####

RESULTS=$(cat -s "$OUTPUTDIR/$FILEBASE.txt")$'\n'

ORIGIFS="$IFS"
IFS=$'\n'

IFACESIDS=($(sed -n "s/^\([^ ]\+\)[ ]\+.*HWaddr.*/'\1' [IF]/p" <<< "$IFCONFIG"))
IFACESMACS=($(sed -n 's/^[^ ]\+[ ]\+.*HWaddr \([^ ]\+\)[ ]*/\1/p' <<< "$IFCONFIG"))
IFACESIP6S=($(ip6-mac "${IFACESMACS[@]}"))

WLAPSIWLIDS=($(sed -n "/^[ ]*Cell [0-9]\+/,/^[ ]*ESSID:/ {/^[ ]*Cell [0-9]\+/h; /^[ ]*ESSID:/ {H;g;s/^[ ]*Cell 0\?\([0-9]\+\).*ESSID:\"\(.*\)\"$/'\2' [AC\1]/p}}" <<< "$IWLISTSCAN"))
WLAPSIWLMACS=($(sed -n 's/^[ ]*Cell [0-9]\+.*Address: \([^ ]\+\)/\1/p' <<< "$IWLISTSCAN"))
WLAPSIWLIP6S=($(ip6-mac "${WLAPSIWLMACS[@]}"))

WLAPSNMRAW=$(sed -n '/^##### NetworkManager info #####/,/^##### / {/^[ ]*Wireless Access Points/,/^$/ {/Wireless Access Points/d;s/^[ ]\+\*\?//;s/:[ ]\+/\t/;p}; /^SSID[ ]\+BSSID[ ]\+/,/^$/ {/^SSID[ ]\{2,\}BSSID[ ]\{2,\}/d;s/[ ]\{2,\}/\t/;p}}' <<< "$RESULTS")
WLAPSNMIDS=($(awk -F '\t' '{printf "'\''%s'\'' [AN%d]\n", $1, NR}' <<< "$WLAPSNMRAW"))
WLAPSNMMACS=($(grep -o '\([[:alnum:]]\{2\}:\)\{5\}[[:alnum:]]\{2\}' <<< "$WLAPSNMRAW"))
WLAPSNMIP6S=($(ip6-mac "${WLAPSNMMACS[@]}"))

IFS="$ORIGIFS"

for IFACENR in "${!IFACESMACS[@]}"; do
    MACMASKSED+="s;${IFACESMACS[$IFACENR]};<MAC ${IFACESIDS[$IFACENR]-address}>;I;"
    MACMASKSED+=" /${IFACESIP6S[$IFACENR]}/ s;${IFACESIP6S[$IFACENR]/#\\(::/\(};<IP6 ${IFACESIDS[$IFACENR]-from MAC}>;I;"
done

for WLAPIWLNR in "${!WLAPSIWLMACS[@]}"; do
    MACMASKSED+="s;${WLAPSIWLMACS[$WLAPIWLNR]};<MAC ${WLAPSIWLIDS[$WLAPIWLNR]-address}>;I;"
    MACMASKSED+=" /${WLAPSIWLIP6S[$WLAPIWLNR]}/ s;${WLAPSIWLIP6S[$WLAPIWLNR]/#\\(::/\(};<IP6 ${WLAPSIWLIDS[$WLAPIWLNR]-from MAC}>;I;"
done

for WLAPNMNR in "${!WLAPSNMMACS[@]}"; do
    MACMASKSED+="s;${WLAPSNMMACS[$WLAPNMNR]};<MAC ${WLAPSNMIDS[$WLAPNMNR]-address}>;I;"
    MACMASKSED+=" /${WLAPSNMIP6S[$WLAPNMNR]}/ s;${WLAPSNMIP6S[$WLAPNMNR]/#\\(::/\(};<IP6 ${WLAPSNMIDS[$WLAPNMNR]-from MAC}>;I;"
done

sed "$MACMASKSED /\([[:alnum:]]\{2\}:\)\{6,\}/! s/\([[:alnum:]]\{2\}:\)\{5\}[[:alnum:]]\{2\}/<MAC address>/" <<< "$RESULTS" > "$OUTPUTDIR/$FILEBASE.txt"

##### The End #####

dialog_info "${TERMOUT+\n}Results saved in \"$OUTPUTDIR/$FILEBASE.txt\".${TERMOUT+\n}"

if (( $(stat -c %s "$OUTPUTDIR/$FILEBASE.txt") > 19968 )); then
    tar -czf "$OUTPUTDIR/$FILEBASE.tar.gz" -C "$OUTPUTDIR" "$FILEBASE.txt" && \
    dialog_info "Results also archived in \"$OUTPUTDIR/$FILEBASE.tar.gz\",${DIALOGBREAK}as they exceed the 19.5 kB size limit for \".txt\" attachments${DIALOGBREAK}on the Ubuntu Forums.${TERMOUT+\n}" || \
    dialog_error "Results exceed the 19.5 kB size limit for \".txt\" attachments${DIALOGBREAK}on the Ubuntu Forums, but archive could not be created.${TERMOUT+\n}"
fi

if [ -x /usr/bin/pastebinit ] && ping -nc 3 -w 6 -i 0.2 paste.ubuntu.com > /dev/null 2>&1; then
    PASTEBIN=$(dialog_question "Do you also want to post them${DIALOGBREAK}to your default 'pastebinit' provider?")
    if [[ ! $PASTEBIN =~ ^no?$ ]]; then
    PASTERESULT=$(pastebinit -i "$OUTPUTDIR/$FILEBASE.txt" -f text 2>&1) && PASTESUCCESS="yes"
    if [ "$PASTESUCCESS" = "yes" ]; then
        dialog_info "${TERMOUT+\n}Pastebin successful:\n\n${PASTERESULT}${TERMOUT+\n}"
    else
        if [ -n "$PASTERESULT" ]; then
        dialog_error "${TERMOUT+\n}Pastebin failed, error message is:\n\n${PASTERESULT}${TERMOUT+\n}"
        else
        dialog_error "${TERMOUT+\n}Pastebin failed, no error message given.${TERMOUT+\n}"
        fi
    fi
    else
    echo
    fi
fi    
 
########## wireless info START ##########

Report from: 21 Oct 2015 14:36 EDT -0400

Booted last: 21 Oct 2015 13:52 EDT -0400

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-51-generic #84-Ubuntu SMP Wed Apr 15 12:08:34 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash

##### desktop ###########################

Ubuntu

##### lspci #############################

07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 003: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 005: ID 0b05:17ab ASUSTek Computer, Inc. USB-N13 802.11n Network Adapter (rev. B1) [Realtek RTL8192CU]
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 001 Device 004: ID 046d:09a1 Logitech, Inc. QuickCam Communicate MP/S5500
Bus 001 Device 003: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

3: phy3: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

mxm_wmi                13021  0 
rtl8192cu              67723  0 
rtl_usb                18448  1 rtl8192cu
rtlwifi                63475  2 rtl_usb,rtl8192cu
rtl8192c_common        53172  1 rtl8192cu
mac80211              630669  3 rtl_usb,rtlwifi,rtl8192cu
cfg80211              484040  2 mac80211,rtlwifi
wmi                    19177  1 mxm_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan3     Link encap:Ethernet  HWaddr <MAC 'wlan3' [IF]>  
          inet addr:10.10.10.105  Bcast:10.10.10.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan3' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13835 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10525 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14374925 (14.3 MB)  TX bytes:1539654 (1.5 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan3     IEEE 802.11bgn  ESSID:"SUPERFITTER1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'SUPERFITTER1' [AC1]>   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=48/70  Signal level=-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:150   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.10.10.1      0.0.0.0         UG    0      0        0 wlan3
10.10.10.0      0.0.0.0         255.255.255.0   U     9      0        0 wlan3

##### resolv.conf #######################

nameserver 127.0.1.1
search hsd1.mi.comcast.net

##### network managers ##################

Installed:

    NetworkManager

Running:

root       989     1  0 13:52 ?        00:00:01 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan3  [Auto SUPERFITTER1] -------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan3' [IF]>

  Capabilities:
    Speed:           18 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    HomeNetwork:     Infra, <MAC 'HomeNetwork' [AN1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 7 WPA WPA2
    HOME-F48C:       Infra, <MAC 'HOME-F48C' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 4 WPA WPA2
    Karma:           Infra, <MAC 'Karma' [AC4]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 4 WPA WPA2
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AN4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 7
    *SUPERFITTER1:   Infra, <MAC 'SUPERFITTER1' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 58 WEP

  IPv4 Settings:
    Address:         10.10.10.105
    Prefix:          24 (255.255.255.0)
    Gateway:         10.10.10.1

    DNS:             75.75.76.76
    DNS:             75.75.75.75

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

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

[[/etc/NetworkManager/system-connections/Auto SUPERFITTER1_5GEXT]] (600 root)
[connection] id=Auto SUPERFITTER1_5GEXT | type=802-11-wireless
[802-11-wireless] ssid=SUPERFITTER1_5GEXT | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto SUPERFITTER1_2GEXT]] (600 root)
[connection] id=Auto SUPERFITTER1_2GEXT | type=802-11-wireless
[802-11-wireless] ssid=SUPERFITTER1_2GEXT | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/dlink]] (600 root)
[connection] id=dlink | type=802-11-wireless
[802-11-wireless] ssid=dlink | mac-address=<MAC 'wlan3' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Auto SUPERFITTER1-2b9cceb2-7048-4b98-ab2f-2179af4fab0f]] (600 root)
[connection] id=Auto SUPERFITTER1 | type=802-11-wireless
[802-11-wireless] ssid=SUPERFITTER1 | mac-address=<MAC 'wlan3' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto KLEISMIT-COMCAST]] (600 root)
[connection] id=Auto KLEISMIT-COMCAST | type=802-11-wireless
[802-11-wireless] ssid=KLEISMIT-COMCAST | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto dlink]] (600 root)
[connection] id=Auto dlink | type=802-11-wireless
[802-11-wireless] ssid=dlink | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Auto NETGEAR27]] (600 root)
[connection] id=Auto NETGEAR27 | type=802-11-wireless
[802-11-wireless] ssid=NETGEAR27 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto SUPERFITTER1-8968c2d7-90b0-4d20-a254-626e5868ca0b]] (600 root)
[connection] id=Auto SUPERFITTER1 | type=802-11-wireless
[802-11-wireless] ssid=SUPERFITTER1 | mac-address=<MAC 'wlan3' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto HomeNetwork]] (600 root)
[connection] id=Auto HomeNetwork | type=802-11-wireless
[802-11-wireless] ssid=HomeNetwork | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto SUPERFITTER1]] (600 root)
[connection] id=Auto SUPERFITTER1 | type=802-11-wireless
[802-11-wireless] ssid=SUPERFITTER1 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto SUPERFITTER1-54ac5203-bd5e-428c-8d74-d5526237e750]] (600 root)
[connection] id=Auto SUPERFITTER1 | type=802-11-wireless
[802-11-wireless] ssid=SUPERFITTER1 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto SUPERFITTER1-217eb2ad-fe92-4685-b0ec-442a6c33969d]] (600 root)
[connection] id=Auto SUPERFITTER1 | type=802-11-wireless
[802-11-wireless] ssid=SUPERFITTER1 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto xfinitywifi]] (600 root)
[connection] id=Auto xfinitywifi | type=802-11-wireless
[802-11-wireless] ssid=xfinitywifi | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Auto SUPERFITTER1-2801515f-edb6-4cd8-b5b4-62d78c501597]] (600 root)
[connection] id=Auto SUPERFITTER1 | type=802-11-wireless
[802-11-wireless] ssid=SUPERFITTER1 | mac-address=<MAC 'wlan3' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto TP-LINK_2DC442]] (600 root)
[connection] id=Auto TP-LINK_2DC442 | type=802-11-wireless
[802-11-wireless] ssid=TP-LINK_2DC442 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto ATT600]] (600 root)
[connection] id=Auto ATT600 | type=802-11-wireless
[802-11-wireless] ssid=ATT600 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto Bonkowski-N1]] (600 root)
[connection] id=Auto Bonkowski-N1 | type=802-11-wireless
[802-11-wireless] ssid=Bonkowski-N1 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/New_York (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan3     11 channels in total; available frequencies :
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
          Current Frequency:2.462 GHz (Channel 11)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.422 GHz (Channel 3)
      3   APs on   Frequency:2.462 GHz (Channel 11)

wlan3     Scan completed :
          Cell 01 - Address: <MAC 'SUPERFITTER1' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"SUPERFITTER1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000639e32d9f3
                    Extra: Last beacon: 88ms ago
          Cell 02 - Address: <MAC 'HOME-F48C' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"HOME-F48C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003c927aa896
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC '\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00' [AC3]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000126a5b64bed
                    Extra: Last beacon: 2128ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Karma' [AC4]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:on
                    ESSID:"Karma"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000126a5b1b678
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'xfinitywifi' [AC5]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000008d8f5c9180
                    Extra: Last beacon: 1776ms ago
          Cell 06 - Address: <MAC '' [AC6]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000008d8f678180
                    Extra: Last beacon: 1084ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8192cu]
filename:       /lib/modules/3.13.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
srcversion:     2E676CE01D91070679A9EF3
depends:        rtlwifi,rtl8192c-common,rtl_usb,mac80211
intree:         Y
vermagic:       3.13.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        82:2A:53:9B:EB:8B:75:6F:17:7F:E0:44:DF:98:55:A9:99:39:61:9E
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl_usb]
filename:       /lib/modules/3.13.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtl_usb.ko
description:    USB basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     9A4393167BB287C0A5DC011
depends:        rtlwifi,mac80211
intree:         Y
vermagic:       3.13.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        82:2A:53:9B:EB:8B:75:6F:17:7F:E0:44:DF:98:55:A9:99:39:61:9E
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.13.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     730FEE1A7696EA37A982482
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        82:2A:53:9B:EB:8B:75:6F:17:7F:E0:44:DF:98:55:A9:99:39:61:9E
sig_hashalgo:   sha512

[rtl8192c_common]
filename:       /lib/modules/3.13.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     32F826C623BC49F764F7974
depends:        
intree:         Y
vermagic:       3.13.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        82:2A:53:9B:EB:8B:75:6F:17:7F:E0:44:DF:98:55:A9:99:39:61:9E
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-51-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     29A87AE7782ED3657631C32
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        82:2A:53:9B:EB:8B:75:6F:17:7F:E0:44:DF:98:55:A9:99:39:61:9E
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-51-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     176113E009F723E69BE9BAB
depends:        
intree:         Y
vermagic:       3.13.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        82:2A:53:9B:EB:8B:75:6F:17:7F:E0:44:DF:98:55:A9:99:39:61:9E
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8192cu]
debug: 0
swenc: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

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
blacklist bcm43xx
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
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (r8712u)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"
# PCI device 0x168c:0x0030 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2"
# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan3' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan3"

##### dmesg #############################

[ 2028.168182] wlan3: authenticated
[ 2028.168362] rtl8192cu 5-1:1.0 wlan3: disabling HT/VHT due to WEP/TKIP use
[ 2028.168367] rtl8192cu 5-1:1.0 wlan3: disabling HT as WMM/QoS is not supported by the AP
[ 2028.168370] rtl8192cu 5-1:1.0 wlan3: disabling VHT as WMM/QoS is not supported by the AP
[ 2028.170595] wlan3: associate with <MAC 'SUPERFITTER1' [AC1]> (try 1/3)
[ 2028.173688] wlan3: RX AssocResp from <MAC 'SUPERFITTER1' [AC1]> (capab=0x411 status=0 aid=1)
[ 2028.173729] wlan3: associated
[ 2038.182807] wlan3: deauthenticating from <MAC 'SUPERFITTER1' [AC1]> by local choice (reason=3)
[ 2039.087683] wlan3: authenticate with <MAC 'SUPERFITTER1' [AC1]>
[ 2039.103078] wlan3: send auth to <MAC 'SUPERFITTER1' [AC1]> (try 1/3)
[ 2039.123729] wlan3: authenticated
[ 2039.123904] rtl8192cu 5-1:1.0 wlan3: disabling HT/VHT due to WEP/TKIP use
[ 2039.123917] rtl8192cu 5-1:1.0 wlan3: disabling HT as WMM/QoS is not supported by the AP
[ 2039.123919] rtl8192cu 5-1:1.0 wlan3: disabling VHT as WMM/QoS is not supported by the AP
[ 2039.127038] wlan3: associate with <MAC 'SUPERFITTER1' [AC1]> (try 1/3)
[ 2039.145409] wlan3: RX AssocResp from <MAC 'SUPERFITTER1' [AC1]> (capab=0x411 status=0 aid=1)
[ 2039.145446] wlan3: associated
[ 2116.868882] wlan3: deauthenticating from <MAC 'SUPERFITTER1' [AC1]> by local choice (reason=3)
[ 2129.617245] rtl8192cu: Chip version 0x11
[ 2130.096451] rtl8192cu: MAC address: <MAC 'wlan3' [IF]>
[ 2130.096458] rtl8192cu: Board Type 0
[ 2130.097218] rtl_usb: rx_max_size 15360, rx_urb_num 8, in_ep 1
[ 2130.097251] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[ 2130.097447] ieee80211 phy3: Selected rate control algorithm 'rtl_rc'
[ 2130.098694] rtlwifi: wireless switch is on
[ 2130.124746] systemd-udevd[3264]: renamed network interface wlan0 to wlan3
[ 2130.129955] rtl8192cu: MAC auto ON okay!
[ 2130.329455] rtl8192cu: Tx queue select: 0x05
[ 2131.071952] IPv6: ADDRCONF(NETDEV_UP): wlan3: link is not ready (repeated 2 times)
[ 2132.717110] wlan3: authenticate with <MAC 'SUPERFITTER1' [AC1]>
[ 2132.772976] wlan3: send auth to <MAC 'SUPERFITTER1' [AC1]> (try 1/3)
[ 2132.797773] wlan3: authenticated
[ 2132.797955] rtl8192cu 5-2:1.0 wlan3: disabling HT/VHT due to WEP/TKIP use
[ 2132.797959] rtl8192cu 5-2:1.0 wlan3: disabling HT as WMM/QoS is not supported by the AP
[ 2132.797961] rtl8192cu 5-2:1.0 wlan3: disabling VHT as WMM/QoS is not supported by the AP
[ 2132.800500] wlan3: associate with <MAC 'SUPERFITTER1' [AC1]> (try 1/3)
[ 2132.823115] wlan3: RX AssocResp from <MAC 'SUPERFITTER1' [AC1]> (capab=0x411 status=0 aid=1)
[ 2132.823145] wlan3: associated
[ 2132.823180] IPv6: ADDRCONF(NETDEV_CHANGE): wlan3: link becomes ready
[ 2132.825061] wlan3: deauthenticating from <MAC 'SUPERFITTER1' [AC1]> by local choice (reason=2)
[ 2132.855179] wlan3: authenticate with <MAC 'SUPERFITTER1' [AC1]>
[ 2132.864338] wlan3: send auth to <MAC 'SUPERFITTER1' [AC1]> (try 1/3)
[ 2132.881150] wlan3: authenticated
[ 2132.881329] rtl8192cu 5-2:1.0 wlan3: disabling HT/VHT due to WEP/TKIP use
[ 2132.881334] rtl8192cu 5-2:1.0 wlan3: disabling HT as WMM/QoS is not supported by the AP
[ 2132.881337] rtl8192cu 5-2:1.0 wlan3: disabling VHT as WMM/QoS is not supported by the AP
[ 2132.884468] wlan3: associate with <MAC 'SUPERFITTER1' [AC1]> (try 1/3)
[ 2132.900248] wlan3: RX AssocResp from <MAC 'SUPERFITTER1' [AC1]> (capab=0x411 status=0 aid=1)
[ 2132.900280] wlan3: associated
[ 2142.901325] wlan3: deauthenticating from <MAC 'SUPERFITTER1' [AC1]> by local choice (reason=3)
[ 2143.808771] wlan3: authenticate with <MAC 'SUPERFITTER1' [AC1]>
[ 2143.825744] wlan3: send auth to <MAC 'SUPERFITTER1' [AC1]> (try 1/3)
[ 2143.842681] wlan3: authenticated
[ 2143.842862] rtl8192cu 5-2:1.0 wlan3: disabling HT/VHT due to WEP/TKIP use
[ 2143.842867] rtl8192cu 5-2:1.0 wlan3: disabling HT as WMM/QoS is not supported by the AP
[ 2143.842869] rtl8192cu 5-2:1.0 wlan3: disabling VHT as WMM/QoS is not supported by the AP
[ 2143.844162] wlan3: associate with <MAC 'SUPERFITTER1' [AC1]> (try 1/3)
[ 2143.856406] wlan3: RX AssocResp from <MAC 'SUPERFITTER1' [AC1]> (capab=0x411 status=0 aid=1)
[ 2143.856434] wlan3: associated

########## wireless info END ############   
```

---

### Post by ian-weisser on 2015-10-21
Sure, that's the script.
We want to see the output that the occurs when you run the script.

---

### Post by SUPERFITTER on 2015-10-21
> **ian-weisser said:**
> Sure, that's the script.
We want to see the output that the occurs when you run the script.

Sorry, I thought this ran the script?

wget -N -t 5 -T 10 [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info) && \
chmod +x wireless-info && \
./wireless-info

_[https://github.com/UbuntuForums/wireless-info](https://github.com/UbuntuForums/wireless-info)_

  This will download the script, make it executable, and [COLOR=#0000ff]**run **[/COLOR]it, all in a row.

---

### Post by ian-weisser on 2015-10-22
My apologies. The output is indeed at the bottom! Sorry I missed it.

Here's one issue:
> Channel occupancy:
      1   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.422 GHz (Channel 3)
      **3   APs on**   Frequency:2.462 GHz (**Channel 11**)
One of those three is yours (Superfitter). Possible congestion and interference. Easy solution: Log into your router and change channels.

Here's a bigger issue:
> ##### dmesg #############################

[ 2028.168182] wlan3: authenticated
[ 2028.168362] rtl8192cu 5-1:1.0 wlan3: disabling HT/VHT due to WEP/TKIP use
[ 2028.168367] rtl8192cu 5-1:1.0 wlan3: disabling HT as WMM/QoS is not supported by the AP
[ 2028.168370] rtl8192cu 5-1:1.0 wlan3: disabling VHT as WMM/QoS is not supported by the AP
[ 2028.170595] wlan3: associate with <MAC 'SUPERFITTER1' [AC1]> (try 1/3)
[ 2028.173688] wlan3: RX AssocResp from <MAC 'SUPERFITTER1' [AC1]> (capab=0x411 status=0 aid=1)
[ 2028.173729] wlan3: associated
[ 2038.182807] wlan3: deauthenticating from <MAC 'SUPERFITTER1' [AC1]> by local choice (reason=3)
[ 2039.087683] wlan3: authenticate with <MAC 'SUPERFITTER1' [AC1]>
[ 2039.103078] wlan3: send auth to <MAC 'SUPERFITTER1' [AC1]> (try 1/3)
This cycle of authenticate/deauthenticate repeats about every 10 seconds (or, sometimes, 100 seconds). And, yes, it will really screw up your ability to do anything online. The simplest things to try are to power-cycle your router/access point, and to move a bit closer to the access point.

If those super-easy things to try don't fix your problem, then unfortunately...
> State: connected (global)

- Device: wlan3  [Auto SUPERFITTER1] -------------------------------------------
  Type:              802.11 WiFi
  **Driver:            rtl8192cu**
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan3' [IF]>
...unfortunately, the rtl8192cu driver has a rather lousy reputation in some quarters.
You can see complaints --and how other fixed the problem-- [here]("http://ubuntuforums.org/showthread.php?t=2148130"). And [here]("http://askubuntu.com/questions/471208/realtek-wireless-adapter-issues-rtl8192ce-and-rtl8192cu").

---

### Post by kurt18947 on 2015-10-22
I can confirm that pvaret's fix on github still works. I just used it on 15.10 Mate.

[pvaret/rtl8192cu-fixes · GitHub]("https://github.com/pvaret/rtl8192cu-fixes")

---

### Post by SUPERFITTER on 2015-10-23
Thank You: ian-weisser and kurt18947

I tried: [URL="https://github.com/pvaret/rtl8192cu-fixes"]pvaret/rtl8192cu-fixes · GitHub


[/URL]                         The wireless icon in the upper right of the desktop went up one bar to full capacity. I have rebooted and cold booted a few times and have had no problems so far.
 

 On  this problem: Channel occupancy:
1 APs on Frequency:2.412 GHz (Channel 1)
2 APs on Frequency:2.422 GHz (Channel 3)
**3 APs on** Frequency:2.462 GHz (**Channel 11**)  
 

 When I click on the wireless icon and go to my Wi-Fi Network and click my Wi-Fi I get:
 Auto SUPERFITTER1
 Auto SUPERFITTER1
 Auto SUPERFITTER1

   I can click on any one and it disconnects and then reconnects to full capacity.  It seems that  pvaret's fix is the solution to the problem with [B]Driver:            rtl8192cu
[/B]
I will run the computer a few days and if there is no problem I will mark this as fixed.

Thank You both again

---

