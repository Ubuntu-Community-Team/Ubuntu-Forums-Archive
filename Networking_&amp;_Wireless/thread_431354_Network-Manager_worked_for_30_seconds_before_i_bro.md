---
title: "Network-Manager worked for 30 seconds before i broke it"
date: 2007-05-02
forum: Networking &amp; Wireless
---

### Post by herbert42 on 2007-05-02
Hi, 
I had a TrendNet TEW-423 card which I beat my head against last night trying to get working.  Compatible wireless list gives it as usable if you follow the instructions exactly.  While playing with the 423 I did several things, including installing Ndiswrapper with the Utils 1.1 and 1.8 and adding the XP driver that came with the wireless card, and installing Network-Manager.   Finally, being drunk and frustrated I just went back to NewEgg and bought a TEW-443 which the Comp. Wir. List gives as "Works out of the box", then deleted the WinXP -423 driver from Ndiswrapper.  

Today, I installed the -443 card and booted the system. Network-Manager fired up and found all the surrounding wireless.  I tried to connect mine giving the WEP password, and it failed and fell back to the wired connection.  I then got frustrated and popped open the Networking panel and tried to set up the wireless through that by manually entering the SSID of the router I want to connect to. It wouldn't connect through that, and now Network-Manager won't see any wireless networks.  

I'd really like to get network manager to regain control of the wireless (and maybe even connect properly to a wireless network).  

I've tried deleting everything from /etc/network/interfaces except for:
auto lo
iface lo inet loopback

and then rebooting (what can i say, i'm an old windows guy), but i can no longer see the wireless networks in network-manager.

sudo iwconfig outputs:
ath0      IEEE 802.11g  ESSID:"21-23_Cameron"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

iwscan gives:
lo        Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      No scan results
eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.


Help, please.

---

### Post by herbert42 on 2007-05-03
my current thoughts are that i screwed up the drivers (somehow) because the blinken-lights on the wireless card begin with the green power light during the bios boot up, then start alternating between the connect and link lights after ubuntu boot.
suggestions on how to verify the proper driver?
thanks.

---

