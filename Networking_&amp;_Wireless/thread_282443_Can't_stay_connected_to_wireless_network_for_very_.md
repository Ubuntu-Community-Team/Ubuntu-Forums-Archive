---
title: "Can't stay connected to wireless network for very long"
date: 2006-10-22
forum: Networking &amp; Wireless
---

### Post by chriscrutch on 2006-10-22
When I boot up my few-day-old Kubuntu install, my wireless internet works fine.  It automatically connects to my home network just fine.  But it will only stay that way for an hour or two.  Then, with no warning or error message, I will lose my connection to my network.  Opening up my wireless assistant at that point will fail to turn up any available wireless networks.  At all.  It doesn't matter if I try for four or five hours straight.  Once it goes down, it won't come back up.  But as soon as I reboot, everything is hunky-dory for an hour or two.  Once it goes down, running

```
ifup wlan0
```

returns an error, the text of which I cannot recall at the moment.

I'm a linux and Kubuntu noob, so please pardon me for anything stupid I may say.  What could be the trouble here?  Thanks for replying.

--chriscrutch

---

### Post by lloyd_b on 2006-10-22
You really need to post that error message.  You aren't providing enough information for the folks here to start diagnosing the problem.

Lloyd B.

---

### Post by cd-r80 on 2006-10-23
My usb-dong had dropped one tiny resistor. It worked sometimes and sometimes turned off.

---

### Post by chriscrutch on 2006-10-24
Call it "reverse Murphy's law".  The wireless network connection has now been up for 18 hours straight.  When I *want* my computer to break, it won't.  :-D 

Also, remember I mentioned that I'm a Linux noob?  The error message I was getting from ifup was because I wasn't running it as root.  Duh...

I'll bump this thread later if the behavior starts again.

--chriscrutch

---

### Post by chriscrutch on 2006-10-24
The problem occurred again this afternoon.  I was online one minute, I opened a webpage, and halfway through loading, I lost my wireless network.  My wireless network manager suddenly could not find any networks, despite the fact that, not 20 seconds earlier, it was picking up three of them.  iwconfig showed nothing out of the ordinary.  I ran (as root! :)  ) ifdown wlan0, and then ifup wlan0 with no change.  I have a wireless network applet in my panel, and it showed a "Link Quality" of 0%, while it normally shows 100%.  Once again, a quick reboot fixed the problem and I was again online.

Again, as a linux noob, I'm not sure what else to check on.  I'm looking to all of you for assistance.

Thanks very much.

--chriscrutch

---

### Post by swiftsam on 2006-10-24
It seems like I have the same problem as you, so perhaps we could get the threads merged, or at least I'll let you know if I find a solution.
here's the thread I started:
[http://ubuntuforums.org/showthread.php?t=283728](http://ubuntuforums.org/showthread.php?t=283728)

I was thinking it would be half the battle if I could just hit a command that would restart the wireless components to save the time of rebooting.

---

### Post by swiftsam on 2006-10-25
Hey chriscrutch,

try running 
```
sudo /etc/init.d/networking restart
``` 
from terminal and see if that gets you back online without having to reboot.  it seemed to work for me so far

---

### Post by chriscrutch on 2006-10-26
Thanks for that tip, but it didn't work for me, as I see it doesn't consistently work for you.

Anyone else have any thoughts on our plight?

--chriscrutch

---

### Post by swiftsam on 2006-10-26
yeah, the ```
/etc/init.d/networking restart
``` only worked once for me really, and I got excited and posted it.  It was just a fluke/coincidence though, it's never worked since.

It would be great if somebody had any kind of suggestion or road to go down and investigate.  Is there anything else we can provide?

---

### Post by lloyd_b on 2006-10-26
This is *really* weird.  I see two possibilities:

1.  Flaky hardware.  As was noted in a previous post, sometimes a piece of hardware will work fine, then quit.  Usually this is related to temperature - when a given transistor reaches a certain temp, it starts acting flaky.  But you say that a reboot fixes the problem (for another hour), so I wonder about this.

2.  A driver problem.  Maybe there's a bug in the device driver, where something overflows after a certain number of packets or something.

A question: is that machine set for dual-boot (Ubuntu/Windows, for example)?  If so, does the hardware in question work without fail from Win?  If so, then we can rule out hardware as the source of the problem.

Do you know what model of network card you're using?  If not, then could you post the output of the following two commands?
```

[B]sudo lspci
sudo lshw[/B]
```

This will let us ID the card. 

Also, could you post the kernel version that you're running?  It can be obtained with the following command:

```
**cat /proc/version**
```

Lloyd B.

---

### Post by chriscrutch on 2006-10-26
As for me, this is what I can say:

1) Although hardware trouble was my first thought as well, the very same adapter on the very same network plugged into the same USB port running in Windows (as it happens, I am running a dual-boot machine) will stay up for several days at a time.  In Kubuntu I haven't been able to stay on more than 27 hours at a time since the troubles began, most often it is much less time.

