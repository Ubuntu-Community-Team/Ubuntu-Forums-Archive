---
title: "Basic Networking Help"
date: 2006-08-29
forum: Networking &amp; Wireless
---

### Post by thornomad on 2006-08-29
Hi - I am a Ubuntu/Linux Newbie.  I have a wireless card that works fine at home.  However, this week, I am traveling and am having trouble establishing connections with this card to some wireless networks.  These networks work perfectly well in Windows.

I am not sure what steps to take to troubleshoot my wireless networking.  I have gone to my "Networking" options panel, selected the wlan0, checked properties, made sure the correct network was selected, but it isn't working (I should mention it was working for some time, now it is not).

On the windows side, I can connect to that network no problem.

Can anyone point in the diretion of basic network troubleshooting ?

Thanks,
Damon

---

### Post by funchords on 2006-08-30
Can you describe what happens/doesn't happen when you're having trouble connecting to a wireless network?

Do you have your linux wireless card configuration such that addresses are assigned via DHCP?

---

### Post by thornomad on 2006-08-30
Yea, I can describe as best I am able: thanks.

When I got to this location, opened Networking, hit properties for the wlan0 device (which was active).  Selected the new network from that little drop down list and cleared the WEP password field (no password needed).  I connected to the network, all was groovey.

Later: I could no longer open pages in Firefox, Giam wasn't working, etc.  I hadn't changed anything.  Went back to properties, looked around, wasn't sure what to do.  Took my laptop to another wireless network area, hooked it up to that network, did work.  Brought it back where I was staying.  Couldn't connect to the network there anymore.  Dual booted back to Windows -- could use the network. Ubuntu, no.

I haven't changed anything since it was working and then stopped -- not sure what to do.

Thanks,
Damon

---

### Post by dannyboy79 on 2006-08-30
This has happened to me also. I am using a netowrk card that has the AR5212 chipset. It's a Netgear WG511T I beleive, I know it something something 511T for sure but I forget what the first 2 characters are. It worked out of the box for Xubuntu on my laptop and all of a sudden it doesn't work and I haven't changed anything on my wireless network at home? Can anyone help me troubleshoot this? I am not trying to hi-jack your thread, I am merely stating that it sounds like we are having the same problem so if someone helps me I'll inform you what we did and hopefully vice-versa for you. If this is unacceptable with you and you don't want people answering me in your thread just post that and I'll open my own thread. Sorry if it's not ok.

---

### Post by funchords on 2006-08-30
> **thornomad said:**
> 
When I got to this location, opened Networking, hit properties for the wlan0 device (which was active).  Selected the new network from that little drop down list and cleared the WEP password field (no password needed).  I connected to the network, all was groovey.

Later: I could no longer open pages in Firefox, Giam wasn't working, etc.  I hadn't changed anything.  Went back to properties, looked around, wasn't sure what to do.  Took my laptop to another wireless network area, hooked it up to that network, did work.  Brought it back where I was staying.  Couldn't connect to the network there anymore.  Dual booted back to Windows -- could use the network. Ubuntu, no.

Hmmm. It's hard to know exactly where it's going south.

Next time this happens, please do an **ifconfig wlan0 && iwconfig wlan0** and copy/paste the results into a text file.  

Then do

**sudo ifdown wlan0**

wait about 15 seconds, then

**sudo ifup wlan0**

and let's see if that helps you get back online.  If it does, then repeat the **ifconfig wlan0 && iwconfig wlan0** step.  Perhaps, by comparing the outputs, we can figure out why this is happening for you and make adjustments to prevent it.

---

### Post by funchords on 2006-08-30
> **dannyboy79 said:**
> This has happened to me also. I am using a netowrk card that has the AR5212 chipset. It's a Netgear WG511T I beleive, I know it something something 511T for sure but I forget what the first 2 characters are. It worked out of the box for Xubuntu on my laptop and all of a sudden it doesn't work and I haven't changed anything on my wireless network at home?

thornomad has a working wireless card in linux that eventually disconnects from networks or he can't connect to certain networks that appear in a site survey.

The same tips I gave may help you.  But if they don't, and if your problem is different, then you should start your own thread.

