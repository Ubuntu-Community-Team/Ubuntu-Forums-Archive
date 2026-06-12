---
title: "i LOVE ubuntu except for WiFi"
date: 2005-11-28
forum: Networking &amp; Wireless
---

### Post by myke on 2005-11-28
OK .. so far most things with ubuntu have gone well.  I managed to burn a disk image for installation, partition my win drive, and get everything up and running fairly easily with a few minor kinks along the way.   I even managed to easily use the package manager to install KDE so I could try out both systems.  Kinda  nice ... in effect I have 3 desktops installed to play around with (including the win one).  

My ethernet connection with the cable modem was picked up right away.  Someone pointed me to automatix which I quickly installed and used to then install win drivers for my linksys wifi card and it was recognized right away.  It also logged onto the wireless connection easily after I pulled out the ethernet cable.  

Here's the problem:  I can only get it to log onto a wifi signal from home and only after I use the ethernet port first.  I use wifi hotspots out of my home quite a lot and this is the only thing stopping me from using Ubuntu now as my main os as I've got everything else on it working nicely ... cd burners and all.  On a win system, when it picks up the signal you can either click the 'connect' button or set it to automatically connect to the most prevalent signal.   On unbuntu, there's no way to do this that I can find.  I installed 'wifi radar' thru the package manager which should do this for linux.  It picks up the signal easily and there is a 'connect' button but the cursor just spins and spins when I click it and the program then has to be forced to shut down as it snags.

I've tried everything I can think of.  Is there any other sniffer program or connection prog I can install to help out?  I've checked all of my settings and they seem to be correct. I use at least 3 different wifi spots throughout the day and need to be able to move from one to the other & they are all free.  Being confined to the one at home won't work for me.  I really like this unbuntu system and would very much like to make it my main os and if I could got comfortable enough with it, I'd easily drop win all together.  I just need to get this wifi problem worked out.

Any help or suggestions would be greatly appreciated.

---

