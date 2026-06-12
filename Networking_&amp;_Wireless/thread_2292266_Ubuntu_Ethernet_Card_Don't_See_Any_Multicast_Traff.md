---
title: "Ubuntu Ethernet Card Don't See Any Multicast Traffic on the Network"
date: 2015-08-26
forum: Networking &amp; Wireless
---

### Post by ubunfan08 on 2015-08-26
I hope someone can help me resolve this issue.

I installed an Ethernet card as eth3 on an Ubuntu 14.04 server as 10.42.0.21.  It is an Ethernet card using Realtek 8168 chipset (Startech ST1000SPEX2L).  We installed the latest driver from their site.  There are a ton of multicast streams on the network.  I can ping other machines no problem.  Using VLC, I can't seem to see any of actual stream info.  I been doing some digging and someone posted that you have to turn off reverse path filtering, which I did.  Still, I can't seem to read any of the multicast streams.  I got another server on the same network and switch and it has no problem reading info off the same multicast stream.  IGMP snooping is turned on.  I even tried to unicast directly to this machine and still it can't see any info on the multicast stream.

**Here are some output for ifconfig -a**

eth3      Link encap:Ethernet  HWaddr 00:13:3b:10:69:a8
          inet addr:10.42.0.21  Bcast:10.42.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:3bff:fe10:69a8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:72877388 errors:0 dropped:22367 overruns:0 frame:0
          TX packets:42320 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:31308389172 (31.3 GB)  TX bytes:17550573 (17.5 MB)
          Interrupt:51 Base address:0xc000


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Here is the output for ethtool eth3:



**user@admin101-System-Product-Name:~$ ethtool eth3**
Settings for eth3:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supported pause frame use: No
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Advertised pause frame use: No
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        MDI-X: Unknown
Cannot get wake-on-lan settings: Operation not permitted
        Current message level: 0x00000033 (51)
                               drv probe ifdown ifup




**Here is the VLC command I used to extract info off multicast streams on the network: vlc -I dummy --extraintf=oldrc rtp://@234.1.1.1:5501**

Here is the output I get:



user@admin101-System-Product-Name:~$ vlc -I dummy --extraintf=oldrc rtp://@234.1.1.1:5501
VLC media player 2.2.1 Terry Pratchett (Weatherwax) (revision 2.2.1~trusty1)
Remote control interface initialized. Type `help' for help.
[0000000000d1d3e8] core interface error: no suitable interface module
[0000000000cef118] core libvlc error: interface "globalhotkeys,none" initialization failed
[0000000000d1d3e8] dbus interface error: Failed to connect to the D-Bus session daemon: Unable to autolaunch a dbus-daemon without a $DISPLAY for X11
[0000000000d1d3e8] core interface error: no suitable interface module
[0000000000cef118] core libvlc error: interface "dbus,none" initialization failed
[0000000000d1f018] dummy interface: using the dummy interface module...
info
status change: ( new input: rtp://@234.1.1.1:5501 )
status change: ( play state: 3 )
+----[ end of stream info ]
status
status change: ( new input: rtp://@234.1.1.1:5501 )
status change: ( audio volume: 0 )
status change: ( play state: 3 )
status: returned 0 (no error)


**Here is the output I should be getting (on another machine) using the same command:**

vlc -I dummy --extraintf=oldrc rtp://@234.1.1.1:5501
VLC media player 2.1.5 Rincewind (revision 2.1.4-49-gdab6cb5)
[0x7f9738] main audio output error: no suitable audio output module
Remote control interface initialized. Type `help' for help.
[0x8003f8] main interface error: no suitable interface module
[0x762148] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x8003f8] dummy interface: using the dummy interface module...
libdvbpsi error (PSI decoder): TS discontinuity (received 15, expected 0) for PID 0
libdvbpsi error (PSI decoder): TS discontinuity (received 15, expected 0) for PID 80
[0x7f7c28003af8] main decoder error: corrupt module: /usr/lib/vlc/plugins/codec/libzvbi_plugin.so
[0x7f7c28003af8] main decoder error: no suitable decoder module for fourcc `h264'. VLC probably does not support this sound or video format.
[0x7f7c28003af8] main decoder error: No suitable decoder module
[0x7f7c28003af8] main decoder error: VLC does not support the audio or video format "h264". Unfortunately there is no way for you to fix this.
[0x7f7c28000958] ts demux error: MPEG-4 descriptor not found
[0x7f7c28003f58] main decoder error: corrupt module: /usr/lib/vlc/plugins/codec/libzvbi_plugin.so
[0x7f7c28003f58] main decoder error: no suitable decoder module for fourcc `mp4a'. VLC probably does not support this sound or video format.
[0x7f7c28003f58] main decoder error: No suitable decoder module
[0x7f7c28003f58] main decoder error: VLC does not support the audio or video format "mp4a". Unfortunately there is no way for you to fix this.
info
status change: ( new input: rtp://@234.1.1.1:5501 )
status change: ( play state: 3 )
+----[ Stream 0 ]
|
| Type: Video
| Original ID: 256
| Codec: H264 - MPEG-4 AVC (part 10) (h264)
|
+----[ Stream 1 ]
|
| Type: Audio
| Original ID: 512
| Codec: MPEG AAC Audio (mp4a)
|
+----[ end of stream info ]



Any idea?  Thanks for any help in advance.

---

### Post by TheFu on 2015-08-27
Saw that v17 of those chips had a multicast filter bug.

The easy answer is to return the realtek card and buy one like the other machine has or get the standard card, an Intel PRO/1000 ($25).  It uses the e1000 driver.  Save yourself headaches - and not just this one - get the PRO/1000.

I used to fight with other cards before the PRO/1000 became cost effective (they were $100+ for many years). Now they are cheap and just work, so it isn't worth my time to fight.

Learned some similar things about disks, controllers, and printers. If it costs $10 more to get great linux support - do it. Plug, play, works, is worth it - IMHO.

---

### Post by ubunfan08 on 2015-08-27
> **TheFu said:**
> Saw that v17 of those chips had a multicast filter bug.

The easy answer is to return the realtek card and buy one like the other machine has or get the standard card, an Intel PRO/1000 ($25).  It uses the e1000 driver.  Save yourself headaches - and not just this one - get the PRO/1000.

I used to fight with other cards before the PRO/1000 became cost effective (they were $100+ for many years). Now they are cheap and just work, so it isn't worth my time to fight.

Learned some similar things about disks, controllers, and printers. If it costs $10 more to get great linux support - do it. Plug, play, works, is worth it - IMHO.


Thanks for the reply.  I think I will go buy the Intel PRO/1000 card right away since I am drained from dealing with issue.  I also tested on a HP 2 port server card and ran into the same problem.  I really hope this Intel card will solve the problem.  You sure e1000 support reading multicast streams right?  Thanks again for the help.

---

### Post by TheFu on 2015-08-27
Haven't touched multcast since 1996 when we used mbone at the site I worked and that was on an OSF box.

Did a little more searching ...  i dunno.  [http://manpages.ubuntu.com/manpages/trusty/man7/capabilities.7.html](http://manpages.ubuntu.com/manpages/trusty/man7/capabilities.7.html) probably won't help.

This talks about verifying that multicast is enabled in the kernel and a few other settings:
[http://ubuntuforums.org/showthread.php?t=1405360](http://ubuntuforums.org/showthread.php?t=1405360)


I DO NOT KNOW that a PRO/1000 will work in this situation, just that it is THE standard card.  Saw an intel notice about multicast. [http://downloadmirror.intel.com/25016/eng/readme.txt](http://downloadmirror.intel.com/25016/eng/readme.txt)

---

### Post by ubunfan08 on 2015-08-29
> **TheFu said:**
> Haven't touched multcast since 1996 when we used mbone at the site I worked and that was on an OSF box.

Did a little more searching ...  i dunno.  [http://manpages.ubuntu.com/manpages/trusty/man7/capabilities.7.html](http://manpages.ubuntu.com/manpages/trusty/man7/capabilities.7.html) probably won't help.

This talks about verifying that multicast is enabled in the kernel and a few other settings:
[http://ubuntuforums.org/showthread.php?t=1405360](http://ubuntuforums.org/showthread.php?t=1405360)


I DO NOT KNOW that a PRO/1000 will work in this situation, just that it is THE standard card.  Saw an intel notice about multicast. [http://downloadmirror.intel.com/25016/eng/readme.txt](http://downloadmirror.intel.com/25016/eng/readme.txt)

Thanks for the help.  I have ordered a PRO/1000 card.   I will test it as soon as I get a chance.  Hopefully, it will work.  I will get back with the results after the test.  If anyone else got any other suggestions, please share since this issue has been causing me to lose some hair lol.

---

