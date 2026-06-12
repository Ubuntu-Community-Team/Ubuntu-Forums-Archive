---
title: "wireless won't work and icon doesn't show"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by WolfLust on 2008-11-04
Hello all,

I have recently dist-upgraded from 8.04 to 8.10 and now my wireless doesn't work, and my network icon (from which I could choose wireless and wires configuration) doesn't show anymore. I have also noticed that it's no longer in System -> Preferences or Administration.

I have a Dell Inspiron 1300 Laptop, and my wireless driver is:

```
lspci -v | less

02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
        Subsystem: Intel Corporation Device 2722
        Flags: bus master, medium devsel, latency 64, IRQ 17
        Memory at dfbfd000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [dc] Power Management version 2
        Kernel driver in use: ipw2200
        Kernel modules: ipw2200
```


Also, please note that /etc/network/interfaces contains no eth1:

```
cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth0
```

I have added :
iface eth1 inet dhcp
auto eth1

to /etc/network/interfaces but that didn't solve anything.

Please advise and thank you in advance.

---

### Post by WolfLust on 2008-11-04
Just an update:

In System -> Preferences -> Network Configuration I have added my wireless router's information (SSID, MAC...) and it connected. The networking icon appeared again.

Is that a common issue?

---

### Post by eiffel on 2008-11-04
I was having this problem after the recent upgrade and I found somewhere (well, here: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/253948](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/253948)) that the solution for getting NetworkManagr back in the system tray was to delete all the lines in /etc/network/interfaces apart from:

auto lo
iface lo inet loopback

That worked for getting NetworkManager back but now my laptop freezes up when I boot up with my network card inserted or shortly after inserting my network card.  Maybe it won't do this for you. So I'm looking for a better solution so that I can get my laptop back online.

So I'd recommend making a copy of /etc/network/interfaces first, if you want to try that.

---

### Post by WolfLust on 2008-11-06
eiffel thank you for replying.

What you proposed didn't solve the problem, I still cannot see the networking icon and that used to ease all my wireless connectivity problems.

Can we get that icon back somehow?

Thanks.

---

### Post by WolfLust on 2008-11-06
Oh and another thing to add, nm-applet can be added to my panel but it doesn't show eth1, only eth0 and loopback although /etc/network/interfaces contains eth1

Thanks :)

---

### Post by eiffel on 2008-11-07
I got fed up with Network-Manager in the end. Ironic since it worked fine in 8.04 and 8.10 was supposed to be lot better at networks.  Hmmmm.

I downloaded Wicd instead from:

[http://sourceforge.net/project/showfiles.php?group_id=194573](http://sourceforge.net/project/showfiles.php?group_id=194573)

Had to uninstall NM first but Wicd works just great.

---

### Post by WolfLust on 2008-11-10
eiffel,

Thank you so much for Wicd it solved my problem!!!
Thanks a lot.

---

### Post by soh on 2008-11-10
I have the same problem.
Just upgraded to 8.10 and then the nm-applet icon has dissapeared, and when I start nm-applet from the command line I get:

** (nm-applet:21139): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:21139): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

Does anybody know what the problem is?

The profile I was using when I upgraded seems to work.
But as I cant get nm-applet to start I cant change.

Søren

---

### Post by WolfLust on 2008-11-10
Søren,

I couldn't get the old icon back, so I just removed the NM and installed wicd instead.
Works great now.

---

### Post by soh on 2008-11-10
Thank you, I might end up doing that too.
But I think that there should be a Ubuntu/NetworkManager solution :-)
(For a couple of hours at least)

Søren

---

### Post by ThiOz on 2008-11-17
Hi Guys,

I had the same problem and was about to fix it with the Wicd solution... I removed the network-manager using apt and when I was about to install Wicd the thought of re-installing the network-manager came to me ... why not I thought... 

After the install and the requested reboot ... The icon was back and I could select my wireless network as you would in 8.04 

I was actually dumbfounded it worked... but it did ;) 

hope this helps you guys out.

---

### Post by razorxpress on 2008-11-17
If the icon at top right is now gone which previously showed, you have to see what's in "/etc/network/interfaces" and make is as mine or what it was on fresh installation.

i.e. cat /etc/network/interfaces show give only these lines

auto lo
iface lo inet loopback

If you have tried some other methods of connecting to internet e.g pppoeconf, or pppoe-setup, then this file will be edited and won't show on top right corner. So just delete anything else and restart and it should work now.

---

