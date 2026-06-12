---
title: "Network profile manager for laptops?"
date: 2005-08-27
forum: Networking &amp; Wireless
---

### Post by wabble on 2005-08-27
Is there any good network profile manager for laptops?

Is there any way to turn of all eth adapters to short down boot time and not turning them on before selecting the network profile you want to use from x with the click of one buttun? (using a laptop you have more places you want to be than one, right?)

I don't want to compare, but i have an ibm laptop and used to have windows on it. The ibm access connections is really a killer app and i was wondering if there is anything like it for ubuntu?

An app that configures firewall on/off, what network card to use (with all network settings), and disables other networking interfaces not used (and maybe as a bonus also manages bluetooth devices?

Well, just wondering. I'm no expert at ubuntu, but im learning :)

---

### Post by s_p_a_r_k_y on 2005-08-27
[http://people.redhat.com/dcbw/NetworkManager/](http://people.redhat.com/dcbw/NetworkManager/) is supposed to be kick ass, but there is no official ubuntu build of it yet. I tried my luck at compiling it but ended up needing do get libraries and dev packages and blah. So I gave up. Hopefully soon it will be in ubuntu, maybe breezy. For now I just have my network interfaces start in the background during boot so it doesn't slow up the entire systems bootup if it doesn't find an internet connection.

change 
 ifup -a >/dev/null 2>&1
to
  ifup -a & >/dev/null 2>&1

in /etc/init.d/networking and the system will continue booting even if no internet conneciton is found.

---

### Post by ACK!! on 2005-08-27
[QUOTE=wabble]Is there any good network profile manager for laptops?

....

Well, just wondering. I'm no expert at ubuntu, but im learning :)[/QUOTE]


This is interesting the network tool for gnome-system-tools which is included in Ubuntu in System -> Administration -> Networking supports profiles.

For example on my laptop I have a work profile that includes the setup for the eth0 interface and a Home setup where that same eth0 is disabled and my wireless connection is the only device enabled in that profile.  In that home profile, eth0 is NOT configured.  

The only issue of course being to remember to switch between the two as I leave for home or start to go to work.

Try using profiles in the network admin tool.  It is a bit too manual and the network-manager for gnome will be better but still ... it works.

---

### Post by benplaut on 2005-08-27
google for GTKwifi  ;-) 

are you using an Intel chipset or Atheros?

---

### Post by ACK!! on 2005-08-27
[QUOTE=benplaut]google for GTKwifi  ;-) 

are you using an Intel chipset or Atheros?[/QUOTE]

madwifi and I have Gtkwifi installed.  But I never use GTKwifi because the network-admin in Ubuntu is fine and the fact I have only two profiles -- Work and Home.

---

### Post by benplaut on 2005-08-27
[QUOTE=ACK!!]madwifi and I have Gtkwifi installed.  But I never use GTKwifi because the network-admin in Ubuntu is fine and the fact I have only two profiles -- Work and Home.[/QUOTE]

yeah... madwifi is kinda sucky right now... can't be connected and scan at the same time. borks everything but network-admin and wifi-radar (breezy)  ;-)

---

### Post by wabble on 2005-09-14
[QUOTE=s_p_a_r_k_y][http://people.redhat.com/dcbw/NetworkManager/](http://people.redhat.com/dcbw/NetworkManager/) is supposed to be kick ass, but there is no official ubuntu build of it yet. I tried my luck at compiling it but ended up needing do get libraries and dev packages and blah. So I gave up. Hopefully soon it will be in ubuntu, maybe breezy. For now I just have my network interfaces start in the background during boot so it doesn't slow up the entire systems bootup if it doesn't find an internet connection.

change 
 ifup -a >/dev/null 2>&1
to
  ifup -a & >/dev/null 2>&1

in /etc/init.d/networking and the system will continue booting even if no internet conneciton is found.[/QUOTE]

Sorry for me answering so slow.

So i change this under Configuring, Deconfiguring, Reconfiguring or all?

---

### Post by NRios on 2005-09-19
> This is interesting the network tool for gnome-system-tools
> which is included in Ubuntu in System -> Administration -> Networking
> supports profiles.
 
Sure, the button is there, but it does not work.

My centrino laptop was running fine out of the box and connecting to my Wifi access point. Then I stayed at a friend's over the weekent, and wifi turnd to nightmare. The network configuration applet let me create a new place, but then it wouldn't remember the settings.

Everytime I restarted, I got a weird mix of ESSID, WEP keys and key types (ASCII or HEX), and I had to choose every option again and reinput the WEP key. The link would then work but it seemed that it did only until I closed the netconf applet; then, the link was lost and I was back to square one.

I'm back home now, and wifi is working after I chose the old parameters.

I think the network config application is mostly useless for a moving user at this moment, unless he knows well how everything works and has the patience of a saint. The thought of imposing this onto my father makes me cringe.

Is there a chance this will be fixed for Breezy? It is *really* sorry now.

---

### Post by kingsidy on 2005-10-22
i use wifi radar. Once you setup a profile yu are all set. I use it at work and at home.

---

### Post by landotter on 2005-10-22
install network-manager via Synaptic, then remove any network monitors from your panel, alt+f2, and start nm-applet. You'll want to add nm-applet to your sessions to autostart. You can configure it to not search and connect by default, works fabulously.

[IMG]http://static.flickr.com/27/54470842_93048e050c_o.jpg[/IMG]

---

### Post by wabble on 2005-10-22
This looks like a great tool. I installed it now and cant wait to get around and configure it :D

Thanks!

-edit-

Does it support static ip's?

---

### Post by landotter on 2005-10-22
[quote=wabble]This looks like a great tool. I installed it now and cant wait to get around and configure it :D

Thanks!

-edit-

Does it support static ip's?[/quote]

Vet inte. :S I just let it all happen automatically. :p

When I installed it, it picked up some settings from my standard Gnome network settings: I didn't have to enter my WEP key. So you might be able to do it like that-enter the settings in the regular Gnome Network settings. 

For unsecured networks, just right click and select your network, if it requires WEP, you get a dialog to enter a key. It remembers the keys for future use.

I'm a real nob when it comes to networking, only been wireless for a couple weeks, so no more info from me. :D

---

### Post by wabble on 2005-10-23
This last one here works ok :)

---

### Post by fwendt on 2007-03-07
The Network Manager is a great tool, "it just works"<tm> but - it also disables my bluetooth interfaces which is terribly annoying when I need that to get connected to the internet. I use my cellphone (SonyEricsson M600i) and GPRS and I got it all working under Dapper Drake. However I didn't have the opportunity to use Network Manager on that machine/install, perhaps I would've had the same problem if I did?

Any help on making Network Manager leave my bluetooth interfaces up would be highly appreciated.

Oh, and what it does is:
```

NetworkManager: <debug info>^I[1173258857.403359] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_a5c_200a_2035B0000001_if0'). 
NetworkManager: <debug info>^I[1173258857.405169] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_a5c_200a_2035B0000001_if1'). 
NetworkManager: <debug info>^I[1173258857.405839] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_a5c_200a_2035B0000001_if2'). 
NetworkManager: <debug info>^I[1173258857.408927] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_a5c_200a_2035B0000001_usbraw'). 
NetworkManager: <debug info>^I[1173258857.409997] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_a5c_200a_2035B0000001'). 
```

---

