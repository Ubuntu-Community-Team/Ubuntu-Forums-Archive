---
title: "Wireless Woes"
date: 2005-11-08
forum: Networking &amp; Wireless
---

### Post by Tadhg on 2005-11-08
Well, i've gotten hold a laptop that is perfect for college (for free!), and i would really like to keep linux on it but getting wireless up and going is causing a lot of hassle. 
I posted on the newbie forum but the problem remains so hopefully here i can get an answer. 
My Wireless card is Belkin with a rt2500 chipset (AFAIK). Now, i've reinstalled Ubuntu (breezy badger) so im running a clean install. The card was in during installation, so its showing up in network manager, and seems to be being picked up. Thing is, i cant ping the router (netgear DG311(?)). Here's some info:

"iwlist scan"
> ra0       Scan completed :
          Cell 01 - Address: 00:09:5B:D5:DA:8E
                    Mode:Managed
                    ESSID:"Wireless"
                    Encryption key:on
                    Channel:8
                    Quality:0/100  Signal level:-43 dBm  Noise level:-200 dBm

for some reason "sudo iwlist scan" gives no results.

"sudo ifconfig"
> ra0       Link encap:Ethernet  HWaddr 00:11:50:8F:0F:B2
          inet6 addr: fe80::211:50ff:fe8f:fb2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1145 errors:0 dropped:0 overruns:0 carrier:0
          collisions:8 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:36088 (35.2 KiB)
          Interrupt:5 Base address:0xc000


sudo iwlist key
> ra0       2 key sizes : 40, 104bits
          4 keys available :
                [1]: DC18-5C5B-EE (40 bits)
                [2]: off
                [3]: off
                [4]: off
          Current Transmit Key: [1]
          Security mode:open

sudo dhclient ra0
> 
.
.
.
Listening on LPF/ra0/00:11:50:8f:0f:b2
Sending on   LPF/ra0/00:11:50:8f:0f:b2
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


i really would like to get this running. It's been wrecking my head all week and im getting close to going back to windows.I havent messed with the card at all on this install so its basically as is. No ndiswrappering etc!
Any help is ggggggreatly appreciated!

---

### Post by gruepig on 2005-11-09
It looks like your card/driver is working since your wireless card has a hardware address and you can scan the network.  The next thing to do is determine whether you're having problems associating with a wireless network.

Post the output of 'sudo iwconfig'.

If iwconfig shows an ESSID and a hardware address for the Access Point, then you have wireless connectivity, just not IP-level connectivity.  If instead you are seeing something like 'Access Point: 00:00:00:00:00:00', then you have not joined a wireless network.

---

### Post by Tadhg on 2005-11-09
here's the sudo iwlconfig:
> ra0       RT2500 Wireless  ESSID:"Wireless"
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:11 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:DC18-5B5E-DD   Security mode:open
          Link Quality=0/100  Signal level=-54 dBm  Noise level:-199 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


I don't know why its not showing a MAc address? It has the ESSID correct though
still stumped

---

### Post by Tadhg on 2005-11-09
Right, im not getting anywhere with the belkin card. Luckily for me, i have a different Netgear card so i switched them and lo and behold, the internet doesnt work. But still, things are where they should be.
i get a mac address. iwlist scan brings up the network. everything is there but yet, when i run dhclient, it doesnt recieve any offers. What could be the problem. I have WEP enabled and i have a suspicious that this is causing the probs.

---

### Post by Tadhg on 2005-11-09
WOOOOOOOOOOOOOOOO

it works. I disabled WEP key on the router and now im surfing wirelessly! Happy me. Now i have to figure out how to get it working with the key enabled.

---

### Post by Tadhg on 2005-11-10
well. That was an anticlimax.So it works without wep encryption....for about 30 seconds. I can check sites and ping the router for about 2 minutes before the connection drops and the card starts blinking. A whole new problem, hopefully easier solved. Any ideas again. Sometimes the internet connection drops, but i can still ping the router. Once again i'm stumped. It's a turbulent road to becoming an Ubunutu user.

---

### Post by TimelessRogue on 2005-11-10
Hey, glad to hear of you success!  Regarding using a WEP key, there have been numerous posts regarding using spaces or a dash within the key, something like: 0000-0000-00 (using your numbers, of course!)  Not sure, but you might want to do a search.

In the meantime, MY wireless problem has reared its ugly head again ... worked fine, as before, then dropped, also as before ...

Good luck ...

---

### Post by wapitiscat on 2005-11-11
Tadhg,

Check that you don't have a network switching/managing program running that automatically scans for wireless LANS. This was a problem for me. My connection would behave like yours and drop after a minute or two. If this is the case, try removing the manager app and rebooting. As for getting the WEP to work, I've had success in configuring the wireless interface through The System > Administration > Networking dialog. Set the SSID, select Hexideciamal or ASCII, and enter the WEP key (hex or ascii to match). Sometimes a deactivate/reactivate toccle will help.

---

### Post by TimelessRogue on 2005-11-12
Hey, thanks for that hint ... although I can't recall installing any sort of manager aside from the original Breezy plus updates, I'll check it out.  

Speaking of that, this is exactly what happened the first time.  I installed Breezy, fresh rather that over Hoary since I didn't have any real data onboard, and all was well with wireless 'til one (and I never did figure out which) of the various updates and wireless just quit.  After fiddling with things into the wee hours (more than once) I decided to do a fresh install.  Lo and behold, all was well once again ... 'til last week when the exact same scenario reared it's ugly head after allowing an update of SOMETHING!

This time it's been lot's of late hours spent trying to ferret out the problem WITHOUT using ndiswrapper or any other outside processes.  Now ... I'm gonna do another fresh install with the only difference being that I will absolutely very carefully monitor each and every update 'til the problem surfaces.  Perhaps ... just perhaps ... I will finally solve the "Mystery of the Disappearing Linksys"!

I will add that I know it's not the card:  it was just fine with both Hoary and Breezy and is fine with Windoze.  It comes up on eth1 with eth0 serving for my Verizon connection.

I won't bother anyone further with this 'til I DO find the problem ...

Later, guys ...

---

