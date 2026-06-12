---
title: "Getting Belkin Card &amp; Wireless Setup"
date: 2008-07-10
forum: Networking &amp; Wireless
---

### Post by Exxon on 2008-07-10
Really would appreciate some help on this I'm leaving for california tomorrow and would like to take my laptop along but I need internet on it.

ok I downloaded 8.04 heron....it detected "Belkin Unknown Device 701f (rev20)......but I have no internet or wireless signal detected, and the lights on my card arn't flashing....I entered in the code sudo ndiswrapper -i BLKWGNv7.sys.inf (also tried net8185)  and it says couldn't copy at /usr/sbin/ndiswrapper line 135 for both codes...

Heres the info from the wireless section....

>  Belkin
	

F5D7010 v7
	

Realtek 8185
	

no must use(ndiswrapper)
	

Works in Feisty with ndiswapper-utils and the Realtek Windows driver (net8185.inf). Belkin's driver won't work well. After installing the driver, use the command "ndiswrapper -a" to link the driver to the card. My computer would intermittently freeze for 5 seconds, but this is rare after I stopped NetworkManager (sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop); got my network's SSID (iwlist wlan0 scan) and configured the interface (sudo iwconfig wlan0 essid <ESSID>)
	

2007-10-10
	

PCMCIA 

---

### Post by chili555 on 2008-07-10
> sudo ndiswrapper -i BLKWGNv7.sys.infPlease recheck the name of your file. It is usually something.inf, not something.sys.inf.

Were you in the correct directory when you issued the command?```
cd Desktop/BroadcomStuff/wherever_I_put this
sudo ndiswrapper -i something.inf
```

---

### Post by Exxon on 2008-07-10
I got that commmand figured out..........but now it says invalid driver....its the right one listed in the link below....




[http://www.uluga.ubuntuforums.org/showpost.php?p=3539832&postcount=26](http://www.uluga.ubuntuforums.org/showpost.php?p=3539832&postcount=26)


I'm following that post perfectly, but it says invalid driver........

---

### Post by Exxon on 2008-07-10
bump updated previous post for more info:guitar:

---

