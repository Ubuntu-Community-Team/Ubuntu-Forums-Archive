---
title: "Can't connect to wireless internet with D-Link DWL-520+"
date: 2007-12-15
forum: Networking &amp; Wireless
---

### Post by whalecommando on 2007-12-15
I am having lots of trouble connecting to the internet. I am running ubuntu's gutsy gibbon and it recognizes the wireless card (D-Link DWL-520+) and all networks and their signals  but i can't connect to any networks. I am a complete NOOB at this so all the other topics sadly did not help me at all as I got lost in all the terminal crap. I heard you need firmware or what not from ACX but their website is even more confusing about. Please help, thanks in advance. Please make it beginner friendly, thanks again.
:KS

---

### Post by gilf on 2007-12-15
If you do see the network lines, try clicking on one of them to connect to that network.

---

### Post by whalecommando on 2007-12-16
I do but it never connects then gutsy gets all screwy and I can't open applications so I have to reboot.

---

### Post by gilf on 2007-12-16
That's a little disturbing. The "gutsy gets all screwy" part.

Does the same thing happen when you open a liveCD session from the liveCD disk and you try the same procedure of clicking on the network lines?

If so, where did you get your LiveCD disk, and have you checked the disk with the disk checksum?

---

### Post by Psycam on 2007-12-16
Same problem here. It clearly detects all available networks in the vicinity, but when I click the open network, the two little globes shows it's trying to connect (they don't blink though) and then it fails.

Same thing happens from LiveCD.

---

### Post by whalecommando on 2007-12-17
Same thing psycam said, live cd doesn't work either. I got the cd by downloading, the checksum matched when i checked it and the cd integrity had no problems. When I mean Gutsy gets all screwy.... nothing screwy happens except applications won't open. I heard you need to download ACX drivers or something, I'm sooooo nooby at terminal I can't understand what to do.

---

### Post by Psycam on 2007-12-17
Guh... After hours of messing around, I found that I am able to stay connected to my router by manually configuring it (through the applet), whereas by clicking my router directly from the applet would only attempt to connect. It's not the driver/firmware's fault.

How confusing, but at least I have internet now :)

---

### Post by whalecommando on 2007-12-17
I got the internet sorta working on the live cd, it connected and showed the bars but when i opened mozilla, I couldn't go to any websites.... so internet is a bit weird. I think I'm going to re-install Gutsy and thats gonna take some time so maybe some other day. The ACX driver seems to be my answer as its for the ACX chipsets or whatever which I have. just google acx100 for their website if your wondering what it is.

---

### Post by gilf on 2007-12-19
> The ACX driver seems to be my answer as its for the ACX chipsets or whatever which I have. just google acx100 for their website if your wondering what it is.

Not if you showed available networks in a LiveCD session. If you got that far on the LiveCD the liklihood is that **the stock Ubuntu drivers work as shipped**. As well as network manager. In order to show those bars, the nic must be receiving wireless signals from  the wireless router, and network manager is correctly reporting to you what is being communicated to it. By running LiveCD you have bypassed all of your prior system changes, including the ACX driver you mentioned above.

If you click on one of those little network name bargraph lines that you want to connect to in LiveCD session, you will be given a password dialog (if you need WPA or WEP). If you successfully enter this you will see an icon for[COLOR="Red"] two little black screens superimposed[/COLOR] in the top right corner of your screen. That means CONNECTED.

[COLOR="Red"]Edit: note the description of the icon in red above is incorrect. This is what is seen in a wired card. A wireless card presents a single bar graph when connected -- this is not the same as the network lines with bargraphs that you click on in an earlier stage. -- gilf[/COLOR]


The circling balls before that mean that your network card is trying to authenticate (via WEP or WPA) with the router. Authentication means you have to have the right password type  (WPA, WEP 128 bit or 64 bit, passphrase or hex, etc). If you don't get past that point to the connection symbol, you don't have the right password or password type for the router --  Or your router is WPA enabled and your nic can only do WEP -- in other words the NIC is not 802.11g compatible.

