---
title: "Manual IP not being remembered between reboots"
date: 2008-11-17
forum: Networking &amp; Wireless
---

### Post by mfearby on 2008-11-17
I have a relatively new Mythbuntu installation (less than three weeks) where my manually-entered IP keeps being trashed and DHCP being used after every reboot. I've right-clicked on the Wired Network Connection icon at the top-right panel and added my IP several times, but it won't stay. What am I doing wrong?

Also, does anybody have any recommendations for sharing a folder via SMB in Mythbuntu? I've tried entering one in my smb.conf but keep getting bizarre NTFS tree disconnect errors. Is there an easier graphical GUI for setting up SMB shares in xfce/mythbuntu?  Thanks

---

### Post by kartal on 2008-11-28
Hi

I have the same problem. Is there a solution to this issue?

---

### Post by bab1 on 2008-11-28
I assume that both of you are manually seting a static IP address.  If this is so, then either disable the DHCP client or remove Network Manager.

---

### Post by kartal on 2008-11-28
bab1,

I am assigning manual ip yes. But everytime I restart ip settings go back to automatic dhcp.

How can i disable dhcp client? Removing network manager does nto sound that appealing to me because i like how everything is organized in there.

---

### Post by bab1 on 2008-11-28
> How can i disable dhcp client? 

I would remove the client.  You can do that from ```
System>>Administration>>Synaptic
```
and search on dhcp3.  You can remove the dhcp3-client and the dhcp3-common packages.

I Have not disabled dhcp myself.  I wonder if you could just  rename the ```
/etc/dhcp3/dhclient.conf
```

My preference is to remove the Network Manager.  I never use the thing and it is a known problem maker.  Just search for it like we did above.  The packages to remove are: network manager and network manager-gnome

[COLOR="Blue"]EDIT: The NM libs are the culprit.  read the Synaptics description of the packages[/COLOR]

---

### Post by kartal on 2008-11-28
Yes I can probably remove the client but i really do not want to do network setup from the terminal, I am a windows convert :)

---

### Post by bab1 on 2008-11-28
At your own risk.  You can always remove NM later.  If you think about it, you omly edit 2 files one time (about 2 minutes) how hard is that?  :D

---

### Post by mfearby on 2008-11-28
I'm not near my Mythbuntu box at the moment but I manually edited the files underneath, but I don't think I removed the network manager. In any case, it's now keeping the IP I want it to have. Thanks.

---

### Post by kartal on 2008-11-28
mfearby

Which files did you edit?


> **mfearby said:**
> I'm not near my Mythbuntu box at the moment but I manually edited the files underneath, but I don't think I removed the network manager. In any case, it's now keeping the IP I want it to have. Thanks.

---

### Post by kevdog on 2008-11-28
I would just add the instructions manually to the /etc/network/interfaces file, or simply install wicd as an alternative to networkmanager.

---

