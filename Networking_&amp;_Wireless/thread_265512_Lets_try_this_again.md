---
title: "Lets try this again"
date: 2006-09-26
forum: Networking &amp; Wireless
---

### Post by bollocks00 on 2006-09-26
I have tried and failed previously to get wireless running on my laptop.  Now I have a little time on my hands so I'm going to try again with a clean install of Ubuntu 6.06.  Please do not direct me to a tutorial, as I can assure you I have tried them all.  What I'm hoping for is someone who knows what they are doing to tell me EXACTLY what to do each step of the way.  I'd be willing to wager $20 that even the slickest linux guru can't get wireless running on this thing ;).

Hardware:
IBM Thinkpad Z60t w/ Atheros AR5212 wlan chipset
Netgear WGT624 Super G Wireless Router

I have downloaded nothing extra (virgin box?) except wireless assistant, which will not run, giving "no usable wireless device found".  Here are some outputs for your viewing pleasure:

ifconfig:
```

lenny@IBM:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:F5:A1:83
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fef5:a183/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:421 errors:0 dropped:0 overruns:0 frame:0
          TX packets:361 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:481761 (470.4 KiB)  TX bytes:74899 (73.1 KiB)
          Interrupt:201

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:672 (672.0 b)  TX bytes:672 (672.0 b)

```

iwconfig:
```

lenny@IBM:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

sit0      no wireless extensions.

```

dmesg | less:
```

...
[17179586.240000] ath_hal: module license 'Proprietary' taints kernel.
[17179586.240000] ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
...
[17179586.396000] wlan: 0.8.6.0 (EXPERIMENTAL)
[17179586.428000] ath_rate_sample: 1.2
[17179586.432000] ath_pci: 0.9.6.0 (EXPERIMENTAL)
...
[17179587.092000] ath_attach: unable to attach hardware: 'Hardware didn't respond as expected' (HAL status 3)

```

It is probably useful to note that the green WLAN light never comes on in linux.  I'm thinking maybe the card is having trouble initializing for whatever reason, but I could be wrong.  It seems to me that the WLAN light would not depend on the OS, and everybody likes to tell me how my chipset is supported by drivers in Dapper Drake so I should have no problems.

Do your worst!

---

### Post by wieman01 on 2006-09-26
Ok, let's get going, buddy. Just a few questions up front...

1. Have you tried "ndiswrapper"?
2. Have you got the Windows driver for the wireless chipset?

I'd say we ditch the native Linux drivers if you're saying you cannot get it hooked up. I believe you there, every computer is different. So I'd like to use "ndiswrapper" instead if you can find the drivers. Ready for it?

---

### Post by wieman01 on 2006-09-26
I checked it out on the web... Your chipset is definitely no problem with "ndiswrapper". That said, simply tell me if you're ready to try.

Just FYI: I am using "ndiswrapper" for my wusb54g v4, so I am familiar with it... somehow.

---

### Post by tturrisi on 2006-09-26
atheros chipsets don't need ndiswrapper, they use the linux madwifi driver.  Do this:

1. run Synaptic. (System > Administration > Networking)
2. Settings Menu > Repositories
3. put a check next to all of them & OK out of the dialog.
4. press the Reload button on the toolbar.
5. install the linux-restricted-modules that match your kernel.  example: If have kernel 2.6.15.7-386 then install linux-restricted-modules-2.6.15.7-386.  (the restricted-modules include the madwifi drivers)
6. reboot.

The wlan adapter should now be detected.  If check /var/log/dmesg there will be aq section near end that says something like this:
```
ath_hal: module license 'Proprietary' taints kernel.
ath_hal: 0.9.17.2 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
wlan: 0.8.4.2 (svn r)
ath_rate_sample: 1.2 (svn r)
ath_pci: 0.9.4.5 (svn r)
PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 169
wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
wifi0: H/W encryption support: WEP AES AES_CCM TKIP
wifi0: mac 7.8 phy 4.5 radio 5.6
wifi0: Use hw queue 1 for WME_AC_BE traffic
wifi0: Use hw queue 0 for WME_AC_BK traffic
wifi0: Use hw queue 2 for WME_AC_VI traffic
wifi0: Use hw queue 3 for WME_AC_VO traffic
wifi0: Use hw queue 8 for CAB traffic
wifi0: Use hw queue 9 for beacons
```

6. go to System > Administration > Networking
7. the wifi device should be listed, config it & activate it.

Is the wlan adapter onboard or a pcmcia card? If onboard then the problem is likely a problem of the laptop itself and not Ubuntu.  I have never had any trouble getting atheros cards to work, in fact, they have been the easiest to get working.

---

### Post by wieman01 on 2006-09-26
> **tturrisi said:**
> atheros chipsets don't need ndiswrapper, they use the linux madwifi driver.
I know. But since he mentioned that he has tried every to get his card working it's worth a shot. 

Anyway, try tturrisi's solution first, if it does not work out for you we can try "ndiswrapper". I am always in favor of native Linux drivers (well, not always to be precise but most of the time).

---

