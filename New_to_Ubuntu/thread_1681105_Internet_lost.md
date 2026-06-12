---
title: "Internet lost"
date: 2011-02-03
forum: New to Ubuntu
---

### Post by e.jejcic on 2011-02-03
Good afternoon to everybody:
I have a home network as follows:one desktp with Ubuntu 10.04 connected to a Motorola Gateway via ethernet cable. This Gateway has wireles. On the other side I have a notebook with Windows XP side by side with Ubuntu 10.04. I don't know why I lost connecyion to internet on Linux side (windows is connected fine) Some smart gay installed AVG antivirus ( is not running). Since then I have no internet connection (internet  applet missing). The WIFI card was mounted with XP. I'm not a computer savy that is why appealing to people who knows. I was thinking if it is possibly to alter settings that to avoid me to connect to Internet from the Ubuntu side.I know that my english is not very god, so be gently. I thank you al in advance. I don't know where to start from.Regards from Eduardo.

---

### Post by vinnywright on 2011-02-03
try starting the network applet frome the CLI or run dialog box with ```
nm-applet
``` and post the output of ```
ifconfig
``` and ```
iwconfig
```

VINNY

---

### Post by e.jejcic on 2011-02-04
Good morning "winny":
Sorry the delay but since I am in a wheelchair I have to wait for my wife to get the notebook.
Anyway iI ran nm-applet and the output was that nm is in other package and suggest to run "sudo apt-get install network-manager-gnome". So the output is:E:the package doesn't have candidate (?) for its instalation.
Some words might be wrong because I'm translating from spanish. Anyway regards from Eduardo, and thank you very much for the help.

---

### Post by e.jejcic on 2011-02-04
I would like to add that I was at Software Center and the network manager gnome is installed. Thank's from Eduardo.

---

### Post by e.jejcic on 2011-02-04
Any help, please.

---

### Post by e.jejcic on 2011-02-04
ifconfig gives:
eth0    Link encap:Ethernetdire4ction:Hw 08:00:46:81:9d:46
        ACTIVO DIFUSION MULTICAST MTU:1500 Metrica:1
        Packages RX:0 errors:0 lost:0 overruns:0 frame:0
        Packages TX:0  errors:0 Lost:0 overruns:0 carrier:0
        Colisions:0 long.colaTX:1000
        Bytes RX:0  (0.0 B)  TX bytes:0 (0.0 B)
lo      Link encap:Local Loop
        Direc. inet:127.0.0.1 Mask:255.0.0.0
        Direc. inet6: ::1/128 Reach (?)::Localhost
        ACTIVE LOOP FUNCTIONAL MTU:16436 Metrica:1
        PackagesRX:176 errors:0 lost:0 overruns:0 frame:0
        Packages TX:176 errors:0 lost:0 overruns:0 carrier:0
        Colissions:0 long.colaTX:0
        Bytes RX:13152 (13.1KB)  TX bytes:13152 (13.1 KB)
 iw follows. Thanks from Eduardo.

---

### Post by drdos2006 on 2011-02-04
It appears that you have an IPv6 network address, not an IPv4 network address.

This is from a previous thread I saved because it helped me.
My ISP had made some changes to the network and I had constant dropouts until I disconnected IPv6.

> 
You may be having connection issues because of IPv6 even though it shows an IPv4 connection. 

 How do I prove ipv6 has been successfully disabled
There seems to be much disagreement between distros regarding how ipv6 is disabled, even between different versions of the same distro. Rather than just follow instructions for disabling ipv6 for a given distro, I would like to also test that ipv6 is not used any more. Any software or executable that relies on ipv6, that I can use to confirm that ipv6 has been successfully disabled?

