---
title: "Problems connecting to the school wifi network"
date: 2007-09-04
forum: Networking &amp; Wireless
---

### Post by Amablue on 2007-09-04
I can connect to my network fine at home, but it doesn't work at all when I'm at school. 

I click on the Network Manager tray icon to show the networks in range and it sees the network just fine (with signal strength around 70%) but then when I click the network it sits there trying to connect but it never does and eventually gives up. 

When I'm in windows it works fine. 

Just for reference, the way it normally works is that you connect to the network then the first time you open the browser it redirects you to a log in page, and then you can go where ever once you're logged in.  There's no WEP or WPA key or anything.

---

### Post by Ken101 on 2007-09-04
I'm no expert, but while having wireless connection problems, I found a network management program called[** Wicd** ]("http://wicd.sourceforge.net/") and it works just great!

---

### Post by Amablue on 2007-09-08
I got Wicd to work on my school network, but I must've messed up a setting or something becuase now I can't connect at home. I tried uninstalling and reinstalling but no dice. I even tried switching back to network manager and that's not connecting either. It's not even picking up the wireless signals. There should be at least 3 or 4 on my street that my laptop can see, but it's not picking up anything with either manager.

---

### Post by supaman2slick on 2007-10-25
Yikes, Amablue, I'm having the exact same problem as you, I was wondering if you ever figured this one out. I have great wifi working at home and everything, but when i'm at school (connect using same method as you, using cisco's perfigo) I get sporadic results. A few times, I actually connected and logged in, but after about 5 mins or so it died and wouldnt ever connect again. I have the dell 1390 card and am on the restricted bcm43xx driver. I really want to ditch windows and have gutsy as my main os, but it is little things like this that makes me go back to windows.

---

### Post by portach king on 2007-10-25
So am I. It will connect to the university network for a few minutes but always cut out (usually crashing Firefox too in the process). This never happens on my home network, it's incredibly disheartening.
I never had any trouble on the college network with Fiesty.

---

### Post by Amablue on 2007-10-26
I  have a class in windows programming right now so I've been booting windows most of the time so I havn't had to deal with the problem in a while. I did get someone to help me figure it out though. I can't remember exactly what I did, but it was some weird fix from the command line. It didn't even show I was connected in the network manager icon, but I was still able to browse the internet. I think the command was sudo dh... something-or-other.... Gah, I can't remember now. Sorry I cant be more help. I'm sure someone else knows what I'm talking about.

---

### Post by HokeyFry on 2007-10-26
i used to have this problem on my college network. i found that compiling ndiswrapper from source fixes many many issues, including this one. even if the wireless card has a native linux driver, i find that for me ndiswrapper works better 9 times out of 10, if you need help on how to set it up from source check out the link in my sig

---

### Post by supaman2slick on 2007-10-26
> **Amablue said:**
> I  have a class in windows programming right now so I've been booting windows most of the time so I havn't had to deal with the problem in a while. I did get someone to help me figure it out though. I can't remember exactly what I did, but it was some weird fix from the command line. It didn't even show I was connected in the network manager icon, but I was still able to browse the internet. I think the command was sudo dh... something-or-other.... Gah, I can't remember now. Sorry I cant be more help. I'm sure someone else knows what I'm talking about.

Does anyone know what command he is referring to?!?!!?


> **HokeyFry said:**
> i used to have this problem on my college network. i found that compiling ndiswrapper from source fixes many many issues, including this one. even if the wireless card has a native linux driver, i find that for me ndiswrapper works better 9 times out of 10, if you need help on how to set it up from source check out the link in my sig

I have a problem with this method. If I installed ndiswrapper and I use WPA at home, I would have to input static connection information into the config files right? What if I hop around to different APs or the school APs. Will I have to edit the file everytime I want to connect to a different AP?

---

### Post by linux4us on 2007-10-26
hi, 

i have the same problem with dell truemobile 1300, restart NetworkManager will do it.

ps -ef |grep NetworkManager
find the PID,
sudo kill 'PID of networkmanager'
sudo NetworkManager,

hope this helps.

yong

---

### Post by kevdog on 2007-10-26
The missing command is 
sudo dhclient <interface name>  <----like eth0, wlan0, etc

If you want to connect manually take a look at the link in my signature

---

### Post by supaman2slick on 2007-10-30
Thanks, looks like killing NetworkManager and connecting manually does the trick. I just wished I had a wifi meter graphically :) As long as its working I guess. Thanks again

---

