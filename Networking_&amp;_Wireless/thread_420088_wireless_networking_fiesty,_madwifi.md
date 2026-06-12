---
title: "wireless networking fiesty, madwifi"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by kpjoyce on 2007-04-23
I have not been able to use wireless networking in 7.04, which is a bit of a dealbreaker since I don't have access to a wire.
I have been working on this for a while, assuming that the issue was with the madwifi drivers, but I'm not so sure anymore.  I've reloaded, and recompiled, and there is no change.  (tried ndiswrapper too)
I have ditched Network Manager for WifiRadar, which is able to see all of the usual wireless networks out there, but tells me that it is unable to get an IP address.
I can't mess with the access point settings, since (I'm embarrassed to say) the signal is 'borrowed' from an anonymous neighbor.
I was using Dapper before the upgrade, because I gave up trying to solve a similar problem in Edgy.

Any help is appreciated.  I am excited to get this thing up and running.  I enjoy working to solve these kinds of issues, but enjoy it more when it works out in the end.

The particulars:

> 
lshw:
           *-network:1
                description: Wireless interface
                product: AR5211 802.11ab NIC
                vendor: Atheros Communications, Inc.
                physical id: a
                bus info: pci@02:0a.0
                logical name: wifi0
                version: 01
                serial: 00:90:96:3d:73:6a
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3) latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11b
                resources: iomemory:fcee0000-fceeffff irq:11


> 
kpjoyce@kpjoyce-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11a  ESSID:"linksys"  Nickname:"linksys"
          Mode:Managed  Frequency:5.3 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:0 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-98 dBm  Noise level=-98 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


> 
kpjoyce@kpjoyce-laptop:~$ iwlist ath0 scan
ath0      Scan completed :
          Cell 01 - Address: 00:E0:B8:6B:A4:4C
                    ESSID:"Gateway"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=3/94  Signal level=-92 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:11:95:50:84:BD
                    ESSID:"Robbins Network"
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Quality=10/94  Signal level=-85 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 03 - Address: 00:0F:66:0B:20:6D
                    ESSID:"linksys"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=13/94  Signal level=-82 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 04 - Address: 00:12:17:0E:27:7F
                    ESSID:"Nate&Sarah"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=6/94  Signal level=-89 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100


---

### Post by chili555 on 2007-04-23
I would try:```
sudo iwconfig ath0 essid linksys
sudo iwconfig ath0 ap 00:0F:66:0B:20:6D
sudo dhclient ath0
```See if specifying the access point's MAC address helps.

---

### Post by kpjoyce on 2007-04-23
Thank you for your help.
Unfortunately, this wasn't the magic bullet.

> 
kpjoyce@kpjoyce-laptop:~$ iwlist ath0 scan
ath0      Scan completed :
          Cell 01 - Address: 00:11:95:50:84:BD
                    ESSID:"Robbins Network"
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Quality=5/94  Signal level=-90 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:0F:66:0B:20:6D
                    ESSID:"linksys"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=9/94  Signal level=-86 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100

kpjoyce@kpjoyce-laptop:~$ sudo iwconfig ath0 essid linksys
Password:
kpjoyce@kpjoyce-laptop:~$ sudo iwconfig ath0 ap 00:0F:66:0B:20:6D
kpjoyce@kpjoyce-laptop:~$ sudo dhclient ath0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:90:96:3d:73:6a
Sending on   LPF/ath0/00:90:96:3d:73:6a
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
kpjoyce@kpjoyce-laptop:~$ 

---

### Post by alex77 on 2007-04-23
Is your neighbor using encryption of any sort?

---

### Post by kpjoyce on 2007-04-23
I'm confident that there is no encryption involved.  I'm using their access point now on the same machine running XP ... with no key.

When I scan for access points, linksys has decent signal strength (9/94 per above).  But when I check iwconfig, the report says that there is no usable signal at all.  Why would one utility see a signal and another not?  I'm afraid I just don't know enough about how all this is put together to figure it out.

thanks

---

### Post by kpjoyce on 2007-04-23
Any more ideas?
I'm not ready to give up.
Your insight is appreciated.

---

### Post by chili555 on 2007-04-24
Would you please try```
sudo iwpriv ath0
```and see if you have *auth_mode* If so, please do:```
sudo iwpriv ath0 auth_mode
```and let us see what mode it thinks it's in.