If you are connected with the conmnection icon, don't give up at this point the whole problem is narrowed down. You've eliminated 95% of the possibilities. (other than something out of left field like bad computer memory or hardware) 

The most likely cause after connecting in a LiveCD session (where you have modified nothing in the session manually)  is that you don't have Mozilla Firefox configured for your network.

You might try this:

Open Firefox, click on Edit at the top of the screen, select Preferences, pick the Advanced tab at the top of the window, select the Network tab, click on Settings, try first "direct connection to the internet". If that doesn't work, try "auto detect proxy settings". If that doesn't work, be sure to return Firefox to its original setting.

You also want to double check that your modem or gateway or router or whatever you have is actually connected to the internet.

---

### Post by gilf on 2007-12-19
Important things to remember about Network Manager:

You should be in roaming mode.

You should click on the little network icon on the top right of the screen.

The networks shown are AVAILABLE networks, not connected networks.

To connect to any one of them you must click on that one's network name (essid) line.

Then (and only then) will you be asked for a password if WPA or WEP.

If the connected (big bar graph) icon shows up after the circling balls, then  (and only then) are you actually CONNECTED.

Seeing the network bargraph lines DOES NOT mean you are connected. You will not be able to open Firefox and be on the internet simply because you happen to see AVAILABLE networks. You must connect by clicking on one of them.

The network name (essid) line or lines almost always does mean (in a LiveCD session)  that your stock Ubuntu card drivers and your network manager are working correctly, however.

---

### Post by whalecommando on 2007-12-19
I did click on one of the networks, I removed the password so i just directly connected to it and the bar graphs appeared and not the two computers with black screens. So you're saying i click on the network once again? Also if I do get the internet working on the cd, how do I get those settings on my comp without reinstalling?

---

### Post by gilf on 2007-12-19
Are you running Kubuntu or Ubuntu?

In Kubuntu you do get a bargraph if you are connected. 

In Ubuntu you get the two little black screens icon.

This is the problem with language, heh. Any possibility you can get a snapshot of what you are seeing, and post it here.

The program Ksnapshot works well for this and you can snapshot just a small region of the screen instead of a whole window or screen. Ksnapshot works in Ubuntu and Kubuntu both.

---

### Post by whalecommando on 2007-12-20
Ubuntu and it gives me bargraphs

---

### Post by whalecommando on 2007-12-20
but thats the LiveCD I'm reinstalling Gutsy cuz I seemed to have messed it up. Hopefully I'll have more luck. By the way I did go to the drop down menu and clicked on the network but it can never authenticate the network password.

---

### Post by gilf on 2007-12-20
Then the most likely explanation is you either have the password wrong or you are entering it as the wrong type for your wireless router:

The various types include WPA, WEP-128 bit, WEP-64 bit, and as an ASCII passphrase and as a hex string.

You have to select which of these you are entering in the password dialog, and select  the right type, and then enter the password.

If you can check your wireless router try to see what type of password it is expecting.

---