### Post by bollocks00 on 2006-09-26
tturrisi:
I tried going through the steps you laid out.  I already had the linux-restricted modules installed for my kernel, but I went ahead and reinstalled them anyway.  The sytem still does not recognize my wlan chip, and the /var/log/dmesg file makes no mention of wifi0.  The chip is onboard, but everything works fine in windows, so it must be a problem with ubuntu.  Any other thoughts?

wieman:
I haven't tried ndiswrapper, but I guess I have something against using linux to run a windows driver at some amount of inefficiency.  If I'm running windows components, what's the point in using linux?  Anyhow, just a thought.  I may ultimately end up trying ndiswrapper just to see if that fixes the problem, but I'm going to exhaust the madwifi route first.


Thanks for the help, keep it coming!

---

### Post by wieman01 on 2006-09-26
Ok, go ahead with Linux drivers first & see how it goes. I have got one machine running "ndiswrapper" and the performance is great. So far I have not had problems with it. Let me know if you want to try it out yourself. Good luck.

---

### Post by sharkcohen on 2006-09-27
Have you previously tried installing the latest madwifi-ng driver from CVS?  If not, we can walk you through it.

---

### Post by bollocks00 on 2006-09-27
> **sharkcohen said:**
> Have you previously tried installing the latest madwifi-ng driver from CVS?  If not, we can walk you through it.

I believe so.

I have been fiddling with it some more and now I get

iwconfig:
```
lenny@IBM:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"SharonGreen"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:09:5B:51:0C:66
          Bit Rate:36 Mb/s   Tx-Power:8 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=4/94  Signal level=-91 dBm  Noise level=-95 dBm
          Rx invalid nwid:9415  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

irda0     no wireless extensions.

sit0      no wireless extensions.

```

ifconfig:
```

lenny@IBM:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:14:A4:60:FA:46
          inet6 addr: fe80::214:a4ff:fe60:fa46/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:42 (42.0 b)  TX bytes:342 (342.0 b)

eth0      Link encap:Ethernet  HWaddr 00:C0:9F:F5:A1:83
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fef5:a183/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2016 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1467 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2612043 (2.4 MiB)  TX bytes:165731 (161.8 KiB)
          Interrupt:201

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:908 (908.0 b)  TX bytes:908 (908.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-14-A4-60-FA-46-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27953 errors:0 dropped:0 overruns:0 frame:89918
          TX packets:1530 errors:12 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199
          RX bytes:2449815 (2.3 MiB)  TX bytes:69999 (68.3 KiB)
          Interrupt:74 Memory:f8c40000-f8c50000

```

Which certainly seems promising, but I still can't connect to the router.  At this point I know it is possible to use the card, since it recognizes all of the available networks in wireless assistant.  When I try to open wireless assistant, however, I get 
"You might have insufficient priviledges... Did you open it using sudo?"
Does anyone know the gksudo term used to run wireless assistant?

---

### Post by wieman01 on 2006-09-27
Man, you're connected. A few question the may help you:

1. Have you got a firewall (e.g. Firestarter)? Turn it off.
2. Have you got MAC filtering enabled? Disable it.
3. Can you ping your router? Try ping...
4. Does your card run on the same Bit Rate as the router? Make sure it's the same.

The link quality is really poor. So perhaps this has something to do with the router's settings.

---

### Post by sharkcohen on 2006-09-27
I would recommend not using the GUI wireless tools.  In my opinion, they're trash.  We can get this set up from the command line.  Let's start with what you can see.  Please post the name of your SSID and the output of

iwlist ath0 scan

---

### Post by wieman01 on 2006-09-27
SharkCohen, look at his previous post. He seems to be connected. His wireless card has associated.

---

### Post by bollocks00 on 2006-09-27
I live in an apartment so I have plenty of options for connecting.  The router I want is G22 (note the signal level is good for it).  I think I am all set if I can just get into wireless assistant with admin priviledges.  How can I launch it with sudo?

```

lenny@IBM:~$ iwlist ath0 scan
ath0      Scan completed :
          Cell 01 - Address: 00:0D:72:B8:5B:49
                    ESSID:"2WIRE802"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=44/94  Signal level=-51 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:16:B6:F2:A1:47
                    ESSID:"linksys1"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=20/94  Signal level=-75 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 03 - Address: 00:0D:0B:AE:D6:4B
                    ESSID:"hogehoge"
                    Mode:Master
                    Frequency:2.417 GHz (Channel 2)
                    Quality=14/94  Signal level=-81 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 04 - Address: 00:17:31:21:CA:6B
                    ESSID:"hitoshikawano"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=8/94  Signal level=-87 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 05 - Address: 00:14:6C:FA:32:B0
                    ESSID:"G22"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=62/94  Signal level=-33 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra:wme_ie=dd180050f2020101000003a4000027a4000042435e0062322 f00
                    Extra:ath_ie=dd0900037f0101000eff7f

```

---

### Post by sharkcohen on 2006-09-27
Associated with the access point's MAC, but no IP address on ath0.  He'll definitely be able to ping the router because eth0 has an IP address.

I'd definitely like to know if any of the security features on the router have been enabled.  Any encryption or MAC filtering should be disabled at this time for troubleshooting.

