---
title: "Setting a temporary static IP address"
date: 2008-10-08
forum: Networking &amp; Wireless
---

### Post by CarlWalters on 2008-10-08
Hello - I'm hoping that someone is able to help me with this.

I need to assign a static IP address to my laptop temporarily - I don't want to change the default settings. 

I need to do this in order to access the Configuration Page of a Belkin F5D7132UK Wireless Range Extender which has an IP addrrss of 192.168.2.254. Once I can get into the Belkin Configuration page then I can set it up to work with my home wireless network by setting the IP/SSID/WEP KEY etc. I then hope it will be able to "see" my home wireless network and do the job of extending the range of it. 

However my laptop has an IP address of 192.168.1.65 (my wireless router is 192.168.1.254 - an O2 Wireless II box) and if I plug my laptop directly into the Belkin box (at 192.168.2.254)it cannot "see" it. 

So I think that I need to assign an IP address of say 192.168.2.xx to my laptop? 

Would I do something like on the laptop

1. disable Laptop wireless connection
sudo ifconfig wlan0 down

2. disable Laptop wired connection 
sudo ifconfig eth0 down

3. enable Laptop wired connection with new IP
sudo ifconfig eth0 192.168.2.xx 255.255.255.0 255.255.255.0 up

4. plug laptop into Belkin

5. in firefox navigate to Belkin config page 
192.168.2.254

6. Set Belkin Configuration
  IP Address to 192.168.1.xx
  SSID to my wireless network SSID
  WEP to my wireless network WEP KEY (64 bit-hex)

7. unplug laptop from Belkin

8. disable Laptop wired connection 
sudo ifconfig eth0 down

9. enable Laptop wireless connection
sudo ifconfig wlan0 up

---

### Post by pytheas22 on 2008-10-08
That sounds like it would work, provided that things are set up correctly on the router's end to allow you to have a static IP address in that range.  Any chances you make to your addresses and routing using the 'ifconfig' command will be forgotten after a restart, so you don't have to worry about damaging your configuration (you would need to edit /etc/networking/interfaces for changes to become permanent).

If your router is set up to provide dynamic IP addresses via dhcp, it might also work to simply type:
```

sudo dhclient -r wlan0 ###release IP on the wireless interface
sudo ifconfig wlan0 down
sudo ifconfig eth0 up
sudo dhclient eth0 ###request IP on ethernet interface
```

---

### Post by CarlWalters on 2008-10-08
thanks for the quick reply :)

Do I have to worry about what my wireless router is doing though if I'm simply plugging the laptop into the Belkin range extender? I was hoping not to have to touch the actual wireless router box settings at all if I could help it. Just assign a temporary IP address to the laptop and wire that into the Belkin box to make any changes.

---

### Post by pytheas22 on 2008-10-08
If you're only concerned with modifying the configuration of the Belkin wireless extender and it has its own IP address, then no, you shouldn't have to deal with the router itself in any way.  As long as the static IP really (or dynamic IP if the extender supports it) allows you to get connectivity to the Belkin device, things should be fine; just call '192.168.2.254' in Firefox and you should be able to make the changes that you need (I assume, although without knowing the specifics of this equipment, I of course can't say anything with certainty).

---

### Post by CarlWalters on 2008-10-08
Excellent I'll give it a go this evening. Thanks :)

---

### Post by CarlWalters on 2008-10-08
I've fallen fairly early :(

sudo ifconfig wlan0 down ## OK

sudo ifconfig eth0 down ## OK

sudo ifconfig eth0 192.168.2.20 255.255.255.0 255.255.255.0 up 
SIOCSIFADDR: Invalid argument
SIOCSIFADDR: Invalid argument

I've obviously done something wrong but not sure what.

---

### Post by pytheas22 on 2008-10-08
Maybe your driver doesn't like to accept the arguments when you give them as you did (or maybe it was just the wrong syntax; I admit I'm no expert on this).  Does this work better: 
```

sudo ifconfig -a eth0 192.168.2.20 netmask 255.255.255.0
sudo route add default gw 192.168.2.254
```

Also, I don't think you want your gateway to be '255.255.255.0'.  I think you want it to be 192.168.2.254, the IP address of the Belkin device.

Also, should have mentioned this earlier, but keep in mind that you can do this all through a GUI by going to System>Administration>Network.  The catch is that changes you make there will be saved permanently, persisting throughout reboots.  But if you erase them after you do what you need, there should be no problem (in a worst case, just replace your /etc/networking/interfaces file with a default template; this is the only file that the GUI modifies).

---

### Post by CarlWalters on 2008-10-09
> **pytheas22 said:**
> Maybe your driver doesn't like to accept the arguments when you give them as you did (or maybe it was just the wrong syntax; I admit I'm no expert on this).  Does this work better: 
```

sudo ifconfig -a eth0 192.168.2.20 netmask 255.255.255.0
sudo route add default gw 192.168.2.254
```

Also, I don't think you want your gateway to be '255.255.255.0'.  I think you want it to be 192.168.2.254, the IP address of the Belkin device.

Also, should have mentioned this earlier, but keep in mind that you can do this all through a GUI by going to System>Administration>Network.  The catch is that changes you make there will be saved permanently, persisting throughout reboots.  But if you erase them after you do what you need, there should be no problem (in a worst case, just replace your /etc/networking/interfaces file with a default template; this is the only file that the GUI modifies).

Thanks for the suggestions. 

I'll try 

```

sudo ifconfig -a eth0 192.168.2.20 netmask 255.255.255.0
sudo route add default gw 192.168.2.254

```

this evening. Do you think I need the second line if I am just going to plug into the Belkin Range Extender to tweak its configuration page? 

I think I understand about using System>Administration>Network to make changes but to be honest I don't want to risk making any permanent changes (since all is working well at the moment).

---

### Post by pytheas22 on 2008-10-09
I think you need the second line--otherwise your machine won't know how to route the packets.

Also, if you want to use the GUI, you can just backup your current settings by typing:
```

cp /etc/network/interfaces ~/interfaces.backup
```

If something goes wrong, you can restore it later with:
```

sudo cp ~/interfaces.backup /etc/network/interfaces
```

Either way, it's up to you, of course.

---

### Post by theDaveTheRave on 2008-10-22
Carl Waters,

I was wondering if you had been able to sort out your static IP issue??

if so great, if not another possibility for you is the following.

If you are using network manager you could set a static IP through that, and save this as a "location" so as it could then be available to you nice and easily should you ever need it again!

I also understand you are setting a static IP for a wireless connection, I currently have no experience of doing this and was wondering how it had gone?

Dave

---

### Post by CarlWalters on 2008-10-22
:oops:. I should have replied that I had got this working OK. Very remiss of me.

Thanks to the help offered by pytheas22 I managed to temporarily assign an IP to my laptop which was in the same range as the Belkin range extender (192.168.2.xxx) and then connect the laptop directly into the Belkin so that I could change its IP back into the range of my home network (192.168.1.xxx). 

I didn't make any changes using the GUI available at System>Administration>Network so that any changes would be reverted on a laptop reboot (but I still took a copy of /etc/networking/interfaces just in case :))

as I remember it I did something like

sudo ifconfig wlan0 down
sudo ifconfig eth0 down
sudo ifconfig -a eth0 192.168.2.20 netmask 255.255.255.0
sudo route add default gw 192.168.2.254
sudo ifconfig eth0 up

then connect into the Belkin, navigate ti its config page and change its IP address. reboot the laptop abd all done :)

---