### Post by Cheap Webcam on 2008-11-28
**Very good reviews JXD638 mp5 player** This[** mp5 player**](http://www.agoodic.com/viewproduct.asp?/Very_good_reviews_JXD638_mp5_player.htm)is very good and cheap There aer very good[** reviews mp5 player**](http://www.agoodic.com/viewproduct.asp?/Very_good_reviews_JXD638_mp5_player.htm).It is very popular in the world.So come to[buy](http://www.agoodic.com/viewproduct.asp?/Very_good_reviews_JXD638_mp5_player.htm) it quickly.

---

### Post by kartal on 2008-11-29
kevdog,

I installed Wicd. It seems to work fine. However there are couple glitches. I hope someone can help me out with these or offer better alternatives.

-If the connection drops(wireles s or wired), Wicd does not pick up or reconnect

-There is no tray icon. I tried couple network tray utilities but none seemd helpful and convenient as the network managers.

---

### Post by AceRimmer on 2008-11-29
I have the same problems, only since 8.10.  Network manager doesn't allow me to make permanent changes, it resets to DHCP every time.

---

### Post by kartal on 2008-11-29
As it turns out I cannot be connected to both wired and wireless at the same time with Wicd. I click on wired connected, it disables wireless. I click on wireless connect then it disables wired connection. Quite confusing to be honest

---

### Post by Sandsound on 2008-11-29
This is a serious bug :-( using DHCP is NOT an option for me.

I have disabled network-manager from sessions and made the changes to /etc/network/interfaces, that did the trick.

---

### Post by kartal on 2008-11-29
Guys, can someone please direct me to how to edit the file properly. I swear god I have spent straigth 5 hours, read at least 15 tutorials and none of those manual ip assigning etc methods worked for me. Now Network manager is not installing properly I cannot even get that one back.  I am using wpa as security setting.

Here is the last one I have tried
[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

All I have wanted was to have 192.168.1.102 as my laptop`s ip adress. Now it is all gone berserk and cannot even  connect to my lan anymore. Quite disgusted at the moment.

---

### Post by bab1 on 2008-11-29
Kartel,

I believe you can disable these things in the menu item:```
System>>preferences>.Sessions
```
I've not used this but I'm sure that's what Sandsound is referring to.

Edit:  Here is my /etc/network/interfaces file:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet static
address 192.168.1.12
netmask 255.255.255.0
gateway 192.168.1.1

# Bring the interface up automatically upon boot
auto eth0

```

This is just a text file.  you can use gedit or vi or nano to edit it.

---

### Post by bab1 on 2008-11-29
@kartal,

> As it turns out I cannot be connected to both wired and wireless at the same time with Wicd. I click on wired connected, it disables wireless. I click on wireless connect then it disables wired connection. Quite confusing to be honest

Are you using wireless to connect to the LAN?  Why do you need the complication of 2 interfaces?  I have wireless hosts (XP) but they connect to the LAN via an AP.  T

he connection to the wireless router has 2 components (RF and Ethernet) do you know what is failing?  The WPA is for the RF (radio) portion.

---

### Post by kartal on 2008-11-29
bab1

I have wireless to connect to internet, wired to connect to my desktop((direct connection without router. This was just working fine when I had gnome network manager. Everything started to go down the hill since I have installed Wicd to get static ip and unistalled gnome manager. Now I cannot get back gnome manager work properly. It shows me wlan0 and eth0 as wired network in the interface and is not letting me delete any of the configs. I would be so happy to to wipe out gnome manager with all the settings and traces. I did compleet removal but that does not remove settings they come back in next install

The best I can have at the moment is Wicd with either wireless or wired. It cannot connect to both at the same time.

At the moment I took everything from the interfaces. This is how it looks now. 

auto lo
iface lo inet loopback


These are my last ditches really. If I solve this I will stick to Ubuntu if not I am really done with it. I am not rich enough to use a free application that will make me loose money by wasting my time like this. I am sure it works fine for many but so far it is not helping me much here.

---

### Post by bab1 on 2008-11-29
It always seems to end up like this when non-standard practices are used.  I assume now that you are using a x-over cable to connect to your desktop host.  

The proper way is to connect the laptop and the desktop to a switch  and then to the router.  The 2 hosts then can talk locally to each other via the switch.  

As far as reinstalling NM and uninstalling wicd, it really depends on how you (what method) got to where you are now.  If you used synaptics to remove or install then you should be able to reinstall and/or remove the apps using Synaptics.  You can do this from the CLI if you wish.  I believe the following is correct to remove wicd```
sudo apt-get remove wicd
``` and to purge all files use```
sudo apt-get purge wicd
```

You should also be able to reinstall Network Manager with ```
sudo apt-get install network-manager
```

---

### Post by kartal on 2008-11-29
Bab1

I am now where I was. I have wireless, gnome manager and auto assigned eth0. And I need to ask my original question again, how can i assign static ip to eth0 without getting rid of gnome manager, as it turned out it was a nightmare to uninsall it and wasted my 6 hours straight.

I understand the need for a router but my practice is not uncommon. I prefer this method especially when these 2 comps just 20 cm apart from eachother. It makes no sense to use 40m of network cable in my house or buy a  new router (since my original router is also a my wireless gateway that needs to sit where cable modem is). This cabling works in Xp, Macos and Ubuntu(when custom ip assigned). Also custom ip is a necessity if you are using vnc, ftp etc etc. I use thes computers for projects and I need the best speed I can get for fast synching. So resorting to wireless is not an option either.


Is it possible to have static IP while runnign gnome manager? I am looking for a proven-used method that is not 5 pages to apply. I have never typed(in the terminal) this much in my 16 years of my computer use.  I really do not want to mingle from now on. I really appreciate all the help and feedback here.

---

### Post by bab1 on 2008-11-30
> is it possible to have static IP while runnign gnome manager?  Sure.  But, it's very problematic and dependent on what else you have setup.  Network Manager is running on my desktop.  I just never touch it.

> I am looking for a proven-used method that is not 5 pages to apply. I have never typed(in the terminal) this much in my 16 years of my computer use. This does not exist at this point.  Gnome (and therefore NM) is being revised.  the new libs break other long standing practices. 

> I really do not want to mingle from now on. I really appreciate all the help and feedback here.
Hope you find a solution.

---

### Post by kartal on 2008-11-30
bab1,

It looks like I can disable wired network control inside gnome manager. At least I can maybe delete the profile. Do you think that letting another program to take care of wired networking is a good idea while GNM takes care of wireless only, since it does a damn good job on that one. Is there such a program designed only for ethernet? 

The other thing is why I cannot have dhcp letting assign ip numbers is that for security, I limit the number of ips(number of comps in my system) in the network, put a range for ip access and I disable dhcp. That way only the ip adresses in the network can access the network, in case of an ip conflict I would know that there is a security breach. I know it is not that great of a method but limiting keeps me sane here.

---

### Post by bab1 on 2008-11-30
> Is there such a program designed only for ethernet?   The NM applet is really for the RF (radio) side of wireless. As i said Wireless uses Ethernet as a networking protocol, just like the wired connection.

Ethernet requires only an IP address, a nameserver address and a gateway address.  your problems stem more from trying to turnoff DHCP after it was allowed to be configured (probabley at install time).

> The other thing is why I cannot have dhcp letting assign ip numbers is that for security, 
There are many reasons user want static IP addresses.  Servers typically have known (static) addresses so clients know where they are.  why do you need a static IP? 

> 

I limit the number of ips(number of comps in my system) in the network, put a range for ip access and I disable dhcp. That way only the ip adresses in the network can access the network,  What does this mean?  Are you running internet assigned IP's facing the public?  Disabling dhcp does nothing for security.  It helps in administering a larger network from a centralized location.

> 

 in case of an ip conflict I would know that there is a security breach. I know it is not that great of a method but limiting keeps me sane here.
It does nothing for security.

---

