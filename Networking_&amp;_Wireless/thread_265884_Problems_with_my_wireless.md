---
title: "Problems with my wireless"
date: 2006-09-26
forum: Networking &amp; Wireless
---

### Post by Lillis on 2006-09-26
Hi!
I have just recently installed Ubuntu 6.06 but I cant get my wireless network working. I'm getting really frustrated now. Been searching all over the web but I'm still on square 1.

I have a Dlink DWL-510 rev. C2 and Ubuntu installed this as ra0 (Ralink), which it should. I then change the settings under Administration->Network and I can see my essid from my wireless. I type in the encryption key I have for my network, but nothing works. 

**Iwconfig gives me this:**
ra0
RT61 Wireless ESSID:******
Mode:Managed Frequency 11 MHz Access Point: ****************
Bit Rate=54 Mb/s
RTS thr:off Fragment thr:off
Link Quality=91/70 Signal level:-48 dBm Noise level:-79 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

**and ifconfig:**
Link encap:Ethernet HWaddr *****************
inet addr:192.168.1.15 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr:fe80::215:e9ff:fef8:29d2/64 Scope:Link
UP BROADCAST RUNNING MULTICAST  MTU:1500 Metric:1
RX packets:62131 errors:0 dropped:0 overruns:0 frame:0
TX packets:37355 errors:0 dropped:0 overruns:0 carrier:0
collisions:17 txqueuelen:1000
RX bytes:4939064 (4.7 MiB) TX bytes:23604 (23.0 KiB)
Interrupt:11

**/etc/network/interfaces:**
auto lo
iface lo inet loopback

auto ra0
iface ra0 inet static
wireless-essid ********
wireless-key s:********
address 192.168.1.15
netmask 255.255.255.0
gateway 192.168.1.1


The funny thing is that I can see my essid in the config, but I cant ping anything. And the frequency working at 11 MHz, what about that?!?!

Please help me, I really want this to work.
Cheers!

---

### Post by og-emmet on 2006-09-26
Give this a spin in /etc/network/interfaces

auto ra0
iface ra1 inet static
     pre-up ifconfig ra0 up
     pre-up ifconfig ra0 down
     pre-up ifconfig ra0 up
     pre-up ifconfig ra0 down
     pre-up iwconfig ra0 essid "******"
     pre-up iwconfig ra0 mode Managed
     pre-up iwpriv ra0 set AuthMode=WPAPSK
     pre-up iwpriv ra0 set EncrypType=TKIP
     pre-up iwpriv ra0 set WPAPSK="*********"
     pre-up ifconfig ra0 up
     address 192.168.1.15
     netmask 255.255.255.0
     gateway 192.168.1.1

---

### Post by Lillis on 2006-09-27
It didn't help. I have now turned off the encryption on my router and switched to dhcp instead, but I still cant access the network. I dont even get an IP. I only have a inet6 address :-?

---

### Post by wieman01 on 2006-09-27
> **og-emmet said:**
> Give this a spin in /etc/network/interfaces

auto ra0
iface ra1 inet static
     pre-up ifconfig ra0 up
     pre-up ifconfig ra0 down
     pre-up ifconfig ra0 up
     pre-up ifconfig ra0 down
     pre-up iwconfig ra0 essid "******"
     pre-up iwconfig ra0 mode Managed
     pre-up iwpriv ra0 set AuthMode=WPAPSK
     pre-up iwpriv ra0 set EncrypType=TKIP
     pre-up iwpriv ra0 set WPAPSK="*********"
     pre-up ifconfig ra0 up
     address 192.168.1.15
     netmask 255.255.255.0
     gateway 192.168.1.1
No, this is not correct and refers to WPA rather than WEP.

---

### Post by wieman01 on 2006-09-27
Lillis, you ARE using WEP I take it?

---

### Post by Lillis on 2006-09-27
Yes I do. I didnt used everything og-emmet proposed. 
Only this:

auto ra0
iface ra1 inet dhcp
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up iwconfig ra0 essid "******"
pre-up iwconfig ra0 mode Managed
pre-up ifconfig ra0 up

---

### Post by wieman01 on 2006-09-27
Ok, your original "interfaces" file was fine. Please restore it. Then try this & post the stuff:
> iwlist ra0 scan
BTW: Your first post suggests that you have been connected. What actually makes you say that "nothing works"? Is it the internet connection?

Can you ping your gateway:
> ping 192.168.1.1

---

### Post by Lillis on 2006-09-27
Crap, now I've messed it up so bad that gnome wont start. I'm just gonna reinstall it and get back to you later ](*,)

If I cant get this to work I will drill a hole in the roof and install a cable :-?

---

### Post by Lillis on 2006-09-27
Ok, this is what I get when I scan with no encryption:

Scan completed:
Cell 01 - 
Address: 00:12:A9:05:D6:B2
Mode: Managed
ESSID:"*********"
Encryption key: off
Channel: 11

When I ping 192.168.1.1 it says "Network is unreachable"

I can see the computer on my routers client list though.

---

### Post by wieman01 on 2006-09-27
Ok, a few more things:

1. You ARE using static IP rather than DHCP on both ends (router, clients), correct?
2. No firewalls on the clients?
3. No tools such as "wirless assistant" or "wifi-radar"?
4. Encryption/authentication (WEP) completely turned off)?

Your "interfaces" file must look like this now (WEP turned off):
> auto lo
iface lo inet loopback

auto ra0
iface ra0 inet static
wireless-essid [COLOR="Red"]**your_essid**[/COLOR]
address 192.168.1.15
netmask 255.255.255.0
[COLOR="Blue"]network 192.168.1.0
broadcast 192.168.1.255[/COLOR]
gateway 192.168.1.1
[COLOR="Blue"]dns-nameservers 192.168.1.1[/COLOR]
I have added a few things, perhaps that helps.

Now restart the network and tell us what the output says:
> sudo /etc/init.d/networking restart
Also do one more scan:
> iwlist ra0 scan

---

### Post by Ralphthedog on 2006-09-28
Can I suggest the drivers/rutilt config. tool here:

[http://www.ubuntuforums.org/showthread.php?t=240669](http://www.ubuntuforums.org/showthread.php?t=240669)

My rt61 is up and running OK (with WEP) using these.


RTD.

---

### Post by Lillis on 2006-09-28
I added the lines you suggested wieman01 and restarted my network, but the process hanged and when I restarted the computer, I couldn't login. So now I have reinstalled Ubuntu AGAIN (think I've done this 9 times now :evil: )

I have donwloaded and installed the drivers and utlit that RTD suggested and am now going to see what happens.

Do I have to reboot the computer to access this utilt config tool, or how do I open it? I'm noob to these things :)

---

### Post by Lillis on 2006-09-28
Ahh, I managed to open the Rutilt now, yay progress :D 

I've added a profile for my network and use dhcp now, and *poff*. Now I get an IP from the router :-D

Anyone knows how I can make this Rutilt config tool to start automaticly at bootup?

---

