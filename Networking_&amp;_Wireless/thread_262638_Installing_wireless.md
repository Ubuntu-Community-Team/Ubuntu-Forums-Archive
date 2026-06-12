---
title: "Installing wireless"
date: 2006-09-22
forum: Networking &amp; Wireless
---

### Post by rshadarack on 2006-09-22
A little background:  I have a Dell Latitude D600, which I just installed Ubuntu (the first time I have a linux computer myself, although I've used linux in small amounts before) today.

Under device manager, it says I have a BCM4306 802.11b/g card.  I've gone to the IRC chat and I was told to do a few different things, but nothing really worked, so I came here.

Right when I installed ubuntu, it recognized that I had a wireless card.  So I go into networking, highlight "Wireless connection" and hit properties.  Under network name there is supposed to be a dropdown menu of networks, but it is empty.

By the advice of the people in IRC, I loaded WiFi Radar, but it detects no networks.

I know the network is setup and running properly as the windows desktop I'm typing this on right now is using the same network.

Any suggestions?

---

### Post by wieman01 on 2006-09-22
What happens if you execute ths command? Please post the output:
> iwconfig
[COLOR="Blue"][Run this command from a terminal windows... the command line.][/COLOR]

---

### Post by rshadarack on 2006-09-22
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"ssid"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

---

### Post by wieman01 on 2006-09-22
Next thing... Please post the contents of:
> /etc/network/interfaces
...Let's see what's going on. Is "ssid" your network?

---

### Post by rshadarack on 2006-09-22
I have no idea how to tell if "ssid" is my network.

Contents of the file:

auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

### Post by wieman01 on 2006-09-22
Put it this way... Do you have a wireless router at all? Do you know how to access it?

---

### Post by rshadarack on 2006-09-22
Yes to both.

---

### Post by wieman01 on 2006-09-22
Ok, is wireless enabled? And what is the wireless id (essid)? That's your network. Is it "ssid"? If so, then we are one step closer.

---

### Post by rshadarack on 2006-09-22
The ssid of my network is "Jahrling".

---

### Post by wieman01 on 2006-09-22
> **rshadarack said:**
> The ssid of my network is "Jahrling".
Do you have a Windows computer somewhere by chance? Does it find your network ("Jahrling")? It's strange that your wireless card finds an alien network, but not yours. Makes me believe your router does not have wireless enabled...

---

### Post by rshadarack on 2006-09-22
The Windows desktop I am typing right now is connected to the same network I am trying to get ubuntu connected to (my laptop).

Why is it that you say my wireless card finds an alien network?

---

### Post by wieman01 on 2006-09-22
Because I am dumb as hell and misread your second post... I thought "ssid" is a network when you showed me the output of "iwconfig" but I should have known better. Let me think for a while and get back to you.

---

### Post by wieman01 on 2006-09-22
Ok, another try:
> iwlist eth1 scan
If your wireless network adapter works, your network should appear now.

---

### Post by rshadarack on 2006-09-22
I got this reply:

eth1 No scan results

---

### Post by wieman01 on 2006-09-22
> **rshadarack said:**
> I got this reply:

eth1 No scan results
Ok, so your wireless card has not been recognized. I reckon that I won't be able to help you with this since I don't happen to have this model. My apologies.

---

### Post by wieman01 on 2006-09-22
So you have tried other howtos for your Broadcom wireless card? To no avail?

---

### Post by haxx on 2006-09-23
you need to do a "apt-get update" for the BCM4306 firmware. I have exactly the same WiFi card and faught with this for months.

Now i can get get it in under an hour.

I dont have the info on my system right now but ill post bak when i reboot to Kubuntu.

Are you using 6.06lts (codename Dapper) for your distro.

---

### Post by Craga_89 on 2006-09-23
Having the exact same problem as rshadarack. It picks up my wirless card (as far as I can tell), but i get no scan results. I've installed ndiswrapper and my BT Voyager drivers, rebooted, it picks it up. However, if I go to System Control -> Network Settings, and try to enable my eth0 Wireless card, it turns on, but immediately gets disabled again, very strange, any suggestions on this?

---

### Post by rshadarack on 2006-09-26
Sorry for the late reply.  I had a CS project that was kicking my *** all weekend.

> Are you using 6.06lts (codename Dapper) for your distro.

Yes.

> So you have tried other howtos for your Broadcom wireless card? To no avail?

Yes.  I tried using the ndiswrapper.  I'll post a walkthrough of everything I did (as I found many steps confusing and was doing a bit of guesswork) if haxx's solution does not pan out.

---

### Post by rshadarack on 2006-09-26
I did apt-get update to get a list of updated packages.  I installed all the updates, and rebooted.  eth1 (my wireless) now says "Broadcom 4306" where as it used to say "Jahrling" although I believe that was my doing.  Everything else suggested in this thread remained the same.

Is there a specific package I am supposed to install from my wireless card?

---

### Post by haxx on 2006-09-27
heres how to get the firmware updated from there its just inputting settings.
--------------------------------
Updating BCM43xx Broadcom Wifi firmware in Kubuntu Dapper 6.06LTS.
	
	-1
	Open a terminal
	-2
	Type:
		sudo nano -w /etc/apt/sources.list

	-3
	Paste into the end of the file:
		deb [http://au.ubuntu.cafuego.net](http://au.ubuntu.cafuego.net) dapper-cafuego bcm43xx
		deb-src [http://au.ubuntu.cafuego.net](http://au.ubuntu.cafuego.net) dapper-cafuego bcm43xx

	-4
	Run in terminal:
		sudo apt-get update

	-5
	Then run in terminal:
		sudo apt-get install

	-6
	The BCM43xx firmware should have been updated.

	-7
	Log out of your user and log back in to initialize the BCM43xx native linux driver.

	-8
	Go to “System Settings”/”Network Settings” & enter the administrator zone.

	-9
	Disable “Eth0” or whatever the hard wire Network adapter is intitled.
	Select “Eth1” and press the “Configure Interface”. Choose “manual” under TCP/IP
	Enter the IP address and the Netmask.
	Enter the ESSID name of your wireless routers wlan.
	Leave the WEP/WPA encryption blank.

	-10
	Open “Wireless assistant”

---

### Post by sgardne on 2006-09-27
An addendum to Haxx's post: you'll want to run this command to avoid GPG errors: ```
wget http://au.ubuntu.cafuego.net/969F3F57.gpg -O- | sudo apt-key add -
```

Also, so far this has not worked for me, but I am doing some more testing now. I will post back in a few.

=Scott

---

### Post by sgardne on 2006-09-27
Okay, I'm still having problems. Specifically, I'm not seeing any of the access points available to me, all of which are open and available to my windows machine. Here is the output of iwconfig eth1: > eth1      IEEE 802.11a/b/  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0I'm using Xubuntu 6.06.1. When I did the update, it didn't seem like anything downloaded from cafuego. How do you tell what driver version is installed?

iwlist eth1 scan outputs: no scan results

Thanks in advance for any assistance.

---

### Post by rshadarack on 2006-09-27
When I ran sudo apt-get install, it said:

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Which I would assume is wrong.  I double checked afterwards that the lines I appended to sources.ist were still there.

Also, by "Go to “System Settings”/”Network Settings” & enter the administrator zone." I assume you mean System, Administration, Networking.  And by "Select “Eth1” and press the “Configure Interface”. Choose “manual” under TCP/IP" I assume you mean "Properties" and "Static IP Address".  Let me know if these are wrong.

I was also confused about what ip address they wanted.  By default, the ipaddress is 192.168.1.1 and the net mask is 255.255.255.0, right?  ESSID I entered "Jahrling", the name of the network.

And I couldn't seem to find wireless assistant either.

---

### Post by rshadarack on 2006-09-28
I was looking through my package list and found that my bcm43XX firmware was there but not installed.  I installed it, restarted, but still no luck.

](*,)

---

### Post by livestockPimp on 2006-09-28
have you done...
iwconfig eth1 essid jharling
iwconfig eth1 mode managed
iwconfig eth1 key XXXX-XXXX-XXXX-XXXX(your wep key here if you use it)
iwconfig eth1 channel (insert channel no here...)

then see if iwconfig gives you anything a little better.

---

### Post by rizzy on 2006-09-29
> **rshadarack said:**
> I was looking through my package list and found that my bcm43XX firmware was there but not installed.  I installed it, restarted, but still no luck.

](*,)

I just put ubuntu on a dell laptop last night and I have the bcm43 wireless card as well. I followed thru this thread and was getting the exact same results as you, until this step. I found the firmware in the package list and installed it and when I restarted the system it worked. 

If you just installed ubuntu and do not have anything important on there I would try to do a complete reinstall and see how it goes.

---

### Post by rshadarack on 2006-09-29
I ran wlassistant, and got the following errors:

X Error: BadDevice, invalid or uninitialized input device 168
   Major opcode:   145
   Minor opcode:   3
   Resource id:   0x0
Failed to open device.

I'll try reinstalling ubuntu latter tonight and see if that helps.

---

### Post by rshadarack on 2006-09-29
> iwconfig eth1 essid jharling
iwconfig eth1 mode managed
iwconfig eth1 key XXXX-XXXX-XXXX-XXXX(your wep key here if you use it)
iwconfig eth1 channel (insert channel no here...)

What should I set channel to?

I just reinstalled everything, follow the things from the top of this page and down, and still no luck.

---

