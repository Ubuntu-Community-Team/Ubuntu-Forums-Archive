---
title: "ndsiwrapper &amp; zd1211B for wireless"
date: 2006-10-24
forum: Networking &amp; Wireless
---

### Post by somersetsimon on 2006-10-24
I haven't managed to get my zd1211b card to connect to my wireless network even though it seems to see the network ok.

[http://www.ubuntuforums.org/showthread.php?t=280176](http://www.ubuntuforums.org/showthread.php?t=280176)

As a last resort I'm going to try the windows driver with ndsiwrapper. I'm not at my linux machine at the moment so I have a few questions before I try it out at home tonight. 

Is ndsiwrapper part of the normal Ubuntu install? If not, where can I get it? Remember, I can't connect to the internet from Ubuntu! I have got the standard and alternate install CD's

How do I run ndiswrapper? 

Do I need to disble or remove my existing ZD1211B driver? how?

What driver files do I need from windows?

Should I remove Network Manager and/or wi-fi radar? If so, how?

Any information or links to other threads/wiki's would be appreciated.

---

### Post by wieman01 on 2006-10-24
Ok, I don't want to beat a dead horse, BUT your current setup seems perfectly fine. "iwconfig" shows your wireless configuration, "iwlist" recognizes your network. PLUS... "wlan0" indicates that you have installed "ndiswrapper" & deployed the native Windows driver.

So your problem is to connect PC & wireless router, right? Before we continue please answer the following questions:

1. Is the router set to DHCP? Is DHCP enabled?
2. Have you turned off encryption/authentication (WEP)?
3. MAC filtering disabled?
4. What channel (e.g. 1, 2, 3, 4, etc.) is the network running on?
5. What's the ESSID?
6. Your network card is a wireless B device, right? Is the router set to "wireless B"?

All these questions relate to your router settings. Please confirm each of them.

---

### Post by somersetsimon on 2006-10-24
> **wieman01 said:**
> Ok, I don't want to beat a dead horse, BUT your current setup seems perfectly fine. "iwconfig" shows your wireless configuration, "iwlist" recognizes your network. PLUS... "wlan0" indicates that you have installed "ndiswrapper" & deployed the native Windows driver.

So your problem is to connect PC & wireless router, right? Before we continue please answer the following questions:

1. Is the router set to DHCP? Is DHCP enabled?
2. Have you turned off encryption/authentication (WEP)?
3. MAC filtering disabled?
4. What channel (e.g. 1, 2, 3, 4, etc.) is the network running on?
5. What's the ESSID?
6. Your network card is a wireless B device, right? Is the router set to "wireless B"?

All these questions relate to your router settings. Please confirm each of them.

1. Yes, yes
2. Yes
3. Yes
4. 10
5. BridgeNet
6. The USB wireless device supposed to be b/g. The router is set to b/g. My windows laptop has a g card, but my Mp101 music player only receives b, so I need both ;) 

Thanks

---

### Post by wieman01 on 2006-10-24
Looks good. So please post the other stuff as well. :-)

Plus do me a favor and post the contents (open the files with a text editor) of whatever is in this folder:
> cd /etc/Wireless/

---

### Post by az on 2006-10-24
> **somersetsimon said:**
> I haven't managed to get my zd1211b card to connect to my wireless network even though it seems to see the network ok.

