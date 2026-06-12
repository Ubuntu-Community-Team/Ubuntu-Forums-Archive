---
title: "Linux newbie (first install) needs network help."
date: 2009-01-20
forum: New to Ubuntu
---

### Post by Scott-B on 2009-01-20
I've just successfully installed Ubuntu 7.10 and an old laptop and it has no internet access. Because the laptop was made in 2004, I struggled to find a release of Ubuntu that would install, but 7.10 worked. Ecerythig appears operational, but the network manager can't connect to the internet either through hardline or wireless.

Ubuntu is freshly installed with no 'fiddling'. I have no network access to d/l updates to the OS. :(

Computer:
Averatec laptop, 3250 series, P/N: AV3250H1-01 (made 10/2004)
Athelon XP-M processor, 1.6GHz
1GB memory
Ethernet, Wi-Fi b/g, modem, 20GB HDD

[If I need to post my chipset manufacturer and details, please tell me how I would find them through Ubuntu.]

Router:
Belkin 4-port + Wi-Fi b/g s/n: BEL1B65J
Hardware: F5D7230-4
Connection Type: PPPoE
Subnet mask: [omitted from this post]
Wan IP: [omitted from this post]
Default Gateway: [omitted from this post]
DNS address: [omitted from this post]
NAT Enabled
Firewall & Security Enabled

DSL Modem:
Efficient Networks - Speedstream
"Extended Reach System"???

My default network manager shows the eth0, wlan0, and internal modem (PPP0).
I've disabled my wireless lan chipset and network manager entry (I want to keep the connection simple for now, so I've used a patch cable to the router).
My router LED confirms that it 'sees' the patch cable plugged-in.
All router and modem LEDs confirm the internet connection is fine (and my main computer has internet access, no problem).

Scanning through the Ubuntu help files ("thank you" to the community that wrote this file BTW, helpful), I found "Connect to a network", "2.2.2 Use the ifup command to connect to a network".

I first typed: **sudo ifdown eth0** and received:
scott@ubuntu:~$ sudo ifdown eth0
[sudo] password for scott:
There is already a pid file /var/run/dhclient.eth0.pid with pid 14094
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:40:45:25:00:23
Sending on   LPF/eth0/00:40:45:25:00:23
Sending on   Socket/fallback
scott@ubuntu:~$

I then typed: **sudo ifup eth0** and received:
scott@ubuntu:~$ sudo ifup eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:40:45:25:00:23
Sending on   LPF/eth0/00:40:45:25:00:23
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
scott@ubuntu:~$

The help file doesn't give advice on what to do if 'ifup' fails to connect. :(

Does this say that Linux does not have the right hardware driver for my Ethernet device? How would I identify the right driver? d/l the driver? Install the driver? [Newbie, but I ask ok questions...]

Also, I found a thread where a user "turned-on PPPoE", but I don't see that option in my Network Manager.
[http://ubuntuforums.org/showthread.php?t=894368&highlight=no+internet+connection](http://ubuntuforums.org/showthread.php?t=894368&highlight=no+internet+connection)

Thanks for your help.




-Scott-B

---

### Post by cariboo on 2009-01-20
The LED's always lightup when a cable is attached even if the connection doesn't work. Could you open an Applications-->Accessories-->Terminal and type:

```
sudo lshw -C network
```

paste the output in your next post. The above command list the network hardware attached to your computer and will tell us if the correct driver is loaded.

Jim

---

### Post by Scott-B on 2009-01-21
Thanks for your help. Here is what I get:

scott@ubuntu:~$ **sudo lshw -C network**
  *-network:0             
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: wmaster0
       version: 01
       serial: 00:11:09:0c:29:4a
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci latency=32 module=rt2500pci multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:40:45:25:00:23
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=32 link=no maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s
scott@ubuntu:~$

---

### Post by cariboo on 2009-01-26
It looks like your network adapter is detected and the proper driver loaded. Could you type in a terminal:

```
sudo dhclient eth0
```

To see if can get an ipaddress assigned.

Jim

---

### Post by russu52 on 2009-01-26
this is what i did to connect to my broadband service (wired)

right-click on network icon, select edit connections.
select dsl tab (last one on the left)
click add
insert username, service name, password.
check "connect automatically"
give admin password and store permanentley on keyring

bingo

hope it works for you.

btw if you are using 7.10 because you feel machine is a bit old, have you tried the little mouse (xubuntu)? it's very lightweight and quite good

---

### Post by Hobgoblin on 2009-01-26
What issues did you have installing Ubuntu 8.10?

If you can I would suggest trying that (at least try it from the live CD) because networking is vastly improved (in most cases ;)).

The laptop is perfectly capable of running it (I have 8.10 on a much older laptop, a PII 266, with no problems).

---

### Post by mrbiggbrain on 2009-01-26
Your useig a averatech, they are HORRIBLE driverwise, its even near impossible to get the hardware working under windows, everytime we get one at my job we send it away, tell them the drivers are too hard to find. we have them that sit in the back room for weeks waiting for the drivers to be found to restore them.

---

### Post by Scott-B on 2009-01-27
** Cariboo907 **
scott@ubuntu:~$ **sudo dhclient eth0**
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:40:45:25:00:23
Sending on   LPF/eth0/00:40:45:25:00:23
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
scott@ubuntu:~$ 

Nope, no IP assigned.

And thanks for working with me.



** russu52 **
When I right-click on my network icon, I don’t get ‘edit connections’. I get ‘enable networking’ (which is checked), ‘connection information’ (which is greyed-out), and ‘About’

If I left-click, ‘Manual configuration’, I get a list of wireless (I want it off-line for now), Wired (which is checked), and Modem (not connected).

I don’t see a ‘DSL’ tab anywhere in my searchings.

