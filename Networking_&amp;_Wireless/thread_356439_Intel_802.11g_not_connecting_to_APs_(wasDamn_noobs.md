---
title: "Intel 802.11g not connecting to APs (was:Damn noobs!!!!!!)"
date: 2007-02-08
forum: Networking &amp; Wireless
---

### Post by whayong on 2007-02-08
Hello everyone!  I'm a noob, go easy.

I just installed ubuntu 6.10 yesterday and have been having problems with my wireless card.  I tried a few things I found while searching the forums but none of them worked.  Because of this, I did a fresh reinstall of 6.10 this morning via the Live CD.

My system:
Sony VAIO PCG-SRX77
Pentium III M 800 Mhz
384 MB RAM
20 GB HD

The wireless card that came with the laptop was replaced.  It used to be an ORINOCO 802.11b.  It was replaced to an intel 802.11g.  

Here's the problem:

I cannot connect to my router wirelessly, lol!  I do not/cannot see any wireless networks.  The only way I can connect to the router is via ethernet cable.

The wireless card appears under system>administration>networking.  The card falls under eth2.  Is that correct?  Shouldn't it be wlan0 or something like that?  Could this be the cause of the problem?  In my previous installation, I tried using Network-manager but that too didn't work.  It just said "No network available" or something to that extent.  Could I have the wrong driver?  

Thanks for the help.

---

### Post by Brunellus on 2007-02-08
thread re-titled to reflect help request.  Please use your thread title to describe your problem;  that way, users who know how to help you know that they CAN help you.  Appeals to mercy will not result in meaningful or useful technical assistance.

---

### Post by whayong on 2007-02-08
Thanks!

---

### Post by dannyboy79 on 2007-02-08
FYI, edgy and wg511t was not good out of the box supposedly per this link. [http://madwifi.org/ticket/1016](http://madwifi.org/ticket/1016)
madwifi fixed this issue around 2/6/07 for the wg511t, Gnome NetworkManager (using wpa_supplicant, using madwifi-ng, using ath_pci).

so maybe this is the issue for your wifi card as well?

---

### Post by whayong on 2007-02-08
OK.  After searching around, apparently, I do not have an intel card.  

I have a ISL 3890 PrismGT/Prism Duette

According to this site [http://www.prism54.org/index.html](http://www.prism54.org/index.html) these cards are now supported.  Also, there apparently seems to be a firmware upgrade for the said cards.  How do I find out if I need it?  How do I install the firmware if needed.  The site says to put the firmware here: /usr/lib/hotplug/firmware/isl3890

How do I go about doing this?

Thanks again!

---

### Post by dannyboy79 on 2007-02-08
well, you need to download the file they have here, [http://www.prism54.org/fullmac.html](http://www.prism54.org/fullmac.html)
and simply rename it so that it's named isl3890 and make sure you put it in that location. /usr/lib/hotplug/firmware/

also, have you followed all the threads about how to troubleshoot your wireless connection? I suggest you do that after you get this new firmware. Also, it's always a good idea to unplug your ethernet cable while you're trying to enable wireless because they can conflict with 1 another.

---

### Post by whayong on 2007-02-08
Is there a way that it can be done through the terminal?  I can't seem to do it in the window.  The location /hotplug/firmware doesn't exist so I made new folders but can't seem to put the /hotplug/firmware/isl3890 in the /usr/lib

Am I making sense? lol!  Obvious windows user here.

---

### Post by whayong on 2007-02-09
I got the firmware moved and renamed, finally!  I still can't get the wlan to work though.

---

### Post by Brunellus on 2007-02-09
time to get gritty.  post the output of ifconfig -a and iwconfig

---

### Post by dannyboy79 on 2007-02-09
brunellus, thanks for helping him. I can't stand to help with another wireless issue. they are very mentally draining!!! it's to bad that there is still this much trouble with a feature that is pretty much a must for laptop owners who want to swtich from winbloz to ubuntu so you would think that the developers would try to get more testers of every wireless chipset out there. NOT to say they haven't done a lot of work cause they do and Ubuntu is really awesome as fast as it's moving. I mean, what other distro's release a new release every 6 months?

---

### Post by whayong on 2007-02-09
I really appreciate all this guys.....

ifconfig -a
eth0      Link encap:Ethernet  HWaddr 08:00:46:45:71:8D  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth2      Link encap:Ethernet  HWaddr 00:60:B3:13:B8:82  
          inet6 addr: fe80::260:b3ff:fe13:b882/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:139 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:45954 (44.8 KiB)
          Interrupt:9 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:300 (300.0 b)  TX bytes:300 (300.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11b/g  Mode:Managed  Frequency:2.432 GHz  
          Access Point: Not-Associated   Bit Rate:0 kb/s   Tx-Power=31 dBm   
          Sensitivity=20/200  
          Retry min limit:8   RTS thr:2347 B   Fragment thr:2346 B   
          Link Quality:117  Signal level:0  Noise level:188
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

I was looking around last night/early morning and saw something about "hotplug" being used with the firmware.  I compared the firmware size with the driver that is installed under /lib/firmware/ and they are the same size so I think it's already up to date.

---

### Post by Brunellus on 2007-02-09
something is missing here.  Where's the ESSID and so forth from iwconfig?

try

sudo iwconfig eth2 ssid any

and see what happens

---

### Post by whayong on 2007-02-09
sudo iwconfig eth2 ssid any
error : unrecognised wireless request "ssid"

Did I do something wrong?

---

### Post by Brunellus on 2007-02-09
sorry.  

sudo iwconfig eth2 essid any

---

### Post by whayong on 2007-02-09
No problem, 

sudo iwconfig eth2 essid any
brings me back to ~$
 Nothing came out :(

---

### Post by Brunellus on 2007-02-09
silence means the program executed properly.  post the output of iwconfig

---

### Post by whayong on 2007-02-09
iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11b/g  ESSID:"wireless2"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0F:3D:62:09:59   
          Bit Rate:11 Mb/s   Tx-Power=31 dBm   Sensitivity=20/200  
          Retry min limit:8   RTS thr:2347 B   Fragment thr:2346 B   
          Link Quality=244/0  Signal level=-54 dBm  Noise level=-31 dBm
          Rx invalid nwid:0  Rx invalid crypt:60  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


I should say I'm at work right now.  We use WEP with static IP.  I know a static IP that I can use and the WEP key.  At home however, I use WPA with auto IP.  I am not able to connect to either one........ yet.

I'm using a flash drive to transfer the logs, lol.

---

### Post by Brunellus on 2007-02-09
> **whayong said:**
> iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11b/g  ESSID:"wireless2"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0F:3D:62:09:59   
          Bit Rate:11 Mb/s   Tx-Power=31 dBm   Sensitivity=20/200  
          Retry min limit:8   RTS thr:2347 B   Fragment thr:2346 B   
          Link Quality=244/0  Signal level=-54 dBm  Noise level=-31 dBm
          Rx invalid nwid:0  Rx invalid crypt:60  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


I should say I'm at work right now.  We use WEP with static IP.  I know a static IP that I can use and the WEP key.  At home however, I use WPA with auto IP.  I am not able to connect to either one........ yet.

I'm using a flash drive to transfer the logs, lol.
now we've got progress.  you can at least see the wireless access points.

---

### Post by whayong on 2007-02-09
> **Brunellus said:**
> now we've got progress.  you can at least see the wireless access points.

Next step? lol!

---

### Post by Brunellus on 2007-02-09
> **whayong said:**
> Next step? lol!
next step is getting an IP.  where was it that you had dhcp again?

---

### Post by whayong on 2007-02-09
IP that I can use here at work is 192.168.0.201
DHCP is at home

BTW, I installed Network manager via add/remove programs.  It still doesn't detect the AP

---

### Post by Brunellus on 2007-02-09
> **whayong said:**
> IP that I can use here at work is 192.168.0.201
DHCP is at home

BTW, I installed Network manager via add/remove programs.  It still doesn't detect the AP
I've never used network manager.  keep it to the terminal.  what happens when you

sudo iwlist eth2 scanning

---

### Post by whayong on 2007-02-09
sudo iwlist eth2 scanning

eth2      Scan completed :
          Cell 01 - Address: 00:0F:3D:62:09:59
                    ESSID:"wireless2"
                    Mode:Master
                    Encryption key:on
                    Frequency:2.462 GHz (Channel 11)
                    Quality:24/0  Signal level:-53 dBm  Noise level:-77 dBm

---

### Post by whayong on 2007-02-09
OK.  I followed this [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

I can ping the router
I can ping 216.239.57.99
I CANNOT ping [www.google.com](www.google.com)

According to that guide I would then have a dns nameserver problem.  What's that and how do I fix it?

---

### Post by Brunellus on 2007-02-09
you'd have to add the router as the nameserver in resolv.conf  

I'm not near a linux box atm, so I can't really talk you through it.

---

### Post by whayong on 2007-02-09
ok.  I appreciate all your help brunellus.  Can you post or perhaps pm/email me when you get a chance to get on linux?  

Question: Would I have to add all the routers I will be accessing into that resolv.conf
?  I mean, what happens when you're in a hotspot?  

Be back in 30 min. going for lunch.  If you're in so cal, I owe you lunch as well.

---

### Post by whayong on 2007-02-09
I ran into this [http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/](http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/) 

Are these the steps I need to do for the dns nameserver problem?

---

### Post by Brunellus on 2007-02-09
> **whayong said:**
> I ran into this [http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/](http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/) 

Are these the steps I need to do for the dns nameserver problem?
not at all.  that's local DNS caching, which is only useful if you actually DO get connected to the network, generally.

all you'd need to do is add the nameserver to resolv.conf  and you should be good.

---

### Post by whayong on 2007-02-09
How about this?

[http://www.opendns.com/start/ubuntu.php](http://www.opendns.com/start/ubuntu.php)

Will that do the trick?  Or would I have to reconfigure my router to use that DNS?  My current ISP is Verizon DSL.

---

### Post by whayong on 2007-02-10
Well, I'm stuck.  I don't know if I can go any further.  I really don't want to switch back to windows, lol

---

### Post by Brunellus on 2007-02-10
if you're using the GUI, configure the IP of the router as the default DNS (in your fixed-IP network).

Under DHCP, that should be done for you when the router assigns an IP to your host.

You should be in good shape now.   The other DNS things you've been googling up don't really apply--one of them is for local caching of DNS requests, which makes sense if you're serving up lots of DNS requests on your local networ.  The other is an alternative set of root DNS servers.  Interesting (I'll see about trying it out one of these days) but again not relevant., since that's one network hop away from where you are now.

If you still can't get any love from dhclient, it may just be that the wireless driver is wonky.  I've just had that problem (I think) in the latest edgy and feisty kernels on my old Orinoco wireless card.  Kernel 2.6.17 (stock edgy, right off the install disk) seems to work, but subsequent kernels are less than helpful--interface goes up, but dhclient keeps failing.

---

### Post by whayong on 2007-02-10
definitely not getting any love from DHCP at my home network.  I'm using WPA here as well.

---

