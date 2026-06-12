---
title: "driver installed, but no ip..."
date: 2006-11-01
forum: Networking &amp; Wireless
---

### Post by velozoom on 2006-11-01
First, I've been using Linux for all of about 5 days, so please bear with my noobness.  ;) 

I have an HP dv9000 laptop running Edgy.  I used FWCutter to build NIC drivers for the onboard Broadcom BCM4310 UART wireless NIC.  The drivers installed and after reboot the wnic (eth1) showed in the network config tools.  

To my very inexperienced eyes, everything looks good and as if it should be working.  However I can't get the nic to grab an ip.  I am 100% sure that my network settings are correct with the proper SSID and WEP key.  

Here is the output of ifconfig -a for my two nics.  
```

eth0      Link encap:Ethernet  HWaddr 00:16:36:9E:BD:5C  
          inet addr:10.10.10.102  Bcast:10.10.10.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe9e:bd5c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5956 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5028 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4669144 (4.4 MiB)  TX bytes:959977 (937.4 KiB)
          Interrupt:10 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:14:A5:E7:5F:F2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:6370 (6.2 KiB)
          Interrupt:255 Base address:0x8000 

```  

The simple fact is I am too new to Linux to know where to look next.  Any ideas where I should start poking around?  Thanks...

---

### Post by balloniw on 2006-11-02
I am relatively new too, but I think I can give you a few next steps.

Try the command iwconfig. This wireless-tools command will dump the wireless configuration for your wireless interfaces when invoked with no arguments. Confirm that the ESSID, encryption key, auth mode, etc. are all correct. If not, go back to the configuration and make changes. You can also make the changes manually with the iwconfig, for example: "iwconfig eth1 essid <net-name>" where <net-name> is the name of your wireless network.

Once iwconfig output seems correct configuration wise, confirm that the wireless interface is associated with an access point. Look for something like "Access Point: XXXXXXXXXX" in the iwconfig output. Make sure it doesn't say Invalid or something else obviously bad. Also, make sure you have numbers for link quality and signal level (besides 0).

If this looks good, issue the command "iwlist eth1 scan". This command should list the access points in your area. If you see nothing, something is definitely wrong.

Good luck.

Bill

---

### Post by kellere on 2006-11-04
velozoom,

wireless on the dv9000 is a piece of cake.

1.  download ndiswrapper.
2.  compile it ( make; sudo make install )
3.  install the windows driver ( bcmwl5.inf )
    which is found in your windows C:\SWsetup
    ie  ndiswrapper -i bcmwl5.inf
4. blacklist the kernel driver by adding
   "blacklist bcm43xx" to /etc/modprobe.d/blacklist
5. add "ndiswrapper" to your /etc/modules file
6. reboot

You should see the wireless card in gnomes
network interface:  System -> Admin -> networking

-John

---

