---
title: "I installed Ubuntu 2004 and I keep losing the WIFI connection."
date: 2022-08-23
forum: Networking &amp; Wireless
---

### Post by SUPERFITTER on 2022-08-23
I installed Ubuntu 2004 and I keep losing the WIFI connection.  As you can see everything is upgraded.  What did I miss?
Thank you



```
me@me1:~$ sudo apt update
[sudo] password for me: 
Hit:1 http://us.archive.ubuntu.com/ubuntu focal InRelease
Hit:2 http://us.archive.ubuntu.com/ubuntu focal-updates InRelease
Hit:3 http://us.archive.ubuntu.com/ubuntu focal-backports InRelease
Hit:4 http://security.ubuntu.com/ubuntu focal-security InRelease
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
me@me1:~$ sudo apt dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
me@me1:~$ sudo apt install pastebinit
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  pastebinit
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 14.2 kB of archives.
After this operation, 156 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu focal/main amd64 pastebinit all 1.5.1-1 [14.2 kB]
Fetched 14.2 kB in 0s (114 kB/s)      
Selecting previously unselected package pastebinit.
(Reading database ... 186823 files and directories currently installed.)
Preparing to unpack .../pastebinit_1.5.1-1_all.deb ...
Unpacking pastebinit (1.5.1-1) ...
Setting up pastebinit (1.5.1-1) ...
Processing triggers for man-db (2.9.1-1) ...
me@me1:~$ wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
> chmod +x wireless-info && \
> ./wireless-info
--2022-08-23 16:39:40--  https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info
Resolving github.com (github.com)... 140.82.113.3
Connecting to github.com (github.com)|140.82.113.3|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info [following]
--2022-08-23 16:39:40--  https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 2606:50c0:8003::154, 2606:50c0:8002::154, 2606:50c0:8001::154, ...
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|2606:50c0:8003::154|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 17534 (17K) [text/plain]
Saving to: ‘wireless-info’

wireless-info       100%[===================>]  17.12K  --.-KB/s    in 0.002s  

Last-modified header missing -- time-stamps turned off.
2022-08-23 16:39:40 (7.26 MB/s) - ‘wireless-info’ saved [17534/17534]


Results saved in "/home/me/wireless-info.txt".

Results also archived in "/home/me/wireless-info.tar.gz", as they exceed the 19.5 kB size limit for ".txt" attachments on the Ubuntu Forums.


```

---

### Post by chili555 on 2022-08-26
> Results saved in "/home/me/wireless-info.txt".Please post them.

---

