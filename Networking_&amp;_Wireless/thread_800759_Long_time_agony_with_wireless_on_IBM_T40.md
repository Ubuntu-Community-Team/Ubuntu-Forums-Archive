---
title: "Long time agony with wireless on IBM T40"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by raid996 on 2008-05-20
Please help me out here, because this thing is driving me crazy.
I have at the present time an IBM T40 (awesome pc by the way) with feisty (which works flawlessly).

The first problem I have is that the lspci command outputs states:
```
02:02.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
```
in real-life however I can't even see g protocol networks let alone connect to one, anyway, I think maybe my Wifi card could be broken or flawed and I dont want to blame it on Ubuntu who has always proven to have exceptional HW support.

So I bought a Wifi PCMCIA Card with b protocol support so I could connect to one of the public networks when I'm at college, it was recognised out-of-the-box and it can see the Wifi networks but with a real low quality and signal strenght (all of them are under 15%) even so I tried to connect but every time it gets an IP as soon as I try to go through the auth process the networks drops like a ton of bricks and I have to wait again to reconnect and so on.

I thought I had chosen the wrong card and bought a lousy one, so I bought another one with g protocol and all... as before it worked out-of-the-box and the signal strength was MUCH better (around 25-35%) but same as before, every time I tried to connect it would constantly disconnect and reconnect.
I tried not to use network-manager and manage the whole through the /etc/network/interfaces file, the problem changed because whenever I restarted the network service with
```
sudo /etc/init.d/networking restart
```
it wouldn't find any dhcp server, after a few minutes the connection would like wake-up miraculously and allow me to authenticate and use internet for no more than 10 minutes before droping again.
:confused::confused::confused::confused::confused::confused::confused:

Haven't finished. I went though a ton of HOWTOs and threads on this forum, I tried to use ndiswrapper with windows drivers but it wouldn't even connect. Anyway I noticed that even when singal strength was over 25% the quality was poor so I concluded I had bought another lousy USB Wifi pen... and bought a new one which everyone say works out-of-the-box and works great, a friend of mine uses it with windows and told me it had good reception.
I bougth an ASUS WL 167g and it does work AWESOME, as I plug it in I have to wait a bit then it shows me the list of networks available, the strenghth of signal and the quality are great but it just doesn't connect to the network. If i click it just through the IP assignment process and then disconnects...
So I removed network-manager and set it up manually... NADA!
I installed Wifi-radar and used that one... NADA!
I tried to install its drivers from asus but I couldn't make it and dropped the idea basically because everyone says it works great on their pc's, so it can't be a driver problem.

With time I noticed also that with this new USB Wifi pen when I try to connect to a network and then id disconnects, the network disappears from the list for some 5 to 10 minutes before it shows up again and I can try to reconnect.

I simply dont understand wht's happening, I've always had problems with this wireless stuff, and I'm kinda tired of it... ubuntu works perfectly for me and i don't even think of going back to windows
It's been alreayd 2 years since I completely switched to linux and I'm not going back. But this wireless stuff is really annoying, everytime I need to connect to internet I find out I can't. Please give me some direction cause I couldn't find anything useful in the forum.

One more thing, both my usb wifi pendrives show up on the "Administration&#8594;Networks" Menu with a wmaster and a wlan0, I tried configuring both on the /etc/network/interfaces and then one at a time, it still doesn't work.
One more thing, when I have to choose which interface to use to connect on the Network Applet in the panel I always find a wlan0:avahi interface and it doesn't work but it has an IP assigned to it, if i change it to wlan0 it shows the signal strength but it doesn't have an IP and i can't authenticate.

I mean, it's a mess and I couldn't get to understand what to do. So please help me out here....

---

### Post by lisati on 2008-05-20
I'm baffled by it too: LSPCI reports the same kind of card for my Toshiba's wifi card, which works brilliantly with bpth Feisty & XP...... Perhaps it's not so much the card but some other setting

Anyone?

Correction: Mine's a AR5005G, not an AR5212, but otherwise identical report from lspci

---

### Post by raid996 on 2008-05-20
Sigh! My desperation grows...

---

### Post by chili555 on 2008-05-20
Your Atheros requires non-free drivers which you can get with:```
sudo apt-get install linux-restricted-modules-generic
```Then you will see a Restricted Drivers Manager in System -> Administration. Enable the Atheros driver and you should be able to configure your card.

Let's see *iwconfig* for the card that gets 25-30%, please.

My T40 has the Aironet 350 card and works quite well; however, changing the internal card is a formidable task. T40s are getting quite cheap on Ebay these days; I almost want to get another just to have a backup!

---

### Post by raid996 on 2008-05-21
Already installed those and the drivers are already in use, at the present time I only have the Asus Wifi Pendrive on me (the last one I bought), maybe, and I'm saying MAYBE, since I wrote the post on this forum I may have found some sort of configuration to make it work...
I just kept trying and trying and today, for the first time in the past 2 years, I am NOT having problems with the WiFi at college...

I'll check in later to see if this is working steadily or alternatively just like all the other times...
Here is the output of the iwconfig command with the Asus pen, I managed to connect with WICD, I saw it had gone though some development and decided to give it another shot, yesterday I installed it through their repository, and it seems that the last version has covered my connection problems.