---

### Post by sharkcohen on 2006-09-27
> **bollocks00 said:**
> I live in an apartment so I have plenty of options for connecting.  The router I want is G22 (note the signal level is good for it).  I think I am all set if I can just get into wireless assistant with admin priviledges.  How can I launch it with sudo?

Heheheh, you're trying to connect to an open access point of other people's networks in your apartment complex, right?  You'll need to find one that says 'encryption key: off'.

---

### Post by bollocks00 on 2006-09-27
> **wieman01 said:**
> Man, you're connected. A few question the may help you:

1. Have you got a firewall (e.g. Firestarter)? Turn it off.
2. Have you got MAC filtering enabled? Disable it.
3. Can you ping your router? Try ping...
4. Does your card run on the same Bit Rate as the router? Make sure it's the same.

The link quality is really poor. So perhaps this has something to do with the router's settings.

1. No firewalls setup
2. I just disabled it, no change
3. How do I ping my router?
4. How do I check this?

---

### Post by bollocks00 on 2006-09-27
> **sharkcohen said:**
> Heheheh, you're trying to connect to an open access point of other people's networks in your apartment.  You'll need to find one that says 'encryption key: off'.

I do like using other people as troubleshooting guinea pigs 8) , but I'm disabling encryption for my router until I get this setup.

---

### Post by sharkcohen on 2006-09-27
Is 'G22' your's?  It says it has WPA enabled.  If that's your's, you'll need to disable WPA until we get the basics working.

---

### Post by bollocks00 on 2006-09-27
Roger dodger.  I have disabled it since that post.

---

### Post by wieman01 on 2006-09-27
This you do to restart your network:
> sudo /etc/init.d/networking restart
Post the output please.

Then check:
> route
Also show us the output.

---

### Post by bollocks00 on 2006-09-27
```

lenny@IBM:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:c0:9f:f5:a1:83
Sending on   LPF/eth0/00:c0:9f:f5:a1:83
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:14:a4:60:fa:46
Sending on   LPF/ath0/00:14:a4:60:fa:46
Sending on   Socket/fallback
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:c0:9f:f5:a1:83
Sending on   LPF/eth0/00:c0:9f:f5:a1:83
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
ip length 314 disagrees with bytes received 534.
accepting packet with data after udp payload.
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
ip length 314 disagrees with bytes received 534.
accepting packet with data after udp payload.
DHCPACK from 192.168.1.1
bound to 192.168.1.2 -- renewal in 34582 seconds.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

wifi0: unknown hardware address type 801
SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
wifi0: unknown hardware address type 801
Bind socket to interface: No such device
Failed to bring up eth1.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

wifi0: unknown hardware address type 801
SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
wifi0: unknown hardware address type 801
Bind socket to interface: No such device
Failed to bring up eth2.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:14:a4:60:fa:46
Sending on   LPF/ath0/00:14:a4:60:fa:46
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
ip length 314 disagrees with bytes received 534.
accepting packet with data after udp payload.
DHCPOFFER from 192.168.1.1
DHCPREQUEST on ath0 to 255.255.255.255 port 67
ip length 314 disagrees with bytes received 534.
accepting packet with data after udp payload.
DHCPACK from 192.168.1.1
bound to 192.168.1.3 -- renewal in 33862 seconds.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

wifi0: unknown hardware address type 801
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
wifi0: unknown hardware address type 801
Bind socket to interface: No such device
Failed to bring up wlan0.
              
                                                           [ ok ]

```


```

lenny@IBM:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
192.168.1.0     *               255.255.255.0   U     0      0        0 ath0
default         192.168.1.1     0.0.0.0         UG    0      0        0 ath0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```

---

### Post by wieman01 on 2006-09-27
The try pinging your router:
> ping 192.168.1.1
And post the output.

Then last but not least show us your interfaces file:
> gedit /etc/network/interfaces
Then I am sure we're through. WPA will be a different story though.

---

### Post by bollocks00 on 2006-09-27
ping works fine when wired connection is present, gives "connect: network is unreachable" when wired connection is removed.

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

################
pre-up wpa_supplicant -Bw -Dwext -ieth0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant

```

So everything is dynamic.  The last part is there in an attempt (a futile one) to get it working with WPA.  I can comment it out if need be.

---

### Post by bollocks00 on 2006-09-27
I tried it again after rebooting with the WPA part commented out, there was no change.

---

### Post by wieman01 on 2006-09-27
The ping does not work when your have pulled the plug? That means wireless is still useless. Update your interfaces file so that it looks like this (make a safety copy of the old one):
> sudo gedit /etc/network/interfaces
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto ath0
iface ath0 inet dhcp
[COLOR="Red"]wireless-essid G22[/COLOR]

Then restart the network (still unplugged please):
> sudo /etc/init.d/networking restart

---

### Post by bollocks00 on 2006-09-27
```