### Post by SUPERFITTER on 2022-08-26
[https://paste.ubuntu.com/p/ttsDCB9W7t/](https://paste.ubuntu.com/p/ttsDCB9W7t/)


Your submission could not be processed because a security token was missing.

 If this occurred unexpectedly, please [inform the administrator]("https://ubuntuforums.org/sendmessage.php")  and describe the action you performed before you received this error.  If possible, please include the error page URL plus the date and time  the error occured. 

 Tip : Please shorten long posts by using [https://paste.ubuntu.com/](https://paste.ubuntu.com/) for terminal and log output and link to it in your posts.
             
             Ubuntu Forums

---

### Post by chili555 on 2022-08-26
I see two things here. First, you have two possibly conflicting drivers installed. Let's blacklist one and see if the performance improves:

```
sudo -i
modprobe -r rtl8192cu
echo "blacklist rtl8192cu  >>  /etc/modprobe.d/blacklist.conf
exit
```

Any improvement?  

Second, the log shows that your wireless is roaming from among two access points. One, MOTO45DF, has a very low signal strength and so we would expect it to drop. The other, MOTO45DF_RPT, has a very good signal strength and should preform well. I suggest that you open the Network Manager settings and select MOTO45DF and click 'Forget Connection.'

Also, please consider my troubleshooting steps here: [https://askubuntu.com/questions/1355577/wifi-not-working-after-sometime-in-ubuntu-21-04/1355583#1355583](https://askubuntu.com/questions/1355577/wifi-not-working-after-sometime-in-ubuntu-21-04/1355583#1355583)

---

### Post by SUPERFITTER on 2022-08-27
So far working OK.   

I will let you know if the problem returns.  

Thank you again for the great job that you do for the community.

---

### Post by chili555 on 2022-08-27
Awesome! Glad it's working.

Thank you so much for your kind words.

---

### Post by SUPERFITTER on 2022-08-28
I have the same problem again.  
Saturday, Ubuntu ran for about 4 hours no problem.  
Today it ran for 30 minutes and stopped.  
I rebooted and it is working now, but I do not know for how long.  
The WIFI icon shows that I am on line, but I get a no connection message.

---

### Post by chili555 on 2022-08-28
> I get a no connection message.That typically means that you are connected to the router but not the internet. That usually indicates a DNS issue. May we see:```
ping -c3 192.168.0.1
ping -c3 8.8.8.8
ping -c3 www.ubuntu.com
ls -al /etc/resolv.conf
```Are there any clues in the log?```
sudo dmesg | grep -e wlx -e rtl
```

---

### Post by SUPERFITTER on 2022-08-28
me@me1:~$ ping -c3 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=12.0 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=2.06 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=2.26 ms

--- 192.168.0.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 2.058/5.431/11.974/4.627 ms
me@me1:~$ ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=114 time=19.6 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=114 time=19.8 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=114 time=18.0 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 18.048/19.156/19.806/0.787 ms
me@me1:~$ ping -c3 [www.ubuntu.com](www.ubuntu.com)
PING [www.ubuntu.com(website-content-cache-1.canonical.com](www.ubuntu.com(website-content-cache-1.canonical.com) (2620:2d:4000:1::26)) 56 data bytes

--- [www.ubuntu.com](www.ubuntu.com) ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2035ms

me@me1:~$ ls -al /etc/resolv.conf
lrwxrwxrwx 1 root root 39 Aug 23 15:23 /etc/resolv.conf -> ../run/systemd/resolve/stub-resolv.conf
me@me1:~$ 

me@me1:~$ sudo dmesg | grep -e wlx -e rtl
[sudo] password for me: 
[   16.283942] rtl8192cu: Chip version 0x11
[   16.764841] rtl8192cu: Board Type 0
[   16.765916] rtl_usb: rx_max_size 15360, rx_urb_num 8, in_ep 1
[   16.765948] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[   16.766037] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   16.766497] usbcore: registered new interface driver rtl8192cu
[   16.867604] usbcore: registered new interface driver rtl8xxxu
[   17.063830] rtl8192cu 5-1:1.0 wlx08606ecdf61a: renamed from wlan0
[   33.235038] rtl8192cu: MAC auto ON okay!
[   33.433806] rtl8192cu: Tx queue select: 0x05
[   42.145372] wlx08606ecdf61a: authenticate with 60:45:cb:af:9a:28
[   42.172550] wlx08606ecdf61a: send auth to 60:45:cb:af:9a:28 (try 1/3)
[   42.175209] wlx08606ecdf61a: authenticated
[   42.175956] wlx08606ecdf61a: associate with 60:45:cb:af:9a:28 (try 1/3)
[   42.197971] wlx08606ecdf61a: RX AssocResp from 60:45:cb:af:9a:28 (capab=0x1411 status=0 aid=1)
[   42.313883] wlx08606ecdf61a: associated
[   42.408080] IPv6: ADDRCONF(NETDEV_CHANGE): wlx08606ecdf61a: link becomes ready
me@me1:~$

---

### Post by chili555 on 2022-09-02
> [ 16.766497] usbcore: registered new interface driver rtl8192cu
[ 16.867604] usbcore: registered new interface driver rtl8xxxu
[ 17.063830] rtl8192cu 5-1:1.0 wlx08606ecdf61a: renamed from wlan0
[ 33.235038] rtl8192cu: MAC auto ON okay!
[ 33.433806] rtl8192cu: Tx queue select: 0x05But didn't we blacklist rtl8192cu several steps ago in favor of rtl8xxxu??

Please show us:

```
cat /etc/modprobe.d/blacklist.conf
ip a
```

---

### Post by SUPERFITTER on 2022-09-03
```
me@me1:~$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
me@me1:~$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp7s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether 50:e5:49:c4:df:a1 brd ff:ff:ff:ff:ff:ff
3: wlx08606ecdf61a: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 08:60:6e:cd:f6:1a brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.14/24 brd 192.168.0.255 scope global dynamic noprefixroute wlx08606ecdf61a
       valid_lft 86218sec preferred_lft 86218sec
    inet6 2601:408:c083:32f0::8/128 scope global dynamic noprefixroute 
       valid_lft 7018sec preferred_lft 7018sec
    inet6 2601:408:c083:32f0:aa44:e88f:11ed:801c/64 scope global temporary dynamic 
       valid_lft 345583sec preferred_lft 85971sec
    inet6 2601:408:c083:32f0:330a:bd6c:3be7:1a6a/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 345583sec preferred_lft 345583sec
    inet6 fe80::b95e:d57f:1245:d6ee/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
me@me1:~$ 


```

---

### Post by chili555 on 2022-09-03
It appears that the blacklist change wasn't made; possibly because of my slight typo. Let's try again:

```
sudo -i
modprobe -r rtl8192cu
echo "blacklist rtl8192cu"  >>  /etc/modprobe.d/blacklist.conf
exit
```Check:

```
cat /etc/modprobe.d/blacklist.conf
```The very last line should now read:

```
blacklist rtl8192cu
```Were you able to implement my troubleshooting steps? [https://askubuntu.com/questions/1355577/wifi-not-working-after-sometime-in-ubuntu-21-04/1355583#1355583](https://askubuntu.com/questions/1355577/wifi-not-working-after-sometime-in-ubuntu-21-04/1355583#1355583)

---

### Post by SUPERFITTER on 2022-09-04
The connection seems to be working.  I can switch from my router modem to my router repeater, so far without a problem.  I did read your troubleshooting steps? [https://askubuntu.com/questions/1355...355583#1355583]("https://askubuntu.com/questions/1355577/wifi-not-working-after-sometime-in-ubuntu-21-04/1355583#1355583")  I am using a desktop computer.  I turn off the power after every use.  My problem started when I updated to 2204.  I reinstalled Ubuntu 2004 and found this problem with the WIFI connection.  I will run Ubuntu for a few days and see if I have any more problems.

Thank you again for your help

---

### Post by SUPERFITTER on 2022-09-07
Solved

---

