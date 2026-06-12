---
title: "Network Monitoring Options?"
date: 2007-11-10
forum: Networking &amp; Wireless
---

### Post by Giradman on 2007-11-10
New to Ubuntu 7.1, but have been able to connect to my home router & a public network w/ my wireless NIC (in an IBM ThinkPad) - being a long time Windows user & not familiar w/ the Linux options for monitoring networks (e.g. available connections, network strength, etc.), I was interested in what might be suggested beyond the standard installation offerings of this OS? 

I've read about *NetworkManager*, which seems like the program I'm after but wonder about whether that much 'power' is needed and 'how' intrusive it may be?  At any rate, I would certainly appreciated any comments or software suggestions that will allow a better way to 'see' the networks around my computer (and yes, I'm just getting into the BASH Shell, so hopefully that learning experience will help) - thanks all - :D

---

### Post by Fire_Chief on 2007-11-13
NetworkManager should be installed by default on your Gutsy system. It's the icon in the top panel that shows the computer icons when connected or not connected to a network. Left-clicking on it will display the wireless networks that your system can see and allow you to choose which to connect to. Right-clicking will allow you to enable/disable wired or wireless networking.

If you don't see it up there, right click on the panel and add applet...then choose network manager (I think).

---

### Post by Giradman on 2007-11-15
**Fire_Chief** - thanks for your response and the comments - I do have a 'Dual Monitor' icon on the far right of the top bar of the desktop - lies between the battery & sound control icons, however, did not seem to provide much information nor control of the network, i.e. 'left-click' brought up the option to do 'Manual Configuration' (associated w/ my wireless connection - OK); 'right-click' brought up a 'grey-out' information choice, plus a choice to enable or disable networking - not as much info as desired.

But I did 'right-click' on a blank area of the top bar, and was given the choice of adding icons/applets - did add the networking icon (which looks identical to the other described above except there is a vertical green bar which I assume is the signal strength of my 'wireless' connection); 'left-click' brings up my 'connection properties' for my eth1 (presumably my wireless connection w/ my home router); 'right-click' brings up a context menu which includes 'Properties' - provides same info as previously mentioned; also another option was 'About' giving *Network Monitor 2.12.1* - assume this is the program mentioned in your post.  

So, I guess the bottom line is that I do have this program installed - not sure 'why' there are two 'dual' monitor icons needed vs. just one?  But, this has added more choices for me - thanks again - Dave :)

---

### Post by Fire_Chief on 2007-11-15
I also have a Thinkpad with 7.10 running. When I connect to a wireless network, the dual monitors changes to a signal strength set of bars (small to large like the Cingular commercial ;) ) that fill in depending on signal strength. Also, if I put my mouse over the bars, a pop up shows the name (SSID) of the wireless network I'm connected to. When there are other wireless networks around, if I click on the bars, a drop down menu shows the list of nearby SSIDs that my laptop can see along with the Manual Configuration option and stuff on the bottom of the drop down.

---

### Post by Giradman on 2007-11-15
**Fire_Chief** - thanks for the additional info - at the present time, I'm not getting the same features (but connecting fine and w/o a problem - don't want to do anything drastic, if you know what I mean!) - I ran Synaptic PM w/ a search on 'Network Manager' - plenty of returns (many of which were already installed) - some of which were not!  I'll have to research these more to see if additional functions can help me; so far, I'm doing fine, and would not want to completely 'upset' my current settings - thanks again! :)

---

### Post by nimphelos on 2007-11-16
I have same problem. I just opened a thread about it. 

Same problem, got wireless network. Work greak. But I can't see wireless networks around me by right clicking or left clicking the icon. By left click on network icon -> Manual Configuration I can open network settings by entering my password.

It should look like this but I can't se it.
[IMG]http://www.gnome.org/projects/NetworkManager/images/wireless-at-tealuxe.png[/IMG]

---

### Post by Giradman on 2007-11-16
> **nimphelos said:**
> I have same problem. I just opened a thread about it. 

Same problem, got wireless network. Work greak. But I can't see wireless networks around me by right clicking or left clicking the icon. By left click on network icon -> Manual Configuration I can open network settings by entering my password.

It should look like this but I can't se it.
[IMG]http://www.gnome.org/projects/NetworkManager/images/wireless-at-tealuxe.png[/IMG]

I've never seen this 'dialog' box - again, I'm connected to the internet via my Linksys router in the other room - no problem; but do not get the 'details' that others mention - not a big problem as long as it works, I guess; but, seems to be a lot of various returns on these network options?  Thanks - :)

---

### Post by moulsonp on 2007-11-17
As far as I  can tell the only way to get the proper wireless monitoring (i.e. showing signal strength etc) is to enable "roaming mode". That is to left click on the icon -> manual configuration -> select your wireless connection and chose properties. 

This is fine except that by selecting roaming you cannot chose to have a static IP address which I need.

Anyone else know of a way round this?

---

### Post by Giradman on 2007-11-17
> **moulsonp said:**
> As far as I  can tell the only way to get the proper wireless monitoring (i.e. showing signal strength etc) is to enable "roaming mode". That is to left click on the icon -> manual configuration -> select your wireless connection and chose properties. 

This is fine except that by selecting roaming you cannot chose to have a static IP address which I need.

Anyone else know of a way round this?

Actually, I took the computer 'on the road' a week ago & had 'wireless' in the room, so I did switch to 'roaming' to connect to the hotel's network - did not look much at the settings though - will take another look - thanks! :)