lenny@IBM:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:c0:9f:f5:a1:83
Sending on   LPF/eth0/00:c0:9f:f5:a1:83
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:14:a4:60:fa:46
Sending on   LPF/ath0/00:14:a4:60:fa:46
Sending on   Socket/fallback
DHCPRELEASE on ath0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:c0:9f:f5:a1:83
Sending on   LPF/eth0/00:c0:9f:f5:a1:83
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:14:a4:60:fa:46
Sending on   LPF/ath0/00:14:a4:60:fa:46
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
ip length 314 disagrees with bytes received 534.
accepting packet with data after udp payload.
DHCPOFFER from 192.168.1.1
DHCPREQUEST on ath0 to 255.255.255.255 port 67
ip length 314 disagrees with bytes received 534.
accepting packet with data after udp payload.
DHCPACK from 192.168.1.1
bound to 192.168.1.3 -- renewal in 38665 seconds.
                                                                         [ ok ]

```

---

### Post by wieman01 on 2006-09-27
You have not installed Wifi-Radar or anything like that?

---

### Post by bollocks00 on 2006-09-27
I have installed wireless assistant.  Should I install wifi radar?

---

### Post by wieman01 on 2006-09-27
No, I would uninstall the "wireless assistant". It seems to interfere with our stuff. Just remove it and restart the network after changing the interfaces file.

I'll have to continue later tonight.

---

### Post by bollocks00 on 2006-09-27
Good call wieman!  I just removed wireless assistant and now I'm submitting this via wifi.

Some assistant it is...

Now I just have to get WPA up and running.;)

---

### Post by wieman01 on 2006-09-27
Man, let's embark on WPA later tonight. We'll get through this one as well. :-)

Talk to you later.

---

### Post by bollocks00 on 2006-09-27
I'm going to reward myself with some sleep.  If you have any thoughts on how to start the WPA process I'd love to hear them.  I'm no good with the command line stuff and it seems like a lot of the applets in ubuntu are wishy-washy.  Hopefully this way I can understand a little better what is going on too.

Thanks for all the help!

---

### Post by wieman01 on 2006-09-27
Ok, have sweet (Ubuntu) dreams. :-)

Good news is that I know a solution for both WPA(1) and WPA(2)... We can start using this thread:

[http://www.ubuntuforums.org/showthread.php?t=225290&page=11&highlight=wpa2+rsn]("http://www.ubuntuforums.org/showthread.php?t=225290&page=11&highlight=wpa2+rsn")

But don't worry, I will guide you through it.

---

### Post by wieman01 on 2006-09-27
Tell you what... I'll go straight ahead with WPA(1) with TKIP. If this works out, we continue trying to get WPA(2) with AES working which is way more secure than anything else.

1. Open the "interfaces" file:
> sudo gedit /etc/network/interfaces
2. Paste this:
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto ath0
iface ath0 inet dhcp
wpa-driver madwifi
wpa-conf managed
[COLOR="Red"]wpa-ssid G22[/COLOR]
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
[COLOR="Red"]wpa-psk your_hex_key[/COLOR]
3. Before you save the file, generate your WPA-PSK key (your_essid = G22, your_ascii_password = router's WPA password):
> wpa_passphrase <your_essid> <your_ascii_key>
4. And copy the hex-key (in red) and replace the relevant section in "interfaces" (your_hex_key):
> network={
ssid="test"
#psk="12345678"
psk=[COLOR="Red"]fe727aa8b64ac9b3f54c72432da14faed933ea511ecab1 5bbc6c52e7522f709a
[/COLOR]}
5. Save "interfaces".

6. Reboot the computer.

7. If the network is not up after reboot, then restart the network manually:
> sudo /etc/init.d/networking restart
That's it. You have got WPA(1) running. Want more?

Now, some users have experienced (including myself) that the network has to be restarted every time after startup... Apparently this is a bug. Should you have the same problem, simply follow the last post found here (very simple):[http://www.ubuntuforums.org/showthread.php?t=202834]("http://www.ubuntuforums.org/showthread.php?t=202834")

---

### Post by bollocks00 on 2006-09-27
Unfortunately that did not work.  My /etc/network/interfaces looks like:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto ath0
iface ath0 inet dhcp
#wireless-essid G22
wpa-driver madwifi
wpa-conf managed
wpa-ssid G22
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk 00b5ca9e240f8d82aa3e59a01d5bf6186efeefd211e0f5613fe29bb97b617fe8

#pre-up wpa_supplicant -Bw -Dwext -ieth0 -c/etc/wpa_supplicant.conf
#post-down killall -q wpa_supplicant

```

network restart goes like:
```

lenny@IBM:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:c0:9f:f5:a1:83
Sending on   LPF/eth0/00:c0:9f:f5:a1:83
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:14:a4:60:fa:46
Sending on   LPF/ath0/00:14:a4:60:fa:46
Sending on   Socket/fallback
DHCPRELEASE on ath0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:c0:9f:f5:a1:83
Sending on   LPF/eth0/00:c0:9f:f5:a1:83
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:14:a4:60:fa:46
Sending on   LPF/ath0/00:14:a4:60:fa:46
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                       [ ok ]

```

Any ideas on what is going wrong?

---

