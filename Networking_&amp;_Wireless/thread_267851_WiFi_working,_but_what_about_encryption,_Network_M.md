---
title: "WiFi working, but what about encryption, Network Manager?"
date: 2006-09-29
forum: Networking &amp; Wireless
---

### Post by sjbshark on 2006-09-29
I managed to get my WiFi working by scanning these other threads and resources, but to do so I had to disable encryption on my router so...

How do I go about re-encrypting?  My Router is a Netgear WGT624 v3 and here are my possible security settings:
[LIST]
[*]WEP
[*]WPA-PSK [TKIP]
[*]WPA2-PSK [AES]
[*]WPA-PSK [TKIP] + WPA2-PSK [AES]
[/LIST]
So I assume I pick one of those in my wireless interface and assign a password, but what do I do in Ubuntu?

Second question deals with Network Manager.  I can't get it to see my wireless connection, even though the connection is up and working fine.  Same with Knetwork Mangager. What up with that?

Thanks

---

### Post by reacocard on 2006-09-29
For network manager, is your /etc/network/interfaces file set up correctly? All the entries (except lo) need to be either commented out or look something like this:
```
auto eth0
iface eth0 inet dhcp

```

As for your other problem, when you get NM working, you can just tell it to connect, and it'll ask for the password. That's it.

---

### Post by sjbshark on 2006-09-29
Hmmm...

I guess I don't know what to look for with NM.  I'm new to Linux, so I need help when operating in the world of the terminal.

If someone could direct me to a guide or set of instructions...

thanx

---

### Post by dppowell on 2006-09-29
NM is kind of a proxy application for the 'normal' way that Linux deals with network interfaces (i.e. the /etc/network/interfaces file).

You can edit that file with nano, a nice little terminal-based text editor.  Because it's a system file, you'll need to edit it via sudo, so your command will look like this:

sudo nano /etc/network/interfaces

Then go down and comment out all the definitions you'll see for eth0, etc. These are the traditional configs for your network interfaces.  If the system takes control of them first, NM can't use them, which is what you're experiencing.

So just stick a '#' in front of each line of those definitions, and reboot.  Assuming NM installed okay, you should be up and running.

---

### Post by reacocard on 2006-09-29
> You can edit that with nano
Or if you'd prefer a GUI app, use gedit
```
gksudo gedit /etc/network/interfaces
```

---

### Post by sjbshark on 2006-09-30
OK. got it working.

Thanks for the help.

---

