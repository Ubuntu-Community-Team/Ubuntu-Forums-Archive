---
title: "XFCE Wireless Problem"
date: 2008-02-19
forum: Networking &amp; Wireless
---

### Post by uberlube on 2008-02-19
First off I would like to just mention that I am using XFCE Linux Mint. I know that you are probably going to tell me to go ask in the Mint forum but I really dont like using it, I prefer Ubuntus. Anyway that aside here is my issue. I have installed my drivers for my wifi (broadcom43xx) and have it working properly, using Wicd Manager I can see all the networks in my area plus my own. Now the problem is that after putting in my WEP key and all that jazz I still cant connect. I feel it might be something i changed in the Preference tab. I changed the 'Wireless Interface' field from whatever it was to my usual 'wlan0' without even thinking about it and now I cant remember what was originally there. If anyone can suggest what the other inferface would have been, or knows what the problem might be Id appreciate the help. THNX:)

---

### Post by uberlube on 2008-02-19
Howard Dean says........BYAAAH!!!!

---

### Post by dmizer on 2008-02-19
to figure out what your actual wireless interface designation is, check this command:

```
sudo iwconfig
```

---

### Post by uberlube on 2008-02-19
Here is the output that:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Like I said it seems to be working correctlly and I can see all the networks available but cant log into mine.

---

### Post by jhetrick62 on 2008-02-19
I believe the WEP may get held inside of gnome keyring.  At least I'm pretty sure that applies in gnome, not sure if it's still true in xfce.

Can you connect if you open up the network without WEP?

Jeff

---

### Post by uberlube on 2008-02-20
I have not really used gnome. Always been a KDE fan and the only reason I am trying xfce is to get a faster work environment out of my notebook. Gnome keyring is installed but when I open it up it doesnt give any relevant info. If anyone wants to take over here Id really like to get this up and running. Like I said before I can see the networks, but when I try to log into them it hangs on 'obtaining IP address'

---

### Post by uberlube on 2008-02-20
Anyone?

---

### Post by jhetrick62 on 2008-02-21
Honestly, unfortunately, wireless drivers in Linux are very squirrely at times and not as efficient as we may think.  I built a new computer over the weekend with a usb wireless adapter that worked just fine out of the box with Ubuntu 6.10.  When installing Gutsy, it all looked good and worked when I was close to the router, but when moved 50 feet away, it had tons of errors and many times would not sign in on WEP and sometimes without WEP.

I blacklisted the driver, installed ndiswrapper and built the driver from WinXP files and it has worked flawlessly since then.  

You might want to take this approach with ndiswrapper and see if it solves your problem as it is relatively quick and should fix your issue.

Goodluck,
Jeff

---

### Post by dmizer on 2008-02-21
from the wicd FAQ found here: [http://wicd.sourceforge.net/wiki/doku.php?id=faq](http://wicd.sourceforge.net/wiki/doku.php?id=faq)

> - Why doesn't my WEP key work?

Sometimes this can be fixed by putting quotation marks " " around the key, inside the text box.

---

### Post by uberlube on 2008-02-21
> **jhetrick62 said:**
> Honestly, unfortunately, wireless drivers in Linux are very squirrely at times and not as efficient as we may think.  I built a new computer over the weekend with a usb wireless adapter that worked just fine out of the box with Ubuntu 6.10.  When installing Gutsy, it all looked good and worked when I was close to the router, but when moved 50 feet away, it had tons of errors and many times would not sign in on WEP and sometimes without WEP.

I blacklisted the driver, installed ndiswrapper and built the driver from WinXP files and it has worked flawlessly since then.  

You might want to take this approach with ndiswrapper and see if it solves your problem as it is relatively quick and should fix your issue.

Goodluck,
Jeff

I already installed my drivers using ndiswrapper, and the wirless is working. The problem is that i still cant connect to any networks.

here are my outputs: iwconfig

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

ifconfig:

```
 eth0      Link encap:Ethernet  HWaddr 00:1B:24:57:18:A5  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1627 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1497 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1309967 (1.2 MB)  TX bytes:246673 (240.8 KB)
          Interrupt:19 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:1A:73:6E:CA:13  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 Memory:b8000000-b8004000 

wlan0:ava Link encap:Ethernet  HWaddr 00:1A:73:6E:CA:13  
          inet addr:169.254.5.210  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:22 Memory:b8000000-b8004000 

```


And also tryed to wrap quotations around the code. Didnt work either.:confused:

---

### Post by dmizer on 2008-02-22
are you disconnecting your wired internet before you try to connect with your wireless internet?

---

### Post by uberlube on 2008-02-22
Yes I am. You know this is really unfortunate, I never had this many problems usind KDE. I love KDE but i wanted less of a resource hog for my laptop so I decided to try XFCE. O well Back to KDE i guess.

---

### Post by jhetrick62 on 2008-02-22
Just by chance, when you built your wireless drivers with ndiswrapper, did you use WinXP drivers?  You didn't use Vista drivers, correct?  Vista drivers don't work very well for this process.

Jeff

---

### Post by dmizer on 2008-02-24
your problem is not related to xfce.  your problem is related to wicd.  xfce's networking configurator should have the ability to configure your card for wep.  you may have to uninstall wicd before you can get xfce's regular configurator to work.

---

### Post by uberlube on 2008-02-24
LoL, thanks for getting back to me. I decided to switch back to Mint KDE and the wireless is working just fine now, but if I decide in the future to try again ill do what you suggested. :)

---

