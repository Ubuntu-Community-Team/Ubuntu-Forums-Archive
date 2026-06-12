---
title: "Wireless Connection DHCP Problem"
date: 2007-01-30
forum: Networking &amp; Wireless
---

### Post by renzokuken on 2007-01-30
I finally have my wireless card (Realtek 8187) working in Dapper after blacklisting a few kernel modules and using ndiswrapper to install the WIN98 driver.

when i do 

```
iwlist scan
```

it shows my router/access point OK and hardware addresses are present.

the problem i am having is actually connecting to it. running

```
sudo ifup wlan0
```

ends in not being able to obtain an IP

my wireless is set up to use a WPA-PreSharedKey. i dont know really how to edit /etc/network/interfaces properly for my setup, or what terminal commands to pass. if anyone could help me set it up properly i would be eternally greatful. my router is a linksys WAG354Gv2

thanks

---

### Post by spd106 on 2007-01-30
If you use the WPA sticky as a guide, then post here any specific questions. [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

If you get really stuck then post what you have so far (removing any keys etc) and we'll try to help out.

---

### Post by renzokuken on 2007-01-30
Ok thanks spd106, totally missed that thread.

It contains the settings i need by the looks of it.

One quick qusetion though. On my router, i entered a WPA-PSK which was simply the name of somebody with no spaces and lower case (i'm not too worried about heavy protection).

When using XP, i simply enter that exact same password, but the link you gave mentions entering a "hex-key" derived from that password. what is it and why doesnt windows use it? or am i just getting confused between WEP and WPA??

thanks

---

### Post by spd106 on 2007-01-30
WPA uses the same method of encryption as WEP, only it changes the keys continually. This is why you hear of a hex key. If you look at the output of **sudo iwconfig wlan0** regularly, you will see the key change.

You just need to enter the passphrase and essid into the wpa_passphrase utility to generate the actual key that is used. 

XP does this behind the scenes since you don't ever need to see the generated key. I believe this will also be the case on feisty when network configuring gets an overhaul that badly needs. For example Network Manager works quite well... when it works.

---

### Post by renzokuken on 2007-01-30
Ahhh, brilliant, thanks.

I'll give it all a go tonight and let you know how it goes.

---

### Post by renzokuken on 2007-02-02
SUCCESS.

i followed the WPA sticky HOWTO and set up my interfaces file as explained. i then went to network-manager and selected my network, entered my password and connected immediately. woohoo

however, im not sure if it was setting up WPA in the interfaces file, or entering the password in network-manager that actually solved my problem, i've never used network manager before.

does network manager read the interfaces file at all?

---

### Post by spd106 on 2007-02-02
Network Manger only reads the interfaces file to find which cards it shouldn't take control of. The way it works at the moment is that N M looks after your DHCP controlled interfaces. But if you want to set a static address then you use the interfaces file and NM will ignore it. Both use wpa_supplicant for WPA.

---

### Post by renzokuken on 2007-02-02
i see, so editing my interface file didnt really make any difference.

i was actually just being an idiot and not realising that left clicking on network manager listed the networks and i could lick on one to connect to and enter my password when asked for it.

doh!

---