### Post by sharkcohen on 2006-09-28
I would recommend that we verify that wpa_supplicant is working properly before attempting to add it to /etc/network/interfaces.  Additionally, I find just adding a pre-up call for wpa_supplicant into /etc/network/interfaces is much easier, but we can do that later.  First, let's get it working.

We'll need to know if you've configured your wireless router for WPA or WPA2 before we can continue.  I could not get mine to work with WPA, but WPA2 worked perfectly fine, and is more secure.  I would recommend WPA2.  It would also be nice to know your brand and model router.  In the meantime, perform the following:

```

sudo wpa_passphrase SSID PASSPHRASE >> /etc/wpa_supplicant.conf
sudo chmod 640 /etc/wpa_supplicant.conf

```

---

### Post by wieman01 on 2006-09-28
Hello Bollocks, 

"wireless assistant" again? Look at the error message... It says "wifi0".

---

### Post by wieman01 on 2006-09-28
And have you got "wpa_supplicant" installed? If not, please do so.

---

### Post by sharkcohen on 2006-09-28
'wifi0: unknown hardware address type 801' is a benign message, I see this message everytime.  It has to do with how the virtual access point (ath0) is associated with the base device (the hardware, wifi0).

```

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:14:6c:89:40:a9
Sending on   LPF/ath0/00:14:6c:89:40:a9
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
ip length 314 disagrees with bytes received 534.
accepting packet with data after udp payload.
DHCPOFFER from 10.37.43.1
DHCPREQUEST on ath0 to 255.255.255.255 port 67
ip length 314 disagrees with bytes received 534.
accepting packet with data after udp payload.
DHCPACK from 10.37.43.1
bound to 10.37.43.2 -- renewal in 988060712 seconds.

```

---

### Post by wieman01 on 2006-09-28
Sharkcohen, 

I suspect that this has to do with "wireless assistant" or similar tools. What would you think it is? Looks strange to me.

---

### Post by bollocks00 on 2006-09-28
No I haven't messed with wireless assistant yet.  My router is a netgear WGT624 super G router.  I would like to go ahead and setup WPA2 if possible.  How can I tell if wpa_supplicant is working properly?

---

### Post by bollocks00 on 2006-09-28
Also I just removed knetwork manager and network manager applet from my system.

---

### Post by sharkcohen on 2006-09-28
Cool, I have the same router, so this should be easy.  Under Wireless Settings>Security Options, choose 'WPA2-PSK [AES]'

If you haven't already, do the following as I mentioned earlier, substituting your actual SSID name for SSID and a passphrase of your choosing for PASSPHRASE:

```

sudo wpa_passphrase SSID PASSPHRASE >> /etc/wpa_supplicant.conf
sudo chmod 640 /etc/wpa_supplicant.conf

```

Then open /etc/wpa_supplicant.conf in your favorite editor:

```

sudo <your favorite editor> /etc/wpa_supplicant.com

```

The file should look something like:

```

network={
        ssid="YOUR SSID"
        #psk="YOUR PASSPHRASE"
        psk="some long 64 character hex number"
}

```

You'll want to add some lines, I'll just post the way it should look with the added lines:

```

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
eapol_version=2
ap_scan=1
fast_reauth=1

network={
        ssid="YOUR SSID"
        scan_ssid=0
        proto=RSN
        key_mgmt=WPA-PSK
        pairwise=CCMP TKIP
        group=CCMP TKIP WEP104 WEP40
        #psk="YOUR PASSPHRASE"
        psk="some long 64 character hex number"
}

```

Then, to test it out, first shut down your network interfaces:

```

sudo ifconfig ath0 down
sudo ifconfig wifi0 down

```

And then, try starting up wpa_supplicant in verbose mode:

```

sudo wpa_supplicant -Dmadwifi -iath0 -c/etc/wpa_supplicant.conf -dd

```

You *should* at this time see something like:

```

State: GROUP_HANDSHAKE -> COMPLETED 
CTRL-EVENT-CONNECTED - Connection to 00:14:a5:8d:34:94 completed (auth) 
EAPOL: External notification - portValid=1 
EAPOL: External notification - EAP success=1 
EAPOL: SUPP_PAE entering state AUTHENTICATING 
EAPOL: SUPP_BE entering state SUCCESS 
EAP: EAP entering state DISABLED 
EAPOL: SUPP_PAE entering state AUTHENTICATED 
EAPOL: SUPP_BE entering state IDLE

```

Let us know how things go.  If it works properly, then we can work transfering things to your /etc/network/interfaces

---

### Post by wieman01 on 2006-09-28
Just a note:
> pairwise=CCMP [COLOR="Red"]**TKIP**[/COLOR]
group=CCMP **[COLOR="Red"]TKIP WEP104 WEP40[/COLOR]**
You can remove TKIP, WEP104, and WEP40 as you are not going to use it. CCMP is WPA2 (AES).

---

### Post by bollocks00 on 2006-09-28
Thanks for the help, sorry to keep you waiting but I will have to get to this tomorrow.  Grad school is ramping up and calling my name...

---

### Post by sharkcohen on 2006-09-28
That's ok, I need to sleep.  I'll check in tomorrow!

---