### Post by whalecommando on 2007-12-21
I removed the password so its impossible I got the password wrong. I reinstalled ubuntu and I still get the bargraphs and firefox still does not work (i did what you said and it still doesn't work). I open up network tools and I'm receiving and transmitting a couple bytes and I looked at help and it told me to run a couple of commands in terminal. When I did it said something about my wlan0 being disabled or something so is there a way to enable it or is that not even a problem? I'll try to get a picture of it.

---

### Post by gilf on 2007-12-21
I think you are getting connected to the network when you are seeing the second bargraph display after you click on the first network line. I believe I've made a mistake in the description of what shows when you are connected. When you are connected in a wired installation, the double black screen shows, BUT when you are connected in wireless mode, the connection icon is a bargraph of signal strength (not to be confused with the earlier stage where there was a bargraph and a network name in a line) Sorry about that confusion. It comes from working with both Ubuntu and Kubuntu wired and wireless computers here, and thinking the double screen icon was a ubuntu symbol. In fact both flavors of network manager do the same thing. ASgain, apologies for any confusion.

Anyway, sounds like you were real close in the LiveCD session where you clicked through and got the final bargraph -- meaning connected.

If you can repeat this (from LiveCD), I'd like to ask you to check the entries for the DNS tab in System>Administration>Network what does it say? Also, if you can read your router in a terminal -- does it have the ability to report what computers are connected to it? If so, does it show your Ubuntu system as connected?

---

### Post by jmbadone on 2008-01-09
Any luck in solving this issue?  I have something VERY similar.  Here's my story:

Dell Precision 330 desktop, Pentium 4 running Ubuntu 7.10 downloaded from Purdue mirror.
DWL-520+ PCI card (it's labeled 802.11 b/g capable)
I can see my wireless network in the upper right hand corner.  Good signal strength (3 bars out of 5?)
When I click to connect on my network "2WIRE314", I'm asked for a passphrase.  I change this to "WEP 64/128 bit Hex" from the drop down box and enter my 10 digit encryption key.
The system tries to connect.  I can see the icon change in the upper right hand corner to the "swirling circle".  After a minute or two, it gives up and asks me for the encryption key again.  Mind you, I've got the encryption key memorized (I use it on multiple computers), and I even double-checked it against the router information.  So I'm CERTAIN I've got the 10 digits correct.

Note that I've tried every Hex/ASCII/Phrase option available in the drop down box that will accept a 10 digit key and none work.  One option actually locks up the computer (frozen mouse/cursor and keyboard with lights flashing on the keyboard).  Forces a hard restart to clear it. 

When I pull up the system logs, I note that the system schedules and starts step 1 of 5 of connecting to the network, and schedules step 2, but never gets any further.

Here are other System Log and Message Log items I'm seeing if it's any help to someone with a heck of a lot more knowledge than me:

From the System Log:
Network Manager: <debug> nm_device_802_11_wireless_get_activation_ap(): Forcing AP '2WIRE314'

From the Message Log:
wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b Scope) -- mabe MAC filtering by peer?)

and another (from I forget where):
Access point 2WIRE314 is encrypted, but NO valid key exists. New key needed.

Any help or suggestions on how to solve this would be greatly appreciated.  Please note that, like many others, I'm relatively new to Linux/Unix. I can move around in directories at the command line, but not much more.  If you have a command line fix, please be VERY explicit in your directions.

Thanks!!!

---

### Post by whalecommando on 2008-01-10
Sorry i've been gone so long, its holidays and break you know. 

I'm sad to say that I'm gonna be pretty busy soon with finals and all that.

---

### Post by larseko on 2008-02-12
Did anyone get a solution to this? Same with my PCI card DWL-520+ and 7.10. Shows the network, but refuses to connect, regardless of encryption. And the nonfree drivers manager says no nonfree drivers are needed :-| 

Do I have to install ndiswrapper manually?

---

### Post by Ian505 on 2008-02-20
jmbadone:

I am having the EXACT same problem as you. I didn't do any of the terminal stuff... but your situation sounds almost exactly like mine. 
> 
Dell Precision 330 desktop, Pentium 4 running Ubuntu 7.10 downloaded from Purdue mirror.
DWL-520+ PCI card (it's labeled 802.11 b/g capable)
I can see my wireless network in the upper right hand corner. Good signal strength (3 bars out of 5?)
When I click to connect on my network "2WIRE314", I'm asked for a passphrase. I change this to "WEP 64/128 bit Hex" from the drop down box and enter my 10 digit encryption key.
The system tries to connect. I can see the icon change in the upper right hand corner to the "swirling circle". After a minute or two, it gives up and asks me for the encryption key again. Mind you, I've got the encryption key memorized (I use it on multiple computers), and I even double-checked it against the router information. So I'm CERTAIN I've got the 10 digits correct.

Note that I've tried every Hex/ASCII/Phrase option available in the drop down box that will accept a 10 digit key and none work. One option actually locks up the computer (frozen mouse/cursor and keyboard with lights flashing on the keyboard). Forces a hard restart to clear it.[COLOR="Blue"]Core 2 Quad Q6600- PNY GeForce 8500GT 512MB - 3GB RAM -160GB HD space - Asus P5N-E SLI MoBo - and, of course, D-Link DWL-520+[/COLOR]

I have tried everything in the above quoted paragraph. What really puzzles me is that I am currently on the same machine using the same card in Windows XP. Here is my current configuration in the Zero Wireless Utility.

[[IMG]http://img120.imageshack.us/img120/5998/zerowirelessconfigyi3.th.png[/IMG]](http://img120.imageshack.us/img120/5998/zerowirelessconfigyi3.png)

What's wrong? I don't know how to find out what the terminal is saying... but I would be happy to find out if somebody would simply give me the commands. (And no rm's either)

-Ian

---

### Post by cnator on 2008-03-05
well, first of all sorry for my english

Second, y succed in conect my pc with wireless with that card, y will post the exact command i use in the terminar windows, y have read, that the native driver of the chip has a bug, with the network manager, so it have to be disables, and configure by terminal

ok first to disable network manager:

sudo /etc/dbus-1/event.d/25NetworkManager stop
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop

know another command to prevent run this services at startup, this has to be executed as root (don't ask why, just i found it like that  and work)

echo "exit" > /etc/dbus-1/event.d/25NetworkManager
echo "exit" > /etc/dbus-1/event.d/25NetworkManagerDispatcher

ok there is the fist step ofit, we have stop the networkmanager, and prevent to start again automaticaly

then to configure the wireless card is the following
*my interface is wlan0 so i will use that as an example, that must be changed by the interface of your own.

sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "essid in quotes"
sudo iwconfig wlan0 key HEX_KEY
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

with that I always connect

one small problem is that im a noob for linux, so y couldn't make the last part as a script,to run automaticaly on startup, so,y have to type all of it, each time y run linux maybe you will find the way to do it.

I hope that this post help someone, and also y apologuise because of my english and im to lazy to correct the words :) mayby i will in the morning, im too sleepy right know :):)

---

### Post by potrick on 2008-03-25
Reading through this brought me to a final solution, so I thought I'd share. 

So first I followed our good friend's instructions as given, first disabling Network Manager:

```

sudo /etc/dbus-1/event.d/25NetworkManager stop
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
```

And then we disable the service from starting at startup, running as root:

```

sudo bash
echo "exit" > /etc/dbus-1/event.d/25NetworkManager
echo "exit" > /etc/dbus-1/event.d/25NetworkManagerDispatcher
```

Close this terminal window and open a new one so we're not running as root anymore. (note: if someone thinks it's not safe or necessary to run as root here let me know and I'll update. I'm just following the suggestions I found elsewhere)

And then we have the series of commands our friend ran every time at startup. I altered them to work well as a script:

```
#!/bin/sh

ifconfig wlan0 down
dhclient -r wlan0
ifconfig wlan0 up
iwconfig wlan0 essid "network name in brackets"
iwconfig wlan0 key HEXCODEHERE
iwconfig wlan0 mode Managed
dhclient wlan0
```

As before you'll have to configure this to fit your network, with the network name in the brackets and the Hexcode where it says HEXCODEHERE. If you want you can save this script where you want, set the permissions to allow it to execute and run it with sudo whenever you want to connect to your network. 

Or, if you only use wireless in one location, you may simply want this script to open when your computer boots. No problem. Open a text editor to write a new script in your /etc/init.d folder (note, if you don't use gnome replace "gedit" with your preferred text editor.)

```
sudo gedit /etc/init.d/startwireless

```


Copy and past the script above in the text editor that opens and save. Then make the script executable:

```
sudo chmod +x /etc/init.d/ startwireless defaults
```

And then run this command to ad it to startup:

```
sudo update-rc.d startwireless defaults
```

This worked for me. Let me know if it works for you.

---

