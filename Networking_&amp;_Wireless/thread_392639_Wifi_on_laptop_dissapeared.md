---
title: "Wifi on laptop dissapeared"
date: 2007-03-24
forum: Networking &amp; Wireless
---

### Post by Neuralgia on 2007-03-24
Huge problem.

Laptop Dell Inspiron 6400.

Just purchased, just installed Ubuntu 6.10 Edgy Eft

Didn't detect wifi out of the box (even though I have an Intel card, which I've read, works ok)

Started working after using Automatix, and installed some things (no idea if it helped, but immediatly after this i had a tray icon to where i could select to which network to connect... which I didn't have before)

everything was great, worked for several days... until I installed wifi radar, and tried to config it.

I'm not completely sure what happend, or if it has to do with wifi radar, since it worked ok for a day or two after install it (but didn't config it)

The problem I'm having is that wifi radar shows me some networks, but just can't connect. What's worse, the tray icon, where I could select which network to use, is just gone... I have a blank space there.

I tried to re-install network-manager, uninstall it and install it again... the same with wifi radar. Nothing happens.

-*-*-*-

If you ask me what I did exactly is this (from a link from linux-on-laptops.com)

Wireless
To get my wireless working better I did the following:

1. Open System>Administration>Networking
2. Enable the Wireless device and give it the SSID of your network.
3. Open System>Administration>Synaptic Package Manager
4. Locate and install wifi-radar
5. Open WifiRadar in Applications>Internet
6. It should locate your SSID, double click on your wireless network SSID and it will prompt you to create a profile for it.  Do it and set it up the way you like.  Then save and connect to it.  Do this for every SSID/location you connect to and whenever that SSID is in range it should connect automatically from now on.

-*-*-*-*-

right now the only network I can choose is a wired one... but common, its a laptop, I need my wifi

PS: one last thing. When my wifi was working ok, my wifi indicator (LED) stayed on... now, it bliks rapidly... in caso someone owns the same laptop and can help me.

---

### Post by Floppyjoe on 2007-03-24
You are probably best off removing wifi-radar and using the network manager applet again. You need to disable all your network interfaces in System/Administration/Networking for Network-Manager to work properly. 
It might also help to edit your /etc/network/interfaces file to comment out all but the loopback (or lo) interface by putting a # in front of the lines in that file.

---

### Post by fdrake on 2007-03-24
try the commands 
iwconfig (to see your wireless configuresion settings/status)
iwlist <interface> scanning (to view available wi-fi networks)
iwconfig <interface> essid <network name>

My wireless interface is eth1, but yours may be different . to find out look at the iwconfig outputs

---

### Post by Neuralgia on 2007-03-24
> **Floppyjoe said:**
> You are probably best off removing wifi-radar and using the network manager applet again. You need to disable all your network interfaces in System/Administration/Networking for Network-Manager to work properly. 
It might also help to edit your /etc/network/interfaces file to comment out all but the loopback (or lo) interface by putting a # in front of the lines in that file.


did this, and everything back to normal... thanks.

Now, we can close this thread.

---