---

### Post by thornomad on 2006-09-20
Hi sorry for the long delay in responding -- since the issue doesn't repeat itself in a consist fashion at home (at least that's something!) I haven't had a chance to test out your suggestions when it stops working.  Today that changed!.

Am at the medical school library today and had a chance to try a new wireless network -- the first time I set up the network I could connect without a problem (is an open network, no password, just had to specify the name).  Internet worked.  Then I moved to a new location in the library and found I could no longer get a connection.  I tried restarting, enabling and disabling the wlan0, and activating and deactivating.  Nothing work.  (All of this done from sys/admin/networking.)

However: on the Windows side of things, I am able to connect to the internet without a problem.  Hooks up easily, consistently, and without fail.  High powered signal.  So: went back here to the forum, got your suggestions, and tried them out.  

> **funchords said:**
> **ifconfig wlan0 && iwconfig wlan0** 

**sudo ifdown wlan0**

**sudo ifup wlan0**

Here are the results.

```
**$ ifconfig wlan0 && ifwconfig wlan0**

wlan0     Link encap:Ethernet  HWaddr 00:80:C8:CF:50:DF
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x4000

wlan0     IEEE 802.11b+  ESSID:"RLB"  Nickname:"acx v0.3.21"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:1 Mb/s   Tx-Power=18 dBm   Sensitivity=187/255
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality=84/100  Signal level=81/100  Noise level=1/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

I don't know much about this, but it says there is a link quality of 84/100 -- seems like something is there.

```
**$ sudo ifdown wlan0**
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/wlan0/00:80:c8:cf:50:df
Sending on   LPF/wlan0/00:80:c8:cf:50:df
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 172.20.8.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
wlanctl-ng: Operation not supported
```

I notice the wlanctl-ng is "not supported" ... 

```
**$ sudo ifup wlan0**
wlanctl-ng: Operation not supported
Failed to enable the device, exitcode= 1 .
run-parts: /etc/network/if-pre-up.d/linux-wlan-ng-pre-up exited with return code 1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/wlan0/00:80:c8:cf:50:df
Sending on   LPF/wlan0/00:80:c8:cf:50:df
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

Seems like something is not connecting (I notice in the GUI networking dialogue box it takes *forever* to close and set something ... as if it is stalling (like above).

```
**$ ifconfig wlan0 && iwconfig wlan0**
wlan0     Link encap:Ethernet  HWaddr 00:80:C8:CF:50:DF
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x4000

wlan0     IEEE 802.11b+  ESSID:"RLB"  Nickname:"acx v0.3.21"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:2 Mb/s   Tx-Power=18 dBm   Sensitivity=187/255
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality=90/100  Signal level=86/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Any thoughts ?  Will be here for a little while (on the WinXP side -- *shudders*).  Do you think I should [install the driver]("http://acx100.sourceforge.net/") (looks complicated, but recommended by D-Link)

THANKS!!  

Damon

---

### Post by tormod on 2006-10-13
The "wlanctl-ng: Operation not supported" comes from the linux-wlan-ng package, which is only used for some specific cards:

[https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb](https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb)

If you don't have any of these cards, you can uninstall the linux-wlan-ng package.

---

### Post by Roger Mudd on 2006-10-13
I'm not sure this will solve your issue, but I've had much better luck connecting to wireless networks using [WiFi Radar]("http://wifi-radar.systemimager.org/").
Another option is [Network Manager]("http://www.gnome.org/projects/NetworkManager/").
I think you can find both of these applications in the repositories.
The "stock" solution in Dapper would never retain connection settings.

---

### Post by thornomad on 2006-10-17
> **Roger Mudd said:**
> I'm not sure this will solve your issue, but I've had much better luck connecting to wireless networks using [WiFi Radar]("http://wifi-radar.systemimager.org/").
Another option is [Network Manager]("http://www.gnome.org/projects/NetworkManager/").

All right!  I will give those a try ... I am going back to the "Dead Zone" tomorrow (where WinXP works but Ubuntu fails) ... hopefully one of those two will help me out.

Thanks,
Damon

---