### Post by bollocks00 on 2006-09-28
Okay, still not working.  I get:

```

lenny@IBM:~$ sudo wpa_supplicant -Dmadwifi -iath0 -c/etc/wpa_supplicant.conf -dd
Initializing interface 'ath0' conf '/etc/wpa_supplicant.conf' driver 'madwifi' ctrl_interface 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ctrl_interface_group=0
eapol_version=2
ap_scan=1
fast_reauth=1
Line: 17 - start of a new network block
ssid - hexdump_ascii(len=3):
     47 32 32                                          G22
scan_ssid=0 (0x0)
proto: 0x2
key_mgmt: 0x2
pairwise: 0x10
group: 0x10
Line 25: Invalid passphrase length 64 (expected: 8..63) '00b5ca9e240f8d82aa3e59a01d5bf6186efeefd211e0f5613fe29bb97b617fe8'.
Line 25: failed to parse psk '"00b5ca9e240f8d82aa3e59a01d5bf6186efeefd211e0f5613fe29bb97b617fe8'.
Line 26: WPA-PSK accepted for key management, but no PSK configured.
Line 26: failed to parse network block.
Failed to read read or parse configuration '/etc/wpa_supplicant.conf'.
Failed to add interface ath0
Cancelling scan request

```

And my /etc/wpa_supplicant.conf file looks like:
```

#network={
#       ssid="G22"
#       scan_ssid=1
#       proto=WPA RSN
#       key_mgmt=WPA-PSK
#       pairwise=CCMP TKIP
#       group=CCMP TKIP
#      psk=00b5ca9e240f8d82aa3e59a01d5bf6186efeefd211e0f5613fe29bb97b617fe8
#}

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
eapol_version=2
ap_scan=1
fast_reauth=1

network={
        ssid="G22"
        scan_ssid=0
        proto=RSN
        key_mgmt=WPA-PSK
        pairwise=CCMP
        group=CCMP
       psk="00b5ca9e240f8d82aa3e59a01d5bf6186efeefd211e0f5613fe29bb97b617fe8"
}

```

---

### Post by wieman01 on 2006-09-28
This line is incorrect:
> psk="00b5ca9e240f8d82aa3e59a01d5bf6186efeefd211e0f5613fe29bb97b617fe8"
You need to remove the ""... That should do.
> psk=00b5ca9e240f8d82aa3e59a01d5bf6186efeefd211e0f5613fe29bb97b617fe8

---

### Post by bollocks00 on 2006-09-29
I removed the quotes, but it is still not working.  It is a new error this time, it keeps scanning over and over:

```

lenny@IBM:~$ sudo wpa_supplicant -Dmadwifi -iath0 -c/etc/wpa_supplicant.conf -dd
Initializing interface 'ath0' conf '/etc/wpa_supplicant.conf' driver 'madwifi' ctrl_interface 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ctrl_interface_group=0
eapol_version=2
ap_scan=1
fast_reauth=1
Line: 17 - start of a new network block
ssid - hexdump_ascii(len=3):
     47 32 32                                          G22
scan_ssid=0 (0x0)
proto: 0x2
key_mgmt: 0x2
pairwise: 0x10
group: 0x10
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='G22'
Initializing interface (2) 'ath0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=19 WE(source)=13 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
Own MAC address: 00:14:a4:60:fa:46
wpa_driver_madwifi_del_key: keyidx=0
wpa_driver_madwifi_del_key: keyidx=1
wpa_driver_madwifi_del_key: keyidx=2
wpa_driver_madwifi_del_key: keyidx=3
wpa_driver_madwifi_set_countermeasures: enabled=0
wpa_driver_madwifi_set_drop_unencrypted: enabled=1
Setting scan request: 0 sec 100000 usec
Using existing control interface directory.
Added interface ath0
Wireless event: cmd=0x8b06 len=8
Ignore event for foreign ifindex 4
RTM_NEWLINK, IFLA_IFNAME: Interface 'ath0' added
RTM_NEWLINK, IFLA_IFNAME: Interface 'ath0' added
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Wireless event: cmd=0x8b1a len=8
Wireless event: cmd=0x8b1a len=12
Wireless event: cmd=0x8b1a len=8
Wireless event: cmd=0x8b1a len=12
Wireless event: cmd=0x8b1a len=8
Wireless event: cmd=0x8b19 len=8
Received 2431 bytes of scan results (12 BSSes)
Scan results: 12
Selecting BSS from priority group 0
0: 00:14:6c:fa:32:b0 ssid='G22' wpa_ie_len=0 rsn_ie_len=22 caps=0x11
   selected based on RSN IE
Trying to associate with 00:14:6c:fa:32:b0 (SSID='G22' freq=2437 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
RSN: using IEEE 802.11i/D9.0
WPA: Selected cipher suites: group 16 pairwise 16 key_mgmt 2
WPA: clearing AP WPA IE
WPA: set AP RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 01 00
WPA: using GTK CCMP
WPA: using PTK CCMP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
No keys have been configured - skip key clearing
wpa_driver_madwifi_set_drop_unencrypted: enabled=1
State: SCANNING -> ASSOCIATING
wpa_driver_madwifi_associate
ioctl[IEEE80211_IOCTL_SETMLME]: Argument list too long
Association request to the driver failed
Setting authentication timeout: 5 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
RSN: added PMKSA cache candidate 00:14:6c:fa:32:b0 prio 1000
RSN: processing PMKSA candidate list
RSN: not in suitable state for new pre-authentication
Wireless event: cmd=0x8b1a len=12
Wireless event: cmd=0x8b1a len=12
Authentication with 00:00:00:00:00:00 timed out.
Added BSSID 00:00:00:00:00:00 into blacklist
State: ASSOCIATING -> DISCONNECTED
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Wireless event: cmd=0x8b1a len=8
Wireless event: cmd=0x8b1a len=8
Wireless event: cmd=0x8b19 len=8
Received 2431 bytes of scan results (12 BSSes)
Scan results: 12
Selecting BSS from priority group 0
0: 00:14:6c:fa:32:b0 ssid='G22' wpa_ie_len=0 rsn_ie_len=22 caps=0x11
   selected based on RSN IE
Trying to associate with 00:14:6c:fa:32:b0 (SSID='G22' freq=2437 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
RSN: using IEEE 802.11i/D9.0
WPA: Selected cipher suites: group 16 pairwise 16 key_mgmt 2
WPA: clearing AP WPA IE
WPA: set AP RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 01 00
WPA: using GTK CCMP
WPA: using PTK CCMP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
No keys have been configured - skip key clearing
wpa_driver_madwifi_set_drop_unencrypted: enabled=1
State: SCANNING -> ASSOCIATING
wpa_driver_madwifi_associate
ioctl[IEEE80211_IOCTL_SETMLME]: Argument list too long
Association request to the driver failed
Setting authentication timeout: 5 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
RSN: added PMKSA cache candidate 00:14:6c:fa:32:b0 prio 1000
RSN: processing PMKSA candidate list
RSN: not in suitable state for new pre-authentication
Wireless event: cmd=0x8b1a len=12
Wireless event: cmd=0x8b1a len=12
CTRL-EVENT-TERMINATING - signal 2 received
Removing interface ath0
State: ASSOCIATING -> DISCONNECTED
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_madwifi_set_drop_unencrypted: enabled=0
wpa_driver_madwifi_set_countermeasures: enabled=0
No keys have been configured - skip key clearing
Removed BSSID 00:00:00:00:00:00 from blacklist (clear)
Cancelling scan request

```

