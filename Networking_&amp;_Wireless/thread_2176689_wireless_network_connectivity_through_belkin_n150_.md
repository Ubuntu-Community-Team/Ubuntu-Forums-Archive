---
title: "wireless network connectivity through belkin n150 adaptor in ubuntu 12.04"
date: 2013-09-25
forum: Networking &amp; Wireless
---

### Post by Gosiv_Mariappan on 2013-09-25
Hi good evening,
       I am completely new for linux community. And I am having ubuntu 12.04 version in parallel connection with my windows 7 ultimate. I knew that the significance of ubuntu through my friends. Unfortunately, they have also known little about the ubuntu. I am using Belkin adaptor to connect internet in my windows operating system. But I am unable to connect this in ubuntu. Whenever I login to ubuntu the signal identified suddenly it is disconnected. I didn't know about the commands and else. If anyone help to me to solve this problem I really thankful to you. while googling regarding this, I found something about the commands. Here I have provided the output of "lsusb" command. 

priya@priya-Aspire-4739Z:~$ lsusb
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 002 Device 003: ID 050d:945a Belkin Components F7D1101 Basic Wireless USB Adapter v1000 [Realtek RTL8188SU]
Bus 001 Device 004: ID 1c4f:0002 SiGma Micro Keyboard TRACER Gamma Ivory
Bus 001 Device 005: ID 2188:0ae1

---

### Post by praseodym on 2013-09-25
Hi,

can you connect temporarily via cable connection? Please show the terminal outputs of:
```

uname -a
iwconfig
rfkill list
lsmod
cat /etc/resolv.conf
route -n
rfkill list
```

---

### Post by Gosiv_Mariappan on 2013-09-26
Goog eveving, 
        At first I really thank you very much for spending your valuable time to help me. I am unable connect through cable connection and also I'm also not having cd/dvd drive. These are all the drawback now for this job. If you resolve this problem with this condition that too pleasure to me. Herewith I am adding the output for the above commands. 

priya@priya-Aspire-4739Z:~$ uname -a
Linux priya-Aspire-4739Z 3.8.0-29-generic #42~precise1-Ubuntu SMP Wed Aug 14 15:31:16 UTC 2013 i686 i686 i386 GNU/Linux
priya@priya-Aspire-4739Z:~$ iwconfig
wlan0     unassociated  Nickname:"rtl_wifi"
          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0 
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
 
lo        no wireless extensions.
 
eth0      no wireless extensions.
 
priya@priya-Aspire-4739Z:~$ rfkill list
priya@priya-Aspire-4739Z:~$ lsmod
Module                  Size  Used by
bnep                   17852  2
rfcomm                 38400  0
bluetooth             211435  10 bnep,rfcomm
parport_pc             27612  0
ppdev                  12849  0
r8712u                163917  0
i915                  550346  3
snd_hda_codec_hdmi     36583  1
snd_hda_codec_realtek    65004  1
snd_hda_intel          38819  3
snd_hda_codec         118613  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                85934  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0
snd_rawmidi            25157  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51593  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         47749  1 i915
drm                   233935  4 i915,drm_kms_helper
snd_timer              28931  2 snd_pcm,snd_seq
coretemp               13324  0
psmouse                82769  0
mei                    36756  0
joydev                 17329  0
serio_raw              13031  0
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    57014  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
acer_wmi               27980  0
sparse_keymap          13658  1 acer_wmi
microcode              18433  0
wmi                    18744  1 acer_wmi
snd_page_alloc         18398  2 snd_hda_intel,snd_pcm
intel_ips              17738  0
i2c_algo_bit           13316  1 i915
video                  19116  2 i915,acer_wmi
mac_hid                13077  0
lpc_ich                17048  0
lp                     17455  0
parport                40930  3 parport_pc,ppdev,lp
ext2                   63952  1
hid_generic            12484  0
usbhid                 46125  0
hid                    83037  2 hid_generic,usbhid
ahci                   25631  3
libahci                26336  1 ahci
atl1c                  36845  0
priya@priya-Aspire-4739Z:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
priya@priya-Aspire-4739Z:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
priya@priya-Aspire-4739Z:~$ rfkill list
priya@priya-Aspire-4739Z:~$