cat /proc/sys/net/ipv6/conf/*/disable_ipv6
They should all be 1.

Disabling IPV6 is best done via sysctl. In ubuntu, add the following to /etc/sysctl.conf

Code:

# Disable IPV6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
ifconfig should not mention an IPV6 address on any interface after you have rebooted.

IPV6 should still be considered in your security setup on your machine, just in case it is, for example, re-enabled after an upgrade etc.

To check if IPv6 is enabled, just simply use netstat:

Code:

netstat -tlv

If you see any "tcp6" entries, then IPv6 is not disabled.

You may be also having IPv6 problems in your browser.
For Firefox, type about:config in the browser bar.
Filter with network.dns
Change IPv6disabled to true
Restart Firefox.


regards

---

### Post by e.jejcic on 2011-02-04
iwconfig gives:

lo     no wireless extentions

eth0   no wireless extentions

wlan0  IEEE 802.11bg  ESSID:off/any
       Mode:Managed  Access Point: Not_associated  Tx-power=0 dBm
       Retry  long limit:7  RTS thr:off  Fragment thr:off
       Power Managment:off

I hope I copy all right. Thank's for the help. Any more information, please ask.Thank's again from Eduardo.

---

### Post by e.jejcic on 2011-02-04
O:K: everything allright, but I can't browse any command you sugest (using brwse bar o somethin like that). Thanks from Eduardo.Looks like somebody was tweaking with my Firefox.

---

### Post by e.jejcic on 2011-02-05
Please help. I'm stuck. Thank you from Eduardo.

---

### Post by drdos2006 on 2011-02-06
Can your desktop connect to the internet ?
Run ifconfig ( from your desktop )and post back here.
Can your laptop connect via ethernet cable ?
Run ifconfig ( from your laptop ) and post back here.
Can you wireless on the laptop connect to the internet ?
Run iwconfig and post back here.
regards

---

### Post by cheapodonuts on 2011-04-09
interesting thread. :)

---

### Post by AiXeLsyD13 on 2011-04-09
I have a similar problem...  Internet isn't lost, but the wireless is.  I've tried to d/l a few apps, like WiFi Radar... all to no avail.

I'm new to Ubuntu...  just want to get the wireless working, I installed Ubuntu on a Lenovo ThinkPad T500 that I just purchased used.

I'm assuming there's a wireless card in the laptop... not sure how to get Ubuntu to recognize it.  I'm very new to all of this.  Using the run prompt?  I haven't done much of that since Windows 3.1 or so...

I ran ifconfic & Iwconfig, this is what I get...

```
eric@Ubuntu-LTP-T500:~$ nm-applet
An instance of nm-applet is already running.

** (nm-applet:4329): WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager.

eric@Ubuntu-LTP-T500:~$ iconfig
No command 'iconfig' found, did you mean:
 Command 'fconfig' from package 'redboot-tools' (main)
 Command 'iwconfig' from package 'wireless-tools' (main)
 Command 'vconfig' from package 'vlan' (main)
 Command 'ifconfig' from package 'net-tools' (main)
 Command 'mconfig' from package 'mono-2.0-devel' (main)
iconfig: command not found
eric@Ubuntu-LTP-T500:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:7e:6b:be:23  
          inet addr:192.168.0.105  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::224:7eff:fe6b:be23/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30518 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18859 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:40093412 (40.0 MB)  TX bytes:1935144 (1.9 MB)
          Interrupt:20 Memory:fc000000-fc020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:252 errors:0 dropped:0 overruns:0 frame:0
          TX packets:252 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22544 (22.5 KB)  TX bytes:22544 (22.5 KB)

eric@Ubuntu-LTP-T500:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eric@Ubuntu-LTP-T500:~$ ^C
eric@Ubuntu-LTP-T500:~$ 
```

---

### Post by AiXeLsyD13 on 2011-04-09
I was looking at a wireless troubleshooting guide, and I wan "lshw -C network" and got this:

```
eric@Ubuntu-LTP-T500:~$ -C network
-C: command not found
eric@Ubuntu-LTP-T500:~$ lshw -C network
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: 82567LF Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:24:7e:6b:be:23
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=1.0.2-k4 firmware=1.8-3 ip=192.168.0.105 latency=0 multicast=yes
       resources: irq:44 memory:fc000000-fc01ffff memory:fc024000-fc024fff ioport:1820(size=32)
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:1e:65:25:3f:48
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.35-28-generic firmware=8.24.2.12 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:46 memory:f4300000-f4301fff
eric@Ubuntu-LTP-T500:~$ 
eric@Ubuntu-LTP-T500:~$ 

```

Any way to easily ENABLE the wireless card?  Ha ha.

---