I had to use ctrl+c to opt out of it.  It does not stop on it's own.

---

### Post by sharkcohen on 2006-09-29
I think you need to try installing the latest madwifi driver from CVS, and then build the latest wpa_supplicant against it.

---

### Post by wieman01 on 2006-09-29
Ok, here is my suspicion... I have tried WPA(2) / AES with another guy (Atheros chipset - same as you) and for the life of me we could not get WPA2 working. Then it turned out that WPA1 with TKIP was not problem, apparently his card did not support AES. This error message suggests that you face the same issue:
```
ioctl[IEEE80211_IOCTL_SETMLME]: Argument list too long
```
So my idea is to try TKIP first. Drop CCMP (=AES) for a minute and try if TKIP works for you (you have to set it in the router too).
```
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
eapol_version=2
ap_scan=1
fast_reauth=1

network={
        ssid="G22"
        scan_ssid=0
        [COLOR="Red"]proto=wpa[/COLOR]
        key_mgmt=WPA-PSK
        [COLOR="Red"]pairwise=TKIP
        group=TKIP[/COLOR]
        psk=00b5ca9e240f8d82aa3e59a01d5bf6186efeefd211e0f5613fe29bb97b617fe8
}
```

---

### Post by wieman01 on 2006-09-29
Also try changing the value of this line:
> scan_ssid=**[COLOR="Red"]1[/COLOR]**

---

### Post by bollocks00 on 2006-09-29
I think you may be right about WPA2 being unsupported.  It doesn't seem to work in windows, so I doubt I will get it working in linux.  I changed ssid to 1 and switched to plain WPA as per your instructions.  I still get a similar error though:

