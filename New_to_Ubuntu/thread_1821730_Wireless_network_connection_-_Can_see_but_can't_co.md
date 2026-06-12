---
title: "Wireless network connection - Can see but can't connect"
date: 2011-08-09
forum: New to Ubuntu
---

### Post by padougla on 2011-08-09
Hello - I'm just after a little advice on getting my Wireless working.  I have a HP NC6220 with the built in Wireless enabled and I'm running Ubuntu 11.04.  The wireless module is detected as 'ipw2200'.

I can see respective wireless networks but I can't get an IP address when it tries to connect.  It's set for DHCP, but even when I set it up manually, it is not reflected in 'ifconfig' or 'iwconfig'.  I can also see all the local networks with 'iwlist'.  I've tried with and without security settings, but the Wireless link just keeps disconnecting after failing to get an IP address.

I have also gone through the basic checks and made sure my user privilege permits Wireless access.

I've tried looking at the **log files** and checked other threads relating to this, so I've listed the output from several scripts as below, but still cant see where the issue is!

```
$ more /var/log/jockey.log | grep ipw2200
2011-08-09 17:36:12,154 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ipw2200', 'jockey_handler': 'KernelModuleHandler'}

$ tail /var/log/syslog
...
Aug  9 18:08:20 paul-lap wpa_supplicant[644]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
Aug  9 18:08:21 paul-lap wpa_supplicant[644]: Trying to associate with 00:14:78:ba:77:4a (SSID='BEAP-BEAP' freq=2417 MHz)
Aug  9 18:08:23 paul-lap wpa_supplicant[644]: CTRL-EVENT-DISCONNECTED bssid=00:14:78:ba:77:4a reason=0

And the respective interface (eth1) for this shows:
$ ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:16:6f:57:3a:36  
          inet6 addr: fe80::216:6fff:fe57:3a36/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:15120 (15.1 KB)
          Interrupt:21 Base address:0x8000 Memory:d0400000-d0400fff 

$ iwconfig eth1
eth1      IEEE 802.11bg  ESSID:"BEAP-BEAP"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:14:78:BA:77:4A   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

$ lsmod
...
ipw2200               145664  0 
...


$ dmesg | grep ipw2200
[   24.508595] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   24.508600] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   24.508728] ipw2200 0000:02:04.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   24.511645] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   24.916989] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)


$ sudo lshw -C network

  *-network
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: eth1
       version: 05
       serial: 00:16:6f:57:3a:36
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
       resources: irq:21 memory:d0400000-d0400fff

$ iwlist scan
...
eth1      Scan completed :
          Cell 01 - Address: 00:14:78:BA:77:4A
                    ESSID:"BEAP-BEAP"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.417 GHz (Channel 2)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=68/100  Signal level=-71 dBm  
                    Extra: Last beacon: 336ms ago
...
          Cell 03 - Address: 06:D0:44:B2:3E:72
                    ESSID:"BTOpenzone"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.472 GHz (Channel 13)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=65/100  Signal level=-61 dBm  
                    Extra: Last beacon: 28ms ago

Further log details:
$ cat /var/log/syslog | grep dhclient
...
Aug  9 18:56:23 paul-lap dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
Aug  9 18:56:34 paul-lap dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
Aug  9 18:56:44 paul-lap dhclient: No DHCPOFFERS received.
Aug  9 18:56:44 paul-lap dhclient: No working leases in persistent database - sleeping.

$ cat /var/log/syslog | grep eth1
...
Aug  9 18:54:59 paul-lap NetworkManager[522]: <info> (eth1): supplicant connection state:  associating -> disconnected
Aug  9 18:55:01 paul-lap NetworkManager[522]: <info> (eth1): supplicant connection state:  disconnected -> associating
Aug  9 18:55:02 paul-lap NetworkManager[522]: <info> (eth1): supplicant connection state:  associating -> disconnected
Aug  9 18:55:02 paul-lap NetworkManager[522]: <warn> Activation (eth1/wireless): association took too long.
Aug  9 18:55:02 paul-lap NetworkManager[522]: <info> (eth1): device state change: 5 -> 9 (reason 7)
Aug  9 18:55:02 paul-lap NetworkManager[522]: <warn> Activation (eth1) failed for access point (BEAP-BEAP)
Aug  9 18:55:02 paul-lap NetworkManager[522]: <warn> Activation (eth1) failed.
Aug  9 18:55:02 paul-lap NetworkManager[522]: <info> (eth1): device state change: 9 -> 3 (reason 0)
Aug  9 18:55:02 paul-lap NetworkManager[522]: <info> (eth1): deactivating device (reason: 0).
Aug  9 18:55:43 paul-lap dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3

$ cat /var/log/syslog | grep wireless
...
Aug  9 18:54:02 paul-lap NetworkManager[522]: <warn> Activation (eth1/wireless): asking for new secrets
Aug  9 18:54:02 paul-lap NetworkManager[522]: <info> Activation (eth1/wireless): connection 'Auto BEAP-BEAP' has security, and secrets exist.  No new secrets needed.
Aug  9 18:55:02 paul-lap NetworkManager[522]: <warn> Activation (eth1/wireless): association took too long.

$ cat /var/log/syslog | grep ipw2200
...
Aug  9 16:41:47 paul-lap kernel: [   24.508595] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
Aug  9 16:41:47 paul-lap kernel: [   24.508600] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Aug  9 16:41:47 paul-lap kernel: [   24.508728] ipw2200 0000:02:04.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Aug  9 16:41:47 paul-lap kernel: [   24.511645] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Aug  9 16:41:47 paul-lap kernel: [   24.916989] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
Aug  9 16:41:47 paul-lap NetworkManager[522]: <info> (eth1): new 802.11 WiFi device (driver: 'ipw2200' ifindex: 3)
```

