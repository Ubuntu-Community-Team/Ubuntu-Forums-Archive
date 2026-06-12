---
title: "Trouble getting a connection with Netgear WG311T"
date: 2007-02-01
forum: Networking &amp; Wireless
---

### Post by Max Carey on 2007-02-01
I've been trying to get a wireless connection in Edgy 6.10 for a couple of days now, and even after browsing the forums and going through the wireless troubleshooting guide I'm not quite there.  My card is a Netgear WG311T 108Mbps.  As far as I can tell, the correct drivers are installed (used iwconfig) and the card is communicating with my router (did an iwlist scan and iwconfig shows an access point).  I read about a few people who had problems with this card due to ivp6 being set...I tried disabling it, but ifconfig will only give me an ivp6 address, no ivp4.  I'm a Linux noob and I have no idea of what to do next, any help would be appreciated.  Thanks.

---

### Post by phossal on 2007-02-01
What is the output to iwconfig? And, are you using ndiswrapper?

---

### Post by Max Carey on 2007-02-01
iwconfig output:

lo         no wireless extensions.

wifi0     no wireless extensions.

ath0     IEEE 802.11g  ESSID:"2WIRE882"
           Mode:Managed  Frequency:2437 GHz  Access Point: 00:14:95:C2:9B:19
           Bit Rate:54 Mb/s  Tx-Power:18 dBm  Sensitivity=0/3
           Retry: off  RTS thr: off  Fragment thr: off
           Encryption key:3635-3433-3938-3439-3838  Security mode:restricted
           Power Management: off
           Link Quality:34/94  Signal level=-61 dBm  Noise level=-95 dBm
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
           Tx excessive retries:0  Invalid misc:0  Missed beacon:0

eth0     no wireless extensions.

sit0      no wireless extensions.

--------------------------------------------------------------------------------------------------------
To answer your second question, I did try installing ndiswrapper, didn't seem to have any problems (except still no internet access).

---

### Post by phossal on 2007-02-02
Max, I'm not sure I understand your response to the ndiswrapper question. Do you use it for this device? Is it properly installed? 

I think I've tried to help someone with a WG311T before. I've been able to work through the problems on a couple different Netgear devices, but a few have stumped us. I can't remember which you have. I'm gonna scan my posts and see if I can find it.

---

### Post by Max Carey on 2007-02-02
I followed the instructions on some tut to install ndiswrapper, but I have no idea if it's installed properly, or if my card is even using it.

---

### Post by phossal on 2007-02-02
Max, looking at the output to iwconfig, it appears you're connected to the router. How would you describe the problem you're having?

---

### Post by Max Carey on 2007-02-02
Maybe it's a firefox problem...I can't connect to any websites through firefox.  I think I tried pinging google but didn't get any output...maybe I should try that again.  I guess that's pretty vague so I'll get back to you when I get a chance later in the day.

---

### Post by Max Carey on 2007-02-02
I tried pinging (ping -c 4 <address>) several websites and IP addresses and got "Cannot reach network address".  Firefox doesn't load any pages either...I have no idea what could be the problem.

---

### Post by phossal on 2007-02-02
Can you ping the router?

---

### Post by chili555 on 2007-02-02
Generally, if you can connect to the router but not the world, it indicates a DNS problem. There are several things you can do. First sudo gedit /etc/resolv.conf and add the following:
```
nameserver 192.168.x.xxx
```

Or, whatever the IP address is of your router. The second, more correct way is to look in the Status page of your router and write down the DNS numbers and put those in /etc/resolv.conf.
```
nameserver 205.12.34.xxx
nameserver 206.78.90.xxx
```

Either way, you should then be able to ping [www.google.com](www.google.com) and surf the world!

---

### Post by Max Carey on 2007-02-02
I edited resolve.conf (which was an empty file) like you suggested (using the router's IP) and then tried pinging the router and google, but got the same message, "connect: Network unreachable" (I quoted it wrong earlier).

---

### Post by chili555 on 2007-02-04
Did you edit /etc/resolve.conf or, as I suggested, /etc/resolv.conf? You want to edit /etc/resolv.conf...not resolve.

Please check you work and let us know.

---

