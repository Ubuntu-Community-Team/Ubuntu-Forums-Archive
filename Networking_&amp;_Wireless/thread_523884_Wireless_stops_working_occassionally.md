---
title: "Wireless stops working occassionally"
date: 2007-08-12
forum: Networking &amp; Wireless
---

### Post by rax_m on 2007-08-12
Hi
I have a Toshiba Satellite P100 laptop. Ever since upgrading to Feisty (clean install), my wireless connection seems to die occassionally and randomly. Network manager can see my wireless AP but just can't connect to it. Once I reboot it works fine. Most often occurs if the laptop is left running for a long time (i.e. a day or more).

Kernel: 2.6.20-16-generic
Using the restricted drivers for the networking which is installed automatically after you install.

Tried doing "sudo /etc/init.d/networking restart" but that doesn't bring it back.

Any ideas what might be causing this? Or a way to bring it back without rebooting?

Cheers
Rax

---

### Post by noob12 on 2007-08-13
Next time you get into the non-working state, can you capture and later post the output of the following?
```

sudo lshw -C network

ifconfig -a

iwconfig

iwlist scan

```

---

### Post by rax_m on 2007-08-13
noob12, Thanks for the reply. I'll try do that as soon as the problem pops up again.

---

### Post by rax_m on 2007-08-19
Well.. it's happenned again. Some additional observations: 

1. Doing a "sudo /etc/init.d/networking restart" allows network manager to think that it is now connected to my wireless network. Before that, it could see the SID but would not attempt to connect (even if I clicked on the SID). 
1.a. Even though it thinks it's connected, I still get a "page not found" error when trying to browse sites. 
2. Loggin in and out does not change this. 
3. Reboot is still the only way to get connected properly. 

Here's the output from the commands you requested:



```

rmistry@rmistry-laptop:~$ sudo lshw -C network
Password:
  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 00
       serial: 00:16:36:86:7b:39
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.15-k2-NAPI firmware=0.5-5 latency=0 link=no multicast=yes port=twisted pair
       resources: iomemory:6c000000-6c01ffff ioport:3000-301f irq:16
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth1
       version: 02
       serial: 00:18:de:23:f5:4e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp firmware=14.2 1:0 () latency=0 link=no multicast=yes wireless=unassociated
       resources: iomemory:6c100000-6c100fff irq:17


```

```

rmistry@rmistry-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:16:36:86:7B:39  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0x3000 Memory:6c000000-6c020000 

eth1      Link encap:Ethernet  HWaddr 00:18:DE:23:F5:4E  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:65 dropped:47058 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:261200760 (249.1 MiB)  TX bytes:22392431 (21.3 MiB)
          Interrupt:17 Memory:6c100000-6c100fff 

eth0:avah Link encap:Ethernet  HWaddr 00:16:36:86:7B:39  
          inet addr:169.254.5.30  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Base address:0x3000 Memory:6c000000-6c020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2274 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2274 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:386043 (376.9 KiB)  TX bytes:386043 (376.9 KiB)


```

```
rmistry@rmistry-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:1  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:46994   Missed beacon:0

```

```

rmistry@rmistry-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:0F:CB:A2:B1:AE
                    ESSID:"SpiderWan"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=93/100  Signal level=-37 dBm  Noise level=-37 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 88ms ago

```

---

### Post by noob12 on 2007-08-19
Hmm.  The driver seems to have completely corrupted its notion of frequency  (nan = not a number = bad floating point value).
> 
Mode:Managed  Frequency=[COLOR="Red"]nan[/COLOR] kHz  Access Point: Not-Associated   
Bit Rate:0 kb/s   Tx-Power:16 dBm   
Retry limit:15   RTS thr:off   Fragment thr:off
Power Management:off
Link Quality:0  Signal level:0  Noise level:0
Rx invalid nwid:0  Rx invalid crypt:1  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:46994   Missed beacon:0


Meanwhile you aren't really associated, and you don't have an IP address on the interface, so you're not going anywhere in that condition.

Try this.

```

sudo iwconfig eth1 freq 2.462G
sudo iwconfig eth1 channel 11

```

If that doesn't work, try the following, which as you can probably tell stops networking, reloads the driver, and then restarts networking.
```

sudo /etc/init.d/networking stop
sudo modprobe -r ipw3945
sudo modprobe ipw3945
sudo /etc/inig.d/networking start

```

Even if this works to restore things, it doesn't really tell us how it's getting that way and how to avoid it, but it indicates a driver issue. I'd look for filed bugs on launchpad or the ipw driver bug site ([http://www.bughost.org/bugzilla/](http://www.bughost.org/bugzilla/)).

I'm going to be gone from the forums for a week, so I won't be able to respond.  Hope this helps.

---

### Post by rax_m on 2007-08-20
Thanks again for the quick reply noob12. I'll keep those commands in mind, and try it the next time things get stuffed up. 

I have filed a report on launchpad as well.

---

### Post by rax_m on 2007-08-27
Hi again.. This problem seems to be happenning more frequently these days. I would say it's a hardware bug, but on reboot it works with no issues.. 

Here's the output from the commands you requested i run:


