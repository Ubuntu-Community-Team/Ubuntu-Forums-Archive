---
title: "WPA in 7.04 &amp; WICD (Solved)"
date: 2007-07-07
forum: Networking &amp; Wireless
---

### Post by phillipchandler on 2007-07-07
Hi Everybody.

I wanted to share this with everyone. If you are trying to set up WPA within Ubuntu, then this may help.

My Spec :
Dell Inspiron 1200
512mb Ram
System = Dual Boot with WinXP & Ubuntu 7.04
Wireless Card = Belkin 54 G card F5D7010 Ver 7
Experience = Newbie.

Ive been looking through all the forums, with added help from a friend (Pat). We have tried everything from writing the wpa_supplicant.conf file.

I had installed ndiswrapper, wpa_supplicant, the net8185 driver files and could only get WEP. We had spent 40 hrs plus over several weeks. I could have gone with PCLinuxOS 2007, as it set up WPA by default. But I wanted to have Ubuntu, so perceviered.

Well the great news is that my oppo (Pat) found WICD ( [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/) ). I installed it last night, then went and tried to connect to his wireless network. 
Had to try a few times changing settings. The only major hurdle was changing the WPA Supplicant Driver to wext in the Preferences drop down box, as this was originally set to NDisWrapper. Once we changed to wext, and click Connect. I was connected straight away to his WPA wireless.

Adam Blackburn is down as writing the package. Id like to send him an email just to let him know that it works great, and see if he's going to release a new version etc. But I cant find an email address for him. Would anyone know of his whereabouts, know his email address, or be able to pass on my thanks.

This is a fantastic piece of kit, and for anyone who's still having problems with WPA in Ubuntu, then I suggest you give this a try, as its just brilliant.

---

### Post by imdano on 2007-07-07
Hi,

I'm working with Adam on wicd development these days.  Head over to [http://wicd.sourceforge.net/phpbb/index.php](http://wicd.sourceforge.net/phpbb/index.php) and look for "adam".  That's him, he posts all the time.  There should be a new version out in the next few weeks with some bug fixes and a couple of new features.

---

### Post by witham on 2007-07-08
I don't know if I did something wrong but my 7.04 hung after installing wcid and couldn't get it to clear and had to reinstall?
I have since dropped to WEP but would like to use WPA in preference so any help would be appreciated

Thanks

---

### Post by imdano on 2007-07-08
Would you mind giving a little more information?  You installed wicd, and as soon as the installation completed your computer froze?  Or did you try doing something in wicd and then it froze?  What do you mean by "couldn't get it to clear"?  And do you mean you had to reinstall wicd or you had to reinstall Ubuntu?

---

### Post by witham on 2007-07-08
sorry if I was a little vague what I did was download and install the stable version of wcid and then I prompted to restart which I did. On restart the splash screen wouldn't load completely and a box with a red cross in came up to say that GNOME may not work properly (sorry I didn't write down the cmplete message) anyway whatever I did I couldn't clear it?

---

### Post by imdano on 2007-07-08
That's odd.  Did you uninstall network-manager completely before trying to install wicd?  They conflict with each other if both are installed, but I haven't heard of someone being unable to boot as a result.  Also, if you're willing to try wicd again, I'd recommend using 1.3.0, 1.2.7 is listed as stable but in reality is a lot buggier.

---

### Post by witham on 2007-07-08
well downloaded the version you recommended and all went well with the installation it has detected the network and I have set the WPA encrytion, at present it has been "flushing the routing table" for 10mins is this normal?

Thanks for your help nearly there!!

---