---

### Post by praseodym on 2013-09-26
There are no nameservers listed:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
sudo service network-manager restart
```

---

### Post by Gosiv_Mariappan on 2013-09-26
Hi good day to you, 
     I gave the above commands, the following results are displayed. Kindly be patience and apologize to me if I did anything mistakenly. Because I know nothing about ubuntu. And then, will you please, If any of the suggestions give me like for a layman. 

priya@priya-Aspire-4739Z:~$ echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4"
nameserver 8.8.8.8
nameserver 8.8.4.4
priya@priya-Aspire-4739Z:~$ sudo tee -a/etc/resolv.conf
[sudo] password for priya:
tee: invalid option -- '/'
Try `tee --help' for more information.
priya@priya-Aspire-4739Z:~$ sudo tee -a /etc/resolv.conf
sudo service network-manager restart
sudo service network-manager restart

I think that I did some mistake while giving the command. So I close the terminal then again I do the same in the terminal the results are below:

priya@priya-Aspire-4739Z:~$ echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4"
nameserver 8.8.8.8
nameserver 8.8.4.4
priya@priya-Aspire-4739Z:~$ sudo tee -a /etc/resolv.conf
[sudo] password for priya:
sudo service network-manager restart
sudo service network-manager restart

---

### Post by praseodym on 2013-09-27
This is one line, you better copy/paste it

---

### Post by Gosiv_Mariappan on 2013-09-27
Hi good evening,
       I gave those commands the output is given below.
 
priya@priya-Aspire-4739Z:~$ echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf sudo service network-manager restart
[sudo] password for priya:
nameserver 8.8.8.8
nameserver 8.8.4.4
priya@priya-Aspire-4739Z:~$

---

### Post by praseodym on 2013-09-27
Restartet the network?

---

### Post by Gosiv_Mariappan on 2013-09-27
At first, I gave the commands in copy and paste format but the last line didn't paste, The results are given below for those commands

priya@priya-Aspire-4739Z:~$ echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
[sudo] password for priya:
Sorry, try again.
[sudo] password for priya:
nameserver 8.8.8.8
nameserver 8.8.4.4
[EMAIL="priya@priya-Aspire-4739Z"]priya@priya-Aspire-4739Z[/EMAIL]:~$

---

### Post by praseodym on 2013-09-27
Check now:
```

ifconfig -a
iwconfig
lsmod
route -n
iwlist chan
sudo iwlist scan
```

---

### Post by Gosiv_Mariappan on 2013-09-27
Sorry for the delay,
       Every time I come to windows to contact you and then I go to ubuntu to follows your suggestions. Restart means I disconnect the network connection and again connect but there is same problem. I unplug the belkin adaptor again I connect now also the same problem occur. Shall I do anything in network manager ?.
Here the output for the above said commands:

priya@priya-Aspire-4739Z:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 04:7d:7b:c8:0d:5d 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
 
lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1312 (1.3 KB)  TX bytes:1312 (1.3 KB)
 
wlan0     Link encap:Ethernet  HWaddr 08:86:3b:91:ff:1c 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:95 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
 
priya@priya-Aspire-4739Z:~$ iwconfig
wlan0     unassociated  Nickname:"rtl_wifi"
          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0 
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
 
lo        no wireless extensions.
 
eth0      no wireless extensions.
 
