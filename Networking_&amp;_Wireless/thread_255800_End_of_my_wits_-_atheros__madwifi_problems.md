---
title: "End of my wits - atheros / madwifi problems"
date: 2006-09-12
forum: Networking &amp; Wireless
---

### Post by bollocks00 on 2006-09-12
I'm running Dapper Drake 6.06 on an IBM thinkpad z60t with an ar5212 (atheros) wlan chipset.

I have tried all manner of tutorials for setting up the wireless connection, and I have it where it seems like it should work.  System>Administration>Network Tools lists my device as ath0 and shows me configuration options, but I have yet to connect wirelessly.  I honestly have no idea of what I should do from here or what I should even search for, so any help will be greatly appreciated.

I get the following for iwconfig and ifconfig:

```

root@IBM:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"WEST5300"
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:8 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:232  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

irda0     no wireless extensions.

sit0      no wireless extensions.
```

```

root@IBM:~# ifconfig
ath0      Link encap:Ethernet  HWaddr 00:14:A4:60:FA:46
          inet6 addr: fe80::214:a4ff:fe60:fa46/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0      Link encap:Ethernet  HWaddr 00:C0:9F:F5:A1:83
          inet addr:192.168.1.91  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fef5:a183/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3752 (3.6 KiB)  TX bytes:4304 (4.2 KiB)
          Interrupt:201

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-14-A4-60-FA-46-00-00-00-00-00-00-00-00-00 -00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:584 errors:0 dropped:0 overruns:0 frame:145
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199
          RX bytes:49990 (48.8 KiB)  TX bytes:3500 (3.4 KiB)
          Interrupt:74 Memory:f8c40000-f8c50000

```

---

### Post by tturrisi on 2006-09-12
The link quality & signal level look to be way off.  Try connecting using System > Admin > Networking when laptop is next to AP.

---

### Post by tturrisi on 2006-09-12
The link quality & signal level look to be way off.  Try connecting using System > Admin > Networking when laptop is right next to the AP.

---

### Post by lupine_nickt on 2006-09-12
Erm, all you need is an IP address.

If using DHCP (most home routers!), just "sudo dhclient ath0", and you're away!

The link quality thing is a bit misleading - it's typically usless.

Edit: If you're currently using a wired connection, *take it down before setting up the wireless*. If not, you'll have all manner of problems with the routes, etc... 

xF,

...Nick

---

### Post by bollocks00 on 2006-09-12
Thanks for the suggestions.  My laptop is close (< 10ft) to the router and the wireless strength is excellent in windows.  I tried the dhclient command to no avail, the response is below.  Also, this may or may not be important, but wifi light (right below the screen) on my laptop does not come on in linux.  I would assume this light is linked to the wlan chip itself and is not run through the OS.  If this is the case, would it indicate some problem in initializing the chip with linux?


```

lenny@IBM:~$ sudo dhclient ath0
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:14:a4:60:fa:46
Sending on   LPF/ath0/00:14:a4:60:fa:46
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

---

### Post by spd106 on 2006-09-12
Your card is not associating with an AP, can you try scanning for any APs near you. **sudo iwlist ath0 scan**.

---

### Post by bollocks00 on 2006-09-12
```

lenny@IBM:~$ sudo iwlist ath0 scan
Password:
ath0      Scan completed :
          Cell 01 - Address: 00:14:A5:07:9B:81
                    ESSID:"Motorola"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=9/94  Signal level=-86 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:12:0E:09:B1:7E
                    ESSID:"WEST5300"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=62/94  Signal level=-33 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100

