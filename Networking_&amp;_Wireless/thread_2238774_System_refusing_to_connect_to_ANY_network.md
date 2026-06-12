---
title: "System refusing to connect to ANY network"
date: 2014-08-10
forum: Networking &amp; Wireless
---

### Post by iSeth on 2014-08-10
I'm new to Ubuntu and am already a big fan, but there is on problem... I cannot, for the life of me, figure out the internet connection. I can see wired and wireless connections, but am unable to connect to any of them. I'm pulling my hair out here so any help/guidance is appreciated. I built my system so I can answer most hardware questions.

---

### Post by dave131 on 2014-08-10
I'm assuming you see the networks in network manager.  What happens when you click on one?  Does it ask for a password/passphrase/key?  Do you have the key?  What type of encryption is being used on the networks, and does your wireless adapter driver support it?

---

### Post by iSeth on 2014-08-10
I was using wpa2, but assuming that it might be the problem, I removed all security from the network. When I click on a network it attempts to join and fails.

---

### Post by nix_weasel on 2014-08-11
were you useing wpa2 [I]personal on the router? 
is the router dhcp enabled?
 is your wireless settings dhcp or manual? if manual is the ip range the same as the one the routers offering and is it set to wpa2 personal as well?
 to me it sounds like either not getting/conflicting ip settings or authorization failure and im assuming you have the right passkey (upper and lowercase sensitive of course)
you said your new to ubuntu so im assuming you had the same hardware working under windows so probably not hardware related

[/I]

---

### Post by iSeth on 2014-08-11
Yes
I don't know, what is dhcp on the router side?
I set the router to open network as to require no key to gain access to the network

---

### Post by nix_weasel on 2014-08-11
log into the router and look for dhcp check its enabled while your there have a look at the wireless settings wpa2 personal/ passkey  if that looks right then on your ubuntu box  click the network icon down by clock look for the wrench click it remove any wireless networks in the screen that opens it removes any setting that may be messing it up close that screen then click network icon again and try connecting again if that fails you can test by bypassing networkmanager,

open a terminal type sudo nano /etc/network/interfaces

 in that i have it like this (details changed of course insert your own router name and passkey)

auto wlan0
iface wlan0 inet dhcp
      wpa-essid Womblenet Webnetworks
      wpa-psk 123456789abc

hit ctl-x,y,enter and close terminal and reboot dont worry about it moaning about the network config on boot once it all started it should be working that narrows it down to network manager settings either keep it as is (although you wont be able to control it from network manager) or repeat the terminal stuff and remove the bit you inserted and reboot and retry with networkmanager with your now proven working (hopefully) passkey

---

### Post by iSeth on 2014-08-11
I am fairly certain that this is a software issue as changing the security type has done nothing, and altering the config file has taken away the networking icon =( I am now having trouble changing the config back...

---

### Post by nix_weasel on 2014-08-11
humer me im trying to narrow down exactly where its going wrong so reset set router to settings that worked under windows

sudo kate /etc/network/interfaces might be easier for you to use 

that file is part of the base linux os before any kde/gnome window managers so if it works there we know its a) the routers fine b)your hardware works and its after that something dosnt
and it will disable control of your wireless from networkmanager as i warned

---

### Post by iSeth on 2014-08-11
All settings always work under windows, that how I'm posting...
System returns - "sudo: kate: command not found"
Oh, i wasn't sure what you meant by that, sorry

---

### Post by nix_weasel on 2014-08-11
kate nano etc are all like notepad under windows have a look under utilitys for  what you have installed look for text editor and substute kate for whatever that is
and sudo is like run as administrator
the point im trying to get to is if this dosnt work its the router thats causing the problem if it does we need to look at network manager settings im picking there is a small mistake in there thats causeing it
 if it does you can do the sudo <texted> /etc/network/interfaces thing again and remove the  entry to return network manager control after reboot

---

### Post by iSeth on 2014-08-11
how can I tell if it works? its still not connected...

I used nano to alter the file, but its still not connected

---

### Post by nix_weasel on 2014-08-11
ohh open a web browser doing it the base way wont show you any pretty icon etc lol its a basic no frills kinda deal the only way to tell is to try surf net if you can its working

---

