---
title: "See available wifi networks on start up"
date: 2014-02-03
forum: Networking &amp; Wireless
---

### Post by Hurst_Vanrooj on 2014-02-03
[FONT=FreeSans, sans-serif]I have a WIFI connection, works perfectly, this question is about re-establishing a network after shut-down and scanning for available previously unknown ones, say in a Cafe.

Justgetting to grips with Ubuntu, and this question is about seeingavailable WIFI networks, most of my questions come from my OSXexperiences.[/FONT]


[FONT=FreeSans, sans-serif]Onmy mac after start-up, this is what I do:[/FONT]

[LIST=1]	
[*][FONT=FreeSans, sans-serif]Turn	on network,[/FONT]

[*][FONT=FreeSans, sans-serif]Network	scans for wireless signals, and shows all in the menu list[/FONT]

[*][FONT=FreeSans, sans-serif]Choose	one from the list and if password protected, tap in password, but if	previously added to keychain, wifi will connect automatically.[/FONT]
[/LIST]


[FONT=FreeSans, sans-serif]Belowis a detailed process that I go through on start-up to connect towifi in Ubuntu but briefly:[/FONT]



[LIST=1]	
[*][FONT=FreeSans, sans-serif]Select	Connect to Hidden Wireless Network[/FONT]

[*][FONT=FreeSans, sans-serif]Select	previously connected network[/FONT]

[*][FONT=FreeSans, sans-serif]Select	connect, network connects[/FONT]

[*][FONT=FreeSans, sans-serif]Other	network signal are now visible in menu[/FONT]
[/LIST]


[FONT=FreeSans, sans-serif]However,and this is important, previously unconnected networks are hidden unless you try to connectto a previous network or a fake test one and then all newtorks are suddenly visible in the list.[/FONT]


[FONT=FreeSans, sans-serif]Longdetailed method of connecting:[/FONT]


[FONT=FreeSans, sans-serif]Firstlyselect the connection icon in the top bar, wireless connection isgreyed out, so I click on 'Connect to Hidden Wireless Network'.[/FONT]


[FONT=FreeSans, sans-serif]Connection:Click New, (now at this point I have already set-my home wirelessnetwork, so clicking on new brings up a menu with my home network init).[/FONT]


[FONT=FreeSans, sans-serif]Choosingmy existing network, auto fills in the blanks; password, networkname; Password etc. I click connect and the Network Icon shimmersuntil it tells me I have a Network established, now if I click on the network  icon the network that I am connected to is in the menu, with adisconnect option below, also now present is next door's wifi.[/FONT]


[FONT=FreeSans, sans-serif]IfI disconnect, both WIFI signals are present in the menu, I select myown network, boom, it connects. If I close the laptop and wake it up,again, the network disconnects, but is visible in the menu. Shut thecomputer down, and the network disappears and I have to start theprocess over again.[/FONT]


[FONT=FreeSans, sans-serif]OKso I go through the process again, but this time I select newconnection: [/FONT]
[FONT=FreeSans, sans-serif]Networkname: Test[/FONT]
[FONT=FreeSans, sans-serif]WirelessSecurity: Test[/FONT]


[FONT=FreeSans, sans-serif]Obviouslythis won't connect,and gives an error. But it does then show my home network in themenu. And my neighbours.I can scroll down the menu and connect to my home network. So, if I go to a cafe, I can't see theirwifi, but if I attempt to log into a test one first,I can wait for the error message then the Cafe networkwill become visible in the menu.[/FONT]


[FONT=FreeSans, sans-serif]I'm,new to Ubuntu, am I doing this wrong? How do I see the wifi signals?In effect I want to turn on the network and let it scan.[/FONT]


[FONT=FreeSans, sans-serif]Manythanks[/FONT]


[FONT=FreeSans, sans-serif]HVR[/FONT]

---

### Post by varunendra on 2014-02-06
Welcome to Ubuntu Forums Hurst_Vanrooj!

You shouldn't need to fake a connection to see available networks. If this is happening, it is a but with either the driver that your card is using, or in Network Manager or some other supporting package, or in Ubuntu itself.

This behaviour has been reported a few times before (typically with BCM4312 cards) but I don't know whether a bug has been reported regarding this or not.

Anyway, you may try this workaround that worked for some users -
```
sudo sed -i 's/^exit 0/iwlist scan\n&/' /etc/rc.local
```
This will add a command "iwlist scan" into your /etc/rc.local file, just above the "exit 0" line. If it doesn't work, we may take a look at a detailed report to see if something else can be tried with your setup.

To post such a detailed report, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

