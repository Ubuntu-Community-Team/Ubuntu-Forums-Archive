---
title: "Ethernet and wireless adhoc simultaneous connection"
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by frup on 2008-04-29
Hi.
I have managed to get the brother MFC-665CW printer working over LPD on ethernet but would prefer to have it going over adhoc wireless. (should be possible with an Intel Corporation PRO/Wireless 3945ABG right?)

To do this I need to have the ethernet going at the same time (for internet) but the wireless of a laptop communicating with the wireless of the printer.

I have been trying all day to get them to communicate but it is very difficult for me.

Some how I need Ubuntu so serve as a Wireless Acess Point (the printer can also do standard wireless communications if this is better) and be able to have 2 IP's at once I suppose. One for the internet via wired connection and DHCP and one for the wireless communications. I don't seem to be able to do this at the same time nor even get the wireless communications to work properly.

I would love to have the printer working as the wireless access point and the ethernet going through it but I do not think that is possible :( it only seems to allow one connection of wireless OR ethernet. 

In the printers settings I can set IP, Subnet masks, DNS servers and gateways.

The printer does not need access to the internet, just Ubuntu so I presume no routing would actually be required.

I can follow guides and have tried several vague ones on Ubuntu forums already but since I have been trying for almost 5 hours plus some time last night I really would prefer direct advice if anyone is willing to give it. Quite frankly I'm exhausted.

The only solution I have at the moment is to unplug the internet connection and place the cable in the router. This is my grandparents computer and I don't think it is fair on them to have to do this. The brother MFC-665CW does not seem to be able to work on USB on Ubuntu, it is detected then not detected and can't print.

I realise getting a switch/hub/multiport router/proper wireless access point is the easiest solution and in the end may have to happen but that is not feasible right now.

**EDIT:**

After a lot more reading and experimenting. I managed to set up simultaneous wireless and wired connections using the commands
sudo iwconfig wlan0 essid 'printer' mode Ad-Hoc
sudo ifconfig wlan0 192.168.0.2 netmask 255.255.0.0

(printer is what I named the printers ssid, no access key, this is out in the country, the nearest neighbours are well out of range. I may set the key later but for testing it was very frustrating to deal with)

reasonably simple. A test page over wireless printed (i set the printer to 192.168.0.4 with a subnet of 255.255.0.0) This is pretty simple basic networking and I should have understood it all from the beginning, its just the whole network manager etc makes this all incredibly hard to do and it's hard to work out what's happening. 

I am going to reboot in a second and make sure that the connections are the same after reboot because I am pretty sure network manager will stuff it all up as it starts again. It's annoying because this is a laptop and if it's taken away from this setting NM really helps but here it could actually be a hindrance.

**EDIT 2:**

This is becoming frustrating to the point where I am getting infuriated. The problem is that I know everything works but I just can't seem to fit the puzzle together. When I reboot, despite having made my /etc/network/interfaces file contain ad-hoc, the ip and the essid, the wlan0 doesn't start correctly. Mainly that ad-hoc is still at managed. This is my grandparents computer so I am not going to expect them to add a command just to print.

stopping network manager from beginning at start up doesn't help much, if anything it makes things harder as I don't seem to be able to get ad-hoc networks to start AT ALL!. I suppose I better start working out how to make Ubuntu act as more of a wireless access point.

some odd things are happening too, I have to run the command:

sudo iwconfig wlan0 essid 'printer' mode Ad-Hoc

twice for it to add both the essid and the ad-hoc mode :S
[B]
Edit 3[/B]

After editing /etc/rc.local to set up the commands

ifconfig wlan0 down
iwconfig wlan0 mode Ad-Hoc
iwconfig wlan0 essid "printer"
ifconfig wlan0 up

ifconfig and iwconfig appear to be set up correctly but the ad-hoc network no longer responds at all. This is the most confusing thing I have experienced in over 2 years of using Ubuntu.

As you can see here the ip's are setup right (ifconfig):

wlan0     Link encap:Ethernet  HWaddr 00:19:d2:7a:a5:4d  
          inet addr:192.168.0.2  Bcast:192.168.255.255  Mask:255.255.0.0
          inet6 addr: fe80::219:d2ff:fe7a:a54d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:12613 (12.3 KB)

and here the ad-hoc mode and essid are correct.(iwconfig):
 
wlan0     IEEE 802.11g  ESSID:"printer"  Nickname:""
          Mode:Ad-Hoc  Frequency:2.462 GHz  Cell: DA:3E:33:09:9E:49   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


The only thing I can think of being wrong is that possibly by some crazy chance it needs to be 802.11b (the printers ad-hoc network is sending/receiving at 11mps not 54mps) but I don't see how that could have changed with what I did

This is the result of the ping to the printer

ping -c 5 -I wlan0 192.168.0.4
PING 192.168.0.4 (192.168.0.4) from 192.168.0.2 wlan0: 56(84) bytes of data.
From 192.168.0.2 icmp_seq=1 Destination Host Unreachable
From 192.168.0.2 icmp_seq=2 Destination Host Unreachable
From 192.168.0.2 icmp_seq=3 Destination Host Unreachable
From 192.168.0.2 icmp_seq=4 Destination Host Unreachable
From 192.168.0.2 icmp_seq=5 Destination Host Unreachable

--- 192.168.0.4 ping statistics ---
5 packets transmitted, 0 received, +5 errors, 100% packet loss, time 4016ms
, pipe 3

I don't understand how adding the commands which make the ad-hoc network go up to the rc.local file can add the information to iwconfig but not result in it going up.


**EDIT 4**
after 10 hours I have finally finished setting this up. I'm sure this is unnecessarily hard and probably related to some sort of bug. This is the content of rc.local layout that finally got everything working

ifconfig wlan0 down
iwconfig wlan0 mode Ad-Hoc
iwconfig wlan0 essid 'printer'
ifconfig wlan0 up
iwconfig wlan0 essid 'printer' mode Ad-Hoc
iwconfig wlan0 essid 'printer' mode Ad-Hoc

if anyone browsing this knows why it had to be like this to get the adhoc network properly initialised I would love to get a pm.

Now I have to get the printer also printing from windows over LPD (if it's even possible) which is going to be even harder lol.

I have to leave my grandparents now and drive for an hour back home but next time I'm up here I'll work on bridging the ethernet to the wireless so their other windows laptop can access the internet too. or maybe I'll just buy them a bloody wireless access point! lol. I'm stuffed and filled with that strange pleasure/euphoria that you get when you succeed at something that you've found extremely frustrating/hard.

---

