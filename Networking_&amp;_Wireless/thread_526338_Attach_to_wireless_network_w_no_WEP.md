---
title: "Attach to wireless network w/ no WEP"
date: 2007-08-15
forum: Networking &amp; Wireless
---

### Post by kklingerman on 2007-08-15
Hi,

  I am trying to access a wireless network that does not have WEP enabled and who's SSID is not broadcasted.  I have just installed Feisty and have not made any changes as of yet.  The Nework control is set to Roaming and does not allow me to change WEP to none.

  I'm fairly new to linux, so any help is definately appreciated.  Thanks.

---

### Post by kevdog on 2007-08-15
We are going to be using the command line or command terminal (for now)!

First determine you interface name:  To do this do a:

lshw -C network

Find the section pertaining to your wireless device, and then look for logical name.  It should be something like eth1, wlan0, ath0, ra0, etc.

Then just to see if you can connect (this is a debugging step, we can automate this later) at command line

sudo ifconfig <interface_name> down
sudo ifconfig <interface_name> up
sudo iwconfig <interface_name> essid <"SSID of Router in Quotes">
sudo dhclient <interface_name>

Something like this:
sudo ifcofig wlan0 down
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "MyRouter"
sudo dhclient wlan0

Tell me if this works!!

---

### Post by kklingerman on 2007-08-15
That worked!  Awesome.  

Is there anyway to put it into a script or batch file?  So I can run it form the desktop?  Also, is there an script/batch that can undo and set it back to roaming (or an additional command to add WEP key info)  for my home network?

Thanks a bunch!

---

### Post by kevdog on 2007-08-15
I knew you were going to ask this!!!

Couple of things, 

To kill the script above (or commands)
sudo dhclient -r <interface_name>
sudo ifconfig <interface_name> down

I dont think roaming mode is going to work in Network Manager since the SSID is not being broadcast.

A couple of alternatives

#1 You could do what we just accomplished by using network manager and using manual configuration.  This should allow you to connect to the specified network, however if you need to connect to "roaming" networks, I believe (could be wrong) you will have to re-enable roaming mode (the tick box) in network manager.

#2.You could just abandon network manager altogether and install wicd.  I think this would do a better job with the roaming vs no roaming networks.  Ive run both network manager and wicd, and prefer wicd, although network manager is more than adequate for what you want to do.

#3 You could just stick this in a shell script (most basic way).
Put everthing you typed in a file with #!/bin/bash at the top. Change the mode of the file to an executable, and then you could run it anytime you want.  You would want to make a corresponding log-out script as described above.

Sky's the limit at this point.  I really dont know what your needs are.  If you arent going to be roaming all that much, use network manager manual configuration and be done with it.  If roaming however is important, Id probably suggest #2.

---

### Post by kklingerman on 2007-08-15
Rebooted the machine and now these commands don't work.  Any ideas?

---

### Post by Geistjaeger on 2007-08-15
KEVDOG--  Not entirely related to this particular thread, but wanted to give you thanks anyway for help--even if it was "behind the scenes."  I've got an old COMPAQ Presario 1235 with a Blitzz BWP612B PCMCIA wireless card--using your ndiswrapper HOWTO, I was able to get the card from the network UNCLAIMED state to the point that all appears to be working.  Will be taking the computer home from work to verify I can actually connect to my home network.  Will try to let you know how that goes! :)

- Geistjaeger

---

### Post by Geistjaeger on 2007-08-15
KEVDOG--  It works like a charm...writing this from home...  Next project: get the sound working!:KS

---

### Post by kevdog on 2007-08-15
> Rebooted the machine and now these commands don't work. Any ideas?

Can you post the error messages you are getting??

Can you also post 
lshw -C network

---

### Post by yogo on 2007-08-15
@Kevdog,

How do you determine which between wicd and Network manager is running your wireless connection?

TIA


Do you just untick the Network manager at startup?

---