### Post by imdano on 2007-07-08
No, something's definitely gone wrong.  Do you have wpasupplicant installed?  From a terminal, run ```
sudo apt-get install wpasupplicant
```  If it returns "wpasupplicant is already the newest version" then it's already installed and that's not the problem.  Also, make sure you're entering the hex version of your wpa passphrase.  From there, the next step in debugging it is to try removing encryption from the network and see if you're able to connect through wicd then.

---

### Post by witham on 2007-07-08
wpasupplicant is installed ok but the problem is my router only gives me the PSK preshared key, I am using WPA-PSK(no server) using TKIP encrytion is this supported?

---

### Post by imdano on 2007-07-08
Yes, WPA-PSK and TKIP should be fine.  Could you try to connect again, then post your /opt/wicd/data/wicd.log?

---

### Post by witham on 2007-07-09
Thanks for your reply, tried to connect and then download the wcid.log (which I pressume you do in the terminal window) and it told me permission denied?

---

### Post by witham on 2007-07-09
Forgot to mention that I did turn off all security and I was able to connect so it must be an encrytion issue.

---

### Post by imdano on 2007-07-09
Use this: ```
sudo gedit /opt/wicd/data/wicd.log
```Are you able to open the file then?

---

### Post by witham on 2007-07-09
Hope this helps and thank again for your patience.


2007/07/09 20:55:19 :: 2007/
07/09 20:55:19 :: wicd initalizing...
2007/07/09 20:55:19 :: 2007/
07/09 20:55:19 :: found wireless interface in configuration... setting wireless interface wlan0
2007/07/09 20:55:19 :: found wired interface in configuration... setting wired interface eth0
2007/07/09 20:55:19 :: found wpa driver in configuration... setting wpa driver wext
2007/07/09 20:55:19 :: wireless configuration file found...
2007/07/09 20:55:19 :: wired configuration file found...
2007/07/09 20:55:19 :: chmoding configuration files 0600...
2007/07/09 20:55:19 :: chowning configuration files root:root...
2007/07/09 20:55:19 :: autodetected wireless interface... automatically detected wireless interface
2007/07/09 20:55:19 ::
2007/07/09 20:55:19 :: using wireless interface... returning wireless interface to client
2007/07/09 20:55:19 ::
2007/07/09 20:55:19 :: autoconnecting... returning wireless interface to client
2007/07/09 20:55:19 ::
2007/07/09 20:55:19 :: attempting to autoconnect to wireless network
2007/07/09 20:55:19 :: scanning start
2007/07/09 20:55:19 :: scanning done
2007/07/09 20:55:20 :: found 0 networks:
2007/07/09 20:55:20 :: returning wireless interface to client
2007/07/09 20:55:20 :: None
2007/07/09 20:55:20 ::

---

### Post by imdano on 2007-07-09
Hmm, the log is showing that it didn't find any wireless networks.  If that's not true, open up the gui, try connecting to your network, then post the log (it may end up being very long).

---

### Post by witham on 2007-07-09
No kidding it looks like its tryng hard?


2007/07/09 21:47:38 :: --------------------------- 
2007/07/09 21:47:38 :: wicd initalizing... 
2007/07/09 21:47:38 :: --------------------------- 
2007/07/09 21:47:38 :: found wireless interface in configuration... setting wireless interface wlan0 
2007/07/09 21:47:38 :: found wired interface in configuration... setting wired interface eth0 
2007/07/09 21:47:38 :: found wpa driver in configuration... setting wpa driver wext 
2007/07/09 21:47:38 :: wireless configuration file found... 
2007/07/09 21:47:38 :: wired configuration file found... 
2007/07/09 21:47:38 :: chmoding configuration files 0600... 
2007/07/09 21:47:38 :: chowning configuration files root:root... 
2007/07/09 21:47:38 :: autodetected wireless interface... automatically detected wireless interface 
2007/07/09 21:47:38 :: 
2007/07/09 21:47:38 :: using wireless interface... returning wireless interface to client 
2007/07/09 21:47:38 :: 
2007/07/09 21:47:38 :: autoconnecting... returning wireless interface to client 
2007/07/09 21:47:38 :: 
2007/07/09 21:47:38 :: attempting to autoconnect to wireless network 
2007/07/09 21:47:38 :: scanning start 
2007/07/09 21:47:38 :: scanning done 
2007/07/09 21:47:39 :: found 0 networks: 
2007/07/09 21:47:39 :: returning wireless interface to client 
2007/07/09 21:47:39 :: None 
2007/07/09 21:47:39 :: returing plugged in False 
2007/07/09 21:48:09 :: returning always show wired interface False 
2007/07/09 21:48:09 :: returned number of networks... 0 
2007/07/09 21:48:09 :: returned number of networks... 0 
2007/07/09 21:48:09 :: returning wireless ip None 
2007/07/09 21:48:09 :: wired connecting False 
2007/07/09 21:48:09 :: wireless connecting False 
2007/07/09 21:48:09 :: returing wired ip None 
2007/07/09 21:48:09 :: returning wireless ip None 
2007/07/09 21:48:09 :: wired connecting False 
2007/07/09 21:48:09 :: wireless connecting False 
2007/07/09 21:48:09 :: returing wired ip None 
2007/07/09 21:48:09 :: returning wireless ip None 
2007/07/09 21:48:10 :: wired connecting False 
2007/07/09 21:48:10 :: wireless connecting False 
2007/07/09 21:48:10 :: returing wired ip None 
2007/07/09 21:48:10 :: returning wireless ip None 
2007/07/09 21:48:10 :: wired connecting False 
2007/07/09 21:48:10 :: wireless connecting False 
2007/07/09 21:48:10 :: returing wired ip None 
2007/07/09 21:48:10 :: returning wireless ip None 
2007/07/09 21:48:10 :: wired connecting False 
2007/07/09 21:48:10 :: wireless connecting False 
2007/07/09 21:48:10 :: returing wired ip None 
2007/07/09 21:48:10 :: returning wireless ip None 
2007/07/09 21:48:10 :: wired connecting False 
2007/07/09 21:48:10 :: wireless connecting False 
2007/07/09 21:48:11 :: returing wired ip None 
2007/07/09 21:48:11 :: returning wireless ip None 
2007/07/09 21:48:11 :: wired connecting False 
2007/07/09 21:48:11 :: wireless connecting False 
2007/07/09 21:48:11 :: returing wired ip None 
2007/07/09 21:48:11 :: returning wireless ip None 
2007/07/09 21:48:11 :: wired connecting False 
2007/07/09 21:48:11 :: wireless connecting False 
2007/07/09 21:48:11 :: returing wired ip None 
2007/07/09 21:48:11 :: returning wireless ip None 
2007/07/09 21:48:11 :: wired connecting False 
2007/07/09 21:48:11 :: wireless connecting False 
2007/07/09 21:48:11 :: returing wired ip None 
2007/07/09 21:48:11 :: returning wireless ip None 
2007/07/09 21:48:12 :: wired connecting False 
2007/07/09 21:48:12 :: wireless connecting False 
2007/07/09 21:48:12 :: returing wired ip None 
2007/07/09 21:48:12 :: returning wireless ip None 
2007/07/09 21:48:12 :: wired connecting False 
2007/07/09 21:48:12 :: wireless connecting False 
2007/07/09 21:48:12 :: returing wired ip None 
2007/07/09 21:48:12 :: returning wireless ip None 
2007/07/09 21:48:12 :: wired connecting False 
2007/07/09 21:48:12 :: wireless connecting False 
2007/07/09 21:48:12 :: returing wired ip None 
2007/07/09 21:48:12 :: returning wireless ip None 
2007/07/09 21:48:13 :: wired connecting False 
2007/07/09 21:48:13 :: wireless connecting False 
2007/07/09 21:48:13 :: returing wired ip None 
2007/07/09 21:48:13 :: returning wireless ip None 
2007/07/09 21:48:13 :: wired connecting False 
2007/07/09 21:48:13 :: wireless connecting False 
2007/07/09 21:48:13 :: returing wired ip None 
2007/07/09 21:48:13 :: returning wireless ip None 
2007/07/09 21:48:13 :: wired connecting False 
2007/07/09 21:48:13 :: wireless connecting False 
2007/07/09 21:48:13 :: returing wired ip None 
2007/07/09 21:48:13 :: returning wireless ip None 
2007/07/09 21:48:13 :: wired connecting False 
2007/07/09 21:48:13 :: wireless connecting False 
2007/07/09 21:48:14 :: returing wired ip None 
2007/07/09 21:48:14 :: returning wireless ip None 
2007/07/09 21:48:14 :: wired connecting False 
2007/07/09 21:48:14 :: wireless connecting False 
2007/07/09 21:48:14 :: returing wired ip None 
2007/07/09 21:48:14 :: returning wireless ip None 
2007/07/09 21:48:14 :: wired connecting False 
2007/07/09 21:48:14 :: wireless connecting False 
2007/07/09 21:48:14 :: returing wired ip None 
2007/07/09 21:48:14 :: returning wireless ip None 
2007/07/09 21:48:14 :: wired connecting False 
2007/07/09 21:48:14 :: wireless connecting False 
2007/07/09 21:48:14 :: returing wired ip None 
2007/07/09 21:48:14 :: returning wireless ip None 
2007/07/09 21:48:15 :: wired connecting False 
2007/07/09 21:48:15 :: wireless connecting False 
2007/07/09 21:48:15 :: returing wired ip None 
2007/07/09 21:48:15 :: returning wireless ip None 
2007/07/09 21:48:15 :: wired connecting False 
2007/07/09 21:48:15 :: wireless connecting False 
2007/07/09 21:48:15 :: returing wired ip None 
2007/07/09 21:48:15 :: returning wireless ip None 
2007/07/09 21:48:15 :: wired connecting False 
2007/07/09 21:48:15 :: wireless connecting False 
2007/07/09 21:48:15 :: returing wired ip None 
2007/07/09 21:48:15 :: returning wireless ip None 
2007/07/09 21:48:16 :: wired connecting False 
2007/07/09 21:48:16 :: wireless connecting False 
2007/07/09 21:48:16 :: returing wired ip None 
2007/07/09 21:48:16 :: returing plugged in False 
2007/07/09 21:48:16 :: returning always show wired interface False 
2007/07/09 21:48:16 :: setting hidden essid: None 
2007/07/09 21:48:16 :: scanning start 
2007/07/09 21:48:16 :: 	##### 00:0E:2E:89:DC:07 
2007/07/09 21:48:16 :: 	##### 00:11:50:0D:FE:EB 
2007/07/09 21:48:16 :: scanning done 
2007/07/09 21:48:16 :: found 2 networks: 0 00:11:50:0D:FE:EB 
2007/07/09 21:48:16 :: 1 00:0E:2E:89:DC:07 
2007/07/09 21:48:16 :: 
2007/07/09 21:48:16 :: returned number of networks... 2 
2007/07/09 21:48:16 :: returned number of networks... 2 
2007/07/09 21:48:16 :: returned number of networks... 2 
2007/07/09 21:48:16 :: returned wireless network 0 property essid of value belkin54g 
2007/07/09 21:48:16 :: returned wireless network 0 property essid of value belkin54g 
2007/07/09 21:48:16 :: returned wireless network 0 property essid of value belkin54g 
2007/07/09 21:48:16 :: returned wireless network 0 property ip of value None 
2007/07/09 21:48:16 :: returned wireless network 0 property netmask of value None 
2007/07/09 21:48:16 :: returned wireless network 0 property gateway of value None 
2007/07/09 21:48:16 :: returned wireless network 0 property dns1 of value None 
2007/07/09 21:48:16 :: returned wireless network 0 property dns2 of value None 
2007/07/09 21:48:16 :: returned wireless network 0 property dns3 of value None 
2007/07/09 21:48:16 :: returned wireless network 0 property automatic of value True 
2007/07/09 21:48:16 :: setting wireless network 0 property automatic to value 1 
2007/07/09 21:48:16 :: setting network option automatic to True 
2007/07/09 21:48:16 :: returned wireless network 0 property enctype of value wpa 
2007/07/09 21:48:16 :: returned wireless network 0 property enctype of value wpa 
2007/07/09 21:48:16 :: returned wireless network 0 property enctype of value wpa 
2007/07/09 21:48:16 :: returned wireless network 0 property enctype of value wpa 
2007/07/09 21:48:16 :: returned wireless network 0 property enctype of value wpa 
2007/07/09 21:48:16 :: returned wireless network 0 property enctype of value wpa 
2007/07/09 21:48:16 :: returned wireless network 0 property key of value w1thamoil 
2007/07/09 21:48:16 :: returned wireless network 0 property quality of value 49 
2007/07/09 21:48:16 :: returned wireless network 0 property bssid of value 00:11:50:0D:FE:EB 
2007/07/09 21:48:16 :: returned wireless network 0 property channel of value 11 
2007/07/09 21:48:16 :: returned wireless network 0 property encryption of value True 
2007/07/09 21:48:16 :: returned wireless network 0 property encryption_method of value WEP 
2007/07/09 21:48:16 :: returned wireless network 1 property essid of value conexant 
2007/07/09 21:48:16 :: returned wireless network 1 property essid of value conexant 
2007/07/09 21:48:16 :: returned wireless network 1 property essid of value conexant 
2007/07/09 21:48:16 :: returned wireless network 1 property ip of value None 
2007/07/09 21:48:16 :: returned wireless network 1 property netmask of value None 
2007/07/09 21:48:16 :: returned wireless network 1 property gateway of value None 
2007/07/09 21:48:16 :: returned wireless network 1 property dns1 of value None 
2007/07/09 21:48:16 :: returned wireless network 1 property dns2 of value None 
2007/07/09 21:48:16 :: returned wireless network 1 property dns3 of value None 
2007/07/09 21:48:16 :: returned wireless network 1 property automatic of value None 
2007/07/09 21:48:16 :: returned wireless network 1 property enctype of value None 
2007/07/09 21:48:16 :: returned wireless network 1 property enctype of value None 
2007/07/09 21:48:16 :: returned wireless network 1 property enctype of value None 
2007/07/09 21:48:16 :: returned wireless network 1 property enctype of value None 
2007/07/09 21:48:16 :: returned wireless network 1 property enctype of value None 
2007/07/09 21:48:16 :: returned wireless network 1 property enctype of value None 
2007/07/09 21:48:16 :: returned wireless network 1 property key of value None 
2007/07/09 21:48:16 :: returned wireless network 1 property quality of value 29 
2007/07/09 21:48:16 :: returned wireless network 1 property bssid of value 00:0E:2E:89:DC:07 
2007/07/09 21:48:16 :: returned wireless network 1 property channel of value 10 
2007/07/09 21:48:16 :: returned wireless network 1 property encryption of value True 
2007/07/09 21:48:16 :: returned wireless network 1 property encryption_method of value WEP 
2007/07/09 21:48:16 :: returning wireless ip None 
2007/07/09 21:48:16 :: wired connecting False 
2007/07/09 21:48:16 :: wireless connecting False 
2007/07/09 21:48:16 :: returing wired ip None 
2007/07/09 21:48:16 :: returning wireless ip None 
2007/07/09 21:48:17 :: wired connecting False 
2007/07/09 21:48:17 :: wireless connecting False 
2007/07/09 21:48:17 :: returing wired ip None 
2007/07/09 21:48:17 :: returning wireless ip None 
2007/07/09 21:48:17 :: wired connecting False 
2007/07/09 21:48:17 :: wireless connecting False 
2007/07/09 21:48:17 :: returing wired ip None 
2007/07/09 21:48:17 :: returning wireless ip None 
2007/07/09 21:48:17 :: wired connecting False 
2007/07/09 21:48:17 :: wireless connecting False 
2007/07/09 21:48:17 :: returing wired ip None 
2007/07/09 21:48:17 :: returning wireless ip None 
2007/07/09 21:48:18 :: wired connecting False 
2007/07/09 21:48:18 :: wireless connecting False 
2007/07/09 21:48:18 :: returing wired ip None 
2007/07/09 21:48:18 :: returning wireless ip None 
2007/07/09 21:48:18 :: wired connecting False 
2007/07/09 21:48:18 :: wireless connecting False 
2007/07/09 21:48:18 :: returing wired ip None 
2007/07/09 21:48:18 :: returning wireless ip None 
2007/07/09 21:48:18 :: wired connecting False 
2007/07/09 21:48:18 :: wireless connecting False 
2007/07/09 21:48:18 :: returing wired ip None 
2007/07/09 21:48:18 :: returning wireless ip None 
2007/07/09 21:48:19 :: wired connecting False 
2007/07/09 21:48:19 :: wireless connecting False 
2007/07/09 21:48:19 :: returing wired ip None 
2007/07/09 21:48:19 :: returning wireless ip None 
2007/07/09 21:48:19 :: wired connecting False 
2007/07/09 21:48:19 :: wireless connecting False 
2007/07/09 21:48:19 :: returing wired ip None 
2007/07/09 21:48:19 :: returning wireless ip None 
2007/07/09 21:48:19 :: wired connecting False 
2007/07/09 21:48:19 :: wireless connecting False 
2007/07/09 21:48:19 :: returing wired ip None 
2007/07/09 21:48:19 :: returning wireless ip None 
2007/07/09 21:48:19 :: wired connecting False 
2007/07/09 21:48:19 :: wireless connecting False 
2007/07/09 21:48:19 :: returing wired ip None 
2007/07/09 21:48:19 :: returning wireless ip None 
2007/07/09 21:48:20 :: wired connecting False 
2007/07/09 21:48:20 :: wireless connecting False 
2007/07/09 21:48:20 :: returing wired ip None 
2007/07/09 21:48:20 :: returning wireless ip None 
2007/07/09 21:48:20 :: wired connecting False 
2007/07/09 21:48:20 :: wireless connecting False 
2007/07/09 21:48:20 :: returing wired ip None 
2007/07/09 21:48:20 :: returning wireless ip None 
2007/07/09 21:48:20 :: wired connecting False 
2007/07/09 21:48:20 :: wireless connecting False 
2007/07/09 21:48:20 :: returing wired ip None 
2007/07/09 21:48:20 :: returning wireless ip None 
2007/07/09 21:48:21 :: wired connecting False 
2007/07/09 21:48:21 :: wireless connecting False 
2007/07/09 21:48:21 :: returing wired ip None 
2007/07/09 21:48:21 :: returning wireless ip None 
2007/07/09 21:48:21 :: wired connecting False 
2007/07/09 21:48:21 :: wireless connecting False 
2007/07/09 21:48:21 :: returing wired ip None 
2007/07/09 21:48:21 :: returning wireless ip None 
2007/07/09 21:48:21 :: wired connecting False 
2007/07/09 21:48:21 :: wireless connecting False 
2007/07/09 21:48:21 :: returing wired ip None 
2007/07/09 21:48:21 :: returning wireless ip None 
2007/07/09 21:48:22 :: wired connecting False 
2007/07/09 21:48:22 :: wireless connecting False 
2007/07/09 21:48:22 :: returing wired ip None 
2007/07/09 21:48:22 :: returning wireless ip None 
2007/07/09 21:48:22 :: wired connecting False 
2007/07/09 21:48:22 :: wireless connecting False 
2007/07/09 21:48:22 :: returing wired ip None 
2007/07/09 21:48:22 :: returning wireless ip None 
2007/07/09 21:48:22 :: wired connecting False 
2007/07/09 21:48:22 :: wireless connecting False 
2007/07/09 21:48:22 :: returing wired ip None 
2007/07/09 21:48:22 :: returning wireless ip None 
2007/07/09 21:48:22 :: wired connecting False 
2007/07/09 21:48:22 :: wireless connecting False 
2007/07/09 21:48:22 :: returing wired ip None 
2007/07/09 21:48:22 :: returning wireless ip None 
2007/07/09 21:48:23 :: wired connecting False 
2007/07/09 21:48:23 :: wireless connecting False 
2007/07/09 21:48:23 :: returing wired ip None 
2007/07/09 21:48:23 :: returning wireless ip None 
2007/07/09 21:48:23 :: wired connecting False 
2007/07/09 21:48:23 :: wireless connecting False 
2007/07/09 21:48:23 :: returing wired ip None 
2007/07/09 21:48:23 :: returning wireless ip None 
2007/07/09 21:48:23 :: wired connecting False 
2007/07/09 21:48:23 :: wireless connecting False 
2007/07/09 21:48:23 :: returing wired ip None 
2007/07/09 21:48:23 :: returning wireless ip None 
2007/07/09 21:48:24 :: wired connecting False 
2007/07/09 21:48:24 :: wireless connecting False 
2007/07/09 21:48:24 :: returing wired ip None 
2007/07/09 21:48:24 :: returning wireless ip None 
2007/07/09 21:48:24 :: wired connecting False 
2007/07/09 21:48:24 :: wireless connecting False 
2007/07/09 21:48:24 :: returing wired ip None 
2007/07/09 21:48:24 :: returning wireless ip None 
2007/07/09 21:48:24 :: wired connecting False 
2007/07/09 21:48:24 :: wireless connecting False 
2007/07/09 21:48:24 :: returing wired ip None 
2007/07/09 21:48:24 :: returning wireless ip None 
2007/07/09 21:48:25 :: wired connecting False 
2007/07/09 21:48:25 :: wireless connecting False 
2007/07/09 21:48:25 :: returing wired ip None 
2007/07/09 21:48:25 :: returning wireless ip None 
2007/07/09 21:48:25 :: wired connecting False 
2007/07/09 21:48:25 :: wireless connecting False 
2007/07/09 21:48:25 :: returing wired ip None 
2007/07/09 21:48:25 :: returning wireless ip None 
2007/07/09 21:48:25 :: wired connecting False 
2007/07/09 21:48:25 :: wireless connecting False 
2007/07/09 21:48:25 :: returing wired ip None 
2007/07/09 21:48:25 :: returning wireless ip None 
2007/07/09 21:48:25 :: wired connecting False 
2007/07/09 21:48:25 :: wireless connecting False 
2007/07/09 21:48:25 :: returing wired ip None 
2007/07/09 21:48:25 :: returning wireless ip None 
2007/07/09 21:48:26 :: wired connecting False 
2007/07/09 21:48:26 :: wireless connecting False 
2007/07/09 21:48:26 :: returing wired ip None 
2007/07/09 21:48:26 :: returning wireless ip None 
2007/07/09 21:48:26 :: wired connecting False 
2007/07/09 21:48:26 :: wireless connecting False 
2007/07/09 21:48:26 :: returing wired ip None 
2007/07/09 21:48:26 :: returning wireless ip None 
2007/07/09 21:48:26 :: wired connecting False 
2007/07/09 21:48:26 :: wireless connecting False 
2007/07/09 21:48:26 :: returing wired ip None 
2007/07/09 21:48:26 :: returning wireless ip None 
2007/07/09 21:48:27 :: wired connecting False 
2007/07/09 21:48:27 :: wireless connecting False 
2007/07/09 21:48:27 :: returing wired ip None 
2007/07/09 21:48:27 :: returning wireless ip None 
2007/07/09 21:48:27 :: wired connecting False 
2007/07/09 21:48:27 :: wireless connecting False 
2007/07/09 21:48:27 :: returing wired ip None 
2007/07/09 21:48:27 :: returning wireless ip None 
2007/07/09 21:48:27 :: wired connecting False 
2007/07/09 21:48:27 :: wireless connecting False 
2007/07/09 21:48:27 :: returing wired ip None 
2007/07/09 21:48:27 :: returning wireless ip None 
2007/07/09 21:48:28 :: wired connecting False 
2007/07/09 21:48:28 :: wireless connecting False 
2007/07/09 21:48:28 :: returing wired ip None 
2007/07/09 21:48:28 :: returning wireless ip None 
2007/07/09 21:48:28 :: wired connecting False 
2007/07/09 21:48:28 :: wireless connecting False 
2007/07/09 21:48:28 :: returing wired ip None 
2007/07/09 21:48:28 :: returning wireless ip None 
2007/07/09 21:48:28 :: wired connecting False 
2007/07/09 21:48:28 :: wireless connecting False 
2007/07/09 21:48:28 :: returing wired ip None 
2007/07/09 21:48:28 :: returning wireless ip None 
2007/07/09 21:48:28 :: wired connecting False 
2007/07/09 21:48:28 :: wireless connecting False 
2007/07/09 21:48:28 :: returing wired ip None 
2007/07/09 21:48:28 :: returning wireless ip None 
2007/07/09 21:48:29 :: wired connecting False 
2007/07/09 21:48:29 :: wireless connecting False 
2007/07/09 21:48:29 :: returing wired ip None 
2007/07/09 21:48:29 :: returning wireless ip None 
2007/07/09 21:48:29 :: wired connecting False 
2007/07/09 21:48:29 :: wireless connecting False 
2007/07/09 21:48:29 :: returing wired ip None 
2007/07/09 21:48:29 :: returning wireless ip None 
2007/07/09 21:48:29 :: wired connecting False 
2007/07/09 21:48:29 :: wireless connecting False 
2007/07/09 21:48:29 :: returing wired ip None 
2007/07/09 21:48:29 :: returning wireless ip None 
2007/07/09 21:48:30 :: wired connecting False 
2007/07/09 21:48:30 :: wireless connecting False 
2007/07/09 21:48:30 :: returing wired ip None 
2007/07/09 21:48:30 :: returning wireless ip None 
2007/07/09 21:48:30 :: wired connecting False 
2007/07/09 21:48:30 :: wireless connecting False 
2007/07/09 21:48:30 :: returing wired ip None 
2007/07/09 21:48:30 :: returning wireless ip None 
2007/07/09 21:48:30 :: wired connecting False 
2007/07/09 21:48:30 :: wireless connecting False 
2007/07/09 21:48:30 :: returing wired ip None 
2007/07/09 21:48:30 :: returning wireless ip None 
2007/07/09 21:48:31 :: wired connecting False 
2007/07/09 21:48:31 :: wireless connecting False 
2007/07/09 21:48:31 :: returing wired ip None 
2007/07/09 21:48:31 :: returning wireless ip None 
2007/07/09 21:48:31 :: wired connecting False 
2007/07/09 21:48:31 :: wireless connecting False 
2007/07/09 21:48:31 :: returing wired ip None 
2007/07/09 21:48:31 :: returning wireless ip None 
2007/07/09 21:48:31 :: wired connecting False 
2007/07/09 21:48:31 :: wireless connecting False 
2007/07/09 21:48:31 :: returing wired ip None 
2007/07/09 21:48:31 :: returning wireless ip None 
2007/07/09 21:48:31 :: wired connecting False 
2007/07/09 21:48:31 :: wireless connecting False 
2007/07/09 21:48:31 :: returing wired ip None 
2007/07/09 21:48:31 :: returning wireless ip None 
2007/07/09 21:48:32 :: wired connecting False 
2007/07/09 21:48:32 :: wireless connecting False 
2007/07/09 21:48:32 :: returing wired ip None 
2007/07/09 21:48:32 :: returning wireless ip None 
2007/07/09 21:48:32 :: wired connecting False 
2007/07/09 21:48:32 :: wireless connecting False 
2007/07/09 21:48:32 :: returing wired ip None 
2007/07/09 21:48:32 :: returning wireless ip None 
2007/07/09 21:48:32 :: wired connecting False 
2007/07/09 21:48:32 :: wireless connecting False 
2007/07/09 21:48:32 :: returing wired ip None 
2007/07/09 21:48:32 :: returning wireless ip None 
2007/07/09 21:48:33 :: wired connecting False 
2007/07/09 21:48:33 :: wireless connecting False 
2007/07/09 21:48:33 :: returing wired ip None 
2007/07/09 21:48:33 :: returning wireless ip None 
2007/07/09 21:48:33 :: wired connecting False 
2007/07/09 21:48:33 :: wireless connecting False 
2007/07/09 21:48:33 :: returing wired ip None 
2007/07/09 21:48:33 :: returning wireless ip None 
2007/07/09 21:48:33 :: wired connecting False 
2007/07/09 21:48:33 :: wireless connecting False 
2007/07/09 21:48:33 :: returing wired ip None 
2007/07/09 21:48:33 :: returning wireless ip None 
2007/07/09 21:48:34 :: wired connecting False 
2007/07/09 21:48:34 :: wireless connecting False 
2007/07/09 21:48:34 :: returing wired ip None 
2007/07/09 21:48:34 :: returning wireless ip None 
2007/07/09 21:48:34 :: wired connecting False 
2007/07/09 21:48:34 :: wireless connecting False 
2007/07/09 21:48:34 :: returing wired ip None 
2007/07/09 21:48:34 :: returning wireless ip None 
2007/07/09 21:48:34 :: wired connecting False 
2007/07/09 21:48:34 :: wireless connecting False 
2007/07/09 21:48:34 :: returing wired ip None 
2007/07/09 21:48:34 :: returning wireless ip None 
2007/07/09 21:48:34 :: wired connecting False 
2007/07/09 21:48:34 :: wireless connecting False 
2007/07/09 21:48:34 :: returing wired ip None 
2007/07/09 21:48:34 :: returning wireless ip None 
2007/07/09 21:48:35 :: wired connecting False 
2007/07/09 21:48:35 :: wireless connecting False 
2007/07/09 21:48:35 :: returing wired ip None 
2007/07/09 21:48:35 :: returning wireless ip None 
2007/07/09 21:48:35 :: wired connecting False 
2007/07/09 21:48:35 :: wireless connecting False 
2007/07/09 21:48:35 :: returing wired ip None 
2007/07/09 21:48:35 :: returning wireless ip None 
2007/07/09 21:48:35 :: wired connecting False 
2007/07/09 21:48:35 :: wireless connecting False 
2007/07/09 21:48:35 :: returing wired ip None 
2007/07/09 21:48:35 :: returning wireless ip None 
2007/07/09 21:48:36 :: wired connecting False 
2007/07/09 21:48:36 :: wireless connecting False 
2007/07/09 21:48:36 :: returing wired ip None 
2007/07/09 21:48:36 :: returning wireless ip None 
2007/07/09 21:48:36 :: wired connecting False 
2007/07/09 21:48:36 :: wireless connecting False 
2007/07/09 21:48:36 :: returing wired ip None 
2007/07/09 21:48:36 :: returning wireless ip None 
2007/07/09 21:48:36 :: wired connecting False 
2007/07/09 21:48:36 :: wireless connecting False 
2007/07/09 21:48:36 :: returing wired ip None 
2007/07/09 21:48:36 :: returning wireless ip None 
2007/07/09 21:48:37 :: wired connecting False 
2007/07/09 21:48:37 :: wireless connecting False 
2007/07/09 21:48:37 :: returing wired ip None 
2007/07/09 21:48:37 :: returning wireless ip None 
2007/07/09 21:48:37 :: wired connecting False 
2007/07/09 21:48:37 :: wireless connecting False 
2007/07/09 21:48:37 :: returing wired ip None 
2007/07/09 21:48:37 :: returning wireless ip None 
2007/07/09 21:48:37 :: wired connecting False 
2007/07/09 21:48:37 :: wireless connecting False 
2007/07/09 21:48:37 :: returing wired ip None 
2007/07/09 21:48:37 :: returning wireless ip None 
2007/07/09 21:48:37 :: wired connecting False 
2007/07/09 21:48:37 :: wireless connecting False 
2007/07/09 21:48:37 :: returing wired ip None 
2007/07/09 21:48:37 :: returning wireless ip None 
2007/07/09 21:48:38 :: wired connecting False 
2007/07/09 21:48:38 :: wireless connecting False 
2007/07/09 21:48:38 :: returing wired ip None 
2007/07/09 21:48:38 :: returning wireless ip None 
2007/07/09 21:48:38 :: wired connecting False 
2007/07/09 21:48:38 :: wireless connecting False 
2007/07/09 21:48:38 :: returing wired ip None 
2007/07/09 21:48:38 :: returning wireless ip None 
2007/07/09 21:48:38 :: wired connecting False 
2007/07/09 21:48:38 :: wireless connecting False 
2007/07/09 21:48:38 :: returing wired ip None 
2007/07/09 21:48:38 :: returning wireless ip None 
2007/07/09 21:48:39 :: wired connecting False 
2007/07/09 21:48:39 :: wireless connecting False 
2007/07/09 21:48:39 :: returing wired ip None 
2007/07/09 21:48:39 :: returning wireless ip None 
2007/07/09 21:48:39 :: wired connecting False 
2007/07/09 21:48:39 :: wireless connecting False 
2007/07/09 21:48:39 :: returing wired ip None 
2007/07/09 21:48:39 :: returning wireless ip None 
2007/07/09 21:48:39 :: wired connecting False 
2007/07/09 21:48:39 :: wireless connecting False 
2007/07/09 21:48:39 :: returing wired ip None 
2007/07/09 21:48:39 :: returning wireless ip None 
2007/07/09 21:48:40 :: wired connecting False 
2007/07/09 21:48:40 :: wireless connecting False 
2007/07/09 21:48:40 :: returing wired ip None 
2007/07/09 21:48:40 :: returning wireless ip None 
2007/07/09 21:48:40 :: wired connecting False 
2007/07/09 21:48:40 :: wireless connecting False 
2007/07/09 21:48:40 :: returing wired ip None 
2007/07/09 21:48:40 :: returning wireless ip None 
2007/07/09 21:48:40 :: wired connecting False 
2007/07/09 21:48:40 :: wireless connecting False 
2007/07/09 21:48:40 :: returing wired ip None 
2007/07/09 21:48:40 :: returning wireless ip None 
2007/07/09 21:48:40 :: wired connecting False 
2007/07/09 21:48:40 :: wireless connecting False 
2007/07/09 21:48:40 :: returing wired ip None 
2007/07/09 21:48:40 :: returning wireless ip None 
2007/07/09 21:48:41 :: wired connecting False 
2007/07/09 21:48:41 :: wireless connecting False 
2007/07/09 21:48:41 :: returing wired ip None 
2007/07/09 21:48:41 :: returning wireless ip None 
2007/07/09 21:48:41 :: wired connecting False 
2007/07/09 21:48:41 :: wireless connecting False 
2007/07/09 21:48:41 :: returing wired ip None 
2007/07/09 21:48:41 :: returning wireless ip None 
2007/07/09 21:48:41 :: wired connecting False 
2007/07/09 21:48:41 :: wireless connecting False 
2007/07/09 21:48:41 :: returing wired ip None 
2007/07/09 21:48:41 :: returning wireless ip None 
2007/07/09 21:48:42 :: wired connecting False 
2007/07/09 21:48:42 :: wireless connecting False 
2007/07/09 21:48:42 :: returing wired ip None 
2007/07/09 21:48:42 :: returning wireless ip None 
2007/07/09 21:48:42 :: wired connecting False 
2007/07/09 21:48:42 :: wireless connecting False 
2007/07/09 21:48:42 :: returing wired ip None 
2007/07/09 21:48:42 :: returning wireless ip None 
2007/07/09 21:48:42 :: wired connecting False 
2007/07/09 21:48:42 :: wireless connecting False 
2007/07/09 21:48:42 :: returing wired ip None 
2007/07/09 21:48:42 :: returning wireless ip None 
2007/07/09 21:48:43 :: wired connecting False 
2007/07/09 21:48:43 :: wireless connecting False 
2007/07/09 21:48:43 :: returing wired ip None 
2007/07/09 21:48:43 :: returning wireless ip None 
2007/07/09 21:48:43 :: wired connecting False 
2007/07/09 21:48:43 :: wireless connecting False 
2007/07/09 21:48:43 :: returing wired ip None 
2007/07/09 21:48:43 :: returning wireless ip None 
2007/07/09 21:48:43 :: wired connecting False 
2007/07/09 21:48:43 :: wireless connecting False 
2007/07/09 21:48:43 :: returing wired ip None 
2007/07/09 21:48:43 :: returning wireless ip None 
2007/07/09 21:48:43 :: wired connecting False 
2007/07/09 21:48:43 :: wireless connecting False 
2007/07/09 21:48:43 :: returing wired ip None 
2007/07/09 21:48:43 :: returning wireless ip None 
2007/07/09 21:48:44 :: wired connecting False 
2007/07/09 21:48:44 :: wireless connecting False 
2007/07/09 21:48:44 :: returing wired ip None 
2007/07/09 21:48:44 :: returning wireless ip None 
2007/07/09 21:48:44 :: wired connecting False 
2007/07/09 21:48:44 :: wireless connecting False 
2007/07/09 21:48:44 :: returing wired ip None 
2007/07/09 21:48:44 :: returning wireless ip None 
2007/07/09 21:48:44 :: wired connecting False 
2007/07/09 21:48:44 :: wireless connecting False 
2007/07/09 21:48:44 :: returing wired ip None 
2007/07/09 21:48:44 :: returning wireless ip None 
2007/07/09 21:48:45 :: wired connecting False 
2007/07/09 21:48:45 :: wireless connecting False 
2007/07/09 21:48:45 :: returing wired ip None 
2007/07/09 21:48:45 :: returning wireless ip None 
2007/07/09 21:48:45 :: wired connecting False 
2007/07/09 21:48:45 :: wireless connecting False 
2007/07/09 21:48:45 :: returing wired ip None 
2007/07/09 21:48:45 :: returning wireless ip None 
2007/07/09 21:48:45 :: wired connecting False 
2007/07/09 21:48:45 :: wireless connecting False 
2007/07/09 21:48:45 :: returing wired ip None 
2007/07/09 21:48:45 :: returning wireless ip None 
2007/07/09 21:48:46 :: wired connecting False 
2007/07/09 21:48:46 :: wireless connecting False 
2007/07/09 21:48:46 :: returing wired ip None 
2007/07/09 21:48:46 :: returning wireless ip None 
2007/07/09 21:48:46 :: wired connecting False 
2007/07/09 21:48:46 :: wireless connecting False 
2007/07/09 21:48:46 :: returing wired ip None 
2007/07/09 21:48:46 :: returning wireless ip None 
2007/07/09 21:48:46 :: wired connecting False 
2007/07/09 21:48:46 :: wireless connecting False 
2007/07/09 21:48:46 :: returing wired ip None 
2007/07/09 21:48:46 :: returning wireless ip None 
2007/07/09 21:48:46 :: wired connecting False 
2007/07/09 21:48:46 :: wireless connecting False 
2007/07/09 21:48:46 :: returing wired ip None 
2007/07/09 21:48:46 :: returning wireless ip None 
2007/07/09 21:48:47 :: wired connecting False 
2007/07/09 21:48:47 :: wireless connecting False 
2007/07/09 21:48:47 :: returing wired ip None 
2007/07/09 21:48:47 :: returning wireless ip None 
2007/07/09 21:48:47 :: wired connecting False 
2007/07/09 21:48:47 :: wireless connecting False 
2007/07/09 21:48:47 :: returing wired ip None 
2007/07/09 21:48:47 :: returning wireless ip None 
2007/07/09 21:48:47 :: wired connecting False 
2007/07/09 21:48:47 :: wireless connecting False 
2007/07/09 21:48:47 :: returing wired ip None 
2007/07/09 21:48:47 :: returning wireless ip None 
2007/07/09 21:48:48 :: wired connecting False 
2007/07/09 21:48:48 :: wireless connecting False 
2007/07/09 21:48:48 :: returing wired ip None 
2007/07/09 21:48:48 :: returning wireless ip None 
2007/07/09 21:48:48 :: wired connecting False 
2007/07/09 21:48:48 :: wireless connecting False 
2007/07/09 21:48:48 :: returing wired ip None 
2007/07/09 21:48:48 :: returning wireless ip None 
2007/07/09 21:48:48 :: wired connecting False 
2007/07/09 21:48:48 :: wireless connecting False 
2007/07/09 21:48:48 :: returing wired ip None 
2007/07/09 21:48:48 :: returning wireless ip None 
2007/07/09 21:48:49 :: wired connecting False 
2007/07/09 21:48:49 :: wireless connecting False 
2007/07/09 21:48:49 :: returing wired ip None 
2007/07/09 21:48:49 :: returning wireless ip None 
2007/07/09 21:48:49 :: wired connecting False 
2007/07/09 21:48:49 :: wireless connecting False 
2007/07/09 21:48:49 :: returing wired ip None 
2007/07/09 21:48:49 :: returning wireless ip None 
2007/07/09 21:48:49 :: wired connecting False 
2007/07/09 21:48:49 :: wireless connecting False 
2007/07/09 21:48:49 :: returing wired ip None 
2007/07/09 21:48:49 :: returning wireless ip None 
2007/07/09 21:48:49 :: wired connecting False 
2007/07/09 21:48:49 :: wireless connecting False 
2007/07/09 21:48:49 :: returing wired ip None 
2007/07/09 21:48:49 :: returning wireless ip None 
2007/07/09 21:48:50 :: wired connecting False 
2007/07/09 21:48:50 :: wireless connecting False 
2007/07/09 21:48:50 :: returing wired ip None 
2007/07/09 21:48:50 :: returning wireless ip None 
2007/07/09 21:48:50 :: wired connecting False 
2007/07/09 21:48:50 :: wireless connecting False 
2007/07/09 21:48:50 :: returing wired ip None 
2007/07/09 21:48:50 :: returning wireless ip None 
2007/07/09 21:48:50 :: wired connecting False 
2007/07/09 21:48:50 :: wireless connecting False 
2007/07/09 21:48:50 :: returing wired ip None 
2007/07/09 21:48:50 :: returning wireless ip None 
2007/07/09 21:48:51 :: wired connecting False 
2007/07/09 21:48:51 :: wireless connecting False 
2007/07/09 21:48:51 :: returing wired ip None 
2007/07/09 21:48:51 :: returning wireless ip None 
2007/07/09 21:48:51 :: wired connecting False 
2007/07/09 21:48:51 :: wireless connecting False 
2007/07/09 21:48:51 :: returing wired ip None 
2007/07/09 21:48:51 :: returning wireless ip None 
2007/07/09 21:48:51 :: wired connecting False 
2007/07/09 21:48:51 :: wireless connecting False 
2007/07/09 21:48:51 :: returing wired ip None 
2007/07/09 21:48:51 :: returning wireless ip None 
2007/07/09 21:48:52 :: wired connecting False 
2007/07/09 21:48:52 :: wireless connecting False 
2007/07/09 21:48:52 :: returing wired ip None 
2007/07/09 21:48:52 :: returning wireless ip None 
2007/07/09 21:48:52 :: wired connecting False 
2007/07/09 21:48:52 :: wireless connecting False 
2007/07/09 21:48:52 :: returing wired ip None 
2007/07/09 21:48:52 :: setting wireless network 0 property automatic to value True 
2007/07/09 21:48:52 :: setting wireless network 0 property ip to value 
2007/07/09 21:48:52 :: setting wireless network 0 property netmask to value 
2007/07/09 21:48:52 :: setting wireless network 0 property gateway to value 
2007/07/09 21:48:52 :: setting wireless network 0 property dns1 to value 
2007/07/09 21:48:52 :: setting wireless network 0 property dns2 to value 
2007/07/09 21:48:52 :: setting wireless network 0 property dns3 to value 
2007/07/09 21:48:52 :: setting wireless network 0 property enctype to value wpa 
2007/07/09 21:48:52 :: setting wireless network 0 property key to value w1thamoil 
2007/07/09 21:48:52 :: setting network profile 
2007/07/09 21:48:52 :: 100: Profile Written 
2007/07/09 21:48:52 :: connecting to wireless network belkin54g 
2007/07/09 21:48:52 :: interface down... 
2007/07/09 21:48:52 :: Setting false ip... 
2007/07/09 21:48:52 :: interface up... 
2007/07/09 21:48:52 :: 
2007/07/09 21:48:52 :: killing wpa_supplicant, dhclient, dhclient3 
2007/07/09 21:48:52 :: generating psk... 
2007/07/09 21:48:52 :: returning wireless ip None 
2007/07/09 21:48:52 :: wired connecting False 
2007/07/09 21:48:52 :: wireless connecting True 
2007/07/09 21:48:52 :: status request 
2007/07/09 21:48:52 :: acqlock True 
2007/07/09 21:48:52 :: 	...lock acquired... 
2007/07/09 21:48:52 :: 	...lock released... 
2007/07/09 21:48:52 :: wireless connect status generating_psk 
2007/07/09 21:48:52 :: returning wireless ip None 
2007/07/09 21:48:52 :: wired connecting False 
2007/07/09 21:48:52 :: wireless connecting True 
2007/07/09 21:48:52 :: status request 
2007/07/09 21:48:52 :: acqlock True 
2007/07/09 21:48:52 :: 	...lock acquired... 
2007/07/09 21:48:52 :: 	...lock released... 
2007/07/09 21:48:52 :: wireless connect status generating_psk 
2007/07/09 21:48:52 :: generating wpa_supplicant configuration file... 
2007/07/09 21:48:53 :: returning wireless ip None 
2007/07/09 21:48:53 :: wired connecting False 
2007/07/09 21:48:53 :: wireless connecting True 
2007/07/09 21:48:53 :: status request 
2007/07/09 21:48:53 :: acqlock True 
2007/07/09 21:48:53 :: 	...lock acquired... 
2007/07/09 21:48:53 :: 	...lock released... 
2007/07/09 21:48:53 :: wireless connect status generating_wpa_config 
2007/07/09 21:48:53 :: returning wireless ip None 
2007/07/09 21:48:53 :: wpa_supplicant -B -i wlan0 -c "/opt/wicd/encryption/configurations/0011500dfeeb" -D wext 
2007/07/09 21:48:53 :: wired connecting False 
2007/07/09 21:48:53 :: wireless connecting True 
2007/07/09 21:48:53 :: status request 
2007/07/09 21:48:53 :: acqlock True 
2007/07/09 21:48:53 :: 	...lock acquired... 
2007/07/09 21:48:53 :: 	...lock released... 
2007/07/09 21:48:53 :: wireless connect status generating_wpa_config 
2007/07/09 21:48:53 :: returning wireless ip None 
2007/07/09 21:48:53 :: wired connecting False 
2007/07/09 21:48:53 :: wireless connecting True 
2007/07/09 21:48:53 :: status request 
2007/07/09 21:48:53 :: acqlock True 
2007/07/09 21:48:53 :: 	...lock acquired... 
2007/07/09 21:48:53 :: 	...lock released... 
2007/07/09 21:48:53 :: wireless connect status generating_wpa_config 
2007/07/09 21:48:53 :: flushing the routing table... 
2007/07/09 21:48:54 :: returning wireless ip None 
2007/07/09 21:48:54 :: wired connecting False 
2007/07/09 21:48:54 :: wireless connecting True 
2007/07/09 21:48:54 :: status request 
2007/07/09 21:48:54 :: acqlock True 
2007/07/09 21:48:54 :: 	...lock acquired... 
2007/07/09 21:48:54 :: 	...lock released... 
2007/07/09 21:48:54 :: wireless connect status flushing_routing_table 
2007/07/09 21:48:54 :: returning wireless ip None 
2007/07/09 21:52:32 :: canceling connection attempt 
2007/07/09 21:52:32 ::

---

### Post by imdano on 2007-07-09
What kind of card / what driver are you using?  Also, see if you can connect with WEP encryption.

---

### Post by witham on 2007-07-10
Thanks for your reply

I am using a Buffalo g54 pci card in the laptop, I have tried to connect using WEP but with no success and the driver installed according to the device manager is 

key: info.linux.driver

Type: string

Value: acx_pci

If it was a driver fault wouldn't that stop any connection because I can connect with no encrytion?

---

### Post by imdano on 2007-07-10
Hmm, need a bit more info about the driver.  Post the output of:
lspci -nn
lshw -C network

---

### Post by witham on 2007-07-10
Thanks again for your patience the information as requested


~$ lspci -nn 
00:00.0 Host bridge [0600]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3580] (rev 01) 
00:00.1 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3584] (rev 01) 
00:00.3 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3585] (rev 01) 
00:02.0 VGA compatible controller [0300]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 01) 
00:02.1 Display controller [0380]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 01) 
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 03) 
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 03) 
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 83) 
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 03) 
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 03) 
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 03) 
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 03) 
01:08.0 Ethernet controller [0200]: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller [8086:103d] (rev 83) 
01:0b.0 CardBus bridge [0607]: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support [1179:0617] (rev 33) 
02:00.0 Network controller [0280]: Texas Instruments ACX 111 54Mbps Wireless Interface [104c:9066] 

lshw -C network 
WARNING: you should run this program as super-user. 
  *-network               
       description: Ethernet interface 
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller 
       vendor: Intel Corporation 
       physical id: 8 
       bus info: pci@01:08.0 
       logical name: eth0 
       version: 83 
       serial: 00:00:39:ae:de:95 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 multicast=yes 
       resources: iomemory:cffff000-cfffffff ioport:cf40-cf7f irq:11 
  *-network 
       description: Wireless interface 
       product: ACX 111 54Mbps Wireless Interface 
       vendor: Texas Instruments 
       physical id: 0 
       bus info: pci@02:00.0 
       logical name: wlan0 
       version: 00 
       serial: 00:0d:0b:0c:17:1e 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=acx_pci latency=64 multicast=yes wireless=IEEE 802.11b+/g+ 
       resources: iomemory:40020000-40021fff iomemory:40000000-4001ffff irq:11

---

### Post by imdano on 2007-07-10
Everything I've been reading about your chipset (ACX 111) suggests the linux driver (acx_pci) doesn't support WPA in linux.  You have to use ndiswrapper (it uses the Windows drivers for your card, which you'll have to find) to get it working.  Try following this guide. 

[http://ubuntuforums.org/showthread.php?p=2718776](http://ubuntuforums.org/showthread.php?p=2718776)

---

### Post by witham on 2007-07-10
Thanks for your help, got to stage 5 and I am stuck I have opened synaptic and have marked ndisgtk, ndiswrapper-common, ndiswrapper-source and ndiswrapper-utils-1.9 for installation but the apply button is greyed out. 
I must be doing smething wrong?

---

### Post by imdano on 2007-07-10
That's strange.  See if you can install them from the command line. ```
sudo apt-get install ndiswrapper-common
```Repeat for all the packages there.  It should find any dependencies automatically as well.

---

### Post by witham on 2007-07-10
I am having a nightmare did all that and now the pci card doesn't even light up showing power on?

The network manager doesn't even give me the option of a wireless connection?

HELP PLEASE

---

### Post by imdano on 2007-07-10
You didn't recieve any errors or anything like that while following the howto?  Post the output of lspci -nn and lshw -C network again.

---

### Post by witham on 2007-07-10
No error messages as far as I could tell?

Thanks very much for your help.


lspci -nn 
00:00.0 Host bridge [0600]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3580] (rev 01) 
00:00.1 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3584] (rev 01) 
00:00.3 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3585] (rev 01) 
00:02.0 VGA compatible controller [0300]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 01) 
00:02.1 Display controller [0380]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 01) 
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 03) 
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 03) 
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 83) 
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 03) 
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 03) 
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 03) 
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 03) 
01:08.0 Ethernet controller [0200]: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller [8086:103d] (rev 83) 
01:0b.0 CardBus bridge [0607]: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support [1179:0617] (rev 33) 
02:00.0 Network controller [0280]: Texas Instruments ACX 111 54Mbps Wireless Interface [104c:9066] 


~$ lshw -C 
Hardware Lister (lshw) - B.02.08.01 
usage: lshw [-format] [-options ...] 
       lshw -version 

        -version        print program version (B.02.08.01) 

format can be 
        -html           output hardware tree as HTML 
        -xml            output hardware tree as XML 
        -short          output hardware paths 
        -businfo        output bus information 

options can be 
        -class CLASS    only show a certain class of hardware 
        -C CLASS        same as '-class CLASS' 
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. ) 
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )

---

### Post by imdano on 2007-07-10
That's ```
lshw -C network
``` That'll show which driver you're using.  I'm wondering if maybe the acx_pci driver didn't get blacklisted like it should have.  Post the output of ```
lsmod | grep acx
``` as well.

---

### Post by witham on 2007-07-11
lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@01:08.0
       logical name: eth0
       version: 83
       serial: 00:00:39:ae:de:95
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI firmware=N/A ip=192.168.2.4 latency=64 maxlatency=56 mingnt=8 multicast=yes
       resources: iomemory:cffff000-cfffffff ioport:cf40-cf7f irq:11
  *-network UNCLAIMED
       description: Network controller
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 0
       bus info: pci@02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: iomemory:40020000-40021fff iomemory:40000000-4001ffff irq:11

I can't make anything come up using lsmod | grep acx but this is the output for lsmod if its any good?

 lsmod
Module                  Size  Used by
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
i915                   24448  3 
drm                    81044  4 i915
speedstep_lib           6148  0 
cpufreq_userspace       5408  0 
cpufreq_conservative     8200  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7360  0 
cpufreq_ondemand        9228  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
dev_acpi               12292  0 
pcc_acpi               13184  0 
tc1100_wmi              8068  0 
sony_acpi               6284  0 
button                  8720  0 
container               5248  0 
ac                      6020  0 
toshiba_acpi           11972  0 
battery                10756  0 
sbs                    15652  0 
i2c_ec                  6016  1 sbs
i2c_core               22656  1 i2c_ec
video                  16388  0 
asus_acpi              17308  0 
backlight               7040  2 toshiba_acpi,asus_acpi
dock                   10268  0 
ipv6                  268960  8 
ndiswrapper           194608  0 
lp                     12452  0 
fuse                   46612  0 
joydev                 10816  0 
snd_intel8x0           34332  1 
snd_ac97_codec         98464  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
pcmcia                 39212  0 
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               7940  0 
yenta_socket           27532  2 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
parport_pc             36388  0 
parport                36936  3 ppdev,lp,parport_pc
soundcore               8672  1 snd
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
intel_agp              25244  1 
pcspkr                  4224  0 
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
psmouse                38920  0 
agpgart                35400  3 drm,intel_agp
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
af_packet              23816  2 
tsdev                   8768  0 
evdev                  11008  4 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
sd_mod                 23428  3 
generic                 5124  0 [permanent]
ata_generic             9092  0 
ehci_hcd               34188  0 
e100                   36232  0 
mii                     6528  1 e100
ata_piix               15492  2 
libata                125720  2 ata_generic,ata_piix
scsi_mod              142348  4 sg,sr_mod,sd_mod,libata
uhci_hcd               25360  0 
usbcore               134280  4 ndiswrapper,ehci_hcd,uhci_hcd
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

---

### Post by imdano on 2007-07-11
Do you remember if something came up when you ran lsmod | grep acx during the initial install?  Also the problem is that right now your wireless card doesn't have a driver attached to it.  Notice this ```
*-network UNCLAIMED
```And the absense of an entry driver=<driver name> in the lshw entry for your wireless card?
It looked like this before you tried installing ndiswrapper: ```
*-network
description: Wireless interface
product: ACX 111 54Mbps Wireless Interface
....
configuration: broadcast=yes driver=acx_pci latency=64 multicast=yes wireless=IEEE 802.11b+/g+
resources: iomemory:40020000-40021fff iomemory:40000000-4001ffff irq:11
```

So something seems to have gone wrong while you were installing ndiswrapper.  Which windows drivers did you try to use?

edit: what is the output of the following commands
ndiswrapper -l
ndiswrapper -v

---

### Post by witham on 2007-07-11
I am really sorry to put you to this trouble it MUST have been me when I installed it, I used the dlink driver because I couldn't get the actual driver on CD to load.


$ ndiswrapper -l
net5211 : driver installed
netl112k : invalid driver!
netwli11 : invalid driver!
deb@deb-laptop:~$ ndiswrapper -v
utils Error: no version specified!
driver version:        1.38
vermagic:       2.6.20-16-generic SMP mod_unload 586

---

### Post by imdano on 2007-07-11
Ok, I'm not sure how well those dlink drivers will work for you, maybe go to Buffalo's website and see if you can find yours for download?  Also it appears that ndiswrapper didn't install properly.  You'll need to uninstall it (try using synaptic to do that). Next:
1. From a terminal run: sudo apt-get install build-essential
2.  Then head here [http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482) and download the source for ndiswrapper (get the stable version 1.47).
3. In a terminal move to the directory you installed ndiswrapper to, and type
```

