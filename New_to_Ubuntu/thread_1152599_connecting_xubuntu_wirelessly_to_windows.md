---
title: "connecting xubuntu wirelessly to windows"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by Dani21008 on 2009-05-08
ok, i'm really good with computers.  i just started using xubuntu, and ive always used windows.  i just want to connect to a wireless network.  the computer im connecting from has no internet connection, thats the xubuntu one.  this computer is windows and has internet.  im trying to get that computer connected to the internet via this computer.

now ive tried looking everywhere for a guide on connected to a network, but everywhere i go, i find the guide referring me to "Administration>System>Networks" or whatever, I don't see administration anywhere.  The other thing i see alot in help guides online is Network Manager, and that is not on my computer, i looked thoroughly and checked through all the applications and everything, i even found a folder with a ton of apps at /usr/share/applications/, but the only thing there i found is Network Connections, which confuses me a ton, because it doesn't search for networks, you have to put each thing in to set up a new connection, and I can't find any guides online to use it.

anyways, there is no icon with like a radar symbol or any wireless network icons in both the panels.  i know my network adapter works because i scanned for networks in the terminal with a command online, it was "sudo iwconfig scan" i think, and it found other networks, including my own.  please, can someone help me out?  go step by step at the very beginning.  it would be very helpful to include screenshots and show me what you're clicking to go to the next step (unless it is unbelievably obvious).  thanks!!!

---

### Post by wallyxwest on 2009-05-08
I am not sure what you mean by "im trying to get that computer connected to the internet via this computer." but if all you're trying to do is connect to your router's wireless network then this is what worked for me:

In the upper right hand corner (next to the time) there should a be an icon of networked computers.

-Right click and make sure you have "enable networking" checked
-Right click again and check "enable wireless"
-Give it a second to find the wireless networks around you
-Now left click on the icon and the menu that pops up should have a list of the local wireless networks
-Choose the one you want
-It will prompt you for the password to that wireless network
-It may prompt you to setup a "keyring" I am not really sure what the purpose of the keyring is, but I know my computer prompts me for it anytime I connect to a wireless network (I assume security).

I hope that helps.

WallyXWest

---

### Post by Dani21008 on 2009-05-08
ok, this looks all good, except that there is no icon of networked computer on my screen next to the time.  I know where you are talking about, but it's not there.  I think I might've originally disabled that or something because i thought i wouldn't be connecting to the internet, but im not sure.  do you know how to enable that icon again then?

---

### Post by achase79 on 2009-05-08
right click on an empty space on the bar and select "add to panel" or some sort and select the network icon

---

### Post by dvl300 on 2009-05-08
Go to control panel in windows then network connections
Now select both your Ethernet port(use a network cable to your Xubuntu PC is going to) and internet connection,

Right click and click on bridge connections give it a minute or two?

And you should now be able to browse the web on both your Xubuntu PC and windows PC!
Enjoy!
:)

---

### Post by Dani21008 on 2009-05-08
> **dvl300 said:**
> Go to control panel in windows then network connections
Now select both your Ethernet port(use a network cable to your Xubuntu PC is going to) and internet connection,

Right click and click on bridge connections give it a minute or two?

And you should now be able to browse the web on both your Xubuntu PC and windows PC!
Enjoy!
:)

dude, i want a wireless connection, i don't want a wire on the floor going from one room to another.


when i looked in the "add new items..." for the panel, the only thing that had network in the name was "network monitor" and that isn't it.  maybe there's another way to connect wirelessly?  does anyone know?

---

### Post by Pjotrovitz on 2009-05-08
You can try pressing alt-f2 and typing nm-applet. If that doesnt work, try to get a command line connection like this:

sudo iwconfig <interface name>(either wlan0 or what its name is) essid <your networks name> key <your key>
sudo dhclient <interface name>

---

### Post by Dani21008 on 2009-05-09
o wow thank you, i think that'll work. im not home right now, im on vacation, but i'll try it out when i do get home
 
thanks!

---