### Post by iSeth on 2014-08-11
oh, no connection =(

---

### Post by wildmanne39 on 2014-08-11
Click on the wireless script in my signature and post the results here using code tags #.

---

### Post by iSeth on 2014-08-11
my linux machine doesn't have ANY internet access

---

### Post by Iowan on 2014-08-11
> **iSeth said:**
> I used nano to alter the file, but its still not connectedHave you restarted networking or rebooted after the edit?

---

### Post by wildmanne39 on 2014-08-11
There is directions for running the script without an internet connection.

---

### Post by iSeth on 2014-08-11
yes

---

### Post by iSeth on 2014-08-11
I ran the file but nothing happened

---

### Post by Iowan on 2014-08-11
> **iSeth said:**
> how can I tell if it works? its still not connected...

I used nano to alter the file, but its still not connectedFrom a terminal ```
ifconfig -a
``` will show you if your interfaces have an IP address.

---

### Post by wildmanne39 on 2014-08-11
Did you follow the directions here for running it without an internet connection? 
[http://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385](http://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385)

---

### Post by iSeth on 2014-08-11
I'm guessing I should look at wlan0?
but what should I look for? I don't see anything about IP

---

### Post by dave131 on 2014-08-11
If you're using default ubuntu, use gedit.  Also - ignore that it works in Windows.  Windows requires a driver to talk to the adapter and everything was set up already in Windows.  Linux is a different animal, and anything dealing with it works in Windows doesn't apply.  Linux needs drivers also.  That's how it communicates with your device.   It may be something with the driver, it may be something else, but there is a lot more to it than something that simple.  Do use gedit or what ever editor you have and follow the advice.  Trying to troubleshoot the issue is best done a step at a time with no presumptions.

---

### Post by dave131 on 2014-08-11
Oh crap - ignore me.  Wildman is here and they are an expert on this stuff - I've watched their help on the forums as I slowly try to learn.

Wildman - so sorry - I really didn't mean to intrude!

---

### Post by wildmanne39 on 2014-08-11
You did not intrude, I am on my way out of town in abut five minutes and I am not going to have much wifi so continue to help and it would tell us a lot if he runs the script and posts the information it is a lot quicker then running the commands one at a time.

---

### Post by iSeth on 2014-08-11
Ok, I just had to bash it in terminal. but now I can't post it because it "has 13 images", if an admin could enable more it would help...

---

### Post by dave131 on 2014-08-17
I am going to assume you downloaded the wireless script file seperately, loaded it into your Ubuntu install with no internet connection, changed the permissions so you could execute it, and finally ran it - all as per Wid Man's posts.  All they want you to do is post the output file from that script:  wireless-info.txt in a reply here.  You can attach it to a reply, or you can include it in the body of the reply if you put it in code tags.  Since you don't have internet on your Ubuntu install, you'll need to copy that file to another media to load using the OS with the internet access.

No pictures, etc., needed - just that info.  We only want to go one step at a time.

---

### Post by varunendra on 2014-08-17
> **iSeth said:**
> Ok, I just had to bash it in terminal. but now I can't post it because it "has 13 images", if an admin could enable more it would help...

If you ran the script correctly, it should have generated a file named "**wireless-info.txt**" or "**wireless-info.tar.gz**" in the same place where you put the script. Search it > copy it to a pen drive (or memory card, or whatever you have to copy files from this system to another) > post that file, or its contents, into your next post here.

For ethernet, this output may help us understand the problem -
```
sudo lshw -C network > Desktop/eth.txt
```
This will create a file named "**eth.txt**" on your desktop. Attach that file as well into your next post (or copy-paste its contents here).
(the 'lshw' command takes a few seconds to complete, so don't close the terminal immediately after running it.)

---

### Post by iSeth on 2014-09-13
Sorry for the inactivity, I've been having internet problems... how do I post the file? I can't post the contents because the forums says it has 13 images...

---

### Post by varunendra on 2014-09-13
Both the methods I explained above will generate plain text files which you need to post here. Where did the "images" come from? Are you talking about screenshots? Nothing else is required but the plain text files mentioned in post #28 above.

---

### Post by iSeth on 2014-09-13
When I copy all of the text from the text file to the post box, I try to post and it tells me that it has images...

---

### Post by jeremy31 on 2014-09-13
Lets try an alternative ```
sudo apt-get install pastebinit
``````
pastebinit eth.txt
``` and paste the resulting URL from terminal and post ```
pastebinit wireless-info.txt
``` and paste that URL as well

---

### Post by iSeth on 2014-09-13
Here's the one for wireless-info - [http://pastebin.com/8HM7V5tZ](http://pastebin.com/8HM7V5tZ)
And the one for eth - [http://pastebin.com/Y6s2Yq3u](http://pastebin.com/Y6s2Yq3u)

---

### Post by jeremy31 on 2014-09-13
> **iSeth said:**
> Here's the one for wireless-info - [http://pastebin.com/8HM7V5tZ](http://pastebin.com/8HM7V5tZ)
And the one for eth - [http://pastebin.com/Y6s2Yq3u](http://pastebin.com/Y6s2Yq3u)

The one that should have been wireless-info is actually the wireless_script, run the script again ```
./wireless_script
``` and do the pastebin again```
pastebinit wireless-info.txt
``` and might as well ```
ls -l
``` in case something weird is happening

---

### Post by iSeth on 2014-09-13
sorry - [http://pastebin.com/RqpWF6Fy](http://pastebin.com/RqpWF6Fy)

---

### Post by varunendra on 2014-09-13
> **iSeth said:**
> When I copy all of the text from the text file to the post box, I try to post and it tells me that it has images...

I think I understand now what might be happening.... - some of the codes changing to smileys is happening :|

It won't happen if you post the code part within 'Code' box. Please follow the "Use Code Tags" link in my signature below to see how to use them.

However, for now, the idea of pastebin is even better. Thanks for joining us jeremy31! :)


@iSeth,
For your Ethernet connection, please try this in a terminal -
```
sudo mii-tool -F 100baseTx-FD eth0
```
If above gives any errors, try instead -
```
sudo ethtool -s eth0 speed 100 duplex full autoneg off
```
..and report back success or failure.

---

### Post by iSeth on 2014-09-13
it did nothing... is that good or bad?

---

### Post by varunendra on 2014-09-13
If by "nothing" you mean no outputs in the terminal, then it is (should be) good. It means there were no errors to report, and the command did what it was supposed to do.

Now if you have an Ethernet cable connected to the ethernet port, is it working now? If still not, please show us the outputs of -
```
sudo lshw -C network
sudo ethtool eth0
```

..and sorry if I'm missing your previous description (in a hurry now), but could you explain why you are using the /etc/network/interfaces file to control the wifi when you have network manager installed?

---

### Post by iSeth on 2014-09-13
the outputs are - 
  *-network                      description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 06
       serial: 74:d4:35:9f:1f:8f
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:74 ioport:b000(size=256) memory:fe200000-fe200fff memory:da100000-da103fff
  *-network
       description: Wireless interface
       product: AR93xx Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 01
       serial: 6c:19:8f:00:12:16
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.13.0-35-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:18 memory:fe100000-fe11ffff memory:fe120000-fe12ffff
  *-network
       description: Ethernet interface
       physical id: 1
       bus info: usb@8:1.2
       logical name: eth1
       serial: b6:f0:ab:74:66:03
       capabilities: ethernet physical
       configuration: broadcast=yes driver=ipheth ip=172.20.10.2 link=yes multicast=yes

and

Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised pause frame use: Symmetric Receive-only
	Advertised auto-negotiation: Yes
	Speed: 10Mb/s
	Duplex: Half
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
			       drv probe ifdown ifup
	Link detected: no


and something in my networkmanager files is borked and i cant figure how to fix it, I guess I should reinstall it...

---

### Post by varunendra on 2014-09-13
The settings are still "half duplex" and "10 Mbps" for eth0. Do you have the ethernet cable plugged in? Do you have two ethernet ports?

Reinstalling Network Manager is a good idea, but do you have an active connection for that? It seems you do - via your iPhone. If yes, please do so as follows -
```
sudo apt-get install --reinstall -d network-manager network-manager-gnome
```
ONLY if the above completes successfully (if not, and there are errors, STOP HERE!) -
```
sudo apt-get purge network-manager-gnome network-manager
```
..followed by a reboot, then -
```
sudo apt-get install network-manager network-manager-gnome
```

This will completely wipe out Network Manager including its configuration files, then reinstall it fresh. But it will work for wifi only when your remove or comment out the entries for wifi in /etc/network/interfaces file.

**PS:**
VERY IMPORTANT - please read my previous posts where I said something about 'Code' tags. You are still posting the codes as normal text, not in 'Code' box, which causes it to lose its formatting and sometimes makes it difficult to read!

---