```

West5300 is the one I want, and I can see it, but there seems to be no connecting to it.

---

### Post by spd106 on 2006-09-12
According to the output from iwconfig you do not have an encryption key set.
> ath0      IEEE 802.11g  ESSID:"WEST5300"
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:8 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:232  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


But iwlist shows the essid as having encryption enabled:confused: 
> Cell 02 - Address: 00:12:0E:09:B1:7E
                    ESSID:"WEST5300"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=62/94  Signal level=-33 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100

So which is it?

---

### Post by FiReiSFuN on 2006-09-12
I'm not sure if you know anything about setting up a static IP, but try doing that through the router for your computer.

Enter those settings into the UBUNTU networking dialog in the ath0 config, and if you use a WEP key, enter it as follows XXXX-XXXX-XX (ie, with a dash between each 4 characters). Currently that is what is working for me, I haven't been able to get DHCP working as of yet.  Keep posting, and I'll keep trying to help!

---

### Post by bollocks00 on 2006-09-12
It's official.  I'm giving up, at least for now anyway.  I see no real benefits to using linux other than it taking 30+ minutes to set anything up.   And I'm fairly convinced that wireless with my hardware is simply not possible through linux.  I consider myself a sharp guy, but there are too many dead end forum posts out there (like this one now) and I have no desire to live (with linux).

Thanks for the effort!

---

### Post by Brandon71065 on 2006-09-15
Don't do that. If you are just trying to troll to get help, don't do that either. I feel your pain, but you have a better chance of getting it fixed, and learning about your box here, than anywhere else. 

Pretending that other OS's/distros/whatever dont have this problem won't help either. They do. 

I am using have/been using linux/freebsd/solaris for 10 years. I have the same card you do and am having the same problem. It was working just fine with Dapper last week. 

Try a quick experiment, boot off your live CD if you have one, bet it will connect just fine. If so, then we need to track this down and submit a bug report. 

I can tell you it's not a problem with the card. It might have something to do with dhclient, but that seems unlikely.

Have you tried assigning an address to your ath0 interface?

I had a driver problem in (same wirelesss card) in WinDoze, about 10 months ago and fixed it by switching to Hoary. You will get more and better support here than from any commercial company anywhere. 

I have been looking at the Madwifi code to try and figure this out, but I don't have a firm grasp on working vs. non working version. I think I might have updated more than once to solve some other problem (which now works just fine).

Brandon.

---

### Post by onioneater36 on 2006-09-25
Bump-a-reeno

I am having the exact same problem with my Netgear WG511T card which is atheros based chipset.  Everything on the WIFI side looks great, but I don't get an IP address from DHCP.

---

### Post by sharkcohen on 2006-09-26
> **onioneater36 said:**
> Bump-a-reeno

I am having the exact same problem with my Netgear WG511T card which is atheros based chipset.  Everything on the WIFI side looks great, but I don't get an IP address from DHCP.

Are you trying to use encryption (WEP, WPA)?

Please post results from:

iwconfig ath0

iwlist ath0 scan

---

### Post by onioneater36 on 2006-09-26
iwconfig ath0

```
onioneater36@dell-c840-linux:~$ iwconfig ath0
ath0      IEEE 802.11g  ESSID:"private"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:B5:10:F9:77
          Bit Rate:36 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=59/94  Signal level=-36 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

iwlist ath0 scan

```
onioneater36@dell-c840-linux:~$ iwlist ath0 scan
ath0      Scan completed :
          Cell 01 - Address: 00:0F:B5:10:F9:77
                    ESSID:"nowakowski_lan_g"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=59/94  Signal level=-36 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100

```

Hope this helps...  Thanks for looking into it...

---

### Post by sharkcohen on 2006-09-26
I can see that you are associated with the access point, and can also see that your access point is using some kind of encryption.  For troubleshooting, try disabling the encryption on the access point, and then see if you can pull an IP address.

What kind of encryption are you trying to use?  Madwifi natively supports WEP, and I've successfully got WEP working with my Netgear hardware.  WPA requires a companion program, wpa_supplicant.  I've followed the wpa_supplicant instructions to the T and have not been able to get it to work properly, but I've put in a request for assistance to the madwifi mailing list.  If I'm able to get WPA working with their help, I'll be posting my resolution in this forum.

---

### Post by Zeram on 2006-09-26
I have the same issue on my IBM T42, the funny thing is some times I start the wpa_supplicant and it connects no problem other times I start it and get nothing. I haven't been able to discern a pattern to it yet.

---

### Post by dannyboy79 on 2006-09-26
DUde, why are you guys having so many problems???? I have Xubuntu 6.06 Dapper Drake and my WG511T is found by default! I am using WEP protection since the WG511T doesn't support WPA. I use a static IP if that helps anyone? Other than that it's all standard! Hope you guys get it working. Oh, my interface is ath0. Good luck!!

---

### Post by sharkcohen on 2006-09-26
> **dannyboy79 said:**
> WG511T doesn't support WPA. 

Is this true?

---

### Post by onioneater36 on 2006-09-26
My WG511T supports WPA just fine in Windows, but you have to upgrade to the latest driver.  I got my WG511T working in Ubuntu this evening with WPA.  It still has very minor issues, but overall works very acceptably.

---

### Post by sharkcohen on 2006-09-27
Must be a particular planetary alignment tonight because I was able to get WPA working tonight, too.

---

### Post by livestockPimp on 2006-09-27
i was getting really wierd problems trying to get my atheros going in ubuntu... similar to what you are experiencing... in the end i solved it with:

iwpriv ath0 authmode 2

give that a shot if its not too late...

---

### Post by dannyboy79 on 2006-09-27
so are you guys using the WG511T with ndiswrapper so you can use the latest windows driver which has the WPA support? I know it didn't support it originally because I bought the pc card with the NEtgear WGR624 which didn't have WPA, it only has MAC address filtering and WEP. I just stick with WEP as first of all I am not to worried about my neighbors picking packets out the air as they are all pretty computer illiterate and secondly, i don't use my wireless connection for anything security critical anyway. i use my ubuntu desktop or winxp desktop to pay bills online etc etc.

---