I'd appreciate any help...

Kindest regards
Paul.

---

### Post by grahammechanical on 2011-08-09
Hi and welcome to the forums. Well done for trying to solve this yourself before asking for help. Compare your readouts from ifconfig and iwconfig with those from my system. Can you notice anything?


> ~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:15:af:0e:9b:e0  
**          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0**
          inet6 addr: fe80::215:afff:fe0e:9be0/64 Scope:Link
          UP BROADCAST **RUNNING** MULTICAST  MTU:1500  Metric:1
          RX packets:192 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33019 (33.0 KB)  TX bytes:4114 (4.1 KB)

~$ iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:"PlusnetWireless"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:26:44:21:E5:81   
          **Bit Rate=12 Mb/s**   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=66/70  **Signal level=-44 dBm**  
          Rx invalid nwid:0  Rx invalid crypt: 0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:11   Missed beacon:0


Ignore the fact that your wireless adapter is called eth1 and mine is called wlan0, notice the parts that I have highlighted in bold print. 

You are not connected to the router, otherwise the second line of ifconfig would be similar to my second line. This information is collected by Network manager from the router. A working connection to the router would have the word RUNNING in the fourth line.

Now look at the readout from iwconfig. Compare my signal level with your signal level. Is the router switched on? We assume that the wireless adapter in the computer is working because iwlist scan detects wireless networks. Which of the two ESSIDs is your router? Is it BEAP-BEAP or is it BTOpenzone? Or is it neither?

I am guessing it is BEAP-BEAP iwlist scan gives it a signal level of 71DBm but iwconfig says signal level:0. I am guessing that your are not using the correct pass phrase or wireless key or you have network manager set to the wrong encryption method. iwlist scan says encryption key: on.

Try editing the connection and making sure that the encryption method is set to WPA & WPA Personal or whatever method the router is using. The setting in network manager must be the same as the setting in the router. Otherwise the two devices do not speak the same language. If encryption is on in the router then you must set the encryption type in Network Manager.

I bet that you do not have any difficult connecting to BTOpenzone. Encryption is off on that router.

Regards.

---

### Post by padougla on 2011-08-11
Thank you for your reply. I did try each of those before posting this.  The BEAP-BEAP WEP key is copied directly from my wireless router (via the Ethernet) and has matched settings.  The BTOpenzone and BTFON also fail to provide me with an IP address.