2) I am using a Belkin Wireless USB adapter, model # F5D7050, driver version 3.  It didn't work "out of the box" when I installed Kubuntu, so I'm using the included Windows drivers with ndiswrapper.

3) My kernel version is 2.6.15-27-386.

4) The only thing that I have come across so far that will fix the problem when it occurs is a reboot.  That, so far, has fixed it without fail, every time.  Next time it happens, I'm thinking about removing the drivers through ndiswrapper and then re-installing them, to see if that will get me back online.  Will that do any good, or would I need to reboot in the middle of that operation to really remove the drivers?

Thanks for thinking on this.

--chriscrutch

---

### Post by lloyd_b on 2006-10-26
> 4) The only thing that I have come across so far that will fix the problem when it occurs is a reboot. That, so far, has fixed it without fail, every time. Next time it happens, I'm thinking about removing the drivers through ndiswrapper and then re-installing them, to see if that will get me back online. Will that do any good, or would I need to reboot in the middle of that operation to really remove the drivers?

I'm no expert on the subject, but I've seen TONS of messages in the forums regarding problems with ndiswrapper and Belkin ethernet devices.  I'd say a driver problem is a very HIGH probability...

If removing/reinstalling the drivers doesn't make a difference, try unplugging from USB and then reconnecting.  If the driver puts the unit into a weird state, this will tend to re-initialize it.  

I don't know how ndiswrapper will respond to such a move, however.  Regular USB drivers are designed around hotplugging, where ndiswrapper might have a problem with it.

Lloyd B.

---

### Post by danohuiginn on 2006-11-05
Hi,

I've been having what seems like the same problem. It's only happened after upgrading to Edgy. Network connection will fail, and can't be brought up either by:

```

# ifdown ath0
# ifup ath0

```
or by

```
# /etc/init.d/networking restart

```
If I run either of the above commands, I'll get something like this (note the first two lines)

```
wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:11:f5:94:82:52
Sending on   LPF/ath0/00:11:f5:94:82:52
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```
However, on rebooting it works fine. I can dual boot, and have no wifi problems in Windows.

The problem seems to happen more often (but not exclusively) if I use Flash in Firefox (watching youtube, for example).

Here's some of the diagnostic output people asked for. I notice that I seem to have both a 'wifi0' and an 'ath0' - is that normal?

```
dan@laputa:~$ cat /proc/version
Linux version 2.6.17-10-386 (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 Fri Oct 13 18:41:40 UTC 2006 (Ubuntu 2.6.17-10.33-386)

```
```
root@laputa:~# lspci
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
09:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
09:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
09:04.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)


```
```
dan@laputa:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:11:F5:94:82:52  
          inet addr:192.168.0.132  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:f5ff:fe94:8252/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1035 errors:0 dropped:0 overruns:0 frame:0
          TX packets:982 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:972561 (949.7 KiB)  TX bytes:133252 (130.1 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6481 (6.3 KiB)  TX bytes:6481 (6.3 KiB)

wifi0     Link encap:UNSPEC  HWaddr 00-11-F5-94-82-52-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12458 errors:0 dropped:0 overruns:0 frame:4111
          TX packets:1035 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:2035106 (1.9 MiB)  TX bytes:165282 (161.4 KiB)
          Interrupt:209 Memory:dca40000-dca50000 

```
```
dan@laputa:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"iskola"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:15:E9:E4:76:FF   
          Bit Rate:36 Mb/s   Tx-Power:16 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=27/94  Signal level=-68 dBm  Noise level=-95 dBm
          Rx invalid nwid:6176  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


```

---