### Post by aznboi on 2005-11-28
Theres ure problem. You;re using wifi-radar. It stinks. I used it and it did the same thing to me. It stinks. First off, go into System>Administration>Networking click the properties of ure eth0 and untick enable this device or connection  idont remember which one it is... ten click ok. Now download this to ure desktop:
[http://prdownloads.sourceforge.net/gtkwifi/gtkwifi-1.09.deb?download](http://prdownloads.sourceforge.net/gtkwifi/gtkwifi-1.09.deb?download)

Then open up the terminal and do:
```
su
```
This iwll ask for a password. Enter the root password and press enter. It is normal not so see any characters when entering the password.

then do this command:
```
dpkg -i gtkwifi-1.09.deb
```
Then right click on ure panel somewhere and press "add to panel..." and look for Wireless Connectivity manager. After that you should see some signal bars in ure panel. Click on it once, and a new window opens up with available access points.

Hope that helps.

---

### Post by az on 2005-11-28
[http://packages.ubuntu.com/breezy/net/network-manager](http://packages.ubuntu.com/breezy/net/network-manager)

[http://packages.ubuntu.com/breezy/net/wifi-radar](http://packages.ubuntu.com/breezy/net/wifi-radar)

Those are two options.

---

### Post by aznboi on 2005-11-28
but he said he already had wifi-radar... so i think he doesnt want to use it anymore cuz wifi-radar is stinky and seems windows worthy....

---

### Post by joseftu on 2005-11-28
Very much a newbie myself, but gtkwifi is working great for me, too.  If I can do it, anyone can!

---

### Post by az on 2005-11-28
[QUOTE=aznboi]but he said he already had wifi-radar... so i think he doesnt want to use it anymore cuz wifi-radar is stinky and seems windows worthy....[/QUOTE]
My bad.

---

### Post by aznboi on 2005-11-28
azz, do u use wifi-radar?

---

### Post by az on 2005-11-28
No, why?


If I needed to travel with a laptop, I would probably try network-manager since I have heard great things about it and it may get into Dapper main.  I think it is supposed to cover more than just wireless connectivity.


Do you know if gtkwifi will enter ubuntu repositories?

---

### Post by aznboi on 2005-11-28
no clue lol... i just kno it works great. I'll try out network-manager tho.

---

### Post by myke on 2005-11-28
You guys RAWK.  Quick, excellent, & friendly help.  I started with the first suggestion and installed gtkwifi.  I deactivated my ethernet connection and put the 'wireless connection manager' for gtkwifi in the upper panel.  It picked up my  home network, I hit 'connect' and instant connection!  It can store several networks and will auto connect on any signal in my preferred list.  I'm going to try it out in town tomorrow but all looks real good so far.  

I'd like to try out network manager as well but have 2 concerns:

1) I can't quite figure out how to install it.  It seems way more complicated and it's not in the repositories (that I can tell). 

2) With gtkwifi working so well, I'm afraid to mess it up!  :rolleyes:

---

### Post by myke on 2005-11-28
I spoke to soon ... I did find network manager through synaptic via networking/universe so I'm going to let synaptic install it and see how it works.  At least then, I can compare the two.   Either way, I'm glad I've got gtkwifi working.  That's at least one out of two.  Or out of three if you count the STINKY wi-fi radar.

---

### Post by myke on 2005-11-28
I really must be having a blonde moment ... man, I installed the network manager to try thru synaptic but it's not listed in any of the drop downs so I need to create a launcher.   The one I created failed to open the prog.  I assumed it was called simply 'networkmanager' but apparantly not or perhaps I didn't create the launcher correctly.

A little help perhaps?

---

### Post by aznboi on 2005-11-28
I havent installed it yet, but when i do ill post up some help for u... if i get it working that is...

---

### Post by NMUrugbysteve on 2005-11-28
Network manager shows up in your panel only if you run the command 'nm-applet'. It's best to add that into your sessions settings prefrebly at a lower number like 10 or 20.

---

### Post by aznboi on 2005-11-29
nice thnx

---

### Post by cloudr on 2005-11-29
I installed gtkwifi after reading these posts and I am mosly impressed excep it doesn't seem to support WPA encryption natively?

The only way I could get it to connect to a WPA network was by running wpa_supplicant from /etc/init.d/bootmisc.sh then gtkwifi connects and sends a dhcp request so all well.
But If I don't run wpa_supplicant, gtkwifi 'sees' the WPA network but when I tell it to connect it asks for a key 'for a WEP network' and it doesn't accep the key I enter both in text or in HEX.

Have I missed something or is this really the way to get WPA with gtkwifi (wpa supplicant + gtkwifi) ?

---

### Post by az on 2005-12-04
Mark Shuttleworth asked for comments on GTKwifi in this thread:

[http://ubuntuforums.org/showthread.php?t=94536](http://ubuntuforums.org/showthread.php?t=94536)

---

### Post by brokenbones on 2005-12-05
The subject of this thread was attractive, but the content didn't help me much.

I installed the drivers for my Linksys WMP54g (version1) with ndiswrapper, also did it with the Linuxant Driverloader.

Well all is fine, device recognized, network found, but it just wont get an IP from my router !!!

I tried to set it up in fixed mode, but it has no idea of who the DNS server is... any idea ? dhclient shows I get no DHCP lease at all...

Same machine when booted under windows (dual boot) connects to the network just fine. And I use no WEP or WAP, there is no one around here to steal my bandwidth anyway...

---

### Post by xxsiriusxburnxx on 2006-01-08
Another way you can try to connect to a wireless hotspot is to use the shell command dhclient, first go into your system/sys tools/ network settings, then find the SSID of the hotspot you want to connect, form there open a terminal and type ... sudo dhclient wlan0 SSID , replaind SSID with the hotspots SSID, If it works right you will send DHCPREQUEST, and hopefully you will get a proper DHCPOFFER, if it fails it will try to default to your last Active IP Lease from whatever AP you were last connected too, Good Luck

---