priya@priya-Aspire-4739Z:~$ lsmod
Module                  Size  Used by
rfcomm                 38400  0
bnep                   17852  2
bluetooth             211435  10 rfcomm,bnep
parport_pc             27612  0
ppdev                  12849  0
r8712u                163917  0
i915                  550346  3
snd_hda_codec_hdmi     36583  1
snd_hda_codec_realtek    65004  1
snd_hda_intel          38819  3
snd_hda_codec         118613  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                85934  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0
snd_rawmidi            25157  1 snd_seq_midi
drm_kms_helper         47749  1 i915
psmouse                82769  0
coretemp               13324  0
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51593  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
drm                   233935  4 i915,drm_kms_helper
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    57014  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mei                    36756  0
serio_raw              13031  0
soundcore              12600  1 snd
joydev                 17329  0
acer_wmi               27980  0
snd_page_alloc         18398  2 snd_hda_intel,snd_pcm
sparse_keymap          13658  1 acer_wmi
microcode              18433  0
wmi                    18744  1 acer_wmi
i2c_algo_bit           13316  1 i915
mac_hid                13077  0
intel_ips              17738  0
lpc_ich                17048  0
video                  19116  2 i915,acer_wmi
lp                     17455  0
parport                40930  3 parport_pc,ppdev,lp
ext2                   63952  1
hid_generic            12484  0
usbhid                 46125  0
hid                    83037  2 hid_generic,usbhid
atl1c                  36845  0
ahci                   25631  3
libahci                26336  1 ahci
priya@priya-Aspire-4739Z:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
priya@priya-Aspire-4739Z:~$ iwlist chan
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
lo        no frequency information.
 
eth0      no frequency information.
 
priya@priya-Aspire-4739Z:~$ sudo iwlist scan
[sudo] password for priya:
wlan0     Scan completed :
          Cell 01 - Address: F4:EC:38:DF:99:AA
                    ESSID:"Research Scholar Hostel"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.472 GHz (Channel 13)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Signal level=48/100 
 
lo        Interface doesn't support scanning.
 
eth0      Interface doesn't support scanning.
 
priya@priya-Aspire-4739Z:~$

---

### Post by praseodym on 2013-09-27
Check
```

sudo dhclient wlan0
ifconfig wlano
route -n
cat /etc/resolv.conf
```

---

### Post by Gosiv_Mariappan on 2013-09-27
priya@priya-Aspire-4739Z:~$ sudo dhclient wlan0
[sudo] password for priya:
ifconfig wlano
route -n
cat /etc/resolv.conf

when I closed the terminal this msg appeared.
There is still a process running in this terminal. Closing the terminal will kill it.

---

### Post by praseodym on 2013-09-27
ESSID:"Research Scholar Hostel"

Is this your network?

---

### Post by Gosiv_Mariappan on 2013-09-28
Yes, that is my network.

---

### Post by praseodym on 2013-09-28
If you have access to the router change the settings to:
[LIST]
[*]
[*]ESSID without blanks
[*]encryption to WPA2-AES (CCMP)
[*]a fixed channel
[*]bandwidth to 20MHz instead of 20/40MHz
[*] Check if a MAC-address filter is on. If so, turn it off
[/LIST]

---

### Post by Gosiv_Mariappan on 2013-10-01
I can't change the route, I have no access about that. There is lots of restriction because this is institution connection

---

### Post by MIJ-VI on 2013-10-01
> Belkin Components F7D1101 Basic Wireless USB Adapter v1000 [_Realtek RTL8188SU_]

Linux priya-Aspire-4739Z _3.8.0-29-generic_ #42~precise1-Ubuntu SMP Wed Aug 14 15:31:16 UTC 2013 i686 i686 i386 GNU/Linux

I don't know about the Realtek RTL8188SU, but the Realtek rtl8192cu doesn't work with Ubuntu 12.04.3's Linux kernel 3.8.0.x (or Ubuntu 12.04.2's kernel 3.5.x) but *does* work with Ubuntu 12.04 /12.04.1's Linux kernel 3.2.x and ubuntu-13.10-beta2-desktop-amd64's kernel 3.11.x:

[ubuntu] Realtek RTL8192CU Driver issues under 13.04 
[http://ubuntuforums.org/showthread.php?t=2148130](http://ubuntuforums.org/showthread.php?t=2148130)

Post #7: [http://ubuntuforums.org/showthread.php?t=2148130&p=12803070#post12803070](http://ubuntuforums.org/showthread.php?t=2148130&p=12803070#post12803070)

---

### Post by praseodym on 2013-10-01
Alternatively, try Wicd instead of the network-manager:
```

wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon01441.tar.gz
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon01441.tar.gz
cd wicd-1.6.x_addon01441
# Installation
sudo ./install_wicd_addon
sudo service network-manager stop
sudo killall wpa_supplicant
sudo service wicd restart
```
Choose **wlan0** as interface name and **wext** as driver.

---

### Post by Gosiv_Mariappan on 2013-10-05
Hi good evening,
I gave the first line in the terminal that results unable to locate package wicd. I had placed the wicd tar file in the desktop. I ddn't know where I need to place.

priya@priya-Aspire-4739Z:~$ sudo apt-get install --reinstall wicd
[sudo] password for priya:
Reading package lists... Done
Building dependency tree      
Reading state information... Done
E: Unable to locate package wicd
priya@priya-Aspire-4739Z:~$

---

### Post by praseodym on 2013-10-05
Did you activate the "universe" sources?

```
sudo apt-get update
```

afterwards

---

### Post by Gosiv_Mariappan on 2013-10-05
I gave the above command, the output 

priya@priya-Aspire-4739Z:~$ sudo apt-get update
[sudo] password for priya: 
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg
  Could not resolve 'extras.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise Release.gpg
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates Release.gpg
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release.gpg
  Could not resolve 'in.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg)  Could not resolve 'in.archive.ubuntu.com'
 
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg)  Could not resolve 'in.archive.ubuntu.com'
 
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg)  Could not resolve 'in.archive.ubuntu.com'
 
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/precise-security/Release.gpg)  Could not resolve 'security.ubuntu.com'
 
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/precise/Release.gpg)  Could not resolve 'extras.ubuntu.com'
 
W: Some index files failed to download. They have been ignored, or old ones used instead.
priya@priya-Aspire-4739Z:~$ 
 

Again I gave the previous comment but the result is same

---

### Post by praseodym on 2013-10-06
Download these files and save them in "Downloads":