```

rmistry@rmistry-laptop:~$ sudo iwconfig eth1 freq 2.462G
Password:
Error for wireless request "Set Frequency" (8B04) :
    SET failed on device eth1 ; Resource temporarily unavailable.


```

```

rmistry@rmistry-laptop:~$ sudo iwconfig eth1 channel 11
Error for wireless request "Set Frequency" (8B04) :
    SET failed on device eth1 ; Resource temporarily unavailable.
rmistry@rmistry-laptop:~$ 

```


```

rmistry@rmistry-laptop:~$ sudo /etc/init.d/networking stop
 * Deconfiguring network interfaces...                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 5951
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:16:36:86:7b:39
Sending on   LPF/eth0/00:16:36:86:7b:39
Sending on   Socket/fallback
Interface "eth1" is already disabled.
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:18:de:23:f5:4e
Sending on   LPF/eth1/00:18:de:23:f5:4e
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.


                                                                         [ OK ]


```

This command just hangs. Even Ctrl-C doesn't kill it. 

```

rmistry@rmistry-laptop:~$ sudo modprobe -r ipw3945


```

This command also hangs:
```

rmistry@rmistry-laptop:~$ sudo modprobe ipw3945
Password:

```


```

rmistry@rmistry-laptop:~$ sudo /etc/init.d/networking start
 * Configuring network interfaces...                                            There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:16:36:86:7b:39
Sending on   LPF/eth0/00:16:36:86:7b:39
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11


```


Some observations I made:
1. Just before the wireless disconnects, the computer seems to hang for a few seconds (e.g. sound playing will stutter, mouse stops moving, etc). 
2. On shutdown, the computer doesn't cleanly stop. I frequently notice it failing on the firestarter module. 
3. Reboot seems to take a bit longer after that happens. 

Any more help would be great. 

NB One more thing.. this didn't happen to me on Edgy and I think I used the free drivers there!

---

### Post by Zorael on 2007-08-27
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ipw3945/+bug/134515](https://bugs.launchpad.net/ipw3945/+bug/134515) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I'm experiencing something similar but not exactly the same, discussed [here](http://ubuntuforums.org/showthread.php?t=533331) and the launchpad entry [here](https://bugs.launchpad.net/ipw3945/+bug/134515).

Fortunately, at least my machine manages to modprobe ipw3945 back. Doesn't sound like fun. :/

---

### Post by rax_m on 2007-08-29
Thanks Zorael... I had a look, but I'm not sure if it's the same?
Anyway I've logged a bug on launchpad as well and it was confirmed.. so guess we wait and see. 

I'm sure this didn't happen with Edgy, which possibly did NOT use the proprietary driver..

---

### Post by incarnis on 2007-08-30
Hi

I have the same problem as this. All the output from iwconfig, iwlist etc looks the same, with the "nan" entry in the frequency area. Nothing seems to be able to reset it, including re-loading the kernel module for the IPW3945.

However, I note that people are saying "it goes away when I reboot". Mine worked for the first day of a new Kubuntu (Feisty Fawn) install, but never after that (the install is 3 days old). Multiple reboots failed to fix it :(.

Simon

---

### Post by noob12 on 2007-08-30
Hey rax_m, can you please post a link to the bug you filed so that others can hop on that as well?

---

### Post by Zorael on 2007-08-30
> **rax_m said:**
> Thanks Zorael... I had a look, but I'm not sure if it's the same?

Mine ends up in an unresponsive state as well, and only a reboot or a complete reload (stop, start) of the ipw3945 module gets it back in shape. Mine doesn't lose its frequency setting to nan, though.

And note, an iwlist scan only reports the result of the last scan performed, you'll have to do it with sudo to have it scan anew.


Could you post a link to your filed bug, please?

edit: actually, it does sometimes end up with nan.

---

### Post by rax_m on 2007-09-03
Hi, sorry for the slow repy.. 

Here's a link to my bug report:
[https://bugs.launchpad.net/ubuntu/+bug/132042]("https://bugs.launchpad.net/ubuntu/+bug/132042")

---

### Post by incarnis on 2007-09-04
I think I have fixed my problem with this.

Mine stopped working a day or two after my new Kubuntu Feisty install. When I dug around in the config, I could find very little in the way of configuration in /etc/network/interfaces (nothing on wireless), and I couldn't find a wpa-supplicant config anywhere.

I came to the conclusion eventually that the WPA-PSK setup I configured on install had been "lost".

I followed the instructions in Wieman01's HOWTO [*** here ***]("http://ubuntuforums.org/showthread.php?highlight=howto&t=202834") and it all started working.

My setup is WPA-PSK, and I put the following items in /etc/network/interfaces:

wpa-driver wext       [I tried ipw3945 first but it moaned, wext worked fine]
wpa-ssid  [my ssid]
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-psk [my hex key generated from 'wpa_passphrase' ]

When I re-inited networking, everything worked. It has also survived several boots now. I get the occasional drop-out, but I think that's due to distance from my access point.

Simon

---

### Post by rax_m on 2007-09-04
Hi incarnis, 

I'm not sure if our problems are the same.. 
My connection drops out.. and then won't come back UNTIL a reboot. So the config is obviously there.. just somehow the driver seems to die. 

Rax

---

