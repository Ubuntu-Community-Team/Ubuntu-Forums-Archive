---
title: "Network Troubles with a Linksys WMP54G"
date: 2008-07-14
forum: Networking &amp; Wireless
---

### Post by Igneo676 on 2008-07-14
Fun trying to get my network to work properly...
...and, here's my problem.

I running Hard Heron, 8.04 (I believe 32 bit, but, not sure. I've no reason to be running 64 bit >.>) and am using the default Wireless connection manager (if neccesary, I will do the ndiswrapper deal, but, i'd much rather not). I'm currently running through the RT2500 thread, since that is my chipset, but I see no one with my exact problem thus far.

The connection works fine, i've had to run a script to bump the 1 mb/s to 54 mb/s and that helped with my download/connection speeds some, however, this is not enough. I get a measly 30 kb/s download speed over the majority of the time when on windows (I have a dual boot system here) I easy get the typical download rate of 600 mb/s. I find that during large data transfers my connection will jump to 100 mb/s, 300 mb/s and, if I am lucky, the normal connection speed. It remains at this rate for about 15 minutes, maybe 30, before dropping again to 30 kb/s, sometimes even 10 kb/s.

I have disabled IPV6 in Firefox, however, not system wide as of yet. It seems to have little effect either way. Here is Iwconfig

```
wlan0     IEEE 802.11g  ESSID:"West"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:16:B6:F4:5E:C9   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=67/100  Signal level=-63 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
*-network:0             
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: wmaster0
       version: 01
       serial: 00:0f:66:f3:e9:e6
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci ip=192.168.1.101 latency=32
```

and, if for some reason you need it, lpsci

```
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0a.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 09)
00:0b.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)

```if anymore information is needed, just post the script and tell me what it does. I have a decent grasp of most commands, but, I never know what might be thrown at me.

---

### Post by Spira on 2008-07-14
New to ubuntu (about a week) and i have the same problem. I have the Linksys WMP54G v4.1(RT61). I have searched all the net and i didn't find any sulution expept this command  iwconfig wlan0 rate 54M.
What i pointed??? That when i put iwconfig wlan0 rate 11M my internet connection boosts up. It seems tha wlan is working only to b mode???
When i set to 54Mb i had download about 80kb/s and very slow internet browsing.
At least now i can download 800kb/s. My line can do 1.2mb/s

You can do a script to auto on every reboot sets speed to 11m

sudo nano /etc/init.d/S99local

Copy in this line (you may need to change wlan0 to wlan1 or eth0 etc):
iwconfig wlan0 rate 11M
Use CTRL-O to write out, then exit with CTRL-X

Now make the script executable:
sudo chmod 755 /etc/init.d/S99local

Next update so that the script will be called as the last thing for runlevels 2-5
sudo update-rc.d S99local defaults 90

This will work and for RT2500 tha you have (v4.0)

---

### Post by Igneo676 on 2008-07-14
It worked momentarily, however, dropped again down to pitiful rates of 11 kb/s

---

### Post by Igneo676 on 2008-07-14
I notice that messing with the rate will momentarily boost performance, however, I still need help for keeping this from fluctuating

---

### Post by Igneo676 on 2008-07-14
Let's...
...bump this once to keep it on the first page.

But only once

---