I haven’t tried xubuntu. I will if I can’t get this to work.

Thanks for your help.



** Hobgoblin **
I tried 8.10, but it hung during install and left me with a :~$ prompt. Quite intimidating for a newbie... :)

The LiveCD also hung on startup. 7.10 was the only version I found that would install. If I can get the network working (minimally), I hope to be able to update to 8.10 and get better drivers, etc.

Thanks Hobgoblin

---

### Post by cariboo on 2009-01-28
I had a look at the link in your first post did you try the following?

> Open a Terminal and try

Code:

**sudo pppoeconf**

You should probably click yes to every option, and there should be a place to enter your username and password.

To turn the connection on, you can type

Code:

**pon dsl-provider**

(the dsl-provider profile may differ for you, but I think that's the default one-- it should tell you which command to use at the end of the configuration process)

To turn the connection off, you can use

Code:

**poff -a**



The above opens up a nice text based setup utility, use the arrow keys, the tab key and the return key to navigate. Just follow the prompts, and hopefully your problems will be solved.

Edit: I'm  running Jaunty alpha3 at the moment, and I just noticed that my Network Manager Icon has disappeared, so I can't check whether there is a adsl tab.

Jim

---

### Post by Scott-B on 2009-01-30
I typed **pon dsl-provider**, but all  I received in return was a line of garbage text. The text kept repeating every three seconds, and I had to close the terminal window to stop it.



In my next window, I typed: **sudo pppoeconf**

The program runs, and finds:
eth0
eth:avah
wlan0

(which are all my connections). I hit 'yes' to prceed.

The program scans, 'Looking for PPPoE access Concentrator' on each, but I get a time-out on all three.

The program re-scans Multi-modem mode, but I still only get time-out errors.

The program recommends I check my modem cable (Belkin, cat-5, PATCH cable)

When the program exits, I get:
SIOCSIFFLAGS: Cannot assign requested address
SIOCSIFFLAGS: Cannot assign requested address
Then the ~ prompt.


I typed **poff -a** and recived
/usr/bin/poff: No pppd is running. None stopped.


I hope this helps.

---

### Post by cariboo on 2009-02-02
Are you using the same connection to connect to the forums? 

If you are getting a time-out it means that there is no connection being made. I would suggest switching out the network cable for another one, just to be sure

Jim

---

### Post by Scott-B on 2009-02-07
I post to the forums using my desktop computer / router / DSL modem.

The laptop is hardwired to the same router (different port, obviously).

I moved the laptop to the patch cable formally used by the desktop computer. Still no connection.

Lastly, a different Internet site mentioned that Ubuntu 5.10 worked great with this Averetec 3250H1 laptop. I tested it with a LiveCD and INDEED GOT AN INTERNET CONNECTION! No problems.

Tonight, I trying to do a simple install of 5.10. The DVD crashed the install (missing files?), so I'm d/l the .iso again and will retry.

Question: Is there a way I can install 5.10, then update the entire OS to 8.10? If so, I'll try it and hope I don't loose the Internet connectivity.

Thanks.

-Scott

---

### Post by Scott-B on 2009-02-10
I looked a while longer on line and found some more information. Apparently other Averetc owners have had this problem, and solved it by installing ver 5.10 of Ubuntu.

I installed 5.10 and everything worked fine! Full network access.

Next I thought I'd try updating the system:
I put the 6.06 (LTS, yes '.06' I checked twice) CD in the drive
Started Synaptic Package Manager
"Added" the CD
It saw the updates
I "marked all updates" and "Applied" them
Synaptic gave me a few chances to change my mind
It ground-away for about 20-minutes applying all the updates
Presto! It works fine.

Next I put 7.10 in the drive
Started Synaptic Package Manager
"Added" the CD
... but it saw no updates for me to mark and apply
It had scanned the CD, found the index files, thought for a few seconds, then came back to the same Synaptic screen with nothing to do.

Maybe the upgrade step was too big ??
Next I put 6.10 in the drive
Started Synaptic Package Manager
"Added" the CD
... but it again saw no updates for me to mark and apply


Any ideas?

---

### Post by Scott-B on 2009-02-10
Oh, I also tried:
sudo apt-get update   &
sudo apt-get upgrade

Neither command found any updates/upgrades for me, and i know my internet connection is good.

Is it possible I *do* have 8.10 installed? I check 'About Ubuntu', and it lists "Welcome to Ubuntu 6.06 LTS" in the help file.


-Scott

---

### Post by cariboo on 2009-02-10
Unfortunately you can't upgrade from 6.06 LTS as it is no longer supported, 8.04.2 is the latest LTS version. Use the link I pm'd to you last week.

Jim

---

### Post by Scott-B on 2009-02-11
Cariboo,

I d/l, burned, and verified a CD with 8.04.2 LTS as you recommended.

The results were the same, no update.

I started Synaptic Package Manager and added the CD.
The package manager scanned the index file and returned to the main screen.
I pressed ‘mark all upgrades’, but nothing showed-up to apply.

Other data (by the way):
When I insert the CD, the file manager view pops-up with a list of files and directories (as expected).
The OS recognizes the nature of the CD and asks if I want to start Synaptic Package Manager; I select yes, but nothing shows-up.



I feel like I’m missing something obvious.



Is my 6.06-version of Synaptic Package Manager not able to recognize the updates on the CD?

Are all the changes from 6.06 to 8.04.2 ‘additional files’, rather than ‘updates to existing files’?

Can I install the 8.10 version of Synaptic Package Manager and let it identify and install all the other updates?

Could I wipe the drive, install 7.10 (which did load, but without network support), update it to 8.10, and then grab the network driver off of the 5.10 CD?


Hey - I’m learning enough to have interesting questions ... :)

Thanks again for your help.


-Scott

---