Each of these works fine with other equipment and the same settings.

I've since completely re-installed Ubuntu 11.04 - but still have exactly the same issue.  I also tried using the wrapper for Microsoft drivers and while this changed the interface from 'eth1' to 'wlan0', I still find I can see the networks, but I can never connect successfully!

Currently back to square one, clean build, same issue.

I have tried in the past with other versions of Ubuntu  and always find it's the Wireless I can never get working!

Thank you for your speedy reply, but still now luck.

---

### Post by zinglax on 2011-08-12
Hey I have the exact same problem.  I would type in the wireless password and then awhile later it would prompt me for it again. I ended up taking it to a wireless signal down the street with no password and it linked up fine.  It was quite annoying, I switched back from 10.04 and 11.04 like 3 times. I'm still in the process of getting my home network to work with it but I agree with grahammechanical. Its probably the wireless router configuration. Try turning of the security and see if you can connect then.  That's my next step to get it working at home.  

Ill let you know if it works.

---

### Post by gandaran on 2011-08-12
> **zinglax said:**
> Hey I have the exact same problem.  I would type in the wireless password and then awhile later it would prompt me for it again. I ended up taking it to a wireless signal down the street with no password and it linked up fine.  It was quite annoying, I switched back from 10.04 and 11.04 like 3 times. I'm still in the process of getting my home network to work with it but I agree with grahammechanical. Its probably the wireless router configuration. Try turning of the security and see if you can connect then.  That's my next step to get it working at home.  

Ill let you know if it works.
check router configuration if DHCP server is enabled, if router doesn't have DCHP server then try a static IP setting on Ubuntu.

---

### Post by padougla on 2011-08-13
SORTED:D
Sorted my problem in the end. I believe it was a hardware issue with the internal wireless (I tried it with several OS's and all of them suffered from the same problems).  I've disabled the card and added a tiny USB one.  Works a treat now on that!

Sometimes it's the simple solutions that work best.  Thank you "grahammechanical" for your advice, but I had tried those, so I'm convinced it's the hardware.

"zinglax" - Mine didn't work originally even with the security off, so I think the problem is not the same. However, in looking at my problem I did try loading Ubuntu on another Laptop and found that even with the right credentials, that one failed (worked with no security OK) until removed the credentials and set it manually (not commend line, still in the GUI - just creating it as though it was a hidden network).  Worked fine then.

:popcorn:
Thank you everyone.

---

### Post by zinglax on 2011-08-13
That's good you narrowed it down. Yeah mine worked fine out of the box and then one day it just wouldn't connect. 

Good luck with the internal wireless if you decide to get that working. 

Cheers

---

### Post by anewguy on 2011-08-13
If yours did "work fine of the box, and then one day it just wouldn't connect", you probably had an update which updated the kernel.  There appear to be problems some users are having with wireless working until a kernel update.  Almost all that I have seen so far go back to the previous kernel.

If you get to the grub menu, see if there is an entry for an older kernel and try it.

---

### Post by zinglax on 2011-08-14
I actually figured out in another thread that it had to do with the security of the wifi, so I was able to get it working on free wireless. I'm still having graphics card problems though.

---

### Post by GMachine_24 on 2011-08-14
Hi - I have had similar problems recently with a Lenovo notebook. I can connect fine on my home network but at a public wifi spot - even though the network is recognized, I cannot get the notebook to connect. Unfortunately this is actually with Debian 6 - and I think there is only one kernel listed when I boot the computer so I will need to see how that goes.

It's a dual boot and, oddly, I can't connect via Windows 7, either - which always used to work. I went to the Lenovo Web site last night and download a bunch of updates and updated my Windows 7 so I'll see how that goes next time. [I'm not sure why I'm telling you about Windows except in the interest of full disclosure.]

Usually, as you probably know, hardware works but there is some problem with the software.

I have many computers at home connected to this network via cable and wireless and since there are like 10 other wireless networks that my wireless comps can "see" sometimes I just unplug my modem, router and switch and just start over again. This is annoying - but it has always worked, eventually.

 good luck - hope you enjoy ubuntu

---

