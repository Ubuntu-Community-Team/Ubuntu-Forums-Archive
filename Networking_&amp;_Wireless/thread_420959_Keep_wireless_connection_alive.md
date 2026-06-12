---
title: "Keep wireless connection alive"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by Alekc on 2007-04-24
Hi, at home i have computer connected to router with wireless (under Feisty Fawn). 
Unfortunately lately i have some issues with keeping connection alive (with ndiswrapper and crapped wl-138g card :mad: ), so i was wondering if there is some package around which tests my connection and restart etc/networking if it's not connected.

Or else maybe it could be done with bash script and cron?
Something like this

if (connectionisnotalive){
/etc/init.d/networking restart
sleep(10000)
if (connectionisnotalive){
reboot
}
}


Thx in advance

---

### Post by Jouke74 on 2007-04-24
Here you go: [http://ubuntuforums.org/showthread.php?t=419727](http://ubuntuforums.org/showthread.php?t=419727)

I am unable to put any search terms / tags in the document. I can't find the link to it in edit message. That's why you don't see it when you do a forum search, which is really nasty. Of course I wanted people like you to get it working. I need to contact probably an administrator for it.... I'll use report maybe.

Read the instructions carefully and apply. Good luck. For 32 bits, check ndiswrapper site for Marvell driver.

P.S. Mine did not even want to connect with WPA.

---

### Post by Alekc on 2007-04-24
Unfortunatly my problem is not connecting to my network but to keep connection alive after some hours :(

Infact i have already done like in your topic (setting connection manualy), but the problem is that when for some obscure reason my connection go down, it doesn't go up anymore. 

So i need to find a way for rebooting networking service on first try and reboot machine on second if first method didn't worked :/

---

### Post by Alekc on 2007-04-24
After searching a bit on google i've come up with this solution (which need to be tested anyway :P). Since i'm not very good in Bash can somebody tell me if the code below has some problems? 
Thx

```

#!/bin/sh
HOST=maya.ngi.it
ping -c 1 -W 10 $HOST &>/dev/null
if  [ $? -eq 0 ]; then
	#ping is ok
	exit
else
	#first try
	ifconfig wlan0 down
	sleep 3
	ifconfig wlan0 upd
	sleep 10
	ping -c 1 -W 10 $HOST &>/dev/null
	if  [ $? -eq 0 ]; then
		exit
	else
		#second try
		/etc/init.d/networking restart
		sleep 10
		ping -c 1 -W 10 $HOST &>/dev/null
		if  [ $? -eq 0 ]; then
			exit
		else
			shutdown -r now
		fi
	fi
fi

```

---

### Post by MaartenNL on 2007-04-24
See [http://ubuntuforums.org/showthread.php?t=413499](http://ubuntuforums.org/showthread.php?t=413499)

This doesn't use ping, but checks the status of wpa_supplicant.

---