tar -zxvf ndiswrapper-1.47.tar.gz
cd ndiswrapper-1.47
make distclean
make
sudo make install

```Now post the output of ndiswrapper -v.  It should say something like "utils version: '1.9', utils version needed by module: '1.9'" instead of "no version specified"

---

### Post by witham on 2007-07-11
ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.47
vermagic:       2.6.20-16-generic SMP mod_unload 586 

looking good so far thanks

---

### Post by imdano on 2007-07-11
At this point you need to install a windows driver.  I'd try to find one that's actually meant for your card if it all possible, since that will maximize the chance that this will work.  I know some people with your same card and chipset had success [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/) but the link posted to the driver used is dead.

---

### Post by witham on 2007-07-11
I have got the installation CD can I use that?

---

### Post by imdano on 2007-07-11
Yes probably.
> Works with drivers in the CBG54L/WinXP directory on the 3.70.3 Buffalo CDThat's from the link in my last post.  See if you can find those on the CD.  I think you're looking for a .inf and .sys file.

---

### Post by witham on 2007-07-12
Hi thanks for your reply I have located those files on the CD and tried to carry on with the previous post I have the following is it correct please:

sudo ndiswrapper -i netcg54l.inf
driver netcg54l is already installed
deb@deb-laptop:~$ sudo ndiswrapper -l
net5211 : driver installed
netcg54l : invalid driver!
netl112k : invalid driver!
netwli11 : invalid driver!

---

### Post by imdano on 2007-07-12
That doesn't look quite right (as you can probably tell).  First remove all the installed drivers with ```
sudo ndiswrapper -e <drivername>.  Then try reinstalling the one you want.  Run the "ndsiwrapper -l" command and make sure you don't get an error.  After you've installed it and verified there wasn't an error, run the command [code]sudo depmod -a
sudo modprobe -i ndiswrapper
```  Also, did you find a .sys file on the cd in the directory with netcg54l.inf?  If yes, did you copy it to the directory you moved the .inf to?

---

### Post by witham on 2007-07-12
I think I have removed it and tried to reinstall got this message (probably ought to just take the hint and get an ethernet cable!!!


deb@deb-laptop:~$ sudo ndiswrapper -i netcg54l.inf
installing netcg54l ...
couldn't find "FwRad16.bin" in "."; make sure all driver files, including .inf, .sys (and any firmware files) are in "." -
installation may be incomplete
couldn't find "FwRad17.bin" in "."; make sure all driver files, including .inf, .sys (and any firmware files) are in "." -
installation may be incomplete
forcing parameter PrivacyMode from 0 to 2
deb@deb-laptop:~$ sudo ndiswrapper -i tnet1140.sys
installing tnet1140.sys ...
couldn't open tnet1140.sys: No such file or directory at /usr/sbin/ndiswrapper line 217.

---

### Post by imdano on 2007-07-12
Ok, I think it's looking for a .bin file that's probably on that installation cd.  See if it's there and copy it into the directory with the .inf and .sys file.  Also make sure you remove the partially installed driver.  Make sure that when you do "sudo ndiswrapper -l" nothing shows up before reinstalling.

---

### Post by witham on 2007-07-13
thanks very much for your reply I have uninstalled everything and have copied all the bin, inf & sys files into my home directory.
I can't get sorted tonight but will come online tommorrow and try again. 
Thanks for your continued support and I  hope I am able to give the same help to new users in the future as you have given me.

---

### Post by kevdog on 2007-07-13
Just one thing --

You cant keep trying to install drivers if they dont work, things will get messed up.

Try this to remove corrupt installations:
sudo rm -R /etc/ndiswrapper/*

Then 
cd /etc/ndiswrapper
ls

Make sure no files or directories are listed.  If they are, delete everything.

Then try installing the windows driver.

---

### Post by witham on 2007-07-15
sorry for my lack of knowledge but I can't get the command to run, maybe the following screenshot (attached) would help.
I have all the Win XP driver files as well as ndiswrapper in the home directory so if I could just ask with some help as to which commands to run??

---

### Post by witham on 2007-07-15
success at last thank you all very much for your help and assistance the more I use ubuntu the more I like it

---

### Post by imdano on 2007-07-15
Awesome!  Just out of curiosity, what did you do to get it working?

---

### Post by witham on 2007-07-20
sorry for not getting back sooner but  have been away, I simply went and did a little research into Linux commands and also got an better understanding of the file structure (which I have to say makes far more sense than windows). I then re-visited the post on ndiswrapper which I followed along knowing a tiny bit more. Again thanks massively for your help and support I could not have done it without you. Even if ubuntu wasn't better than windows (which it is) it is worth using purely because of the community support and I fully intend to become a contributor in the future as well as a recipient.

---

