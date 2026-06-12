---
title: "Disk Check Broke my Wireless?"
date: 2007-06-18
forum: Networking &amp; Wireless
---

### Post by Sweet Mercury on 2007-06-18
I have a BCM4308 wireless card, and I've had it successfully (for the most part) running for a few weeks after installing (wrestling with?) ndiswrapper.

Last night, I booted up my laptop at a friends house, and it forced me to do my "once every 30 boots" disk-check. A minor annoyance, but no problem, right?

Unfortunately, there was a problem. After booting, I could not connect to my friend's WiFi. The wireless had been working the evening before in a Hotel, and the morning before at my home. The only thing that had changed (if it's a change) is the Disk Check.

As it stands, the wireless interface is "stuck" in roaming mode. I can click on the Network Manager icon in the system tray, and the drop down menu shows the available networks (as it normally would in roaming mode). What's more, it showed my friend's network when I was at his house, and mine in my own, so, the card is detecting and showing the correct networks.

The problem is that I cannot connect to them. They show (and I know they have) decent signal strength, but when I click on them, the changes into the "connecting" icon (swirling blue) for a few minutes, then back to the "no connection" icon.

When I open the manual network configuration, I unclick *Enable Roaming Mode*, and click the dropdown menu for "Network Name." It won't detect and show the same networks that it is doing in roaming mode! So, since I can't pick a network, I can't take it out of roaming mode. I can type in my network name, but that won't connect either.

So, any suggestions? I have an ethernet connection (and a desktop without this problem) so I can connect the laptop and access the repositories if I need to.

I've tried going through the process of installing the drivers through ndiswrapper again, but each step tells me that it's already been done.

Also, and I don't kno if this is related, but the actual configuration window for my wireless module is odd. Its title in the title-bar is way offset (pic included). I don't know whether or not that's related.

Thanks in advance for any advice.

---

### Post by Sweet Mercury on 2007-06-20
Bump?

---

### Post by killdragon on 2007-06-20
just for fun try


       sudo ifdown -a 
       sudo ifup -a


  see if that does any thing

---

### Post by Sweet Mercury on 2007-06-21
> **killdragon said:**
> just for fun try


       sudo ifdown -a 
       sudo ifup -a


  see if that does any thing

Tried it, unfortunately no change.

Here's the output:

```
mason@mason-laptop:~$ sudo ifdown -a
Password:
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 5378
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:0d:56:39:8a:df
Sending on   LPF/eth0/00:0d:56:39:8a:df
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
mason@mason-laptop:~$ sudo ifup -a
eth2: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
ath0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:0d:56:39:8a:df
Sending on   LPF/eth0/00:0d:56:39:8a:df
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

I don't know what any of that means though.

---

### Post by killdragon on 2007-06-21
Hi, I was looking around and saw some user's are using fwcutter along with nisdwrapper to 

               get their cards working have you tried that?

---

### Post by Ultra Magnus on 2007-06-21
try this - 

code:    ifconfig

identify your wifi card - if there are a few entries give them all ago
they will be called something like eth1

code: sudo ifconfig eth1 up
code: sudo eth1 scanning

If it says it can't scan or something try another entry

code: iwlist

Find the wireless network and note its "essid"
in my case belkin54g

code : sudo iwconfig eth1 essid belkin54g
code : sudo dhclient

Lots of stuff will scroll down but it should only take a few seconds if it works then hopefully you have wireless!

try 
code: ping [www.google.com](www.google.com) 
or something to see if it worked

---

### Post by Sweet Mercury on 2007-06-22
> **killdragon]Hi, I was looking around and saw some user's are using fwcutter along with nisdwrapper to get their cards working have you tried that?[/quote]

I had read, a little over a month ago when I first installed Ubuntu and discovered this wireless card problem. I'm wary of the fcutter though because it directly effects the hardware and I need the card to be able to connect under an XP boot as well. Plus, the speeds reported weren't as good.

Plus, I had it working without the cutter for almost a month, so I know it *does* work, at full speed, without it. Something I did somehow changed something. Just need to figure that out.

I'll keep it in mind if nothing else works though, thank you.

[QUOTE=Ultra Magnus said:**
> try this - 

Had a few issues. I'll break it up so you can follow what I tried.

> **Ultra Magnus said:**
> code:    ifconfig

```
mason@mason-laptop:~$ code: ifconfig
bash: code:: command not found
mason@mason-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0D:56:39:8A:DF  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 