Also, I note your iwconfig lists the rate and power as zero. Let's try:```
sudo iwconfig ath0 rate auto
sudo iwconfig ath0 txpower auto
sudo iwconfig ath0 sens 2
```Can you connect now?

---

### Post by kpjoyce on 2007-04-24
Alright.

iwpriv gave me two options: authmode and get_authmode

> 
kpjoyce@kpjoyce-laptop:~$ sudo iwpriv ath0 authmode
The command authmode needs exactly 1 argument(s)...
kpjoyce@kpjoyce-laptop:~$ sudo iwpriv ath0 get_authmode
ath0      get_authmode:1  


Trying to set scan and power using iwconfig did not take.  So maybe I'm not communicating with my wireless hardware as well as I hoped.

> 
kpjoyce@kpjoyce-laptop:~$ sudo iwconfig ath0 rate auto
kpjoyce@kpjoyce-laptop:~$ sudo iwconfig ath0 txpower auto
kpjoyce@kpjoyce-laptop:~$ sudo iwconfig ath0 sens 2
kpjoyce@kpjoyce-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11a  ESSID:"linksys"  Nickname:"linksys"
          Mode:Managed  Frequency:5.3 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:0 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-98 dBm  Noise level=-98 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Attempts to connect failed.

Thanks for your help.  Where would you guess is the problem?  Still the driver?  Is it the network management utility?  Should I have Network Manager and WifiRadar completely uninstalled?

---

### Post by chili555 on 2007-04-24
> Where would you guess is the problem? Still the driver?I'd guess not, because it scans, responds to iwconfig, etc. You might look at:```
dmesg | grep ath0
sudo cat /var/log/messages | grep ath0
```Look for any errors or complaints.

Have you disabled NetworkManager? What process did you follow? You certainly don't want NM and wifi-radar battling for world domination. If you disabled NM, did you uncheck Roaming in System -> Administration -> Network?

---

### Post by jgcamp99 on 2007-04-24
Install and use WiFi Radar. I had to get the restricted modules under Edgy and then use WiFi Radar and Network Monitor (Sun) to go back and forth between them to get it to work with an Orinoco Gold ABG. as you can see your ath0 is 5 Ghz, which is "a" wireless, it needs to be 2.4 Ghz for "b" and "g".

After it worked in Edgy, I network update/upgrade to 7.04. It's still a little flakey, but the WiFi Radar and Network Monitor (Sun) with the restricted modules still work.

I have another card, a Netgear MA401RA Rev D that now works out of the box with Feisty Fawn 7.04. I use it instead of the Orinoco ABG since upgrading last Friday.

---

### Post by jgcamp99 on 2007-04-24
> **chili555 said:**
> Have you disabled NetworkManager? What process did you follow? You certainly don't want NM and wifi-radar battling for world domination. If you disabled NM, did you uncheck Roaming in System -> Administration -> Network?

Not on my Dell L400, what he has to do is make sure a Network Manager icon is placed on either top or bottom panel, right click on it and open it first. Set it to ath0 (even if you have to type it in), make sure you have manually configured it correctly for the wireless network there first. Once you get the wireless to get the blue signal reception bars instead of the red ones, you can open WiFi Radar to connect to the network there, but make sure that it is configured as well. It may not get the IP address from your router the first time, but usually the 2nd time the IP address is obtained in short order when repeated immediately after the first attempt. I had to get both to work before it would stay connected indefinitely. Next time you reboot, more than likely you have to go thru the same process. I did and sometimes it was easy, other times it took a few tries. I have to play around with it for a few minutes until it catches, that's the main reason why I use the Netgear MA401RA Rev. D, it's automatic and doesn't require fidgeting or finesse to get it going.

---

### Post by jgcamp99 on 2007-04-24
This is what it looks like on my computer. I made the bottom panel size 100 so you can see the blue bar next to the dual monitors icon on the bottom panel (blue diamond shape with blue up arrows) that I referred to earlier The Network Monitor is 2.12.1 and it's to the right, to the left is WiFi Radar. It took me a couple of tries to get it up from a cold boot. The other screenshots show other aspects. And how I know my card is also connected, there are two leds on the card itself, when it's not working right, only one is on, or they both alternate, but neither is simultaneously on. When it's working properly, they both blink on and off simultaneously, that is, they are both on and off at the same time as they blink.

---

### Post by kpjoyce on 2007-04-25
I've never seen anything concerning in /var/log/messages.  But I have reverted to Edgy to see if it would prove any easier.  So far, things are very similar.

I had completely removed NetworkManager using Synaptic, and installed Wifi Radar.  Now that I'm in Edgy, I'll try intsalling them both per jgcamp's suggestion.

In the meantime, there are a few things that I don't yet understand:

First, why both wifi0 and ath0?  I understand about the proprietary driver creating a device called ath0, but why does wifi0 need to exist?  My wireless card thinks its logical name is wifi0, but all drivers are associated with ath0.  When I used madwifi in dapper 6.06, this duality didn't seem to exist (at least wifi0 didn't)... and things worked.

Speaking of madwifi in dapper, the ath_pci version that worked was 0.9.6.0 (experimental), and the versions used in the later ubuntu releases are earlier.  I can't find a version of madwifi higher than 0.9.3, but I'm probably confusing madwifi version and ath_pci version.  I'll look again after recompiling from the latest snapshot.

What role is the module wlan playing in all this?  It is always hanging around, and it is not something that I have poked around yet.

Thank you for your help.

---

### Post by kpjoyce on 2007-04-25
Okay, I'm getting somewhere.
I pursued the 'experimental' version of madwifi that worked for me in dapper.  It was a branch of development in madwifi that eliminates the proprietary HAL.  I compiled the latest snapshot of that branch (which, curiously, is still earlier than my dapper version) and things are working much better now.  iwconfig shows me actually connected to the access point, and scans show a much more expected list of access point options.  (For a while there, scan would only show one obscure access point, and not the one I wanted.)
Of course, dhclient is still not able to get me an IP address.  But progress is progress.

> 
kpjoyce@kpjoyce-laptop:~$ iwconfig
lo        no wireless extensions.

ath0      IEEE 802.11b  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:66:0B:20:6D   
          Bit Rate:11 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=11/94  Signal level=-84 dBm  Noise level=-95 dBm
          Rx invalid nwid:262  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:75  Invalid misc:75   Missed beacon:6

eth0      no wireless extensions.

sit0      no wireless extensions.


kpjoyce@kpjoyce-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:12:17:08:58:F8
                    ESSID:""
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=4/94  Signal level=-91 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:0F:66:0B:20:6D
                    ESSID:"linksys"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=8/94  Signal level=-87 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
          Cell 03 - Address: 00:12:17:0E:27:7F
                    ESSID:"Nate&Sarah"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=8/94  Signal level=-87 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.


---

### Post by stchman on 2007-04-25
> **kpjoyce said:**
> Okay, I'm getting somewhere.
I pursued the 'experimental' version of madwifi that worked for me in dapper.  It was a branch of development in madwifi that eliminates the proprietary HAL.  I compiled the latest snapshot of that branch (which, curiously, is still earlier than my dapper version) and things are working much better now.  iwconfig shows me actually connected to the access point, and scans show a much more expected list of access point options.  (For a while there, scan would only show one obscure access point, and not the one I wanted.)
Of course, dhclient is still not able to get me an IP address.  But progress is progress.

Try installing the madwifi driver on my website:

[http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html)

It worked for me on my laptop's Atheros card.

---

### Post by kpjoyce on 2007-04-25
Thanks.  I had actually found the HOWTO on your website when I searched the forums before posting.  It was a jumping-off point for me.  The driver you used, the latest release, worked the same as the madwifi version that shipped with Fiesty for me.  In fact, I think that the first post of the thread is a printout of my system using v. 0.9.3.

The madwifi-old-openhal branch is working best for me, but not working.  I feel that I'm close, though.  You know when you can see your hotel from the highway, but have no idea how you drive there?  That's me right now.  I'm able to scan and connect exactly as I would expect, but then no network.

The only anomaly that I've found is that 'Network Tools' in gnome says that ath0 is using ipv6 protocol and nothing else.  Obviously, I'd want it to use ipv4.  Maybe I need to connect via DHCP first.

---

### Post by jgcamp99 on 2007-04-25
Does your's connect quickly upon desktop load ? I have to play with it to get it to catch, even manually configure the network I connect to with the Orinoco Atheros card. The Netgear (I believe it uses Prism driver) card seems to work much better and simply connects without piddling around with the other network and wireless software. The upper/top panel wireless icon in that case shows that I'm using a manually configured network. I think the reason why mine shows the ath0, and wifi0, is that the Netgear was even more difficult than the Orinoco in Edgy. Then there's the 3rd card that I have yet to get to work at all, a D-Link DWL-650+ that is enhanced b+ (22 mbps) and uses a TI ACX-100 chipset. I've used the three cards, they all work fine in Windows (except the drivers for Windows for the Orinoco conflict when I use the Prism interface, but I figured the one that worked best/easiest in Ubuntu was the card this Dell L400 would use, no questions asked. I like the Orinoco, it has A,B & G capability, the Netgear is strictly B and the D-Link B and B+. It doesn't work with either Edgy or Feisty, that is I failed. Either of the other two wifi cards, they were tough nutz to crack in Edgy, I don't think they work perfectly, but they do get reception and internet with continuous connectivity with a little tweaking at initial desktop load up. I accept it for what it is and then surf internet with no issues after this ritual.

---

### Post by kpjoyce on 2007-04-26
Okay, frustration is setting in.  How long have I been working on this one issue now?

I swear that I saw it work this morning.  With a fresh install of fiesty and a fresh compile and install of the latest madwifi-old-openhal, I rebooted and Network Manager told me that it had connected to a wireless access point.  I told Network Manager to disable the wired connection (I had taken the laptop elsewhere to run updates and download build-essential packages), and was able to load cnn.com!

But that was it.  Next boot, it was back to the same story.  Everything looks perfect, I can see all the available networks, and I can connect to the one I want.  iwconfig looks perfect, but I can't get an IP assigned.

I don't know what's next.  Crawl back to Dapper, maybe.  Who says my issues with that release will be any easier?  But they have workarounds.

---

### Post by footloose123 on 2007-04-26
Hi,

I recently had the near exact same problem as you, only with a ralink 2500. The problem was that I installed the low-latency kernel as a suggestion from the install of my video drivers. I found that the package that it suggested wasn't the meta package but just the basic stuff without modules. After installing the meta package that included all the goodies my problem was solved and wireless was working as expected. 

hth

---

### Post by ebohm on 2007-04-26
I have a very similar problem.

IBM Thinkpad G40 D-Link G650 wireless card.

Worked great under edgy eft using the network manager.  I upgraded to feisty and it can't even figure out that I have a wireless card.  There isn't even an ath0 device!

What happened? :confused: 

On a probably unrelated note, feisty also completely broke (only the shadows of windows were visible, so it was entirely unusable) my beryl xgl so I had to remove all of that to get gnome working again.  

So far Feisty is looking like a very big downgrade in usability.  :(

---

### Post by DougJamal on 2007-04-27
Reinstall the networking tools and the WPA supplicant.  That was all it took for me to be able to network wirelessly using WPA2.  I installed Feisty the day before yesterday. initially, I was unable to use my wireless card (Intel 3945abg) even though Feisty detected it and indicated that it was using a restricted driver.  After reinstalling the networking tools as well as the WPA supplicant, my wireless network icon appeared, detected my access point and its settings (WPA2) and then asked for my passphrase.  Voila!  I been wirelessly networking ever since.  I hope this works for you.  Take care.

---

### Post by ebohm on 2007-04-27
Turns out my beryl problem was part of the weak link.  Didn't realize I needed to select the restricted drivers (again?) for the new version and then update.  Now it works!

---

### Post by Monkus on 2007-05-07
I have a Gateway MX6121 with a D-Link G650 wireless card. I worked on it for almost a month and was about to pull out what little hair I have when I discovered the solution. 
I uninstalled the linux-restricted and installed madwifi-old. No problem, everything works fine. Perhaps this will help you.  Good luck.  :)

---

### Post by nomenklatura on 2007-09-16
I've been having the same problems outlined in this thread, and after 48 hours have got absolutely nowhere. I am deeply frustrated at this state of affairs, since the Atheros AR5212 worked absolutely fine in previous versions of Ubuntu (although I must say things got a little worse in 6.10 - all that messing around with ndiswrapper).

Can anyone point me to a solution to this problem?

Thanks

---

