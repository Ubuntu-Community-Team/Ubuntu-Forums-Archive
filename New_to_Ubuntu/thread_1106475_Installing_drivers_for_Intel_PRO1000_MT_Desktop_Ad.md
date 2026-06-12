---
title: "Installing drivers for Intel PRO/1000 MT Desktop Adaptor"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by anon642 on 2009-03-25
I have a Westell Wirespeed DSL modem connected to a Intel PRO/1000 MT Desktop Adaptor (ethernet, and I don't have a router).  I just did a fresh install of Ubuntu but I can't connect to the internet.  Which is expected as this setup does the same thing in Windows XP until I install the drivers and then it automatically connects to the internet.  I spent the last day or so reading these forums for a similiar problem trying to get on the internet without the drivers and tried this method:

[http://ubuntuforums.org/showthread.php?t=762333&page=2](http://ubuntuforums.org/showthread.php?t=762333&page=2)
[http://ubuntuforums.org/archive/index.php/t-214734.html](http://ubuntuforums.org/archive/index.php/t-214734.html)

Which didn't seem to help though I may have made a mistake somewhere in doing that. At this point I've decided to try and update the drivers for my network card which I downloaded from:

[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&ProductID=983&DwnldID=9180&strOSs=39&OSFullName=Linux*&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&ProductID=983&DwnldID=9180&strOSs=39&OSFullName=Linux*&lang=eng) 

To make sure that was the right driver I also compared my info from doing **lshw -c network**

```
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: d
       bus info: pci@0000:02:0d.0
       logical name: eth0
       version: 02
       serial: 00:06:e9:08:d5:b7
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k3-NAPI firmware=N/A 

latency=64 mingnt=255 module=e1000 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: d1:fe:cb:a5:89:08
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A 

multicast=yes
```The DISABLED network in the above is my onboard connection which I disabled in the BIOS long ago. Just for fun I enabled that to see if it would work and it had the same problem.

Next I downloaded the linux drivers in  windows burned them on a CD and then booted up Ubuntu and unpacked it and did **gksu make install** and then it went to work installing to somewhere but it didnt update my driver version when I double checked **lshw -c network** again.  And still no internet access...

Also I've seen in other posts people ask for **sudo dhclient eth0**

Which says:
```
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

If anyone can help me get my drivers updated I would much appreciate it OR if you have any other suggestions for getting Ubuntu connected to the internet. :)

-Anonymous

---

### Post by cariboo on 2009-03-25
Pan0 is not your network aadapter eth0 just like in Windows is your network adapter. It looks like you aren't getting an ip address as the driver for your network card is already installed. In a terminal type:

```
sudo dhclient eth0
```

to see if you get an ipaddress. If you can't connect. do you need PPPoE in windows to connect?

If you need PPPoE to connect in a terminal type:

```
sudo pppoeconf
```

and enter the same details as in Windows.

Edit: I reread your post ignore the part about dhclient

Jim

---

### Post by CRCarl on 2009-03-25
If your machine is sending DHCPDISCOVERs then your interface is working. Not a problem installing the Intel drivers (other than it taints your install) but support for the MT series is in the kernel. 

Couple of things to check - 

1. Do you have any green lights (link) on the MT card?
2. Are you sure eth0 is connected to the DSL modem?
3. Is there a link light on the DSL modem?
4. Have you replaced the cable?
5. Do you know, do you get DHCP from the modem or from your DSL provider? If the later are you sure the cable modem is connected to your provider?

---

### Post by anon642 on 2009-03-25
Cariboo907,  When I **pppoeconf** the scan will timeout and it gives me a message: [color=blue]"... Access concentrator of your provider did not respond. Please check your network and modem cables.  Another reason for the scan failure may also be another running pppoe process which controls the modem."[/color]

---

### Post by anon642 on 2009-03-27
I found the problem and got on the internet. This post is for anyone who has a Westell Wirespeed DSL modem and is having this problem.  I don't know the technical reasons for this but it is finicky about being plugged into multiple computers/networks or switching from one OS to another.  I noticed that if it was working fine in Windows it wouldn't connect to the internet in Ubuntu.  And when it was working fine in Ubuntu and I tried to switch to Windows it wouldn't connect to the internet in Windows.  So basically, when I want to switch OSes I need to unplug the Westelll Wirespeed DSL modem for an hour or two before trying it in another computer or OS. :confused: 

But the good thing is. I'm on the internet and everything is working fine... for now.

---

