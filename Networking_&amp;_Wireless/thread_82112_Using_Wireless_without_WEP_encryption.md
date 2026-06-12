---
title: "Using Wireless without WEP encryption?"
date: 2005-10-25
forum: Networking &amp; Wireless
---

### Post by OneSeventeen on 2005-10-25
I can't seem to connect to wireless networks that don't use WEP encryption.

I have successfully connected to 3 or 4 different WEP encrypted networks first try, but have yet to connect to unsecured networks.

Is there a trick to this?  Do I need to change something somewhere other than the network configuration window?  

I usually get there by double-clicking the network icon, then clicking "configure" and then click on "properties" and choose the network from the drop-down menu... which it always finds the proper network ID easily, then I remove the WEP key from my previous network, click okay, and it takes a good 2 minutes before the window closes, and it looks like it's connected (sending and receiving small packets of info every minute or so), but won't resolve domain names or anything, and won't show me the network I'm on.

This happens on every unsecured network I've tried so far.

---

### Post by sigma2805 on 2005-10-26
have you tried using network manager? I find it works well, especially in your situation where you wont be connecting to WPA protected networks (because from my observations, wpa_supplicant conflicts with network manager) Anyway, open up synaptic and search for networkmanager. install that then go to System->Preferences->sessions then under the startup programs tab and click on add for the command type /usr/bin/nm-applet and then for the order type something low like 10. Then reboot. You should see a little icon in the top right corner and if you click on it it should bring up the network available and you can also configure your wireless network that are using WEP encryption as well.

---

### Post by OneSeventeen on 2005-10-31
I'm trying to stick with officially supported packages, but I may install it if I can't find another solution.

I've even rebooted a few times with no WEP key set up or anything... I have no idea what's going on, but for all I know it may even be a wireless adapter driver issue, since I am using ndiswrapper with a windows driver...

---

### Post by mxyzptlk on 2005-10-31
that's happening because in every unsecured network, if you want to protect it you must enable the MAC address control.

It means that you will be able to connect to that net, but you wont receive any information back at all, unless you set the MAC address of your device to that specific network.

the diference between WEP and the other one is that in WEP you need a Key and thats it, but in unsecured ones the best eay to protect it is usinf MAC address control.

---

### Post by OneSeventeen on 2005-11-02
Well, the network I'm talking about doesn't have any protection at all, it just offers itself to be used for whatever reason with no encryption.  (which is why I won't be typing passwords/checking bank statements on it.)

If I boot into windows, it connects just fine to the unsecured network, it is only in Ubuntu that I cannot connect to the unsecured network.

(of course Ubuntu has this cool feature called "shutting down" whereas the time I booted into windows for networking purposes, it decided shutting down meant to pretend to shut down, but then turn back on and freeze on the "windows is shutting down" screen as soon as I put the laptop in my backpack, successfully raising the temperature of the laptop case to a nice and toasty 98 degrees Ferenheit....)

Anyway, all rantings aside, could this just be a bad driver?  Has anyone here used Ubuntu to connect to an unsecured wireless network?  (without mac filtering)

---

### Post by mxyzptlk on 2005-11-02
actually im connected to a usecured network via wireless

my box is like this

system>administration>network

connections wlan0 active>properties

<youressid> no encryption (hexadecimal) DHCP

connections eth0 active>properties

static ip, subnet mask (usually 255.255.255.x) and gateway same as DHCP

and its working perfectly


hope it helps

---

### Post by tmcastberg on 2005-12-20
[QUOTE=mxyzptlk]
my box is like this
system>administration>network
connections wlan0 active>properties
<youressid> no encryption (hexadecimal) DHCP
[/QUOTE]

I've got the same problem, wep at home - unsecured at uni.

The problem that I've located is that there is no "no encryption" choice in the network dialog, so when a key has been set for a wep network, it remains in the /etc/network/interfaces file for any unsecured network. Removing the line "wireless_key <key>"  from the interfaces file brought the network up fine.

This seems to be a bug in the network dialog. I'm not sure if the "no encryption" choice has fallen out at some point or if gnome has simplified it away...

Cheers,
Tor Magnus

---

### Post by Lambert on 2005-12-20
GUI seems to have bugs in it as others have posted about their small annoyances.

network-manager is supposed to make it into dapper as an official package so you can look there and try it out now. Alot of people have said great things about network manager.

If you want to stay away from that and don't mind a command line to bring up your interface you can do this.

set up two interfaces in your /etc/network/interfaces file (you can do more then 2 if needed)

iface open inet dhcp

iface wep inet dhcp
xxxx
xxxx

add what ever you need below the iface lines. You can use what ever names you want in place of open or wep.

Then to bring up the device and connect you would do this.

sudo ifup wlan0=open
or
sudo ifup wlan0=wep

(replacing wlan0 with the name of your devices logical name; eth0...ath0...etc...)

---

### Post by gangalee on 2005-12-21
[QUOTE=mxyzptlk]that's happening because in every unsecured network, if you want to protect it you must enable the MAC address control.

It means that you will be able to connect to that net, but you wont receive any information back at all, unless you set the MAC address of your device to that specific network.

the diference between WEP and the other one is that in WEP you need a Key and thats it, but in unsecured ones the best eay to protect it is usinf MAC address control.[/QUOTE]

How do you setup MAC control on a dhcp server?

Thanks,

---

### Post by OneSeventeen on 2006-01-13
Okay, here's my current status:
[quote=interfaces]
auto lo
iface lo inet loopback

mapping hotplug
    script grep
    map eth0

iface wlan0 inet dhcp
wireless-essid unm

auto wlan0
[/quote]

If I go to the connection properties for wlan0 I see that I have received 25 packets (1.4Kb) and sent 0 packets (0.0b)

If I click on configure and then view the properties for the wireless interface, I see my essid "unm" listed there, so the wireless card is receiving data just fine.

Then when I "/etc/init.d/networking restart" it restarts the network (usually taking at least 2 full minutes, if not longer) and says it works fine (i.e. no "[fail]" message) yet I still cannot ping google or even ping the computer sitting next to it.

Any more ideas?  (and no, there is no mac filtering.  There used to be, and I added this laptop to the list when there was, so even if they turned it back on, I should be good)

---

### Post by OneSeventeen on 2006-01-13
**Edit:**
In an effort to be more like Windows, Ubuntu required me to restart with the new interfaces file.

Actually, it was probably more my lack of knowing what to do.  How do I force ubuntu to ro-read the /etc/networking/interfaces file?  Because using the default gui doesn't seem to do it.  (I'll check out this network-manager package and see what I think.)

