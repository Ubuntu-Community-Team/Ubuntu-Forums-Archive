---
title: "Asus PCE-N15 on ubuntu 14.04"
date: 2014-09-15
forum: Networking &amp; Wireless
---

### Post by jeroen8 on 2014-09-15
[FONT=arial]Dear all,

At home I always had windows, but Im tired of all the stuff windows is doing.
For that reason I switched to Ubuntu. I'm very new to this OS, but I'm willing to learn about it! At the moment I'm trying to let the internet work.

The WIFI symbol tells me that I'm connected to my router and if do the command nm-tool I do have the status connected and i[/FONT][COLOR=#000000][FONT=sans-serif]f I do the command route I get the IP address of the router.[/FONT][/COLOR][FONT=arial]
The card that I have is an ASUS PCE-N15. I tried to do the command ./scripts/driver-select rtl8192ce, [/FONT][FONT=sans-serif][COLOR=#000000][FONT=arial]but it gives back that everything already exists. 

If I go to the correct folder, where I unzipped everything, and I run the command make it gives me error 2.

I really dont know what to do anymore. Could anybody help me with this problem?  

Thank you all! 

Regards,
Jeroen
[/FONT]

[/COLOR][/FONT]

---

### Post by ian-weisser on 2014-09-15
If the 'route' command can see your router, then the network is working.
Don't install anything else.

Open a terminal. Use the 'ping' command to ping your router. Does it work?
Next, ping a server out on the internet (8.8.8.8 is usually a good one). Does that work?
Finally, ping a server using a domain name (example.com) instead of an IP address. Does that work?

---

### Post by jeroen8 on 2014-09-16
Hi Ian,

The ping for my router is working NOK.
The ping to 8.8.8.8 is working NOK.
The ping for a domain name example.com NOK.

The results of command route is:
**Destination | Gateway | Genmask | Flags Metric  Ref | Use Iface**
default |192.168.2.254  | 0.0.0.0 | UG     0      0 | 0 wlan0
192.168.2.0| * |255.255.255.0| U  9      0 | 0 wlan0

So far I didn't install anything, because "make install" gave an error 2 as well. 

Regards,
Jeroen

---

### Post by praseodym on 2014-09-16
Checked this one?
[http://ubuntuforums.org/showthread.php?t=2244437&p=13123031#post13123031](http://ubuntuforums.org/showthread.php?t=2244437&p=13123031#post13123031)

---

### Post by jeroen8 on 2014-09-16
Hi Praseodym,

Thank you for your answer.
I followed the steps in the post you gave me. 
The following code cause that I'm not connected to my router anymore (see below).
 
echo echo "options rtl8192ce swlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8192ce.conf
sudo modprobe -rfv rtl8192ce
sudo modprobe -v rtl8192ce

I did checked my manual of the router and there is nothing written about how to set up the router or connect to internet for Linux users.
I changed the security status to WPA2, but this also gave no result.

Regards,
Jeroen

---

### Post by praseodym on 2014-09-16
Did you run "double echo" as decribed:
> ```

[COLOR="#FF0000"]echo echo[/COLOR] "options rtl8192ce swlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8192ce.conf
sudo modprobe -rfv rtl8192ce
sudo modprobe -v rtl8192ce
```
If yes overwrite it via

```
echo "options rtl8192ce swlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8192ce.conf
sudo modprobe -rfv rtl8192ce
sudo modprobe -v rtl8192ce
```
If no, remove the file and reboot:
```

sudo rm /etc/modprobe.d/rtl8192ce.conf
```

---

### Post by jeroen8 on 2014-09-17
Hello,

Thank you I removed the file, did a reboot and did the code :
[COLOR=#000000]echo "options rtl8192ce swlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8192ce.conf[/COLOR]
[COLOR=#000000]sudo modprobe -rfv rtl8192ce[/COLOR]
[COLOR=#000000]sudo modprobe -v rtl8192ce

It still doesn't work Now it doesn't connect at all anymore. 
It tries to connect, but then it fails to connect to my router now. 

I did a reboot but that didn't help. 

Regards,
Jeroen[/COLOR]

---

### Post by praseodym on 2014-09-17
Ok, remove the file again, reboot and try to update the driver:

```
sudo apt-get install --reinstall linux-headers-generic linux-headers-$(uname -r) build-essential dkms git
git clone https://github.com/FreedomBen/rtl8188ce-linux-driver
cd rtl8188ce-linux-driver
make
sudo make install
sudo cp -r firmware/* /lib/firmware
```
Reboot again.

---

### Post by jeroen8 on 2014-09-17
Ey praseodym,

I tried what you said, but it isnt working. It says it misses the packages build-essential, dkms and git. You should know I'm not able to connect to the internet by any means except the WiFi. I have no cable going to the computer, because the computer is in another room.

Like I stated in the beginning I'm totally new to this. I just installed Ubuntu and didnt update or downloaded anything to the computer.

Thank you.

Regards,
Jeroen

---

### Post by praseodym on 2014-09-17
Ok, I zipped it here. Download these 2 files and save them in "Downloads":

[https://dl.dropboxusercontent.com/u/2902662/rtl8188ce-linux-driver.zip](https://dl.dropboxusercontent.com/u/2902662/rtl8188ce-linux-driver.zip)

[http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu5_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu5_all.deb)

Unpack the ZIP file there and run:

```
cd ~/Downloads/
sudo dpkg -i *.deb
cd rtl8188ce-linux-driver
make
sudo make install
sudo cp -r firmware/* /lib/firmware
```
Reboot.

---

### Post by jeroen8 on 2014-09-18
Hi,

Thank you for reply.
I tried your command but I got the following back when I do the make command:

jeroen@JeroenEmy:~/Downloads$ sudo dpkg -i *.deb
[sudo] password for jeroen:
Selecting previously unselected package dkms.
(Reading database ... 163789 files and directories currently installed.)
Preparing to unpack dkms_2.2.0.3-1.1ubuntu5_all.deb ...
Unpacking dkms (2.2.0.3-1.1ubuntu5) ...
Setting up dkms (2.2.0.3-1.1ubuntu5) ...
Processing triggers for man-db (2.6.7.1-1) ...
jeroen@JeroenEmy:~/Downloads$ cd rtl8188ce-linux-driver/
jeroen@JeroenEmy:~/Downloads/rtl8188ce-linux-driver$ make
if [ -e verify_branch.sh ] ; \
      then \
          ./verify_branch.sh ; \
      fi;
Verifying a sane branch for your kernel version...
./verify_branch.sh: 14: ./verify_branch.sh: git: not found
./verify_branch.sh: 15: ./verify_branch.sh: git: not found
No (Current branch )
Recommended branch is ubuntu-14.04 based on your kernel version (3.13.0-32-generic)
Should I switch it to ubuntu-14.04 for you?  (y/n): y
./verify_branch.sh: 22: ./verify_branch.sh: git: not found
make: *** [all] Error 127
jeroen@JeroenEmy:~/Downloads/rtl8188ce-linux-driver$ sudo make install
if [ -e verify_branch.sh ] ; \
      then \
          ./verify_branch.sh ; \
      fi;
Verifying a sane branch for your kernel version...
./verify_branch.sh: 14: ./verify_branch.sh: git: not found
./verify_branch.sh: 15: ./verify_branch.sh: git: not found
No (Current branch )
Recommended branch is ubuntu-14.04 based on your kernel version (3.13.0-32-generic)
Should I switch it to ubuntu-14.04 for you?  (y/n): y
./verify_branch.sh: 22: ./verify_branch.sh: git: not found
make: *** [all] Error 127

Also I used the command ping to ping my router, but doesnt bring anything back, but if I look in the router itself it says it is connected to my computer.

Regards,
Jeroen

---

### Post by praseodym on 2014-09-19
Try the 3.14 mainline kernel:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14.1-trusty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14.1-trusty/)

You need all files possible for 32 or 64 bit, respectively (i.e. also "all.deb"), but not the "lowlatency" ones. Save them in Downloads and run

```
sudo dpkg -i ~/Downloads/linux-*.deb
```
Reboot

---

### Post by jeroen8 on 2014-09-19
Hello praseodym,

I downloaded the file and did the code you gave me.
Do you want me to do the commands we discussed before after the reboot?
And which one should I do?

I feel like we're getting closer!

Regards,
Jeroen

---

### Post by praseodym on 2014-09-19
Lets check:
```

dpkg -l linux-image-* | grep ii
dpkg -l linux-headers-* | grep ii
iwconfig
ifconfig -a
route -n
iwlist chan
sudo iwlist scan
dmesg | grep rtl
cat /etc/resolv.conf
```

---

### Post by jeroen8 on 2014-09-20
Hello praseodym,

Here are the outcomes of the codes:
**dpkg -l linux-image-* | grep ii**
ii  linux-image-3.13.0-32-generic                         3.13.0-32.57                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-32-generic                   3.13.0-32.57                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                                   3.13.0.32.38                                        amd64        Generic Linux kernel image

[B]dpkg -l linux-headers-* | grep ii
[/B]ii  linux-headers-3.13.0-32                               3.13.0-32.57                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-32-generic                       3.13.0-32.57                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.14.1-031401                           3.14.1-031401.201404141220                          all          Header files related to Linux kernel version 3.14.1
ii  linux-headers-3.14.1-031401-generic                   3.14.1-031401.201404141220                          amd64        Linux kernel headers for version 3.14.1 on 64 bit x86 SMP
ii  linux-headers-generic                                 3.13.0.32.38                                        amd64        Generic Linux kernel headers

[B]iwconfig
[/B]eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Jeroen&Emy" 
          Mode:Managed  Frequency:2.457 GHz  Access Point: 84:9C:A6:82:04:D4  
          Bit Rate=7.2 Mb/s   Tx-Power=20 dBm  
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=40/70  Signal level=-70 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

[B]ifconfig -a
[/B]eth0      Link encap:Ethernet  HWaddr 74:d0:2b:9c:d6:94 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:598 errors:0 dropped:0 overruns:0 frame:0
          TX packets:598 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:121684 (121.6 KB)  TX bytes:121684 (121.6 KB)

wlan0     Link encap:Ethernet  HWaddr *<mac address>* 
          inet addr:192.168.2.15  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::12c3:7bff:fec7:8b71/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:242 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2850 (2.8 KB)  TX bytes:28835 (28.8 KB)

[B]Route -n
[/B]Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.254   0.0.0.0         UG    0      0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

**sudo iwlist scan**
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 84:9C:A6:82:04:D4
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=38/70  Signal level=-72 dBm 
                    Encryption key:on
                    ESSID:"Jeroen&Emy"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003681170964
                    Extra: Last beacon: 152ms ago
                    IE: Unknown: 000A4A65726F656E26456D79
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010A
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6C0017FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D160A000400000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0503001C127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD910050F204104A00011010440001021041000100103B0001031047001000000000000000030000849CA68204D41021000B436F72706F726174696F6E1023000B564756373531394B5732321024000B30322E30302E31333076321042000A413330353032303632351054000800060050F204000110110014576972656C65737320526F757465722857464129100800020084
                    IE: Unknown: 07064E4C20010D10
          Cell 02 - Address: E8:40:F2:BD:38:9B
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/70  Signal level=-68 dBm 
                    Encryption key:on
                    ESSID:"UPC392393"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000042c07c5ce1
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 0009555043333932333933
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: DD090010180203F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: EA:40:F2:BD:38:9D
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm 
                    Encryption key:on
                    ESSID:"UPC WifiSpots"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000042c07c659f
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 000D555043205769666953706F7473
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080000000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

[B]dmesg | grep rtl
[/B][    1.171916] rtl8192ce 0000:02:00.0: enabling device (0000 -> 0003)
[    1.184727] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[    1.261021] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    1.261140] rtlwifi: wireless switch is on

[B]cat /etc/resolv.conf
[/B]# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search home

The internet is still not working.

Thank you so much for so far!

Regards,
Jeroen

---

### Post by praseodym on 2014-09-20
You forgot the file

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14.1-trusty/linux-image-3.14.1-031401-generic_3.14.1-031401.201404141220_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14.1-trusty/linux-image-3.14.1-031401-generic_3.14.1-031401.201404141220_i386.deb)

Install it again. THIS is the kernel ;)

---

### Post by jeroen8 on 2014-09-20
Hi Praseodym,

I installed the 64bit kernel. All the stuff with i386 in it I didnt installed, because that is or 32 bit, is it? 
Is still necessary that I install this? 

The internet is after all this and reboot still not working.
Like I said, the router finds my computer and my computer finds something to which the computer is connected, but using ping to ping my router is not possible. 
I have 100% package loss.

What could it be actually?

Regards,
Jeroen

---

### Post by praseodym on 2014-09-21
Please show now

```
uname -a
```
plus the other outputs again, plus

```
ping -c 2 $(route -n | grep UG | awk {'print $2'})
ping -c 2 www.ubuntuusers.de
ping -c 2 213.95.41.11 
```

---

### Post by jeroen8 on 2014-09-21
Ey Praseodym,

Here are the outcomes:

**uname -a**
Linux JeroenEmy 3.14.1-031401-generic #201404141220 SMP Mon Apr 14 16:21:48 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

[B]dpkg -l linux-image-* | grep ii
[/B]ii  linux-image-3.13.0-32-generic                         3.13.0-32.57                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.14.1-031401-generic                     3.14.1-031401.201404141220                          amd64        Linux kernel image for version 3.14.1 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-32-generic                   3.13.0-32.57                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                                   3.13.0.32.38                                        amd64        Generic Linux kernel image
[B]
dpkg -l linux-headers-* | grep ii[/B]
ii  linux-headers-3.13.0-32                               3.13.0-32.57                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-32-generic                       3.13.0-32.57                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.14.1-031401                           3.14.1-031401.201404141220                          all          Header files related to Linux kernel version 3.14.1
ii  linux-headers-3.14.1-031401-generic                   3.14.1-031401.201404141220                          amd64        Linux kernel headers for version 3.14.1 on 64 bit x86 SMP
ii  linux-headers-generic                                 3.13.0.32.38                                        amd64        Generic Linux kernel headers

[B]iwconfig
[/B]eth0      no wireless extensions.
 
lo        no wireless extensions.
 
wlan0     IEEE 802.11bgn  ESSID:"Jeroen&Emy"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 84:9C:A6:82:04:D4   
          Bit Rate=7.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=36/70  Signal level=-74 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0

[B]ifconfig -a
[/B]eth0      Link encap:Ethernet  HWaddr 74:d0:2b:9c:d6:94  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:612 errors:0 dropped:0 overruns:0 frame:0
          TX packets:612 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:122947 (122.9 KB)  TX bytes:122947 (122.9 KB)
 
wlan0     Link encap:Ethernet  HWaddr <mac address>  
          inet addr:192.168.2.15  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::12c3:7bff:fec7:8b71/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:172 errors:0 dropped:0 overruns:0 frame:0
          TX packets:211 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17375 (17.3 KB)  TX bytes:26094 (26.0 KB)

[B]route -n
[/B]Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.254   0.0.0.0         UG    0      0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

[B]sudo iwlist scan
[/B]eth0      Interface doesn't support scanning.
 
lo        Interface doesn't support scanning.
 
wlan0     Scan completed :
          Cell 01 - Address: 84:9C:A6:82:04:D4
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"Jeroen&Emy"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004dac27eccc
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 000A4A65726F656E26456D79
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010A
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6C0017FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D160A000400000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05030014127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD910050F204104A00011010440001021041000100103B0001031047001000000000000000030000849CA68204D41021000B436F72706F726174696F6E1023000B564756373531394B5732321024000B30322E30302E31333076321042000A413330353032303632351054000800060050F204000110110014576972656C65737320526F757465722857464129100800020084
                    IE: Unknown: 07064E4C20010D10
          Cell 02 - Address: E8:40:F2:BD:38:9B
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"UPC392393"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000059e5f514fd
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 0009555043333932333933
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: DD090010180203F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: EA:40:F2:BD:38:9D
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"UPC WifiSpots"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000059e5f52684
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 000D555043205769666953706F7473
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080000000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

[B]dmesg | grep rtl
[/B][    1.282422] rtl8192ce 0000:02:00.0: enabling device (0000 -> 0003)
[    1.296061] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[    1.306561] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    1.306714] rtlwifi: wireless switch is on

[B]cat /etc/resolv.conf
[/B]# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search home

[B]ping -c 2 $(route -n | grep UG | awk {'print $2'})
[/B]PING 192.168.2.254 (192.168.2.254) 56(84) bytes of data.
 
--- 192.168.2.254 ping statistics ---
2 packets transmitted, 0 received, 100% packet loss, time 1007ms
 
[B]ping -c 2 [www.ubuntuusers.de]("http://www.ubuntuusers.de")
[/B]ping: unknown host [www.ubuntuusers.de]("http://www.ubuntuusers.de")

[B]ping -c 2 213.95.41.11
[/B]connect: Network is unreachable


Thank you.

Regards,
Jeroen

---

### Post by praseodym on 2014-09-21
Obviously, a nameserver problem: You can not ping the router or website. Lets try:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee /etc/resolv.conf
sudo service network-manager restart
```

---

### Post by jeroen8 on 2014-09-21
Hi Praseodym,

Okay. I did what you said, but I'm still not able to ping my router or a website. 
I also notice that the strength of my wifi is one time maximum and then it is 2 bars in the wifi symbol.

**ping -c 2 $(route -n | grep UG | awk {'print $2'})**
PING 192.168.2.254 (192.168.2.254) 56(84) bytes of data.


--- 192.168.2.254 ping statistics ---
2 packets transmitted, 0 received, 100% packet loss, time 999ms


**ping -c 2 [www.ubuntuusers.de](www.ubuntuusers.de)**
ping: unknown host [www.ubuntuusers.de](www.ubuntuusers.de)


**ping -c 2 213.95.41.11**
PING 213.95.41.11 (213.95.41.11) 56(84) bytes of data.


--- 213.95.41.11 ping statistics ---
2 packets transmitted, 0 received, 100% packet loss, time 999ms


Regards,
Jeroen

---

### Post by praseodym on 2014-09-21
Weird. Can you enter the router interface when typing 192.168.2.254 into your browser?

---

### Post by jeroen8 on 2014-09-21
Ey Praseodym,

No, that is not possible. 
It tries to connect for a few minutes (like 5 minutes) when I type it in Firefox. 

Could it be that the signal of the WiFi it too weak? 
Which will be weird, because my laptop is standing next to the computer and I have full WiFi connection with the laptop.

Regards,
Jeroen

---

### Post by praseodym on 2014-09-21
Is your laptop also an Ubuntu one? If yes (or if you can boot with Live-CD/USB there), please show from there:

```
ifconfig -a
iwconfig
route -n
iwlist chan
sudo iwlist scan
cat /etc/resolv.conf
arp -v
```
Can you enter the router interface from there, installation or Live-system? Maybe it can only handle one connection?!

---

### Post by jeroen8 on 2014-09-21
Ey Praseodym,

No, this one works on Windows 7. 
I can enter the interface of my router through Windows 7.
And the weird thing is that I can see my computer (Ubuntu system) when I log into my router.

Regards,
Jeroen

---

### Post by praseodym on 2014-09-21
Now, thats really weird.

Check via Windows in the router:
[LIST]
[*]
[*]Network not hidden
[*]fixed channel
[*]bandwidth 20 MHz instead of 20/40MHz
[*]MAC-address filter is off
[*]pure WPA2-AES (CCMP) encryption
[*]enough free IP addresses (network 255.255.255.0)
[/LIST]

---

### Post by jeroen8 on 2014-09-21
Ey,

1. The network is not hidden
2. No, it is on automatic. I guess that means it is not fixed.
3. Bandwidth is 20 Mhz
4. No filter.
5. WPA2 only PSK. 
6. I guess I have enough. I can go until 192.168.2.252.

I see the computer in the logging of my router as well. Saying sending ACK to 192.168.2.15 (= Ubuntu system).

Regards,
Jeroen

---

### Post by praseodym on 2014-09-21
So, that is the right IP address as decribed by "ifconfig -a". Lets deactivate IPv6 system wide: 
```

gksudo gedit /etc/sysctl.conf
```
Add these lines:

```
net.ipv6.conf.all.disable_ipv6=1  
net.ipv6.conf.default.disable_ipv6=1  
net.ipv6.conf.lo.disable_ipv6=1
```
Save, close the editor and reboot.

---

### Post by jeroen8 on 2014-09-21
Hi,

I add it to the file. 
The internet is still not working

In the whole file, before every line there is a #. 
Should I add that to the line you gave me as well? 

If I look in the logging from my router I see this:
09/22/2014  00:01:47 TR069:Inform Fail!!(Invalid URL or ACS unreachable)
09/22/2014  00:01:47 TR069:Sending 2 PERIODIC inform.
09/22/2014  00:01:30 If(PPPoE2) send PADI      
09/21/2014  23:59:26 sending ACK to 192.168.2.15

This only appears after sending ACK to 192.168.2.15. This does not appears sending ACK to <other device>.
 
Also pinging still gives the same results.

Regards,
Jeroen

---

### Post by praseodym on 2014-09-21
No, "#" is commenting out! Is the firmware of the router up to date? Are the PPPoE login/PW data added in your router?

---

### Post by jeroen8 on 2014-09-22
Ey Praseodym,

Yes, I thought so I would be something like that.

The firmware is up-to-date. How can I see PPPoE login/PW is added to my router?
It has the option Enable PPPoE passthrough function  enabled.

Regards,
Jeroen

---

### Post by praseodym on 2014-09-22
Imho PPPoE passthrough works like this: The client uses the Login/PW of the ISP. What about disabling it and entering the data in the router itself? Does Windows use this Login/PW?

---

### Post by jeroen8 on 2014-09-23
Hi Praseodym,

Do you mean to add it to NAT port mapping manually? 
I just did, but I'm not sure which ports I have to fill in the LAN Port and Public port. 

I disabled the PPPoE passthrough. 

Regards,
Jeroen

---

### Post by jeroen8 on 2014-09-24
Hi Praseodym,

The internet works now! 
But it is very slow compared to my laptop. 
I see that some of packages still don't arrive if I use the PING command. I have a package loss of 75%.

How can I help this? Should I change something in the router settings?

Regards,
Jeroen

---

### Post by praseodym on 2014-09-24
Try these nameservers:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee /etc/resolv.conf
sudo service network-manager restart
```
and add the mtu-value of your ISP in the wireless profile instead of "automatic"

---

### Post by jeroen8 on 2014-09-24
Hi Praseodym,


I set the MTU value to 1024. It seems that the internet is working now. Only around 50% of the package is lost.
I found a program called WICD on the internet, which should fix that. I didnt install it, because I dont have much time.

I hope I will do it tomorrow.

Regards,
Jeroen

---

### Post by praseodym on 2014-09-24
I don't think 1024 is right?! Try 1500 or 1492 and restart the network, respectively. Check "ifconfig -a" for "errors" after each change.

---

### Post by jeroen8 on 2014-09-26
Ey Praseodym,

Still they internet is very slow. 
It doesnt give an error if I check with ifconfig -a.

I'm trying to do a sudo apt-get update and upgrade, but this goes very slow as well. 

Regards,
jeroen

---

