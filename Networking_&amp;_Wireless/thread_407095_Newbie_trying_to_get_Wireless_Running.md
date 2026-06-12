---
title: "Newbie trying to get Wireless Running"
date: 2007-04-11
forum: Networking &amp; Wireless
---

### Post by mceldon on 2007-04-11
Hi,

I've got as far as I can with a new install of Edgy but now I'm pretty lost.

OK - my wireless card seemes to be operating fine, its in the Network settings, the driver displays correctly after 'lshw -C Network' listing the PRO/Wireless 2200BG Network Connection.

I'm even getting the correct available networks on 'iwlist scanning' ! So I'm stumped because I can't ping anything or connect to the network in any way - I keep getting Network is unreachable.

I looked into installing network manager but couldn't find a .deb package which sent me off on a tangent, now I'm a bit frustrated.

Help would be greatly appreciated.

Thanks,

Mac:confused:

---

### Post by floke on 2007-04-11
try this. open a terminal (accesories/terminal) and enter 

sudo apt-get install wifi-radar

you can also use 

sudo apt-get install network-manager-gnome

hope this helps

---

### Post by mceldon on 2007-04-11
I guess I need to be connected for that to work ? Error says COuldn't find package.

Thanks,

Mac

---

### Post by floke on 2007-04-11
Have you actually enabled wireless and entered your connection data?
Sounds silly but I couldn't work this out in my first time in Edgy.
Turned out I was trying to give it too much info. all I had to do was enter the ESSID, the encryption key and select DCHP automatic and leave the rest blank.

What do you get if you type 'iwconfig' in a terminal?

---

### Post by mceldon on 2007-04-12
IWConfig gives me: 

eth1  unassociated ESSID:"mynetwork"

How do I associate with a network ?

I have put the basics in there but no joy.

Mac

---

### Post by floke on 2007-04-12
What else does iwconfig give you - it must be more than that?

Anyway - from System/Admin/Network
Make sure you have the SSID entered exactly as it appears in iwconfig; enter the key (make sure you select the right encryption); and then select DHCP from configuration and leave everything else blank.

Does that work?

---

### Post by mceldon on 2007-04-12
OK - It says:

eth1      unassociated  ESSID:"machome"  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

If you recall I can actually see the available wireless networks in the vicinity.

I don't need to update drivers do i ?

Thanks for the help,

Mac

---