[http://www.ubuntuforums.org/showthread.php?t=280176](http://www.ubuntuforums.org/showthread.php?t=280176)

As a last resort I'm going to try the windows driver with ndsiwrapper. I'm not at my linux machine at the moment so I have a few questions before I try it out at home tonight. 

Is ndsiwrapper part of the normal Ubuntu install? If not, where can I get it? Remember, I can't connect to the internet from Ubuntu! I have got the standard and alternate install CD's

How do I run ndiswrapper? 

Do I need to disble or remove my existing ZD1211B driver? how?

What driver files do I need from windows?

Should I remove Network Manager and/or wi-fi radar? If so, how?

Any information or links to other threads/wiki's would be appreciated.

If your zd1211 device does ot work with the native linux drivers, you need to get them from upstream.  Download them from here:
[http://zd1211.ath.cx/download/](http://zd1211.ath.cx/download/)
Use the last one, the version 83.  It works for my zd1211B device.

Kernel 2.6.18 will have a re-written version of that driver and it is a bit early to get into that.  Install build-essential and linux-headers-386 from the install cd before you compile the driver.

Those packages are on the install cd - just insert the cd when you are at the Ubuntu desktop and the package manager will start.  Search for and install those packages.

If it still does not work, install ndiswrapper-utils in the same way (from the cd - you don't need to compile anything)  You will need to blacklist the native zd1211 driver that gets loaded when you insert your device.  You will also need the .inf file that came with your device on the windows cd.

---

### Post by wieman01 on 2006-10-24
Hi Azz, 

Apparently "ndiswrapper" has been installed already.

Somersetsimon, 

To blacklist the driver do this:
> echo 'blacklist **[COLOR="Red"]zd1211[/COLOR]**' | sudo tee -a /etc/modprobe.d/blacklist
If I am not mistaken...

---

### Post by somersetsimon on 2006-10-24
What other stuff did I miss?

We'll have to wait a few hours before I can get on to my Linux machine at home.

BTW, I should have mentioned that the USB device works perfectly well in g mode on the same machine, picks up the correct IP and connects to everything.

---

### Post by wieman01 on 2006-10-24
> **somersetsimon said:**
> What other stuff did I miss?

We'll have to wait a few hours before I can get on to my Linux machine at home.

BTW, I should have mentioned that the USB device works perfectly well in g mode on the same machine, picks up the correct IP and connects to everything.
Sorry, got confused. No other stuff to be posted. Just the last thing mentioned.

What USB device? Do you have 2 wireless devices? Or are you saying that this one works perfectly in G mode but not in mixed or B?

---

### Post by somersetsimon on 2006-10-24
I got my driver from the manufacturer website:

[http://www.bluenext.co.uk/products/wifidangle.html](http://www.bluenext.co.uk/products/wifidangle.html)

It's odd that the text on the page talks about the vt6656 chip, but the driver info only mentions ZD1211(b) and the windows driver that it uses identifies itself as zd1211b.

I followed the installation instructions from the pdf on the website. I thought I was installing a Linux driver, rather than installing a windows one under ndsiwrapper. Does 'wlan0' mean a windows driver has been used?

---

### Post by wieman01 on 2006-10-24
> **somersetsimon said:**
> Does 'wlan0' mean a windows driver has been used?
Definitely yes. "ndiwrapper" together with the native Windows driver. If you like it or now.

---

### Post by somersetsimon on 2006-10-24
Perhaps I was adding to your confusion.

I have a laptop running XP with a built in g adaptor

I have a desktop that dual boots XP and Ubuntu. This desktop has a USB wireless adaptor that claims to be b/g. It operates in g mode in XP on that machine. My router is set up to operate as mixed b and g and I have successfully connected b and g devices to it.

---

### Post by somersetsimon on 2006-10-24
Well, you learn something new everyday :-)

I guess I should try disabling ndsiwrapper and running with an actual Linux driver.

---

### Post by somersetsimon on 2006-10-24
> **wieman01 said:**
> Definitely yes. "ndiwrapper" together with the native Windows driver. If you like it or now.

:-k When I checked Synaptic, ndsiwrapper wasn't installed. I'm sure I was using a real Linux driver...

Anyway, I tried installing the latest Linux driver as suggested elsewhere in the thread. I also had a go with ndiswrapper and the windows driver. Both resulted in the same situation as before.

I.e. the wireless network is visible, but I just can't connect. The weird thing is that when I use something like wi-fi radar, I get a message telling me that I have acquired an IP address, but the router shows no log of that. WHen I use the same machine and adaptor with XP I get allocated an IP address, but that is recorded by the router.

It definitely seems like the driver is not the problem. I'm completely lost now ](*,) 

I think I'm going to give up for a few days, then either try a clean install of 6.06 or even 6.10 :(

---

### Post by wieman01 on 2006-10-24
Plus do me a favor and post the contents (open the files with a text editor) of whatever is in this folder:
> cd /etc/Wireless/
That done, just don't give up yet. I suspect that there is a problem with the "wireless channel". That why I am asking you to post the above files... Your router is running on channel 10, I am trying to figure out what your card's setting is. If it's NOT 10 then it's no surprise you cannot connect.

Also run this command please:
> iwlist scan

---

### Post by somersetsimon on 2006-10-25
> **wieman01 said:**
> Plus do me a favor and post the contents (open the files with a text editor) of whatever is in this folder:

That done, just don't give up yet. I suspect that there is a problem with the "wireless channel". That why I am asking you to post the above files... Your router is running on channel 10, I am trying to figure out what your card's setting is. If it's NOT 10 then it's no surprise you cannot connect.

Also run this command please:

I had another go at it. When I rebooted after using ndiswrapper, I had all sorts of problems. None of the networking tools would respond and iwlist scan just hung. I decided to uninstall Network Manager, Wi-Fi radar & ndsiwrapper and just use the latest linux zd1211b driver (v83).

I almost got somewhere. When I rebooted I got the following responses:


simon@linux1:~$ cd /etc/Wireless
bash: cd: /etc/Wireless: No such file or directory

simon@linux1:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0D:54:F9:16:73
                    ESSID:"BridgeNet"
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Extra:SignalStrength=67%,LinkQuality:24%
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100

sit0      Interface doesn't support scanning.


simon@linux1:~$ iwconfig

eth0      no wireless extensions.

wlan0     802.11b/g NIC  ESSID:"BridgeNet"
          Mode:Managed  Frequency=2.457 GHz  Access Point: 00:0D:54:F9:16:73
          Bit Rate:54 Mb/s
          Retry:off   RTS thr=2432 B   Fragment thr:off
          Power Management:off
          Link Quality=88/100  Signal level=56/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:1
          Tx excessive retries:265218  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

This is the first time that an access point was found. Both the router and the adaptor appear to be using channel 10. Looking good! I decided to ping my router

simon@linux1:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.3 icmp_seq=10 Destination Host Unreachable
From 192.168.1.3 icmp_seq=11 Destination Host Unreachable
From 192.168.1.3 icmp_seq=12 Destination Host Unreachable
From 192.168.1.3 icmp_seq=14 Destination Host Unreachable
From 192.168.1.3 icmp_seq=15 Destination Host Unreachable
From 192.168.1.3 icmp_seq=16 Destination Host Unreachable
64 bytes from 192.168.1.1: icmp_seq=18 ttl=64 time=14.3 ms
64 bytes from 192.168.1.1: icmp_seq=31 ttl=64 time=14.3 ms
64 bytes from 192.168.1.1: icmp_seq=32 ttl=64 time=14.2 ms
64 bytes from 192.168.1.1: icmp_seq=40 ttl=64 time=15.9 ms
64 bytes from 192.168.1.1: icmp_seq=60 ttl=64 time=14.3 ms
64 bytes from 192.168.1.1: icmp_seq=62 ttl=64 time=14.4 ms
64 bytes from 192.168.1.1: icmp_seq=63 ttl=64 time=14.3 ms
64 bytes from 192.168.1.1: icmp_seq=96 ttl=64 time=16.0 ms
64 bytes from 192.168.1.1: icmp_seq=101 ttl=64 time=15.9 ms
64 bytes from 192.168.1.1: icmp_seq=103 ttl=64 time=14.4 ms
64 bytes from 192.168.1.1: icmp_seq=104 ttl=64 time=17.6 ms
64 bytes from 192.168.1.1: icmp_seq=107 ttl=64 time=15.9 ms
64 bytes from 192.168.1.1: icmp_seq=108 ttl=64 time=14.5 ms
64 bytes from 192.168.1.1: icmp_seq=116 ttl=64 time=14.4 ms

--- 192.168.1.1 ping statistics ---
117 packets transmitted, 14 received, +6 errors, 88% packet loss, time 116157ms
rtt min/avg/max/mdev = 14.251/15.083/17.659/1.004 ms, pipe 3
simon@linux1:~$


Not sure what that all means. I entered 192.168.1.1 in Firefox. It waited a long time saying 'connecting to 192.168.1.1' then timed out.

I took a look at the log in my router and it said something like IP offered to 192.168.1.3 (?) When I connect with the same wireless device in XP the router gives the same message, but then follows with 192.168.1.3 login.

I think I'm making progress. My wireless adaptor is making contact with the router, but can't login.

---

### Post by wieman01 on 2006-10-25
Great, man. You are there. You're connected for sure! Solution will be to disable "ipv6". Give me a few minute, I'll get back to you soon. Piece of cake.

---

### Post by somersetsimon on 2006-10-25
This is the router log when I tried to connect with XP:

2006.10.24 22:38:30 192.168.1.3 login success
2006.10.24 22:38:30 192.168.1.2 forced logout
2006.10.24 22:38:14 Duplicate user login from 192.168.1.3
2006.10.24 22:38:13 Duplicate user login from 192.168.1.3
2006.10.24 22:35:04 sending ACK to 192.168.1.3
2006.10.24 22:35:03 sending OFFER to 192.168.1.3

and this is the log when I tried to connect with Ubuntu:

2006.10.25 07:49:47 sending ACK to 192.168.1.3
2006.10.25 07:49:45 sending OFFER to 192.168.1.3
2006.10.25 07:49:27 sending OFFER to 192.168.1.3
2006.10.25 07:48:41 sending OFFER to 192.168.1.3
2006.10.25 07:48:00 sending OFFER to 192.168.1.3
2006.10.25 07:44:39 sending ACK to 192.168.1.3
2006.10.25 07:44:33 sending OFFER to 192.168.1.3
2006.10.25 07:43:45 sending OFFER to 192.168.1.3
2006.10.25 07:43:21 sending OFFER to 192.168.1.3
2006.10.25 07:42:02 sending OFFER to 192.168.1.3
2006.10.25 06:57:30 sending OFFER to 192.168.1.3

---

### Post by somersetsimon on 2006-10-25
I hope so! I'm sure I did the ipv6 bit a few days ago...

Apart from using Firefox to connect to a web page, are there any other tests to make sure I'm connected?

I'm not going to be on the Ubuntu machine until about 7pm uk time (another 9 hours) :-(

---

### Post by wieman01 on 2006-10-25
To disable "ipv6" globally, follow this: [http://www.ubuntuforums.org/showthread.php?t=87798&highlight=ipv6]("http://www.ubuntuforums.org/showthread.php?t=87798&highlight=ipv6")

To disable it in Firefox, do this: 
1. URL field, type:
> about:config
2. Filter, search for "ipv6".
3. Right-click on "network.dns.disableIPv6" and choose "Toggle".

That's it. Happy browsing. Let me know how you go.

---

### Post by wieman01 on 2006-10-25
To further test your connection, do this:
> route
> iwconfig
Please post the results.

---

### Post by Erik. on 2006-10-25
Hi Wieman,
I have read someposts of you and i read that many people that you helped the wireless internet works.
Could you please help me?
This is my result:
```

root@ejp:~# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        *               255.255.255.0   U     0      0        0 eth1
default         SpeedTouch.lan  0.0.0.0         UG    0      0        0 eth1
root@ejp:~# iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

---

### Post by wieman01 on 2006-10-25
> **Erik. said:**
> Hi Wieman,
I have read someposts of you and i read that many people that you helped the wireless internet works.
Could you please help me?
Erik:

I am willing to help but please don't hijack other people's threads. I am trying to help someone here... So please open a new thread & send me the link. Out of courtesy... :-)

---

### Post by Erik. on 2006-10-25
I am very sorry!!! i have opend my own threat
[http://ubuntuforums.org/showthread.php?t=284216](http://ubuntuforums.org/showthread.php?t=284216)

---

### Post by somersetsimon on 2006-10-25
> **wieman01 said:**
> To further test your connection, do this:


Please post the results.

simon@linux1:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 wlan0
default         router          0.0.0.0         UG    0      0        0 wlan0
simon@linux1:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g NIC  ESSID:"BridgeNet"
          Mode:Managed  Frequency=2.457 GHz  Access Point: 00:0D:54:F9:16:73
          Bit Rate:54 Mb/s
          Retry:off   RTS thr=2432 B   Fragment thr:off
          Power Management:off
          Link Quality=96/100  Signal level=60/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:40
          Tx excessive retries:64850  Invalid misc:0   Missed beacon:0

simon@linux1:~$


I disabled ipv6 (following all the instructions you posted), but Firefox still can't access anything.

WHen I checked in network devices it told me that I was connected to the right IP address and data was passing between the router and the pc.

---

### Post by DarkN00b on 2006-10-25
If you're interested, the ZD1211 driver source code is available in the repos. All it would take is a quick compile to get a Linux native driver.

---

### Post by wieman01 on 2006-10-25
But there is no other wireless tool (wifi-radar, gnome-network-manager, etc.) installed? And you have not configured your firewall, correct (off by default)?

---

### Post by wieman01 on 2006-10-25
Second thing: Are you behind a proxy?

---

### Post by somersetsimon on 2006-10-26
All the other wi-fi tools have been uninstalled.
In terms of proxies and firewalls, do you mean in ubuntu? The router firewall is on. I haven't intentionally set up proxies anywhere. Also, XP connects through the same device without any additional set up

---

### Post by wieman01 on 2006-10-26
Ok, I was referring to the Ubuntu firewall (IP tables). Another problem could be that router & wireless adapter don't have the same transfer rate (either B or G). 

Could you make sure that both parts run on either B or G, but not mixed?

_**EDIT:**_
Just to test the network. I know you need both (MP3 player). But set the router to G only & try to reconnect.

---

### Post by somersetsimon on 2006-10-26
I'm in work now, so I can't test anything. What are IP tables?

Thanks again for your help

Simon

---

### Post by wieman01 on 2006-10-26
IP tables are the the firewall filters... They are built in the kernel but have all ports open by default. So don't worry about them for the moment if you have not configured them. 

See you later then!

---

### Post by somersetsimon on 2006-10-26
OK, what should I be worrying about then?

:-)

---

### Post by Trafficboy268 on 2006-10-26
Somersetsimon, I'm no expert but I have been having problems playing around with my USB zd1211 wifi adapator.  What I found was my DNS wasn't working (Firefox timing out) and the solution was adding 127.0.0.1 to the DNS list in Systems > Administration > Networking "DNS Tab".  Not sure why this is but worked for me -maybe someone can shed someone light on this.

Hope this helps

---

### Post by wieman01 on 2006-10-26
Tested the wireless B/G thing?

---

### Post by wieman01 on 2006-10-26
One more thing that you can try... Blacklist the Linux driver (if you have installed it):
> echo 'blacklist [COLOR="Red"]ZD1211B[/COLOR]' | sudo tee -a /etc/modprobe.d/blacklist
Then restart the system & try again.

---

### Post by somersetsimon on 2006-10-26
Yes, tried that, but it didn't help

---

### Post by somersetsimon on 2006-10-26
I'm on!!!!

I did a networking restart and got a ip offer & ack.

I'm not 100% sure whether the b/g was connected. I'll check that.

Thanks for all your help. You're a star! :-)

---

### Post by somersetsimon on 2006-10-26
Cancel the party...

Put the kids to bed, came back down and the wireless network was completely dead. COuldn't even get the light on the device to come back on :-(

Why is this so difficult???????

---

### Post by wieman01 on 2006-10-26
> **somersetsimon said:**
> Cancel the party...

Put the kids to bed, came back down and the wireless network was completely dead. COuldn't even get the light on the device to come back on :-(

Why is this so difficult???????
Hello Simon, 

Want to resolve the remaining issues by chat? My AIM account is "wieman001" (2 zeros). I will be online tonight (Hong Kong time) as well as tomorrow morning. Perhaps that's a better way of resolving it.

Piece of cake now. We have got it going once, we'll do it again. 

One question though: Did the light turn off after you had blacklisted the driver?

---

### Post by wieman01 on 2006-10-26
PLUS... Please post "interfaces" so that I see what's been configured there:
> sudo gedit /etc/network/interfaces

---

### Post by wieman01 on 2006-10-26
And my last question: Do you have a hardware switch for your wireless adapter? If the light is off, perhaps you have to switch on the device...

---

### Post by somersetsimon on 2006-10-27
Thanks for the offer, but I'm about to go away for a few days. When I come back I might do a clean install of Dapper or Edgy and have another go from scratch.

Cheers

Simon

---

### Post by somersetsimon on 2006-11-02
OK, I'm back!

I did a clean install of Edgy to see if that would help, but I get stuck at the same point. I installed  ndiswrapper and used the windows driver for my zd1211b card. Ndsiwrapper tells me that the hardware and driver is installed.

I did a /etc/init.d/networking restart

Edgy calls the card eth1, instead of wlan0, but I still get the situation...

simon@linux1:~$ iwconfig eth1
eth1      802.11g zd1211  ESSID:"BridgeNet"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:0D:54:F9:16:73   
          Bit Rate=11 Mb/s   
          Link Quality=42/100  Signal level=60/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

simon@linux1:~$ ping 192.168.1.1
connect: Network is unreachable

I removed everything from my interfaces file and Network Manager.  This almost worked. When I right-clicked on nm, it showed me the ssid of my wireless network, so I clicked that to try and connect. I got some little blue swirls and a message saying 'trying to connect', but it couldn't connect.

When I plug in an ethernet cable, I can connect instantly, so that maybe elimates some router issues. There is no encryption & no Mac filtering on the router.

I still don't understand why Ubuntu can see and identify the network, but can't connect.

---

### Post by wieman01 on 2006-11-02
I would not used NetworkManager in the first place. I would rather edit "/etc/network/interfaces" and start with the easiest possible setup: DHCP, wireless security (e.g. WEP) turned off. But I see that's the case.

My recommendation:

1. Uninstall NetworkManager.
2. Post "interfaces".
3. Make sure "interfaces" includes "wlan0".
4. Then do a scan:
> iwlist scan
The existence of "eth1" suggests that the native Linux driver is still active. Have you blacklisted it in the first place? You should not run the Linux driver & "ndiswrapper" at a time. They will conflict.

---

### Post by somersetsimon on 2006-11-02
I'm away from my machine now, but I'll answer the questions as best I can.

1) I started with the simple system (i.e. no Network Manager, just using terminal commands)

2) I first blacklisted the built-in zd1211 driver and installed the latest release (r83) of the zd1211b Linux driver. This driver seemed ok and I was able to scan and find my wireless network, but not connect.

3) Just in case, I blacklisted that driver and installed the windows one with ndiswrapper. That also seemed ok and reported that the driver and hardware were present. That also allowed me to scan and see the network, but still couldn't connect.

4) Under Dapper, the Linux driver and the windows driver both bring up the wireless connection as wlan0, but in Edgy, they both call it eth1. 

5) iwlist scan picks up my essid with the correct channel and iwconfig also identifies the same

6) Is there a terminal command for uninstalling network manager, or could I just use Synaptic? What do you think the problems are with Network Manager? Some users seems to think that solves their problems? I'm going to start another thread just on Network Manager to see if I can get more info

Thanks again for your input

Simon

---

### Post by wieman01 on 2006-11-02
Ok, I was not aware that Edgy will refer to "ndiswrapper" as "eth1". To reconfirm that please check the contents of:
> gedit /etc/modprobe.d/ndiswrapper
This is where the alias hides.

To uninstall it do:
> sudo apt-get remove network-manager network-manager-gnome
Then restart your PC.

It would help if your posted your scan results & the contents of "/etc/network/interfaces". Then we should be able to hook you up (security & MAC filtering turned off as you have mentioned).

Talk to you later then!

---

### Post by somersetsimon on 2006-11-02
I removed nm.

I now have:

simon@linux1:~$ cat /etc/modprobe.d/ndiswrapper
alias wlan0 ndiswrapper
simon@linux1:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp
#wireless-essid BridgeNet

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp


#iface eth0 inet dhcp

#auto eth0

iface wlan0 inet dhcp
wireless-essid BridgeNet

The help for ndiswrapper says that ndiswrapper -m will always put 'wlan0' in the alias file, but Edgy wants to call the wireless network eth1??

I've tried wlan0 and eth1 in both files, but doesn't make any differnce. I can't get any response from the network card now. What next? I guess I'm starting from scratch again now.

---

### Post by wieman01 on 2006-11-02
Edgy now calls it "eth1" as I have seen in other threads. 

Can you post the scan results please ("eth1")? And also "iwconfig":
> iwlist eth1 scan
> iwconfig
The problem may be the channel (= network frequency)...

---

### Post by somersetsimon on 2006-11-03
simon@linux1:~$ iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:0D:54:F9:16:73
                    ESSID:"BridgeNet"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:10
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=100/100  
                    Extra: Last beacon: 96ms ago

simon@linux1:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      802.11g zd1211  ESSID:"BridgeNet"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   
          Link Quality=93/100  Signal level=91/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

simon@linux1:~$

---

### Post by wieman01 on 2006-11-03
The channel is no problem... 
> Channel 10 = Frequency:2.457
The wireless device is capable of B and G, isn't it? And have you downloaded the latest(!) Windows driver for the device?

Please also do this & post the result:
> lsusb -v
Also restart the network once again...
> sudo /etc/init.d/networking restart
Post the output.

I am beginning to think that this is a driver issue. I have seen other similar posts & all users face the same situation: Scanning works fine, but the adapter won't connect.

_**EDIT 1:**_
Please also include:
> dmesg
_**EDIT 2:**_
Launchpad: [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/68706]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/68706")

_**EDIT 3:**_
There is a section on "ndiswrapper"... Thread is a week old: [http://ubuntuforums.org/showthread.php?t=283250]("http://ubuntuforums.org/showthread.php?t=283250")

---

### Post by somersetsimon on 2006-11-03
This probably sounds like a stupid question, but how do you capture the whole output from these commands? The output is bigger than the terminal window. From my old unix days, I thought I could redirect the output to a file with something with lsusb -v > tmp.txt, but that didn't work.

Also, once I have a big chunk of text that I want to put in a message, then how do I put it in a little box that you can scroll?

Thanks

---

### Post by wieman01 on 2006-11-03
Good old Unix days... :-) Yeah, you're on the right track. Try this instead:
> lsusb -v >> tmp.txt
That's the pipe.

_**EDIT:**_
And when you reply you can "wrap" the text... there is something called "html-wrap" or "code-wrap" in the tool bar when you reply to a message.

---

### Post by wieman01 on 2006-11-03
Aeh... And by the way... Make sure the Ethernet cable is unplugged while you're trying to connect via wireless. I see you have commented "eth0" but just in case.

---

### Post by somersetsimon on 2006-11-03
> **wieman01 said:**
> Good old Unix days... :-) Yeah, you're on the right track. Try this instead:

That's the pipe.

_**EDIT:**_
And when you reply you can "wrap" the text... there is something called "html-wrap" or "code-wrap" in the tool bar when you reply to a message.

Cool :-D 
Here's lsusb -v

[HTML]Bus 005 Device 004: ID 0930:6533 Toshiba Corp. 512M USB Stick
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0930 Toshiba Corp.
  idProduct          0x6533 512M USB Stick
  bcdDevice            1.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval             255
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval             255
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10

Bus 005 Device 002: ID 0ace:1215 ZyDAS 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol       255 Vendor Specific Protocol
  bMaxPacketSize0        64
  idVendor           0x0ace ZyDAS
  idProduct          0x1215 
  bcdDevice           48.10
  iManufacturer          16 
  iProduct               32 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           46
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           4
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1

Bus 005 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval              12

Bus 004 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255

Bus 003 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255

Bus 002 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255

Bus 001 Device 002: ID 1241:1111 Belkin Mouse
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x1241 Belkin
  idProduct          0x1111 Mouse
  bcdDevice            1.00
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Devices
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.00
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      52
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               8

Bus 001 Device 003: ID 04f2:0116 Chicony Electronics Co., Ltd KU-2971 German Keyboard
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x04f2 Chicony Electronics Co., Ltd
  idProduct          0x0116 KU-2971 German Keyboard
  bcdDevice            3.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Devices
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      1 Keyboard
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      65
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10

Bus 001 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255[/HTML]

and dmesg

---

### Post by somersetsimon on 2006-11-03
and here's dmesg

[HTML][17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000000fef0000 (usable)
[17179569.184000]  BIOS-e820: 000000000fef0000 - 000000000fef3000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000000fef3000 - 000000000ff00000 (ACPI data)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 254MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f5b90
[17179569.184000] On node 0 totalpages: 65264
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 61168 pages, LIFO batch:15
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 IntelR                                ) @ 0x000f74d0
[17179569.184000] ACPI: RSDT (v001 IntelR MSI ACPI 0x42302e31 AWRD 0x00000000) @ 0x0fef3000
[17179569.184000] ACPI: FADT (v001 IntelR MSI ACPI 0x42302e31 AWRD 0x00000000) @ 0x0fef3040
[17179569.184000] ACPI: MADT (v001 IntelR AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x0fef6a00
[17179569.184000] ACPI: DSDT (v001 INTELR AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x4008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:8 APIC version 17
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high level)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 10000000 (gap: 0ff00000:eed00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hdd1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[17179569.184000] Detected 933.461 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179573.100000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179573.100000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[17179573.124000] Memory: 248936k/261056k available (1910k kernel code, 11596k reserved, 1070k data, 308k init, 0k highmem)
[17179573.124000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179573.204000] Calibrating delay using timer specific routine.. 1868.64 BogoMIPS (lpj=3737295)
[17179573.204000] Security Framework v1.0.0 initialized
[17179573.204000] SELinux:  Disabled at boot.
[17179573.204000] Mount-cache hash table entries: 512
[17179573.204000] CPU: After generic identify, caps: 0387fbff 00000000 00000000 00000000 00000000 00000000 00000000
[17179573.204000] CPU: After vendor identify, caps: 0387fbff 00000000 00000000 00000000 00000000 00000000 00000000
[17179573.204000] CPU: L1 I cache: 16K, L1 D cache: 16K
[17179573.204000] CPU: L2 cache: 256K
[17179573.204000] CPU serial number disabled.
[17179573.204000] CPU: After all inits, caps: 0383fbff 00000000 00000000 00000040 00000000 00000000 00000000
[17179573.204000] Checking 'hlt' instruction... OK.
[17179573.220000] SMP alternatives: switching to UP code
[17179573.220000] Freeing SMP alternatives: 16k freed
[17179573.220000] checking if image is initramfs... it is
[17179574.312000] Freeing initrd memory: 5564k freed
[17179574.312000] ACPI: Core revision 20060707
[17179574.316000] ACPI: Looking for DSDT ... not found!
[17179574.376000] CPU0: Intel Pentium III (Coppermine) stepping 0a
[17179574.376000] Total of 1 processors activated (1868.64 BogoMIPS).
[17179574.376000] ENABLING IO-APIC IRQs
[17179574.376000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179574.520000] Brought up 1 CPUs
[17179574.520000] migration_cost=0
[17179574.520000] NET: Registered protocol family 16
[17179574.520000] EISA bus registered
[17179574.520000] ACPI: bus type pci registered
[17179574.532000] PCI: PCI BIOS revision 2.10 entry at 0xfb180, last bus=1
[17179574.532000] PCI: Using configuration type 1
[17179574.532000] Setting up standard PCI resources
[17179574.552000] ACPI: Interpreter enabled
[17179574.552000] ACPI: Using IOAPIC for interrupt routing
[17179574.556000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179574.556000] PCI: Probing PCI hardware (bus 00)
[17179574.556000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179574.560000] Boot video device is 0000:00:02.0
[17179574.560000] PCI quirk: region 4000-407f claimed by ICH4 ACPI/GPIO/TCO
[17179574.560000] PCI quirk: region 4080-40bf claimed by ICH4 GPIO
[17179574.560000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179574.560000] PCI: Transparent bridge - 0000:00:1e.0
[17179574.560000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179574.592000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[17179574.596000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179574.596000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179574.596000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179574.596000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179574.596000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179574.596000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179574.596000] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179574.596000] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179574.604000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179574.604000] pnp: PnP ACPI init
[17179574.612000] pnp: PnP ACPI: found 13 devices
[17179574.612000] PnPBIOS: Disabled by ACPI PNP
[17179574.612000] PCI: Using ACPI for IRQ routing
[17179574.612000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179574.628000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[17179574.628000] PCI: Bridge: 0000:00:1e.0
[17179574.628000]   IO window: c000-cfff
[17179574.628000]   MEM window: d4000000-d40fffff
[17179574.628000]   PREFETCH window: disabled.
[17179574.628000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179574.628000] NET: Registered protocol family 2
[17179574.668000] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[17179574.668000] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[17179574.668000] TCP bind hash table entries: 4096 (order: 3, 32768 bytes)
[17179574.668000] TCP: Hash tables configured (established 8192 bind 4096)
[17179574.668000] TCP reno registered
[17179574.668000] audit: initializing netlink socket (disabled)
[17179574.668000] audit(1162536203.668:1): initialized
[17179574.668000] VFS: Disk quotas dquot_6.5.1
[17179574.668000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179574.668000] Initializing Cryptographic API
[17179574.668000] io scheduler noop registered
[17179574.668000] io scheduler anticipatory registered
[17179574.668000] io scheduler deadline registered
[17179574.668000] io scheduler cfq registered (default)
[17179574.668000] isapnp: Scanning for PnP cards...
[17179575.024000] isapnp: No Plug & Play device found
[17179575.084000] Real Time Clock Driver v1.12ac
[17179575.084000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179575.084000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179575.084000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179575.084000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179575.084000] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179575.084000] mice: PS/2 mouse device common for all mice
[17179575.088000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179575.088000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179575.088000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179575.088000] PNP: No PS/2 controller found. Probing ports directly.
[17179575.108000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179575.108000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179575.112000] EISA: Probing bus 0 at eisa.0
[17179575.112000] Cannot allocate resource for EISA slot 4
[17179575.112000] Cannot allocate resource for EISA slot 5
[17179575.112000] EISA: Detected 0 cards.
[17179575.112000] TCP bic registered
[17179575.112000] NET: Registered protocol family 1
[17179575.112000] NET: Registered protocol family 8
[17179575.112000] NET: Registered protocol family 20
[17179575.112000] Using IPI No-Shortcut mode
[17179575.112000] ACPI: (supports S0 S1 S4 S5)
[17179575.116000] Freeing unused kernel memory: 308k freed
[17179575.560000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179576.888000] Capability LSM initialized
[17179577.356000] ACPI: Fan [FAN] (on)
[17179577.368000] ACPI: Processor [CPU0] (supports 2 throttling states)
[17179577.372000] ACPI: Thermal Zone [THRM] (22 C)
[17179578.656000] ICH2: IDE controller at PCI slot 0000:00:1f.1
[17179578.656000] ICH2: chipset revision 17
[17179578.656000] ICH2: not 100% native mode: will probe irqs later
[17179578.656000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:pio
[17179578.656000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
[17179578.656000] Probing IDE interface ide0...
[17179578.944000] hda: WDC WD200EB-00CSF0, ATA DISK drive
[17179579.624000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179579.648000] Probing IDE interface ide1...
[17179580.384000] hdc: SAMSUNG CD-ROM SC-152L, ATAPI CD/DVD-ROM drive
[17179580.664000] hdd: Maxtor 6E040L0, ATA DISK drive
[17179580.724000] ide1 at 0x170-0x177,0x376 on irq 15
[17179581.460000] hda: max request size: 128KiB
[17179581.460000] hdc: ATAPI 52X CD-ROM drive, 128kB Cache, DMA
[17179581.460000] Uniform CD-ROM driver Revision: 3.20
[17179581.460000] hda: 39102336 sectors (20020 MB) w/2048KiB Cache, CHS=38792/16/63, UDMA(100)
[17179581.460000] hda: cache flushes not supported
[17179581.460000]  hda: hda1
[17179581.500000] hdd: max request size: 128KiB
[17179581.504000] hdd: 80293248 sectors (41110 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(33)
[17179581.504000] hdd: cache flushes supported
[17179581.504000]  hdd: hdd1 hdd2 < hdd5 >
[17179582.160000] usbcore: registered new driver usbfs
[17179582.160000] usbcore: registered new driver hub
[17179582.164000] USB Universal Host Controller Interface driver v3.0
[17179582.164000] ACPI: PCI Interrupt 0000:00:1f.2[D] -> GSI 19 (level, low) -> IRQ 169
[17179582.164000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179582.164000] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[17179582.168000] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[17179582.168000] uhci_hcd 0000:00:1f.2: irq 169, io base 0x0000d000
[17179582.168000] usb usb1: configuration #1 chosen from 1 choice
[17179582.168000] hub 1-0:1.0: USB hub found
[17179582.168000] hub 1-0:1.0: 2 ports detected
[17179582.276000] ACPI: PCI Interrupt 0000:00:1f.4[C] -> GSI 23 (level, low) -> IRQ 177
[17179582.276000] PCI: Setting latency timer of device 0000:00:1f.4 to 64
[17179582.276000] uhci_hcd 0000:00:1f.4: UHCI Host Controller
[17179582.276000] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
[17179582.276000] uhci_hcd 0000:00:1f.4: irq 177, io base 0x0000d400
[17179582.276000] usb usb2: configuration #1 chosen from 1 choice
[17179582.276000] hub 2-0:1.0: USB hub found
[17179582.276000] hub 2-0:1.0: 2 ports detected
[17179582.384000] ACPI: PCI Interrupt 0000:01:0b.0[A] -> GSI 22 (level, low) -> IRQ 185
[17179582.384000] PCI: Via IRQ fixup for 0000:01:0b.0, from 11 to 9
[17179582.384000] uhci_hcd 0000:01:0b.0: UHCI Host Controller
[17179582.384000] uhci_hcd 0000:01:0b.0: new USB bus registered, assigned bus number 3
[17179582.384000] uhci_hcd 0000:01:0b.0: irq 185, io base 0x0000c400
[17179582.384000] usb usb3: configuration #1 chosen from 1 choice
[17179582.384000] hub 3-0:1.0: USB hub found
[17179582.384000] hub 3-0:1.0: 2 ports detected
[17179582.492000] ACPI: PCI Interrupt 0000:01:0b.1[B] -> GSI 17 (level, low) -> IRQ 193
[17179582.492000] PCI: Via IRQ fixup for 0000:01:0b.1, from 11 to 1
[17179582.492000] uhci_hcd 0000:01:0b.1: UHCI Host Controller
[17179582.492000] uhci_hcd 0000:01:0b.1: new USB bus registered, assigned bus number 4
[17179582.492000] uhci_hcd 0000:01:0b.1: irq 193, io base 0x0000c800
[17179582.492000] usb usb4: configuration #1 chosen from 1 choice
[17179582.492000] hub 4-0:1.0: USB hub found
[17179582.492000] hub 4-0:1.0: 2 ports detected
[17179582.516000] usb 1-1: new low speed USB device using uhci_hcd and address 2
[17179582.604000] ACPI: PCI Interrupt 0000:01:0b.2[C] -> GSI 18 (level, low) -> IRQ 201
[17179582.604000] PCI: Via IRQ fixup for 0000:01:0b.2, from 11 to 9
[17179582.604000] ehci_hcd 0000:01:0b.2: EHCI Host Controller
[17179582.604000] ehci_hcd 0000:01:0b.2: new USB bus registered, assigned bus number 5
[17179582.604000] ehci_hcd 0000:01:0b.2: irq 201, io mem 0xd4001000
[17179582.604000] ehci_hcd 0000:01:0b.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179582.604000] usb usb5: configuration #1 chosen from 1 choice
[17179582.604000] hub 5-0:1.0: USB hub found
[17179582.604000] hub 5-0:1.0: 4 ports detected
[17179582.692000] usb 1-1: configuration #1 chosen from 1 choice
[17179582.936000] usb 1-2: new low speed USB device using uhci_hcd and address 3
[17179583.120000] usb 1-2: configuration #1 chosen from 1 choice
[17179583.876000] usb 5-1: new high speed USB device using ehci_hcd and address 2
[17179584.012000] usb 5-1: configuration #1 chosen from 1 choice
[17179584.012000] usbcore: registered new driver hiddev
[17179584.036000] input: HID 1241:1111 as /class/input/input1
[17179584.036000] input: USB HID v1.00 Mouse [HID 1241:1111] on usb-0000:00:1f.2-1
[17179584.052000] input: CHICONY USB Keyboard as /class/input/input2
[17179584.052000] input: USB HID v1.10 Keyboard [CHICONY USB Keyboard] on usb-0000:00:1f.2-2
[17179584.052000] usbcore: registered new driver usbhid
[17179584.052000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179584.132000] Attempting manual resume
[17179584.188000] kjournald starting.  Commit interval 5 seconds
[17179584.188000] EXT3-fs: mounted filesystem with ordered data mode.
[17179597.080000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179597.092000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179597.124000] hw_random: RNG not detected
[17179597.176000] i810_smbus 0000:00:02.0: i810/i815 i2c device found.
[17179598.716000] Linux agpgart interface v0.101 (c) Dave Jones
[17179598.808000] agpgart: Detected an Intel i815 Chipset.
[17179598.820000] agpgart: AGP aperture is 64M @ 0xd0000000
[17179598.920000] FDC 0 is a post-1991 82077
[17179599.204000] parport: PnPBIOS parport detected.
[17179599.204000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[17179599.768000] input: PC Speaker as /class/input/input3
[17179599.788000] e100: Intel(R) PRO/100 Network Driver, 3.5.10-k2-NAPI
[17179599.788000] e100: Copyright(c) 1999-2005 Intel Corporation
[17179599.788000] ACPI: PCI Interrupt 0000:01:08.0[A] -> GSI 20 (level, low) -> IRQ 209
[17179599.888000] e100: eth0: e100_probe: addr 0xd4000000, irq 209, MAC addr 00:10:DC:0E:B0:7E
[17179600.932000] ieee80211_crypt: registered algorithm 'NULL'
[17179600.936000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[17179600.936000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179601.296000] ts: Compaq touchscreen protocol output
[17179601.444000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 193
[17179601.444000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17179601.760000] intel8x0_measure_ac97_clock: measured 54769 usecs
[17179601.760000] intel8x0: clocking to 48000
[17179601.936000] zd1211rw 5-1:1.0: firmware version 4725
[17179601.980000] zd1211rw 5-1:1.0: zd1211b chip 0ace:1215 v4810 high 00-02-72 AL2230_RF pa0 g--
[17179601.980000] zd1211rw 5-1:1.0: eth1
[17179601.980000] usbcore: registered new driver zd1211rw
[17179602.224000] lp0: using parport0 (interrupt-driven).
[17179602.296000] Adding 746980k swap on /dev/disk/by-uuid/bc8512ec-673f-4f36-adfb-a5778382b40e.  Priority:-1 extents:1 across:746980k
[17179602.480000] EXT3 FS on hdd1, internal journal
[17179605.020000] ACPI: Power Button (FF) [PWRF]
[17179605.020000] ACPI: Power Button (CM) [PWRB]
[17179605.020000] ACPI: Sleep Button (CM) [SLPB]
[17179605.300000] ibm_acpi: ec object not found
[17179605.356000] pcc_acpi: loading...
[17179609.168000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179609.168000] apm: overridden by ACPI.
[17179618.932000] NET: Registered protocol family 10
[17179618.932000] lo: Disabled Privacy Extensions
[17179618.932000] IPv6 over IPv4 tunneling driver
[17179621.040000] Bluetooth: Core ver 2.8
[17179621.040000] NET: Registered protocol family 31
[17179621.040000] Bluetooth: HCI device and connection manager initialized
[17179621.040000] Bluetooth: HCI socket layer initialized
[17179621.084000] Bluetooth: L2CAP ver 2.8
[17179621.084000] Bluetooth: L2CAP socket layer initialized
[17179621.144000] Bluetooth: RFCOMM socket layer initialized
[17179621.144000] Bluetooth: RFCOMM TTY layer initialized
[17179621.144000] Bluetooth: RFCOMM ver 1.7
[17179923.664000] hdd: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179923.664000] hdd: dma_intr: error=0x40 { UncorrectableError }, LBAsect=3129431, sector=3129431
[17179923.664000] ide: failed opcode was: unknown
[17179923.664000] end_request: I/O error, dev hdd, sector 3129431
[17179923.664000] Buffer I/O error on device hdd1, logical block 391171
[17179940.320000] hdd: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179940.320000] hdd: dma_intr: error=0x40 { UncorrectableError }, LBAsect=4415, sector=4415
[17179940.320000] ide: failed opcode was: unknown
[17179940.320000] end_request: I/O error, dev hdd, sector 4415
[17179940.320000] Buffer I/O error on device hdd1, logical block 544
[17179983.692000] hdd: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179983.692000] hdd: dma_intr: error=0x40 { UncorrectableError }, LBAsect=4319, sector=4319
[17179983.692000] ide: failed opcode was: unknown
[17179983.692000] end_request: I/O error, dev hdd, sector 4319
[17179983.692000] Buffer I/O error on device hdd1, logical block 532
[17180162.144000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17180163.364000] NET: Registered protocol family 17
[17180225.904000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17180291.768000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[17180291.844000] usbcore: registered new driver ndiswrapper
[17180386.672000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17180424.896000] usb 5-3: new high speed USB device using ehci_hcd and address 3
[17180425.132000] usb 5-3: configuration #1 chosen from 1 choice
[17180425.380000] usbcore: registered new driver libusual
[17180425.472000] SCSI subsystem initialized
[17180425.488000] Initializing USB Mass Storage driver...
[17180425.488000] scsi0 : SCSI emulation for USB Mass Storage devices
[17180425.492000] usbcore: registered new driver usb-storage
[17180425.492000] USB Mass Storage support registered.
[17180425.492000] usb-storage: device found at 3
[17180425.492000] usb-storage: waiting for device to settle before scanning
[17180430.504000] usb-storage: device scan complete
[17180430.504000]   Vendor: Kingston  Model: DataTraveler 2.0  Rev: 1.00
[17180430.504000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17180430.600000] SCSI device sda: 1001472 512-byte hdwr sectors (513 MB)
[17180430.600000] sda: Write Protect is off
[17180430.600000] sda: Mode Sense: 0b 00 00 08
[17180430.600000] sda: assuming drive cache: write through
[17180430.608000] SCSI device sda: 1001472 512-byte hdwr sectors (513 MB)
[17180430.608000] sda: Write Protect is off
[17180430.608000] sda: Mode Sense: 0b 00 00 08
[17180430.608000] sda: assuming drive cache: write through
[17180430.608000]  sda: sda1
[17180430.612000] sd 0:0:0:0: Attached scsi removable disk sda
[17180430.644000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17180431.644000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17180927.128000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17180990.664000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17181552.888000] SoftMAC: Authentication timed out with 00:0d:54:f9:16:73
[17181851.008000] usb 5-3: USB disconnect, address 3
[17182449.420000] hdd: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17182449.420000] hdd: dma_intr: error=0x40 { UncorrectableError }, LBAsect=3666455, sector=3666455
[17182449.420000] ide: failed opcode was: unknown
[17182449.420000] end_request: I/O error, dev hdd, sector 3666455
[17182451.328000] hdd: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17182451.328000] hdd: dma_intr: error=0x40 { UncorrectableError }, LBAsect=3666455, sector=3666455
[17182451.328000] ide: failed opcode was: unknown
[17182451.328000] end_request: I/O error, dev hdd, sector 3666455
[17190186.108000] usb 5-3: new high speed USB device using ehci_hcd and address 4
[17190186.344000] usb 5-3: configuration #1 chosen from 1 choice
[17190186.356000] scsi1 : SCSI emulation for USB Mass Storage devices
[17190186.356000] usb-storage: device found at 4
[17190186.356000] usb-storage: waiting for device to settle before scanning
[17190188.352000] hdd: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17190188.352000] hdd: dma_intr: error=0x40 { UncorrectableError }, LBAsect=3666455, sector=3666455
[17190188.352000] ide: failed opcode was: unknown
[17190188.352000] end_request: I/O error, dev hdd, sector 3666455
[17190190.328000] hdd: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17190190.328000] hdd: dma_intr: error=0x40 { UncorrectableError }, LBAsect=3666455, sector=3666455
[17190190.328000] ide: failed opcode was: unknown
[17190190.328000] end_request: I/O error, dev hdd, sector 3666455
[17190191.368000] usb-storage: device scan complete
[17190191.368000]   Vendor: Kingston  Model: DataTraveler 2.0  Rev: 1.00
[17190191.368000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17190191.380000] SCSI device sda: 1001472 512-byte hdwr sectors (513 MB)
[17190191.380000] sda: Write Protect is off
[17190191.380000] sda: Mode Sense: 0b 00 00 08
[17190191.380000] sda: assuming drive cache: write through
[17190191.388000] SCSI device sda: 1001472 512-byte hdwr sectors (513 MB)
[17190191.388000] sda: Write Protect is off
[17190191.388000] sda: Mode Sense: 0b 00 00 08
[17190191.388000] sda: assuming drive cache: write through
[17190191.388000]  sda: sda1
[17190191.388000] sd 1:0:0:0: Attached scsi removable disk sda
[17190191.388000] sd 1:0:0:0: Attached scsi generic sg0 type 0
[17190192.252000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17191134.648000] hdd: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17191134.648000] hdd: dma_intr: error=0x40 { UncorrectableError }, LBAsect=3666455, sector=3666455
[17191134.648000] ide: failed opcode was: unknown
[17191134.648000] end_request: I/O error, dev hdd, sector 3666455
[17191136.548000] hdd: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17191136.548000] hdd: dma_intr: error=0x40 { UncorrectableError }, LBAsect=3666455, sector=3666455
[17191136.548000] ide: failed opcode was: unknown
[17191136.548000] end_request: I/O error, dev hdd, sector 3666455
[17192713.420000] hdd: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17192713.420000] hdd: dma_intr: error=0x40 { UncorrectableError }, LBAsect=3666455, sector=3666455
[17192713.420000] ide: failed opcode was: unknown
[17192713.420000] end_request: I/O error, dev hdd, sector 3666455
[17192715.312000] hdd: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17192715.312000] hdd: dma_intr: error=0x40 { UncorrectableError }, LBAsect=3666455, sector=3666455
[17192715.312000] ide: failed opcode was: unknown
[17192715.312000] end_request: I/O error, dev hdd, sector 3666455[/HTML]

---

### Post by wieman01 on 2006-11-03
"dmesg" suggests that "ndiswrapper" is installed, however, the Linux driver "zd1211rw" is active! Why is that? It seems that you have not configured "ndiswrapper" to use the Windows driver, nor blacklisted "zd1211rw"... Just thinking... Is that possible?

_**EDIT:**_
This command is useful as well:
> lshw

---

### Post by somersetsimon on 2006-11-03
> **wieman01 said:**
> "dmesg" suggests that "ndiswrapper" is installed, however, the Linux driver "zd1211rw" is active! Why is that? It seems that you have not configured "ndiswrapper" to use the Windows driver, nor blacklisted "zd1211rw"... Just thinking... Is that possible?

_**EDIT:**_
This command is useful as well:

I hadn't intentionally installed a driver called zd1211rw. I had previously blacklisted zd1211 and zd1211b. I've blacklisted zd1211rw just to be on the same side.

Here's lshw:

[HTML]linux1
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 254MB
     *-cpu
          product: Pentium III (Coppermine)
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.8.10
          size: 950MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 256KB
     *-pci
          description: Host bridge
          product: 82815 815 Chipset Host Bridge and Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: 82815 CGC [Chipset Graphics Controller]
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: 04
             size: 64MB
             width: 32 bits
             clock: 66MHz
             capabilities: vga bus_master cap_list
             configuration: driver=i810_smbus
             resources: iomemory:d0000000-d3ffffff iomemory:d4100000-d417ffff irq:5
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-network
                description: Ethernet interface
                product: 82801BA/BAM/CA/CAM Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@01:08.0
                logical name: eth0
                version: 03
                serial: 00:10:dc:0e:b0:7e
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=e100 multicast=yes
                resources: iomemory:d4000000-d4000fff ioport:c000-c03f irq:209
           *-usb:0
                description: USB Controller
                product: VT82xxxxx UHCI USB 1.1 Controller
                vendor: VIA Technologies, Inc.
                physical id: b
                bus info: pci@01:0b.0
                version: 61
                width: 32 bits
                clock: 33MHz
                capabilities: uhci bus_master cap_list
                configuration: driver=uhci_hcd
                resources: ioport:c400-c41f irq:185
              *-usbhost
                   product: UHCI Host Controller
                   vendor: Linux 2.6.17-10-generic uhci_hcd
                   physical id: 1
                   bus info: usb@3
                   logical name: usb3
                   version: 2.06
                   capabilities: usb-1.10
                   configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
           *-usb:1
                description: USB Controller
                product: VT82xxxxx UHCI USB 1.1 Controller
                vendor: VIA Technologies, Inc.
                physical id: b.1
                bus info: pci@01:0b.1
                version: 61
                width: 32 bits
                clock: 33MHz
                capabilities: uhci bus_master cap_list
                configuration: driver=uhci_hcd
                resources: ioport:c800-c81f irq:193
              *-usbhost
                   product: UHCI Host Controller
                   vendor: Linux 2.6.17-10-generic uhci_hcd
                   physical id: 1
                   bus info: usb@4
                   logical name: usb4
                   version: 2.06
                   capabilities: usb-1.10
                   configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
           *-usb:2
                description: USB Controller
                product: USB 2.0
                vendor: VIA Technologies, Inc.
                physical id: b.2
                bus info: pci@01:0b.2
                version: 63
                width: 32 bits
                clock: 33MHz
                capabilities: ehci bus_master cap_list
                configuration: driver=ehci_hcd
                resources: iomemory:d4001000-d40010ff irq:201
              *-usbhost
                   product: EHCI Host Controller
                   vendor: Linux 2.6.17-10-generic ehci_hcd
                   physical id: 1
                   bus info: usb@5
                   logical name: usb5
                   version: 2.06
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=0mA slots=4 speed=480.0MB/s
                 *-usb:0
                      description: Generic USB device
                      product: USB2.0 WLAN
                      vendor: ZyDAS
                      physical id: 1
                      bus info: usb@5:1
                      version: 48.10
                      capabilities: usb-2.00
                      configuration: driver=zd1211rw maxpower=500mA speed=480.0MB/s
                 *-usb:1
                      description: Mass storage device
                      product: DataTraveler 2.0
                      vendor: Kingston
                      physical id: 3
                      bus info: usb@5:3
                      version: 1.00
                      serial: 0605130353223
                      capabilities: usb-2.00 scsi
                      configuration: driver=usb-storage maxpower=100mA speed=480.0MB/s
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82801BA ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
        *-ide
             description: IDE interface
             product: 82801BA IDE U100
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE
             resources: ioport:f000-f00f
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   product: WDC WD200EB-00CSF0
                   vendor: Western Digital
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capacity: 18GB
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   product: SAMSUNG CD-ROM SC-152L
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   capabilities: packet
              *-disk
                   product: Maxtor 6E040L0
                   vendor: Maxtor
                   physical id: 1
                   bus info: ide@1.1
                   logical name: /dev/hdd
                   capacity: 38GB
        *-usb:0
             description: USB Controller
             product: 82801BA/BAM USB (Hub #1)
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@00:1f.2
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:d000-d01f irq:169
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb:0
                   description: Mouse
                   product: Mouse
                   vendor: Belkin
                   physical id: 1
                   bus info: usb@1:1
                   version: 1.00
                   capabilities: usb-1.00
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
              *-usb:1
                   description: Keyboard
                   product: USB Keyboard
                   vendor: CHICONY
                   physical id: 2
                   bus info: usb@1:2
                   version: 3.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-serial UNCLAIMED
             description: SMBus
             product: 82801BA/BAM SMBus
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 11
             width: 32 bits
             clock: 33MHz
             resources: ioport:5000-500f
        *-usb:1
             description: USB Controller
             product: 82801BA/BAM USB (Hub #2)
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@00:1f.4
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:d400-d41f irq:177
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-multimedia
             description: Multimedia audio controller
             product: 82801BA/BAM AC'97 Audio
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@00:1f.5
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH
             resources: ioport:d800-d8ff ioport:dc00-dc3f irq:193
  *-scsi
       physical id: 1
       bus info: scsi@2
       logical name: scsi2
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:02:72:56:58:79
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=802.11g zd1211[/HTML]

---

### Post by wieman01 on 2006-11-03
Ok, once you have blacklisted the device please restart. "lshw" tells us that the device has not been enabled, I think this has to do with the native driver & "ndiwrapper" running at the same time. 

I recall that "zd1211rw" is the new Edgy driver. You could not have know that... It's new.

Can you do the whole "ndiswrapper" procedure once again & then post this one:
> gedit /etc/modprobe.d/ndiswrapper
Need to make sure we configure the right interface (wlan0)...

_**EDIT:**_
> *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:02:72:56:58:79
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=802.11g zd1211

---

### Post by somersetsimon on 2006-11-03
> **wieman01 said:**
> Ok, once you have blacklisted the device please restart. "lshw" tells us that the device has not been enabled, I think this has to do with the native driver & "ndiwrapper" running at the same time. 

I recall that "zd1211rw" is the new Edgy driver. You could not have know that... It's new.

Can you do the whole "ndiswrapper" procedure once again & then post this one:

Need to make sure we configure the right interface (wlan0)...

_**EDIT:**_

I'm still not sure how you can make Edgy call the interface wlan0 rather than eth1. The problem with ndiswrapper -m is that is calls the alias wlan0, but Edgy calls the interface eth1...

I downloaded the latest zd1211bu from the Manufacturer's website and done the whole ndiswrapper thing. The alias file now says

alias wlan0 ndiswrapper

When I did a restart I saw something interesting. It mentions wlan0...

[HTML]Listening on LPF/eth1/00:02:72:56:58:79
Sending on   LPF/eth1/00:02:72:56:58:79
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:02:72:56:58:79
Sending on   LPF/eth1/00:02:72:56:58:79
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 20
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

[/HTML]

---

### Post by wieman01 on 2006-11-03
Ok, it appears Edgy creates a new alias for "ndiswrapper"... No problem.

Can you please make sure "interfaces" is like this:
> auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp
wireless-essid BridgeNet
Then restart the PC, and execute this command:
> route
The Ethernet cable must be unplugged, DHCP enabled.

Also post the blacklist please:
> gedit /etc/modprobe.d/blacklist
If this yields no results, we need to chat via AIM if you don't mind. We are missing something else (well, apparently). :-)

---

### Post by somersetsimon on 2006-11-03
I got it working!!!

I found a really brand new windows driver. Edgy was giving me real problems, so I reinstalled Dapper. I installed my brand new windows driver and the latest version of ndiswrapper. Ran ndiswrapper, did the modprobe thing and was connected to my network immediately !!

The update icon then popped up telling me that there were updates available, so I downloaded them and rebooted. When the system booted up, I couldn't get wlan0 to appear anywhere and couldn't get ndiswrapper to work. I think it may be something to do with the updates.

See this thread

[http://www.ubuntuforums.org/showthread.php?t=292235](http://www.ubuntuforums.org/showthread.php?t=292235)

So, I think we have solved the major problem, just need to sort out this new problem!

Thanks once again for your help and all your patience. I really grateful

Simon

---

### Post by wieman01 on 2006-11-03
Great. Reinstalling the old version of "ndiswrapper" should be a piece of cake... I'll check the other thread first.

---

### Post by wieman01 on 2006-11-03
Hello Simon, 

I have read that all your problems have been resolved... Congrats! Has been a long journey. Upgrades occasionally kill wireless but that should not be a problem anymore for us. I have "fixed" my kernel anyway so upgrade don't really have an impact on my system.

If you need help with WPA (encryption, authentication) or WEP, drop me a line. For WPA you can follow this thread:

[http://www.ubuntuforums.org/showthread.php?t=202834]("http://www.ubuntuforums.org/showthread.php?t=202834")

---

### Post by somersetsimon on 2006-11-04
> **wieman01 said:**
> Hello Simon, 

I have read that all your problems have been resolved... Congrats! Has been a long journey. Upgrades occasionally kill wireless but that should not be a problem anymore for us. I have "fixed" my kernel anyway so upgrade don't really have an impact on my system.

If you need help with WPA (encryption, authentication) or WEP, drop me a line. For WPA you can follow this thread:

[http://www.ubuntuforums.org/showthread.php?t=202834]("http://www.ubuntuforums.org/showthread.php?t=202834")


It was a long process, but I'm glad I kept at it. I think the main problem was that I assumed that, just because the driver let me see the wireless network, the driver was working correctly. You mentioned the driver version in one of your more recent posts, which got me started on the right lines. I had assumed that the driver on the manufacturer's website was current (about a year old), but I found another one on the net that was only a couple of months old and that was the one that solved the problem.
I've got a record of the location of that driver on my work computer, so when I find that on Monday, I'll write a new post explaining how I got it all working.

I think having a driver that appears to find the network, but not connect is really confusing and starts you off on the wrong searches. If the driver failed completely, then it might have been more obvious!

---

### Post by wieman01 on 2006-11-04
> **somersetsimon said:**
> I think having a driver that appears to find the network, but not connect is really confusing and starts you off on the wrong searches. If the driver failed completely, then it might have been more obvious!
I must agree. Sadly this isn't an exception, I have seen other similar posts. A nice howto for your card would be great actually. Something I could refer others to. Keep me posted.

---