eth0:avah Link encap:Ethernet  HWaddr 00:0D:56:39:8A:DF  
          inet addr:169.254.7.232  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:710 (710.0 b)  TX bytes:710 (710.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:90:4B:16:51:06  
          inet6 addr: fe80::290:4bff:fe16:5106/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8946 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:482006 (470.7 KiB)  TX bytes:1872 (1.8 KiB)
          Interrupt:5 Memory:faff6000-faff8000
```

This is odd, because my wireless used to be called eth1, and there was no wlan0 module. (But it worked.) I remember changing a system file entry from "eth1" to "wlan0," in hopes to fix the problem. I don't think this is the issue because it stopped working before I changed that.

Regardless, these are the four entries I got.

> **Ultra Magnus said:**
> 
identify your wifi card - if there are a few entries give them all ago
they will be called something like eth1

code: sudo ifconfig eth1 up
code: sudo eth1 scanning

If it says it can't scan or something try another entry

```
mason@mason-laptop:~$ sudo ifconfig wlan0 up
Password:
mason@mason-laptop:~$ sudo wlan0 scanning
sudo: wlan0: command not found
mason@mason-laptop:~$ sudo ifconfig eth0 up
mason@mason-laptop:~$ sudo eth0 scanning
sudo: eth0: command not found
mason@mason-laptop:~$ sodu ifconfig eth0:avah up
bash: sodu: command not found
mason@mason-laptop:~$ sudo ifconfig eth0:avah up
SIOCSIFFLAGS: Cannot assign requested address
mason@mason-laptop:~$ sudo ifconfig lo up
mason@mason-laptop:~$ sudo lo scanning
sudo: lo: command not found
```

I tried the wireless card first, obviously a no-go. I went down the list, and none of them worked. Did I just do something wrong?

Also 'eth1,' what the card used to be, didn't work either.

> **Ultra Magnus said:**
> code: iwlist

Find the wireless network and note its "essid"
in my case belkin54g

```
mason@mason-laptop:~$ iwlist
Usage: iwlist [interface] scanning
              [interface] frequency
              [interface] channel
              [interface] bitrate
              [interface] rate
              [interface] encryption
              [interface] key
              [interface] power
              [interface] txpower
              [interface] retry
              [interface] ap
              [interface] accesspoints
              [interface] peers
              [interface] event
mason@mason-laptop:~$
```

I tried to press on, but this doesn't look like a list of available networks. Is this what the *iwlist* is supposed to look like?

> **Ultra Magnus said:**
> code : sudo iwconfig eth1 essid belkin54g
code : sudo dhclient

Lots of stuff will scroll down but it should only take a few seconds if it works then hopefully you have wireless!

try 
code: ping [www.google.com](www.google.com) 
or something to see if it worked

Thanks for the help so far. I didn't try the rest because it seemed that something was amiss.

---

### Post by Ayuthia on 2007-06-22
Ultra Magnus meant to say was to use:
iwlist scan

This will run through and list all the wireless sites that it sees.

By the way, the last steps of using eth1--use wlan0 instead.  The last two steps work if the network you are connecting is not secured.

---

### Post by Sweet Mercury on 2007-06-22
> **Ayuthia said:**
> Ultra Magnus meant to say was to use:
iwlist scan

This will run through and list all the wireless sites that it sees.

By the way, the last steps of using eth1--use wlan0 instead.  The last two steps work if the network you are connecting is not secured.

Ah, well that gave me what I expected to be the output from that command. Still not working though:

```
mason@mason-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0D:56:39:8A:DF  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 

eth0:avah Link encap:Ethernet  HWaddr 00:0D:56:39:8A:DF  
          inet addr:169.254.7.232  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:710 (710.0 b)  TX bytes:710 (710.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:90:4B:16:51:06  
          inet6 addr: fe80::290:4bff:fe16:5106/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15357 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:810826 (791.8 KiB)  TX bytes:1872 (1.8 KiB)
          Interrupt:5 Memory:faff6000-faff8000 

mason@mason-laptop:~$ sudo ifconfig wlan0 up
Password:
mason@mason-laptop:~$ sudo wlan0 scanning
sudo: wlan0: command not found
mason@mason-laptop:~$ wlan0 scanning
bash: wlan0: command not found
mason@mason-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:12:17:38:C6:26
                    ESSID:"linksys"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:81/100  Signal level:-44 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

mason@mason-laptop:~$ sudo iwconfig wlan0 essid linksys
mason@mason-laptop:~$ sudo dhclient
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:90:4b:16:51:06
Sending on   LPF/wlan0/00:90:4b:16:51:06
Listening on LPF/eth0/00:0d:56:39:8a:df
Sending on   LPF/eth0/00:0d:56:39:8a:df
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 192.168.1.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.106 -- renewal in 35517 seconds.
mason@mason-laptop:~$ ping www.google.com
ping: unknown host www.google.com
mason@mason-laptop:~$ 
```

Does that have anything to do with *sudo wlan0 scanning* code bringing up an error? It still wouldn't connect to the network or show the network in manual configuration.

---

### Post by Ayuthia on 2007-06-22
The 'sudo wlan0 scanning' does not hurt anything because you are telling it to execute wlan0 and it does not exist as a file.

As for where you are at right now, it is beyond my knowledge.  Sorry about that.  I am sure that someone here would know the answer though.  It does seem that you are getting closer though.

From what I recall, the wlan0 comes from /etc/modprobe.d/ndiswrapper.  You could go and update that file (gksudo gedit /etc/modprobe.d/ndiswrapper) and change wlan0 to eth1.  You would have to restart and you should be back to eth1.  wlan0 should work for you though.  Why the name change occurred is something I am still trying to understand.  I had this happen to and I just updated my /etc/modprobe.d/ndiswrapper on my 32-bit side and it seems to be working fine under eth1 again.  I left my 64-bit side alone and it just had it's file check and it still kept it at eth1.

Sorry I can't help you further.

---

### Post by Sweet Mercury on 2007-06-22
> **Ayuthia said:**
> The 'sudo wlan0 scanning' does not hurt anything because you are telling it to execute wlan0 and it does not exist as a file.

As for where you are at right now, it is beyond my knowledge.  Sorry about that.  I am sure that someone here would know the answer though.  It does seem that you are getting closer though.

From what I recall, the wlan0 comes from /etc/modprobe.d/ndiswrapper.  You could go and update that file (gksudo gedit /etc/modprobe.d/ndiswrapper) and change wlan0 to eth1.  You would have to restart and you should be back to eth1.  wlan0 should work for you though.  Why the name change occurred is something I am still trying to understand.  I had this happen to and I just updated my /etc/modprobe.d/ndiswrapper on my 32-bit side and it seems to be working fine under eth1 again.  I left my 64-bit side alone and it just had it's file check and it still kept it at eth1.

Sorry I can't help you further.

The name change is, I think, my fault. I was following different advice from different threads trying to make it work, with no luck unfortunately.

I'm stumped too, really. It went from working to not working without any change on my part, other than the disk check, but I don't see *how* that could effect anything? I had another wireless problem after a partition resize a while back, and that didn't make sense either.

Thanks for the help though.

As I see it, I have a few options:
1. Hope someone else sees the thread and can figure out what went wrong.
2. Uninstall ndiswrapper, the driver, etc. and start that from a fresh slate—but that seems like a huge hassle.
3. Just buy a separate WiFi card for my laptop card-bay.
4. Reinstall Ubuntu and reinstall ndiswrapper.

---

### Post by Sweet Mercury on 2007-06-25
One last bump, maybe a fresh set of eyes can see the solution!

If not, I'll have to reinstall, or *use windows*. (That ought to provoke a few of you!)

---

### Post by killdragon on 2007-06-25
Hi, you know I was just thinking maybe you should check to see if any packages

       got broken during the disk check or were removed as bad.

---

### Post by Sweet Mercury on 2007-06-25
> **killdragon said:**
> Hi, you know I was just thinking maybe you should check to see if any packages

       got broken during the disk check or were removed as bad.

Hmmm, how does one go about doing that?

Broken packages, eh? That happens? Is there a log I need to check?

---

### Post by Sweet Mercury on 2007-06-27
> **killdragon said:**
> Hi, you know I was just thinking maybe you should check to see if any packages

       got broken during the disk check or were removed as bad.

Well holy crap, if that didn't do it.

I did a search for broken package issues and stumbled across a few simple commands that I thought I'd try. *apt-get update*, which I though just updated current packages, and *apt-get install -f*, which I'm not sure what that does.

But I typed those commands into the terminal, unplugged my ethernet cable, and attempted to connect to the wireless network. It connected right away and, well, here I am online! It's a bit slower than it was before, so any advice on that would be appreciated.

Sorry to make everyone go through all the drawn out process for such a simple fix, but hey now I know. I'm going to paste the terminal output here for two reasons: so anyone searching for ho to deal with a similar problem can have as much info as possible, and just in case anyone feels magnanimous enough to explain what happened and why this allowed me to reconnect to the internet.

```
mason@mason-laptop:~$ sudo apt-get update
Password:
Get:1 http://security.ubuntu.com feisty-security Release.gpg [191B]         
Ign http://security.ubuntu.com feisty-security/main Translation-en_US
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US
Get:2 http://security.ubuntu.com feisty-security Release [50.9kB]            
Get:3 http://us.archive.ubuntu.com feisty Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US
Get:4 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US
Get:5 http://security.ubuntu.com feisty-security/main Packages [40.3kB]        
Hit http://us.archive.ubuntu.com feisty Release                                
Hit http://us.archive.ubuntu.com feisty-updates Release                        
Get:6 http://security.ubuntu.com feisty-security/restricted Packages [6350B]   
Get:7 http://security.ubuntu.com feisty-security/main Sources [7622B]          
Get:8 http://security.ubuntu.com feisty-security/restricted Sources [955B]     
Get:9 http://security.ubuntu.com feisty-security/universe Packages [16.9kB]    
Get:10 http://security.ubuntu.com feisty-security/universe Sources [1855B]     
Get:11 http://security.ubuntu.com feisty-security/multiverse Packages [5421B]  
Get:12 http://security.ubuntu.com feisty-security/multiverse Sources [836B]    
Hit http://us.archive.ubuntu.com feisty/main Packages                          
Hit http://us.archive.ubuntu.com feisty/restricted Packages                    
Hit http://us.archive.ubuntu.com feisty/main Sources                           
Hit http://us.archive.ubuntu.com feisty/restricted Sources                     
Hit http://us.archive.ubuntu.com feisty/universe Packages                      
Hit http://us.archive.ubuntu.com feisty/universe Sources                       
Hit http://us.archive.ubuntu.com feisty/multiverse Packages                    
Hit http://us.archive.ubuntu.com feisty/multiverse Sources                     
Hit http://us.archive.ubuntu.com feisty-updates/main Packages                  
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages            
Hit http://us.archive.ubuntu.com feisty-updates/main Sources                   
Hit http://us.archive.ubuntu.com feisty-updates/restricted Sources             
Fetched 132kB in 23s (5505B/s)                                                 
Reading package lists... Done
mason@mason-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
mason@mason-laptop:~$ 
```

---

### Post by Ayuthia on 2007-06-27
I am glad that you are up and running again!  However, I am not certain about what fixed it.  From what you posted, it did not look like the process fixed anything.  The only thing that it posted is that there were two things that could be upgraded, but have not been selected and upgraded.  The apt-get install -f is supposed to do this (from the man page):

This option, when used with install/remove, can omit any packages to permit APT to deduce a  likely solution. Any Package that are specified must completely correct the problem.

By any chance, are there any other access points in your area?  I know that sometimes that if some other routers are seen and using the same channel, it can interfere with your connection.  I had to go to my router and change the channel so that I can get connected.

---

### Post by Sweet Mercury on 2007-06-27
> **Ayuthia said:**
> I am glad that you are up and running again!  However, I am not certain about what fixed it.  From what you posted, it did not look like the process fixed anything.  The only thing that it posted is that there were two things that could be upgraded, but have not been selected and upgraded.  The apt-get install -f is supposed to do this (from the man page):

This option, when used with install/remove, can omit any packages to permit APT to deduce a  likely solution. Any Package that are specified must completely correct the problem.

By any chance, are there any other access points in your area?  I know that sometimes that if some other routers are seen and using the same channel, it can interfere with your connection.  I had to go to my router and change the channel so that I can get connected.

Yeah, I couldn't see anything being really "fixed" by those commands either. But I won't complain!

There actually aren't any other access points that I know of, and the card wasn't showing any networks other than my own. So who knows.

About the speed: my ISP has been pretty craptastic lately, so I'm going to assume that is the problem until I should assume otherwise.

---

### Post by Sweet Mercury on 2007-06-28
Update:

I turned the computer off. When I came home and turned it back on, I was back to the same condition as the OP. I tried the same commands that *seemed* to fix things before, but to no avail!

Yarge!

Maybe a fresh install is the way to go?

---

