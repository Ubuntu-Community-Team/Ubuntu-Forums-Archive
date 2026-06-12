---
title: "Networking question"
date: 2007-05-19
forum: Networking &amp; Wireless
---

### Post by i386DX on 2007-05-19
I want to know if the following is possible.

My current network:
```


Cable    ----->  Windows 2k   -----> switch -----------> Ubuntu Desktop 
Modem            with ICS                       |------> Ubuntu Laptop    
                                                    X

```

The 2 Ubuntu-computers does have a wireless network adapter.  Now I want to be able to make a connection over the wireless network when the laptop isn't wired (connection X).
It should be enough when I'm able to use the shared files on the Ubuntu desktop, but when it's possible internet too should be great...
I know it'll probably easier when I place a wireless router at the beginning of the network, but I want to know if I can do it the cheap way ;-)  

The 2 wireless networkadapters are recognized by networkmanager, but I don't know how to set up such a connection...

---

### Post by veloce on 2007-05-20
> **i386DX said:**
> I want to know if the following is possible.

My current network:
```


Cable    ----->  Windows 2k   -----> switch -----------> Ubuntu Desktop 
Modem            with ICS                       |------> Ubuntu Laptop    
                                                    X

```

The 2 Ubuntu-computers does have a wireless network adapter.  Now I want to be able to make a connection over the wireless network when the laptop isn't wired (connection X).
It should be enough when I'm able to use the shared files on the Ubuntu desktop, but when it's possible internet too should be great...
I know it'll probably easier when I place a wireless router at the beginning of the network, but I want to know if I can do it the cheap way ;-)  

The 2 wireless networkadapters are recognized by networkmanager, but I don't know how to set up such a connection...

Not sure what that windows machine is doing, is it a firewall?  If so is it also the dhcp server for your network?  Is your switch also a wireless access point?

If all this is right, then your Ubuntu desktop and laptop should be able to connect to the local network and be assigned ip addresses in the same range.  Then you can set up shared folders either with samba or nfs.  (I've only ever used samba because I have windows machines on the network, but assume nfs would be straightforward)

I'd prefer to see the windows install replaced with a firewall distro (e.g. IPCop or pfsense) as this would give greater peace of mind and they both provide web based configuration that you can set up from your Ubuntu machines.

---

### Post by i386DX on 2007-05-20
The Windows 2000-machine is used to share the internet with ICS (internet connection sharing). It's not possible to install another operating system on it. (the computer is also used for internet/office-work). My switch doesn't have a wireless access point.

---

### Post by veloce on 2007-05-20
> **i386DX said:**
> The Windows 2000-machine is used to share the internet with ICS (internet connection sharing). It's not possible to install another operating system on it. (the computer is also used for internet/office-work). My switch doesn't have a wireless access point.

I think I now understand what you want to do, but I may not be much help setting it up.  What I think you want is:

[LIST=1]
[*]Set up the desktop as a wireless access point. 
[*]Connect the laptop to the wireless network defined by the desktop
[*]On the desktop, bridge the wireless network to the wired network
[/LIST]

If you get 1 sorted, then 2 is trivial.  I'm not sure about 3.  

Hopefully, this may help with doing searches for what you want. Sorry I can't be more help.

---

### Post by i386DX on 2007-05-24
I created an Adhoc connection between my desktop and laptop. Now I'm able to ping to each other. But at this moment i'm not able to connect to the internet (or other network). I probably have to do something with those bridge-thingies but I don't know how...

Current situation
```


              internet IP       192.168.0.1                      192.168.0.10 (wired)
Cable      ------> Windows 2k  ------------------>  switch ------> desktop (192.168.1.1 wireless)
Modem              ICS                                     - 192.168.0.11 (wired)
                                                           -----> laptop (192.168.1.2 wireless)

```

So now I have to bridge the first network to the second? Any tips?

---

### Post by veloce on 2007-05-24
> **i386DX said:**
> I created an Adhoc connection between my desktop and laptop. Now I'm able to ping to each other. But at this moment i'm not able to connect to the internet (or other network). I probably have to do something with those bridge-thingies but I don't know how...

Current situation
```


              internet IP       192.168.0.1                      192.168.0.10 (wired)
Cable      ------> Windows 2k  ------------------>  switch ------> desktop (192.168.1.1 wireless)
Modem              ICS                                     - 192.168.0.11 (wired)
                                                           -----> laptop (192.168.1.2 wireless)

```

So now I have to bridge the first network to the second? Any tips?

Sorry, that's where you go past my knowledge.  I haven't had to do that. I suggest searching the forum then, if no luck, start a new thread :  "Bridging Wireless Network to Wired"

---