```
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Rm3-WiFi-Shared"  Nickname:""
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:19:E0:10:2B:D4   
          Bit Rate:11 Mb/s   Tx-Power:14 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=32/94  Signal level=-64 dBm  Noise level=-96 dBm
          Rx invalid nwid:1673  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wmaster0  IEEE 802.11g  Channel:0  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

One thing I don't get is that I installed WICD yesterday, and have never connected to the college network with it, the network is WEP protected, yet WICD connected without asking me for the key, and it works!
I just don't get it, I mean, i'm happy it is working but it just doesn't make any sense.
Anyway, I have to say this forum is awesome... as soon as I wrote in it the problem solved by its own without even needing a reply lol... :P:P

Try to beat THAT !!!

---

### Post by raid996 on 2008-05-22
WRONG AGAIN!!!!
I found out what was the catch... yesterday I connected to a replica of the college network broadcasted by a generous guy who was sharing the network and was siting right next to me.
And i connected with the atheros card built-in the laptop, this morning I tried to use the new USB Wifi but its a no go...seems like I can only use the built-in card, and if this one doesnt have enough reach I basically can plug in a space satellite it just wont connect to any network.

Maybe it's a USB problem? I donìt know... somebody please help, the built-in card works decently but has really limited reach compared to the usb wifi pendrive... and I really need the reach...

---

### Post by chili555 on 2008-05-22
> ath0      IEEE 802.11g  ESSID:"Rm3-WiFi-Shared"  Nickname:""
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:19:E0:10:2B:D4   
          Bit Rate:11 Mb/s   Tx-Power:14 dBm   **Sensitivity=0/3**  
Wonder if that tells us something. Please try:```
sudo iwconfig ath0 sens 2
```See if your performance improves. Also, I am not sure how much transmit power your card will output (my Intel 3945ABG says 27 dBm), but you might try:```
sudo iwconfig ath0 txpower 16
```Keep increasing the number until you get reasonable performance.

If this solves your problem, we can surely figure out how to make the settings permanent.

---

### Post by raid996 on 2008-05-23
Ubfortunetly today I got caught up at work for the whole day so I'm not gonna be able to try your tip until monday, but can you exlpain me what this is about? I would like to understand what I'm doing...
Thanx for the help man!!

R.

---

### Post by chili555 on 2008-05-23
Your *iwconfig* is reporting that the cards sensitivity is set at zero on a scale of three. Sound familiar?> the built-in card works decently but has really limited reachSo we are saying, please increase your sensitivity to two out of three. Your transmit power seems low as well, so we are trying to push that up as well.

I don't know the capabilities or limitations of the Atheros card; my T40 has the Aironet, so the *txpower* will take some experimentation to see how high you can push it. 

I hope turning up the sensitivity and transmit power will be just what you need to make the built-in card usable.

---

### Post by raid996 on 2008-05-24
Ok, I'll try it asap and report back in... thanx for helping me out... really appreciate it!

---

### Post by Cahooa on 2008-06-08
The plot thickens.

I recently just inherited a IBM T40 with the Intel PRO Wireless lan 2100 wireless card. I have the exact same problem as you. However, I am using Windows XP sp2. I can always connect to my college's wireless net work, but, like you described the connection drops and re-connects every 2-3 minutes. Sometimes my signal strength is high, and some times its low, it changes everytime it reconnects. I have the latest drivers from Lenovo's website. The weird thing is that it works fine at my home, like flawlessly. I dont know that much about computers, but it seems odd to me that even though we are using different operating systems, we still have the same problem. I have been trying to figure this out for the past month, it is so damn annoying, but to no avail. I hope that someone is able to eliminate some possible problems knowing that the problem does not seem to be related to the operating system. 

Thanks ahead of time for any future help.

Alex

---

### Post by chili555 on 2008-06-08
I don't think anyone here speaks XP. You might get a better response here: [http://forum.thinkpads.com/viewforum.php?f=2&sid=cb1715d84ba6c2a62329b4a90fe8c4c6](http://forum.thinkpads.com/viewforum.php?f=2&sid=cb1715d84ba6c2a62329b4a90fe8c4c6)

---

### Post by raid996 on 2008-06-10
Ok, sorry I report in with so much delay but I had tons of things to do and haven't had the time to go to college. Regarding the last advice from CHILI555, the command to set the power works and it helps me quite a bit, the reception now is higher and cleaner, but the sensitivity command is not supported, your advice kinda gave me the start to do some more testing and I found out about the iwlist command which gave me the commands that my card supports.
Basically I can't modify the sensitivity, so the problem is half solved but it's much better now, I managed to connect from places where I couldn't even see the network.

So thank you, but now I need some more help.

I've checked out some info about the last WiFi pen I bought, the Asus WL 167G, it should be supported out of the box and I remember it did work when I plugged it in.
The problem is I tried to install the drivers but kinda got stuck in the middle of it and now I think I messed up the kernel modules. Is it possible to go back in time and restore the original modules the kernel should use by default?
I would like to try and set up the USB WiFi card through terminal since I kinda learned how to do so with the built-in card. It's much more clean and simple and I think it could work quite well.

Thanx again for all of you who tried to help me, I really appreciate it.

Renato

PS: I'll buy pizza+beer+espresso in Rome to the one that solves me most of my problem :D:D

---

### Post by raid996 on 2008-06-18
Anyone?

---

### Post by chili555 on 2008-06-18
Did you try the built-in rt73usb driver module? Did it not work for you?

I'll bet pizza in Rome would beat pizza in South Carolina any day!

---

### Post by raid996 on 2008-06-30
The fact is... I thought it might do better with the driver provided by asus and ended up messing up th whole thing
well anyway, i'll be reinstalling soon because I kind aplayed with my install too much so I'll get back the use of the pen when I do so hoping that it will work decently with the WICD...

The problem isnt solved though, as even when it does have a signal the connection is ALWAYS poorer than the others...

R.

---

