---
title: "IPW2200 - Dell Inspiron 9300 - Lost and Total Newbie"
date: 2006-08-13
forum: Networking &amp; Wireless
---

### Post by dfa_geko on 2006-08-13
Hi Everyone!

I'm a newbie in Linux. I am trying to move away from Windows and heard about Ubuntu Linux. So I decided to try. I got most of my devices working except for my wireless card. I've read other posts on the subject and tried and tried to no avail. 
I followed these instructions and it didn't do much. [http://www.ubuntuforums.org/showthread.php?t=26623]("http://www.ubuntuforums.org/showthread.php?t=26623") When I did follow these instructions, it wouldn't connect 

So, I just reinstalled Ubuntu, so this is a fresh copy. 

I am using Ubuntu 6.06. Dell Inspiron 9300, Intel PRO/Wireless 2200. I also have a WPA-Secured home network.

Here is my **dmesg | grep ipw2200**
> 
[17179590.048000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.1
[17179590.048000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17179590.048000] Warning: PCI driver ipw2200 has a struct device_driver shutdown method, please update!
[17179590.048000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[17179590.244000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)

The only thing I've done so far is that I have extracted the firmware files to /usr/lib/hotplug/firmware. 

I am so lost! Please help! Just treat me like a total newbie and maybe you can point me in the right direction.

Thanks!!!

dfa_geko

---

### Post by Buffalo Soldier on 2006-08-14
Hi there, welcome to Ubuntu.

I'm using DELL Inspiron 510m and the exact same network card that you're using. So far I did not have to install any additional drivers/firmware to get it working.

Right now I'm at home and using my wired connection. But here's my **iwconfig** output:
```
$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11g  ESSID:"roslan"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:E0:98:46:93:F8
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=56/100  Signal level=-67 dBm  Noise level=-89 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:5

```

And when I'm outside and using wifi it works fine (but I haven't tried with WEP/WPA connections). 

I'm also using the network-manager applet. The instructions that I followed is here -> [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager). Attached is screenshot of the applet in action.

---

### Post by dfa_geko on 2006-08-14
Hi,

Here is my **iwconfig**:

> 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:off/any
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power=off   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


Here is my **ifconfig**:

> 
eth0      Link encap:Ethernet  HWaddr 00:11:43:78:AF:DB
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:43ff:fe78:afdb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:763001 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1904346 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1150549050 (1.0 GiB)  TX bytes:125149190 (119.3 MiB)
          Interrupt:209

eth1      Link encap:Ethernet  HWaddr 00:12:F0:6F:31:63
          inet6 addr: fe80::212:f0ff:fe6f:3163/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:201 Memory:dcffd000-dcffdfff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:572 (572.0 b)  TX bytes:572 (572.0 b)


---

### Post by dfa_geko on 2006-08-14
I already have network-manager and network-manager-gnome installed.

---

### Post by Scheater5 on 2006-08-14
I'm a noob, and probably not one to be giving advice, but it seems to me there have been issues lately with Ubuntu and drivers.  Until recently my Inspiron 9300 has recognized the internal card and had no need for my intervention with the driver.  But recently I've had to reinstall Dapper, and it suddenly stopped working - a problem I traced to the driver.  I have a copy of the windows version of the Proset driver, and in installed it with ndiswrapper.  I don't know if this is a fix for your problem or not, but there certainly seems to be a rash of similar problems lately.

---