---

### Post by nimphelos on 2007-11-17
> **moulsonp said:**
> As far as I  can tell the only way to get the proper wireless monitoring (i.e. showing signal strength etc) is to enable "roaming mode". That is to left click on the icon -> manual configuration -> select your wireless connection and chose properties. 

This is fine except that by selecting roaming you cannot chose to have a static IP address which I need.

Anyone else know of a way round this?

Omigod! That was the trick huh? I now have a good shiny nm-applet. Thanks a lot...\\:D/

---

### Post by Giradman on 2007-11-17
Well, on the road again w/ the same laptop - staying overnight in Charlotte - hotel has 'wireless' in the room - basically, I was able to connect but again am not seeing the details described in several of the other posts - I did 'right-click' the top bar and placed the 'dual monitor' icon there - a vertical bar indicating signal strength is also there; hovering over this icon just shows 'eth1' and not the SSID of my connection (either @ home or on the road); plus, still not able to get a dialog box that shows available wireless networks & their SSIDs - but again wireless networking is functioning! :)

---

### Post by moulsonp on 2007-11-18
Can't see how you have the dual monitor icon as well as a vertical signal strength bar. From one of your previous posts it seems you might have two network monitor applets on your panel? If so I suggest you remove one as you'll just confuse things if you have two.

If you want to sort this lets start from stratch. Can you post the output of 'sudo ifconfig -a'. 

Also, can you confirm that (as my previous post) you confirm that you have "roaming" enabled? You can check this my left clicking on the network monitor icon, clicking on manual configuration, selecting your wireless connection, clicking properties, and clicking the "Enable roaming mode" checkbox in the top left.

Finally, can you give a clear statement as to what you think your problem is?

---

### Post by Giradman on 2007-11-18
**moulsonp** - thanks for your responses to this thread - first, my main objectives are: 1) to 'hover' over some network icon on my DT, and have it show me the SSID of the wireless network connected to (has not happen yet); and 2) to 'see' what 'wireless' networks are available to me, their SSIDs (if broadcasting), and any other info (e.g. protected or not, strength, etc.).

Below as requested is the output of ifconfig -a - currently I'm @ home, and the laptop is connecting to my Linksys router in the other room.

Concerning the 2 icons of 'dual monitors' mentioned, I've had one icon in the notification area next to the sound speakers/date/time - this just shows dual monitors - the 'about' dialog is attached below (left): this permits 'manual configuration'.  The other icon also has 'dual monitors' but w/ a vertical signal strength bar - the 'about' dialog is also shown below (indicating a part of 'Network Manager') - this was added to the top bar by 'right clicking' a blank area and selecting 'add to panel' - right & left clicking this icon gives me different dialog boxes.

Again, I've been able to connect 'wirelessly' @ home and on 2 trips now at hotels, so I'm fine w/ this setup - not sure if the two icons are really detrimental?  I'm just curious why others are getting different results in trying to setup networking - a learning experience for me (and I'm sure other newbies to this OS).  Thanks again for your help & interest - :)

*****************************************************************************
david@ubuntu:~$ sudo ifconfig -a
[sudo] password for david:
eth0      Link encap:Ethernet  HWaddr 00:0A:E4:25:F4:52  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0x7000 Memory:d0200000-d0220000 

eth1      Link encap:Ethernet  HWaddr 00:0C:F1:27:D6:E6  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:f1ff:fe27:d6e6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1844 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1048 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1442279 (1.3 MB)  TX bytes:118309 (115.5 KB)
          Interrupt:22 Base address:0xa000 Memory:d0220000-d0220fff[ATTACH]50632[/ATTACH]

---

### Post by moulsonp on 2007-11-19
OK I'm with you. nm-applet and Network Monitor are actually two different applications. nm-applet is the one you want to get working if you want it to show you available Wireless networks. You can of course do this via the command line, something like 'iwlist eth1 scanning' would show you that. Of course, a nice pretty GUI showing the same would be nice.

From the ifconfig output above you say "the laptop is connecting to my Linksys router in the other room". Is that wireless or via ethernet cable?

Assuming that you are wirelessly connected it seems that the eth1 is your wireless card. Assuming nm-applet is picking up your wireless device (again assuming the ifconfig output was from when you were wirelessly connected it will be eth1) you should be able to left click on the nm-applet, click on manual configuration, select your wireless connection, click properties, and click the "Enable roaming mode" checkbox in the top left. Once that is done it should show the SSID you are connected to, or other available Networks.

If not, then it seems nm-applet is ignoring your wireless interface. Can you post the output of /etc/network/interfaces ? I've heard that nm-applet will not attempt to manage any interfaces for which you specify an SSID so removing the SSID line from you /etc/network/interfaces file might solve it for you. Post the file and we'll see.

---

### Post by Giradman on 2007-11-19
**moulsonp** - the Linksys router connection is wireless & the MAC# for my 'wireless' network card in the computer is the one listed as 'eth1' - yet again I went to 'manual configuration' in the 'dual monitor' icon in the notification area, and selected 'enable roaming' - to my SHOCK (and for whatever reason?), the icon changed to a stepped vertical bar appearance (indicating network strength), and after selecting my home SSID, when I hover over this new icon my network is indicated correctly along w/ signal strength - also, left clicking now shows other networks in the neightborhood.  This now seems to be WHAT I want - probably can remove the other icon mentioned previously - thanks again for your help - think I'll stay w/ this setup for a while & test it out on some more trips! :)

---

