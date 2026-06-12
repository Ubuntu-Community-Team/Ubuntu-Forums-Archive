---
title: "A little help with wireless needed please"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by Schiaparelli on 2010-02-04
Hi all

I managed to finally get my wireless card to connect- it's a wg111t netgear usb dongle. I have an interesting issue:

when I reboot the network (wlan0) goes away. If I boot without the dongle in, then stick it back in, I get wlan0 back and it connects - although since rebooting I haven't been able to browse the net. Even though it's telling me it's connected, my router (unlike before) is showing no connection. When I plug the wired connection in it shows up - in fact when I plugged the wired in while the wireless was theoretically connected BOTH showed up - can only browse via the eth0 though...


Can anyone tell me what I should type in the terminal window to troubleshoot?

thanks in advance...

---

### Post by superprash2003 on 2010-02-04
well just to make sure that your connected to the network and that you have a successful connection please post output of **ifconfig** and **iwconfig** from the terminal

---

### Post by Schiaparelli on 2010-02-06
Hi superprash2003, here we go...

```

gavin@gavin-runningpc:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:4D:FE:A3:D2   
          Bit Rate=54 Mb/s   
          Power Management:off
          Link Quality:96/100  Signal level:-34 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

gavin@gavin-runningpc:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0d:61:53:a0:96  
          inet6 addr: fe80::20d:61ff:fe53:a096/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3062 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:185666 (185.6 KB)  TX bytes:6077 (6.0 KB)
          Interrupt:23 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3040 (3.0 KB)  TX bytes:3040 (3.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:18:4d:d4:fc:0f  
          inet addr:192.168.5.81  Bcast:192.168.5.255  Mask:255.255.255.0
          inet6 addr: fe80::218:4dff:fed4:fc0f/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:639 errors:0 dropped:0 overruns:0 frame:0
          TX packets:727 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:84351 (84.3 KB)  TX bytes:80095 (80.0 KB)


```If I connect via eth0 it connects and my router picks it up... If I first boot up and connect via wlan0 it connects and my router doesn't pick it up (and no internet). If I first connect via eth0 THEN connect via wlan0 it doesnt connect at all... a bit like mastermind this! my router is using WPA PSK and no DHCP. so I decide on an IP to allow and give the linux machine that IP. It also checks Mac address. The eth0 connects via the machine's MAC address, and the wireless connection via the wireless card's MAC address - is this correct?

Also, sometimes (like now) it says under iwconfig that no access point is associated??

---

### Post by superprash2003 on 2010-02-09
yes , it is via MAC address. but your outputs show no sign of it connecting to any wifi network. could you post output of **sudo iwlist scanning** from the terminal

---

### Post by Neural Nut@work on 2010-02-09
So as I understand the problem is that on Reboot it doesnt seem to remember right?!

You say the word **finally**; like you had to use an NDIS Wrapper or something. :D

If so, please be sure to ```
sudo vi /etc/modules
``` and add either **ndiswrapper **or whatever speical module u used to load the driver (would be evident from your steps).

And reboot and try it out...

---

