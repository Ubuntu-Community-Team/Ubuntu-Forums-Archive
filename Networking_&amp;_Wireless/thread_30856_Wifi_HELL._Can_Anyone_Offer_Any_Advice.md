---
title: "Wifi HELL. Can Anyone Offer Any Advice?"
date: 2005-04-30
forum: Networking &amp; Wireless
---

### Post by ifrflyer on 2005-04-30
I am on a centrino notebook (Compaq 4020US) running 5.04 and the wifi card works just fine if I stay connected to a spcific wireless network. Fine that is until I get dumped without warning. 

I am in **hell** because the network connections dialogue which comes with ubuntu borks my connection every time and nothing I have tried to date has helped. It works mainly fine if I stay connected to the same network. If I have the gall to try to change wifi networks it locks up on me, tells me I am connected when I m not, and most often requires a restart of the whole bloody machine to get things right again, sometimes two restarts. 

I am willing, nay, delighted to admit user error yet I  have posted repeatedly and gotten no further than:

I have tried

/etc/init.d/networking restart

Nothing

I have tried 

ifdwn eth0 && ifup eth0

Nichts

It's as if the network connection applet OVERRIDES all other functions. 

Only occassionally does removing all the properties such as the WEP key and all other configuration details and clicking OK then reopening network connection and re-entering them manually -- SOMETIMES this allows me to reconnect to a network I was ALREADY on. 

Can you offer any suggestions? Please oh please? 

Thanks

---

### Post by ifrflyer on 2005-04-30
Some other info: iwconfig:

eth0      IEEE 802.11g  ESSID:"fgwire"
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:0C:41:F6:09:87
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=-35 dBm  Noise level=-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:1

[Note that it does not mention the WEP encryption?]
 
Nothing pertinent in dmesg, however /var/log/messages gave me:

Apr 30 15:53:51 localhost kernel: eth0: duplicate address detected!
Apr 30 15:53:54 localhost kernel: eth0: duplicate address detected!
Apr 30 16:51:45 localhost kernel: eth0: duplicate address detected!
Apr 30 16:52:02 localhost kernel: eth0: duplicate address detected!
Apr 30 17:56:29 localhost kernel: eth0: duplicate address detected!
Apr 30 17:56:50 localhost kernel: eth0: duplicate address detected!

What gives there?

---

### Post by ifrflyer on 2005-05-01
In [this thread](http://ubuntuforums.org/showthread.php?t=30671) Dave9191 gave me the answer to removing the automatc Network Connection connction from starting with the machine, and things are running better. However I am concerned about the double address, and now I have no tool for graphically seeing and connecting to available networks. This does suck a bit.

---

### Post by ZC3rr0r on 2005-05-01
I so agree with you, I was psoting in the other thread you mentioned (i started it) and now that it works, I need some gui tool to do the stuff i did on the commandline, and the tool in gnome doesn't cut it. This laptop has to be idiot-proof, cause my sister needs to work with it as well....

---

### Post by ifrflyer on 2005-05-01
Well, do check out [this thread](http://ubuntuforums.org/showthread.php?t=25398) which gives a link to a PHP script which SHOULD work. If you get it going I'd love to speak with you about how you did....

---

### Post by ifrflyer on 2005-05-11
I believe I have the answer to MY problem, and I have written a how to to share it. I can only hope someone makes a sticky 

Problem:
Users of Ubuntu 5.04 with computers which use the Intel® Pro/Wireless 2200 802.11B/G WLAN experience troubles including:

    * Intermittent connectivity
    * Inability to switch between networks or regain a lost network connection without rebooting
    * Inability to configure wireless connection using Network Connection GUI 

Cause:
Ubuntu 5.04 Hoary Hedgehog ships with version 0.19 of the driver for this card. The current version is 1.0.3. The stable version is 1.0.0, and this is the version it is recommended to use with Ubuntu. Of course, you can try any version you like!

Solution:
Remove completely version 0.19 and upgrade to version 1.0.*


HOW TO:
[http://nickselby.com/articles/technology/index.htm?a=1807](http://nickselby.com/articles/technology/index.htm?a=1807)

---

### Post by epb613 on 2005-05-11
Very well done HowTo. Nice work.


For the record, driver versions 1.0, 1.2, and 1.3 all worked fine for me.

---

### Post by chokidar on 2005-05-29
I'm having the same problem. I followed the howto, but it didn't work. I tried 1.0.0/1/2/3. Same issue. 

My laptop's wireless radio turns on when it boots up, but once the login screen comes up the radio just goes dead. I tried reloading the driver, but the same thing. The radio just doesn't power up anymore. BTW, everything works fine on Windows, and worked fine on Fedora 3.

---

### Post by ifrflyer on 2005-05-30
Don't mean to ask a dumb question, but are you positive that you have the same radio card we're discussing here? Is it also possible that you've got a situation where you need to press a button to activate the card? I know it works in Windows but perhaps there's a kill switch issue? I'm just guessing here.  One idea is the #ipw2100 chat room I mention in the [How To](http://nickselby.com/articles/technology/?a=1807) - those folks are a bit gruff, but will help if you are clear, specific and polite.

Another (and forgive me if I'm telling you how to suck eggs, or if you've tried this and it didn't work) is:

```
sudo rmmod ipw2200
sudo /etc/init.d/networking restart
sudo modprobe ipw2200
sudo ifconfig eth0 up
```

Then see if you can connect using either iwconfig commands or the GUI?

---

### Post by chokidar on 2005-05-30
Actually it turns out I had NetworkManager running. When I killed that everything started to work. I have now 1.0.4 installed without problems.

BTW, has anyone gotten NetworkManager to work on Ubuntu?

---

