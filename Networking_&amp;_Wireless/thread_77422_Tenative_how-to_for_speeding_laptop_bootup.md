---
title: "Tenative how-to for speeding laptop bootup"
date: 2005-10-16
forum: Networking &amp; Wireless
---

### Post by emendelson on 2005-10-16
I'm trying to put together a how-to for speeding bootup and getting efficient wired-wireless networking on a ThinkPad T42, using the least possible steps and the least inteference with the basic setup. This *seems* to work, but it may be possible to make it even faster. (You'll note that I didn't include the usual solution of installing ifplugd - it doesn't seem to be necessary now that network manager is available.)

Start connected to a wired network.

1. Install (from universe) network-manager; use System/Preferences/Session, Startup Programs, add nm-applet with a rank of (for example) 20. Remove the network monitor applet from the panel at the top (right). Log out and log in again. Notice your new network manager applet.

2. Unplug the ethernet cable. Click the network manager applet on the panel and choose a wired network. Follow the prompts. When prompted to create a password for the default keyring, choose something short and easy to type. Wait until you're connected to your wireless network. Test it. Plug in the ethernet cable and see if the network manager applet automatically shifts back to the wired network. (It should.)

3. Open a terminal and disable two startup items by entering:

```
cd /etc/rcS.d
sudo mv S41hotplug.net _S41hotplug.net
sudo mv S51ntpdate _S51ntpdate
```

4. Open a terminal, become root, make a backup copy of /etc/network/interfaces, and, again as root, edit the file. Comment out all lines following "#The primary network interface" and make sure that the **only** line that begins "auto" is the one that says "auto lo".

I'm not sure that item 4 is needed, but all these together do produce a fast bootup whether or not the machine is connected to the ethernet cable, and network manager does a superb job of connecting to a wired or wireless network.

Any comments or corrections will be very welcome.

---

### Post by mlomker on 2005-10-16
> 
cd /etc/rcS.d
sudo mv S41hotplug.net _S41hotplug.net
sudo mv S51ntpdate _S51ntpdate[/CODE]


You could do:

```

sudo update-rc.d -f hotplug-net remove
sudo update-rc.d -f ntpdate remove

```

I use to **chmod 600 /etc/hotplug/net.ifup**, but it is easier with Breezy.

---

### Post by emendelson on 2005-10-16
[QUOTE=mlomker]You could do:

```

sudo update-rc.d -f hotplug-net remove
sudo update-rc.d -f ntpdate remove

```

[/QUOTE]

Yes, that would definitely be more elegant. But the method I suggested is probably easier for beginners (like me) to reverse if they want to (something I'm always grateful for in a how-to). Also, unlike chmod -x, this method doesn't produce an error message during bootup.

---

### Post by mlomker on 2005-10-16
> But the method I suggested is probably easier for beginners (like me) to reverse if they want to 

The chmod of netif.up did not generate an error.  You're thinking of chmodding the /etc/init.d scripts, which is an ugly hack.  :) 

I'd argue that renaming files that require sudo permissions is harder than cuting/pasting these commands.

To put the links back:
```

sudo update-rc.d hotplug-net start 41 2 S . stop 89 0 6 .
sudo update-rc.d ntpdate start 51 S 2 .

```

---

### Post by emendelson on 2005-10-16
[QUOTE=mlomker]The chmod of netif.up did not generate an error.  You're thinking of chmodding the /etc/init.d scripts, which is an ugly hack.  :) 

I'd argue that renaming files that require sudo permissions is harder than cuting/pasting these commands.

To put the links back:
```

sudo update-rc.d hotplug-net start 41 2 S . stop 89 0 6 .
sudo update-rc.d ntpdate start 51 S 2 .

```[/QUOTE]

Apologies for being unclear - yes, I meant exactly what you said - that chmodding the /etc/init.d scripts produced error messages. Thanks for the code for restoring the links - I'd never seen that before.

Anyway, while we're here, does the basic set of four steps seem right to you for Breezy? Is there more (or less) that needs to be done for a fast bootup on a laptop that may or may not be wired when booted?

---

### Post by mlomker on 2005-10-16
> Is there more (or less) that needs to be done for a fast bootup on a laptop that may or may not be wired when booted?

No, those are the two key files.  I clean my config up a little further by removing these, since they are related to software RAID and what laptop user is going to have that?

```

sudo update-rc.d -f mdmadm-raid remove
sudo update-rc.d -f lvm remove
sudo update-rc.d -f evms remove

```

To put back:

```

sudo update-rc.d mdadm-raid start 04 S .
sudo update-rc.d mdadm-raid start 50 0 6 .
sudo update-rc.d lvm start 26 S .
sudo update-rc.d lvm start 50 0 6 .
sudo update-rc.d evms start 27 S .
sudo update-rc.d evms start 49 0 6 .

```

---

### Post by sigma2805 on 2005-10-18
hey everyone,
thanks for the information. my laptop is definetly starting up quicker. One quick reminder i can add in would be to install BUM (sudo apt-get install bum) and then disable some things that you don't need for example in my situation i disabled bluetooth support from starting up since i don't have a bluetooth device in my laptop. I also disabled the HP printing and scanning system as well as powernowd(i have a celeron M which doesn't support cpu scaling)

Also i have a problem right now...
After installing NetworkManager, i can get a signal but i can't access any websites. Now, my theory is that i have wpa_supplicant setup to startup with the laptop and automatically connect to my home network. I think this is conflicting with networkmanager which is also why it still is taking sometime to configure the network devices. Is there any way to have network manager startup but not take over the wireless device?

Thanks everyone!

---

### Post by mlomker on 2005-10-18
> install BUM (sudo apt-get install bum) and then disable some things that you don't need for example 

Wow!  I hadn't looked at that tool but I'd heard of it.  It's much nicer than I expected and pretty much does away with the update-rc.d stuff.

>  Is there any way to have network manager startup but not take over the wireless device?

Looking at that tool has been on my to-do list.  It's been a low priority because I've already invested a lot of time into ifplugd/whereami and it's perfectly configured right now...I never have to touch a thing.

---

### Post by sigma2805 on 2005-10-18
well...right now heres what i'm doing at home to be able to connect to the wireless network.

1) Computer starts up detecting the wireless network(wpa encryption) and connects to it with wpa_supplicant. 
2) Network manager starts up
3) stop all wireless devices through network manager
4) bring up the wireless interface manually through network configuration....

Is there a script i can create that will recognize if i'm connected to my home network and not startup network manager, but if the computer can't connect to my home network, then start up network manager?

---

### Post by mlomker on 2005-10-18
[QUOTE=]Is there a script i can create that will recognize if i'm connected to my home network and not startup network manager, but if the computer can't connect to my home network, then start up network manager?[/QUOTE]

Network location detection is exactly what whereami does.  The problem is that setting it up is a lot of work.  [Here's a thread on it.]("http://www.ubuntuforums.org/showthread.php?p=394505#post394505")

---

### Post by ProPilot on 2005-10-18
I needed the ntpdate fix - I have executed the command and my laptop now has an acceptable bootup speed for me.

Thanks very much for this.

---

