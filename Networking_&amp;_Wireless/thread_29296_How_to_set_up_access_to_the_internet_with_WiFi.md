---
title: "How to set up access to the internet with WiFi"
date: 2005-04-23
forum: Networking &amp; Wireless
---

### Post by hmodiano on 2005-04-23
I am using the Live CD on a Dell D600 notebook computer.  I have 802.11a and 802.11b on an internal card, and a D-Link Wireless Router hooked up to a cable modem.  

How do I set up Ubuntu to get online using WiFi?

Thank you for any help you may have!

Howard

---

### Post by blueplazma on 2005-04-23
Well, it all depends.  

You might be able to just use the included GUI program to do it. Go to System -> Administration -> Networking and activate the wireless interface. You may need to change the dropdown at the bottom for default gateway device, and you may need to enter some info on the other tabs. My preferred method is to use the terminal, but it might be confusing. I've included steps, but beware that they could make your computer totally unable to use the network if you do them wrong or if I screwed them up at some point. If you have another machine this isn't really an issue because someone could help you fix it back up. Try the GUI first, but if it doesn't work and you feel adventurous, try the command line instructions.

The first step it making sure Ubuntu recognizes your wireless card. To test this, try typing ```
sudo iwconfig
``` at a console and see if you gett any output that looks like this ```
lo		no wireless extensions.

eth0	  no wireless extensions.

eth1	  IEEE 802.11g  ESSID:"wirelessnetwork"
		  Mode:Managed  Frequency:2.437 GHz  Access Point: 00:06:25:4B:46:85
		  Bit Rate=54 Mb/s   Tx-Power=20 dBm
		  RTS thr:off   Fragment thr:off
		  Power Management:off
		  Link Quality=100/100  Signal level=-36 dBm  Noise level=-86 dBm
		  Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
		  Tx excessive retries:0  Invalid misc:1   Missed beacon:0

sit0	  no wireless extensions.

```
If you get an interface that doesn't say "no wireless extensions" then you've finished half the battle. The next step it to check and see if the interface, I'll assume it's eth1 and your wired is eth0, is activated or not. To do so, do ```
ifconfig
``` at a console and look for the interface eth1 to come up with some information like this ```
eth1	 Link encap:Ethernet HWaddr 00:0E:35:AC:FB:EA
		  inet addr:192.168.1.150  Bcast:192.168.1.255  Mask:255.255.255.0
		  inet6 addr: fe80::20e:35ff:feac:fbea/64 Scope:Link
		  UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
		  RX packets:23110 errors:0 dropped:1 overruns:0 frame:0
		  TX packets:18290 errors:0 dropped:0 overruns:0 carrier:0
		  collisions:0 txqueuelen:1000
		  RX bytes:16436776 (15.6 MiB)  TX bytes:1920842 (1.8 MiB)
		  Interrupt:7 Memory:faffc000-faffcfff

```
Assuming you see eth1, even if it doesn't have an IP address, then all that remains is to tell Ubuntu to use your wireless card. Be careful in this next step because you're changing your network configurations. At a terminal do this.
```

sudo cp /etc/network/interfaces /etc/network/interfaces.orig
sudo gedit /etc/network interfaces

```
Gedit should pop up and you should make your file look like this. 
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth1 inet dhcp
		# wireless-* options are implemented by the wireless-tools package
		wireless-mode managed
		wireless-essid yourwlan
		name Ethernet LAN card

auto eth1

```
Save your file, and do this last command at a prompt.
```

sudo /etc/init.d/networking restart

```
It should say "OK" and you should now be all set to use your wireless.  Good luck.

---

### Post by moon2js on 2005-04-27
blueplazma: Thanks for your post. I've noticed you're always really helpful on this board.

I'd like to configure my wifi card so that I can use it in coffeeshops. If I have time sometime in the future, I'd like to get it to work on an encrypted home wireless network, but now I just used wired at home. On second thought, if I had time, I'd like to try Linux from Scratch so I wouldn't be so lost when I read man pages.

But today at a coffee shop, I could get online, but I would get cut off usually within a minute and then I'd have to reconfigure the wifi and bring the interface back up again to get another minute of internet browsing.

I'm pretty sure this has something to do with the way my /etc/network/interfaces is not setup correctly.

I've noticed this comment line in other's /etc/network/interfaces on these boards:
```
# wireless-* options are implemented by the wireless-tools package
```
and I'm wondering if there is some kind of script or druid that automatically writes my interfaces file.

I'd like to have it setup so I have to manually bring up the interface after I boot up in a coffeeshop, but I'd also like to stay online for more than a minute without having to reconfigure the interface and bring it back up. Usually when I'm reconfiguring, I try all kinds of "sudo iwconfig ra0 blah blah off/any" until it works. And sometimes it just seems to be random.

Should my /etc/network/interfaces look something like this?
```
iface ra0 inet dhcp
wireless-mode managed
wireless-essid any
wireless-ap any
wireless-key off

``` 
Am I forgetting something? I'm unsure at the syntax I'm supposed to use in this file. I just tried this with my home wireless network after temporarily turning off encryption/security to make it open/coffeeshopesque (and brining down the wired eth0 and I lost connectivity. I don't know why it randomly works sometimes at other times doesn't work at all.

Also, I can't seem to scan for networks using iwlist:
```
mycomp:~$ sudo iwlist ra0 scan
Password:
ra0       Interface doesn't support scanning.
```
I've tried using the utilty that came with my driver, but everytime I execute the file, it completely hoses anything related to nautilus. And when I try to shutdown/restart it will hang at the point where it says "deconfiguring network interfaces." Oddly, the first time I executed the program, it worked perfectly without any problems, and I obviously didn't realize it would never work again.

I tried kwifimanager last week, and it did detect wireless network strength, but I pressed the scan button, it would always return "No network found" even if there was a network. I think it has something to do with my card not supporting scanning? But that utility that came with the rt2400 did work that first time, showing available networks and information about the networks, but as I said, that program doesn't work anymore.

Any advice on any of my issues would be greatly appreciated.

---