```

lenny@IBM:~$ sudo wpa_supplicant -Dmadwifi -iath0 -c/etc/wpa_supplicant.conf -dd Initializing interface 'ath0' conf '/etc/wpa_supplicant.conf' driver 'madwifi' c trl_interface 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ctrl_interface_group=0
eapol_version=2
ap_scan=1
fast_reauth=1
Line: 17 - start of a new network block
ssid - hexdump_ascii(len=3):
     47 32 32                                          G22
scan_ssid=1 (0x1)
proto: 0x1
key_mgmt: 0x2
pairwise: 0x8
group: 0x8
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='G22'
Initializing interface (2) 'ath0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=19 WE(source)=13 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
Own MAC address: 00:14:a4:60:fa:46
wpa_driver_madwifi_del_key: keyidx=0
wpa_driver_madwifi_del_key: keyidx=1
wpa_driver_madwifi_del_key: keyidx=2
wpa_driver_madwifi_del_key: keyidx=3
wpa_driver_madwifi_set_countermeasures: enabled=0
wpa_driver_madwifi_set_drop_unencrypted: enabled=1
Setting scan request: 0 sec 100000 usec
Using existing control interface directory.
Added interface ath0
Wireless event: cmd=0x8b06 len=8
Ignore event for foreign ifindex 4
RTM_NEWLINK, IFLA_IFNAME: Interface 'ath0' added
RTM_NEWLINK, IFLA_IFNAME: Interface 'ath0' added
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=3):
     47 32 32                                          G22
Wireless event: cmd=0x8b1a len=12
Wireless event: cmd=0x8b19 len=8
Received 1572 bytes of scan results (8 BSSes)
Scan results: 8
Selecting BSS from priority group 0
0: 00:14:6c:fa:32:b0 ssid='G22' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
Trying to associate with 00:14:6c:fa:32:b0 (SSID='G22' freq=2437 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2
WPA: set AP WPA IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_madwifi_set_drop_unencrypted: enabled=1
State: SCANNING -> ASSOCIATING
wpa_driver_madwifi_associate
ioctl[IEEE80211_IOCTL_SETMLME]: Argument list too long
Association request to the driver failed
Setting authentication timeout: 5 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
Wireless event: cmd=0x8b1a len=12
Authentication with 00:00:00:00:00:00 timed out.
Added BSSID 00:00:00:00:00:00 into blacklist
State: ASSOCIATING -> DISCONNECTED
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Wireless event: cmd=0x8b1a len=8
Wireless event: cmd=0x8b19 len=8
Received 1956 bytes of scan results (10 BSSes)
Scan results: 10
Selecting BSS from priority group 0
0: 00:14:6c:fa:32:b0 ssid='G22' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
Trying to associate with 00:14:6c:fa:32:b0 (SSID='G22' freq=2437 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2
WPA: set AP WPA IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_madwifi_set_drop_unencrypted: enabled=1
State: SCANNING -> ASSOCIATING
wpa_driver_madwifi_associate
ioctl[IEEE80211_IOCTL_SETMLME]: Argument list too long
Association request to the driver failed
Setting authentication timeout: 5 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
Wireless event: cmd=0x8b1a len=12
Authentication with 00:00:00:00:00:00 timed out.
BSSID 00:00:00:00:00:00 blacklist count incremented to 2
State: ASSOCIATING -> DISCONNECTED
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=3):
     47 32 32                                          G22
Wireless event: cmd=0x8b1a len=12
Wireless event: cmd=0x8b19 len=8
Received 2444 bytes of scan results (12 BSSes)
Scan results: 12
Selecting BSS from priority group 0
0: 00:14:6c:fa:32:b0 ssid='G22' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
Trying to associate with 00:14:6c:fa:32:b0 (SSID='G22' freq=2437 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2
WPA: set AP WPA IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_madwifi_set_drop_unencrypted: enabled=1
State: SCANNING -> ASSOCIATING
wpa_driver_madwifi_associate
ioctl[IEEE80211_IOCTL_SETMLME]: Argument list too long
Association request to the driver failed
Setting authentication timeout: 5 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
Wireless event: cmd=0x8b1a len=12
CTRL-EVENT-TERMINATING - signal 2 received
Removing interface ath0
State: ASSOCIATING -> DISCONNECTED
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_madwifi_set_drop_unencrypted: enabled=0
wpa_driver_madwifi_set_countermeasures: enabled=0
No keys have been configured - skip key clearing
Removed BSSID 00:00:00:00:00:00 from blacklist (clear)
Cancelling scan request

```

---

### Post by bollocks00 on 2006-09-29
I also tried with scan_ssid=0, neither worked...

---

### Post by bollocks00 on 2006-09-29
> **sharkcohen said:**
> I think you need to try installing the latest madwifi driver from CVS, and then build the latest wpa_supplicant against it.

How do I go about doing this?  I just started messing with the wireless maybe 5 days ago at most.  I am pretty sure I downloaded the most recent madwifi drivers at that time.

---

### Post by wieman01 on 2006-09-29
**Windows** does not support WPA2 by default. You have to install a patch (found on the MS website) first before you can enable it. So assuming that you don't have the patch, I am afraid this does not mean much...

---

### Post by bollocks00 on 2006-09-29
Basically I am indifferent as to whether I use WPA or WPA2.  I will ultimately end up using MAC filtering with private ssid, so I don't care too much about the extra security added by WPA2.  I just want to get one of them working 8)

---

### Post by BillThor on 2007-02-22
I noticed a problem with 'wifi0_ifrename: unknown hardware address type 801' warnings this morning, when I failed to connect.  iwscan reported lots of stations.   After doing ifdown ath0, I manually ran the iwconfig commands manually. Cat /etc/network/interfaces.  For each wireless- line, replaced wireless- with iwconfig ath0 and entered the command.  None of these generated  my error.  When I ran dhclient the error occurred twice, so it appears the problem not with the wireless setup.  

I have had problems with TKIP keys in the past.  Monitoring with iwevent show the connection goes down every couple of minutes, and rescanning every  few minutes.

---