---

### Post by OneSeventeen on 2006-02-01
I installed Network-manager, but I'm not sure what the difference is, other than now, when I am on the network just fine, I reboot, it reattaches as it should, even sets the time against ubuntu's servers, then by the time it gets to gnome, the internet connection is no longer there.

I just have to configure the wireless network device, and choose the drop-down menu to choose what network I'm on.  The crazy part: It already knows what network, and has it as the default choice in the drop-down, but I have to select it again, effectively changing nothing at all, but sort of jabbing it in the side so it gets back to work.

I still have to restart to switch between secured and unsecured networks, and still haven't seen network-manager... is there a command I use or is it one of those "behind the scenes" apps?

---

### Post by dehuszar on 2006-02-28
I'm having this trouble too.  Anyone solve this little bug yet?

---

### Post by oyvindh on 2006-03-01
It usually works for me to do:

iwconfig eth1 key off

---

### Post by dehuszar on 2006-03-01
Am I to presume that eth1 is your wireless card?

---

### Post by frogotronic on 2006-05-24
[QUOTE=OneSeventeen]I can't seem to connect to wireless networks that don't use WEP encryption.

I have successfully connected to 3 or 4 different WEP encrypted networks first try, but have yet to connect to unsecured networks.

Is there a trick to this?  Do I need to change something somewhere other than the network configuration window?  

I usually get there by double-clicking the network icon, then clicking "configure" and then click on "properties" and choose the network from the drop-down menu... which it always finds the proper network ID easily, then I remove the WEP key from my previous network, click okay, and it takes a good 2 minutes before the window closes, and it looks like it's connected (sending and receiving small packets of info every minute or so), but won't resolve domain names or anything, and won't show me the network I'm on.

This happens on every unsecured network I've tried so far.[/QUOTE]

I had the same problem.  I have solved the problem.  I downloaded and installed the latest GTKWiFi Release (under the UBUNTU FORUMS main page, 3rd Party projects).  Before installing the GTKWiFi, I UNINSTALLED network manager (and re-booted to make sure it was completely gone) as it broke my wireless connection.  BUT this GTKWiFi did the trick.  Very easy HOWTO on the links.  I can now connect to ANY wireless nework, secure (if I have the password) or unsecured.  And, this GTKWiFi lets you switch on the fly via the panel applet.  Very cool piece of software.

Cheers,
CH

---

### Post by bmasephol on 2006-05-24
I've got the same problem... I have 3 wireless AP at work, I can connect to the one that has WEP but I can't connect to the other 2 that are open and don't require WEP.

By using the iwconfig I can associate with the AP and get the MAC from it, but when I try to get dhcp going with dhclient I get no response.

I'm working on getting gnome installed (installed just base install to start with) so I can try GTKWIFI but it might be a lil while... I got an older laptop.  My Wireless nic is supported (ActionTec 802CAT1).

I should say that I'm using 6.06 Flight 7

---

### Post by frogotronic on 2006-05-24
[QUOTE=bmasephol]I've got the same problem... I have 3 wireless AP at work, I can connect to the one that has WEP but I can't connect to the other 2 that are open and don't require WEP.

By using the iwconfig I can associate with the AP and get the MAC from it, but when I try to get dhcp going with dhclient I get no response.

I'm working on getting gnome installed (installed just base install to start with) so I can try GTKWIFI but it might be a lil while... I got an older laptop.  My Wireless nic is supported (ActionTec 802CAT1).

I should say that I'm using 6.06 Flight 7[/QUOTE]

Sounds good.  BTY, I'm using a five (maybe six) year old Dell Inspiron 8100 using a removable Microsoft MN-720 wireless card.  The card is actually was made by TexasInstruments for Microsoft, or, rather is using a TI chipset.  I was skeptical, but the GTKWiFi makes UBUNTU run great with most (all that I've tried so far) public coffee house type wireless nodes; as well as my secure connection at work and at home.  I do have to "reconnect" after the whole platform has booted (for some yet mysterious reason).  In any case, it worked for me.

-CH

---

### Post by frogotronic on 2006-05-24
[QUOTE=cement_head]Sounds good.  BTY, I'm using a five (maybe six) year old Dell Inspiron 8100 using a removable Microsoft MN-720 wireless card.  The card is actually was made by TexasInstruments for Microsoft, or, rather is using a TI chipset.  I was skeptical, but the GTKWiFi makes UBUNTU run great with most (all that I've tried so far) public coffee house type wireless nodes; as well as my secure connection at work and at home.  I do have to "reconnect" after the whole platform has booted (for some yet mysterious reason).  In any case, it worked for me.

-CH[/QUOTE]


test

---

### Post by bmasephol on 2006-05-25
Finally got gnome up and running, installed GTKWiFi 1.09 but it don't play nice.  I believe it is because I'm using Dapper.

I'm going to play around with gnome and see if I can't get it to connect to non WEP AP's.

---

