---
title: "Wireless network problems (wifi-radar)"
date: 2007-03-28
forum: Networking &amp; Wireless
---

### Post by jochem on 2007-03-28
Hello!

I recently installed Xubuntu, my first linux distro, on the old computer of my mother.
Everything looks great, feels great, works great, except the internet connection, wich is ofcourse quite important for my mother.

Important note: The computer only has a wifi card, no normal ethenet network card, it's broken.

I installed ndiswrapper using .deb files, and loaded the winxp drivers for my sitecom wl-140.
(not sure if it works correctly though)

I also installed network manager, also using .deb files.
(wich I don't see anywhere in the system tray)

Finally I installed wifi-radar. wich sees my connection, and connections of neighbours. This should be a good sign, the wifi-card is working, right?

Now If I input my IP address, gateway, subnet mask, dns server, like I did on my winxp computer, I don't get connected, and I can't go into my router...

I have WPA disabled, and I don't use any connection commands.

I already spend a few days getting it to work, but I'm almost at the point putting windows 98 back on it, wich I really really hate.

Could somebody help me out? If you want more info, I'll try to post it as fast as possible!

regards,

Jochem


EDIT:
My router: Davolink DV-201AMR

---

### Post by jochem on 2007-03-28
Oh, and I'm using Xubuntu 6.10 Edgy Eft.

I still haven't fixed the problem, I'm so frustrated that I can see my wlan connection, and from the neighbour. Did I do something wrong in wifi-radar, or isn't my sitecom wl-140 card functioning correctly? Should I buy a new wlan card?

---

### Post by kubaknopp on 2007-03-28
I had a very similar problem. And the answer is: MAC filtering enabled on the router. Who knows? Maybe it will work for you as well?
By the way...  Xfce Desktop environment is a little bit cruel solution for your mother, don' you think?

---

### Post by jochem on 2007-03-28
ah well, the only things she need is three launchers, one for firefox, one for email, and one for a document writer=)

You mean mac filtering is enabled at the moment? No it isn't =(

Thanks for your reply!

---

### Post by jochem on 2007-03-29
still haven't figured it out!

help appreciated!

---

### Post by fdrake on 2007-03-29
open the terminal and paste the outputs of these commands on the next post:
sudo iwconfig  (this shows your wireless config.)
sudo iwlist <interface> scanning  (this scan the network available around you with all the info needed)
tell us your network's name.

---

### Post by Pizarro on 2007-03-29
You have the same problem as me !!!! WiFi Radar finds 3 networks , but connect to mine no way, fails to get an ip address.   
BTW iwlist gives
martyn@martyn-laptop:~$ sudo iwlist
Usage: iwlist [interface] scanning
              [interface] frequency
              [interface] channel
              [interface] bitrate
              [interface] rate
              [interface] encryption
              [interface] key
              [interface] power
              [interface] txpower
              [interface] retry
              [interface] ap
              [interface] accesspoints
              [interface] peers
              [interface] event
martyn@martyn-laptop:~$

---

### Post by jochem on 2007-03-29
Oke, my results:

wilma@kutcomputer:~$ sudo iwconfig
Password:
lo        no wireless extensions.
eth0      no wireless extensions.
eth2      IEEE 802.11b  ESSID:"Onder"  
          Mode:Managed  Channel=13  Access Point: 00:15:F2:22:AB:57   
          Sensitivity=0/200  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
wilma@kutcomputer:~$ sudo iwlist eth2 scanning
eth2      Scan completed :
          Cell 01 - Address: 00:15:F2:22:AB:57
                    ESSID:"Onder"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:13
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:100  Signal level:0  Noise level:0
                    Extra: Last beacon: 92ms ago
wilma@kutcomputer:~$

lay-out may be bit weird, windows messed it up. Hope this makes some things clear.

Waiting for answers:D

---

### Post by jochem on 2007-03-29
Is this enough to locate the problem? Could somebody give it a try?:)

thanks in advance!

---

### Post by jochem on 2007-03-29
bring my post up!:P

---

### Post by jochem on 2007-03-29
Could somepody take a look at the log?

---

### Post by jochem on 2007-03-30
my result after iwconfig and iwlist:

wilma@kutcomputer:~$ sudo iwconfig
Password:
lo no wireless extensions.
eth0 no wireless extensions.
eth2 IEEE 802.11b ESSID:"Onder" 
Mode:Managed Channel=13 Access Point: 00:15:F2:22:AB:57 
Sensitivity=0/200 
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
wilma@kutcomputer:~$ sudo iwlist eth2 scanning
eth2 Scan completed :
Cell 01 - Address: 00:15:F2:22:AB:57
ESSID:"Onder"
Protocol:IEEE 802.11bg
Mode:Master
Channel:13
Encryption keyn
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
48 Mb/s; 54 Mb/s
Quality:100 Signal level:0 Noise level:0
Extra: Last beacon: 92ms ago
wilma@kutcomputer:~$

somebody has an idea about whats wrong?

---

### Post by stealth17 on 2007-05-07
you are trying to connect to an encrypted access point, are you sure you have the correct security key?

---

### Post by astrosoup on 2007-05-11
I am having the same problem. I am working on a Compaq with a dreaded Broadcom 43xx card. I had the card working to the point where WiFi Radar would recognize it, updated to Feisty Fawn and fiddled with it to get it recognized again. But as far as I can tell, Wi-Fi radar should have some sort of "connect" button or something, and it doesn't.  It finds my network as well as several neighboring ones, but it never connects to anything. Creating an additional connection does not help me either. The "Edit" "Delete" and "Disconnect" buttons warrant no response. I'm brad new to Linux, so I'm not sure where to go from here.

---