[http://de.archive.ubuntu.com/ubuntu/pool/universe/w/wicd/wicd_1.7.2.3-1ubuntu0.1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/universe/w/wicd/wicd_1.7.2.3-1ubuntu0.1_all.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/universe/w/wicd/wicd-gtk_1.7.2.3-1ubuntu0.1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/universe/w/wicd/wicd-gtk_1.7.2.3-1ubuntu0.1_all.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/universe/w/wicd/wicd-daemon_1.7.2.3-1ubuntu0.1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/universe/w/wicd/wicd-daemon_1.7.2.3-1ubuntu0.1_all.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/universe/w/wicd/python-wicd_1.7.2.3-1ubuntu0.1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/universe/w/wicd/python-wicd_1.7.2.3-1ubuntu0.1_all.deb)

[http://www.elektronenblitz63.de/download/wicd-1.6.x_addon01441.tar.gz](http://www.elektronenblitz63.de/download/wicd-1.6.x_addon01441.tar.gz)
```

cd ~/Downloads/
sudo dpkg -i *.deb
tar xvf wicd-1.6.x_addon01441.tar.gz
cd wicd-1.6.x_addon01441
# Installation
sudo ./install_wicd_addon
sudo service network-manager stop
sudo killall wpa_supplicant
sudo service wicd restart
```

---

### Post by Gosiv_Mariappan on 2013-10-09
I did the above suggestions the results are quoted below. Still I can't connect network. there is the same problem. 

priya@priya-Aspire-4739Z:~$ cd ~/Downloads/
priya@priya-Aspire-4739Z:~/Downloads$ sudo dpkg -i *.deb
[sudo] password for priya: 
Selecting previously unselected package python-wicd.
(Reading database ... 143023 files and directories currently installed.)
Unpacking python-wicd (from python-wicd_1.7.2.3-1ubuntu0.1_all.deb) ...
Selecting previously unselected package wicd.
Unpacking wicd (from wicd_1.7.2.3-1ubuntu0.1_all.deb) ...
Selecting previously unselected package wicd-daemon.
Unpacking wicd-daemon (from wicd-daemon_1.7.2.3-1ubuntu0.1_all.deb) ...
Selecting previously unselected package wicd-gtk.
Unpacking wicd-gtk (from wicd-gtk_1.7.2.3-1ubuntu0.1_all.deb) ...
Setting up python-wicd (1.7.2.3-1ubuntu0.1) ...
Setting up wicd-daemon (1.7.2.3-1ubuntu0.1) ...
 * Starting Network connection manager wicd                              [ OK ] 
dpkg: dependency problems prevent configuration of wicd-gtk:
 wicd-gtk depends on python-glade2; however:
  Package python-glade2 is not installed.
dpkg: error processing wicd-gtk (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wicd:
 wicd depends on wicd-gtk (= 1.7.2.3-1ubuntu0.1) | wicd-curses (= 1.7.2.3-1ubuntu0.1) | wicd-cli (= 1.7.2.3-1ubuntu0.1) | wicd-client; however:
  Package wicd-gtk is not configured yet.
  Package wicd-curses is not installed.
  Package wicd-cli is not installed.
  Package wicd-client is not installed.
  Package wicd-gtk which provides wicd-client is not configured yet.
dpkg: error processing wicd (--install):
 dependency problems - leaving unconfigured
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Errors were encountered while processing:
 wicd-gtk
 wicd
priya@priya-Aspire-4739Z:~/Downloads$ tar xvf wicd-1.6.x_addon01441.tar.gz
wicd-1.6.x_addon01441/
wicd-1.6.x_addon01441/special/
wicd-1.6.x_addon01441/Info_WPA_ge
wicd-1.6.x_addon01441/WPA2-Enterprise
wicd-1.6.x_addon01441/WPA2-Enterprise-BSSID
wicd-1.6.x_addon01441/active_1.6.x_original
wicd-1.6.x_addon01441/Version_V.01.4.4
wicd-1.6.x_addon01441/wep-bssid
wicd-1.6.x_addon01441/wep-ttls
wicd-1.6.x_addon01441/wpa-eap-bssid
wicd-1.6.x_addon01441/wpa1
wicd-1.6.x_addon01441/wpa1-bssid
wicd-1.6.x_addon01441/wpa2
wicd-1.6.x_addon01441/wpa2-bssid
wicd-1.6.x_addon01441/wpa-hidden
wicd-1.6.x_addon01441/readme_ge
wicd-1.6.x_addon01441/uninstall_wicd_addon
wicd-1.6.x_addon01441/install_wicd_addon
wicd-1.6.x_addon01441/active_addon
wicd-1.6.x_addon01441/special/WPA1-FH_Giessen
wicd-1.6.x_addon01441/special/WPA2-FH_Giessen
wicd-1.6.x_addon01441/special/WPA2-FH_Zeeland
wicd-1.6.x_addon01441/special/Eduroam_FH-Jena
priya@priya-Aspire-4739Z:~/Downloads$ cd wicd-1.6.x_addon01441
priya@priya-Aspire-4739Z:~/Downloads/wicd-1.6.x_addon01441$ # Installation
priya@priya-Aspire-4739Z:~/Downloads/wicd-1.6.x_addon01441$ sudo ./install_wicd_addon
 
prüfe Wicd 1.6.x Installation...
 
/etc/wicd/encryption/templates/active
 
prüfe Installation
 
find: `active.bak': No such file or directory
 
Installiere Wicd AddOn ...
 
sichere Originaldateien...
 
Kopiere neue Templates...
 
Installation abgeschlossen
priya@priya-Aspire-4739Z:~/Downloads/wicd-1.6.x_addon01441$ sudo service network-manager stop
network-manager stop/waiting
priya@priya-Aspire-4739Z:~/Downloads/wicd-1.6.x_addon01441$ sudo killall wpa_supplicant
priya@priya-Aspire-4739Z:~/Downloads/wicd-1.6.x_addon01441$ sudo service wicd restart
 * Restarting Network connection manager wicd                            [ OK ] 
priya@priya-Aspire-4739Z:~/Downloads/wicd-1.6.x_addon01441$ 
priya@priya-Aspire-4739Z:~/Downloads/wicd-1.6.x_addon01441$

---

### Post by praseodym on 2013-10-09
Choose **wlan0** as interface name and **wext** as driver.

---

### Post by Gosiv_Mariappan on 2013-12-04
Thank you very much for your effort to help me. I got this from another way. My sincere apologize for the delayed response. Due to some technical problem with our network I am unable to proceed and followed you. Once again I thank you.

---

