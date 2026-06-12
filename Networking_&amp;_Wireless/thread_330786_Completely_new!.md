---
title: "Completely new!"
date: 2007-01-03
forum: Networking &amp; Wireless
---

### Post by jemblack on 2007-01-03
Hi,

I'm completely new to Ubuntu (and Linux in general) I've installed it all but I can't get my network working. I've tried both hard wired and wireless options... as i'm guessing the hard wired option is going to be the quick fix option, i just need some help with it.
I've entered all the correct Ip address and gateway addresses in "networking" but not getting an internet connection

I bet it's something really simple (i hope)

Is it?!

---

### Post by kebes on 2007-01-03
You're right: it's easier to get the hard-wired network connection working. Focus on that and once its working you can get wireless working too.

Go to a console/terminal and type:
ifconfig

You should see a bunch of text that describes your network settings. Check that your settings "took." That is, check that the address, gateway and so on reported are what you entered. If you are using a router with DHCP enabled, then you should have an IP address like "inet addr:192.168.0.100" or whatever. For a ethernet jack, this should be in the "eth0" section, probably. You can post the output of this command to the forum, which might help.

Any other description of your setup would help. (New or old computer? Laptop? Specs? Are you using a router, cable modem, etc.? Have you ever had networking working on this computer before? Which version of Ubuntu did you install?)

---

### Post by jemblack on 2007-01-03
the laptop is bout 2-3 years old. i had windows netowrki setup fine sharing both files and internet connection. i'm usin a router with dhcp.
I installed ubuntu 6.06LTS

I've just looked at the ifconfig in console, it's given;

Link encap:Ethernet   HWaddr 00:03:25:2D:CB:81
inet addr:127.0.0.1    Bcast:127.0.0.255     Mask: 255.255.255.0

but wen i go in2 networking, it shows the gateway as 192.168.0.1, mask as 255.255.255.0

wot hav i dun rong?

I can't copy the text from terminal as it's not on this computer

---

### Post by kebes on 2007-01-03
Alright... so it looks like after entering your settings they are not being saved. To be clear, after entering your settings, closing and re-opening the network settings, the correct settings are still there? (But not updated to the system/ifconfig level.) Strange.

Some suggestions:

1. This is going to sound crazy, but try clicking "cancel" instead of "ok" after inputing your settings. First input them and click OK. Then open the network config again, enter the settings again, and instead click "cancel". See if the network now works. Sounds weird but this did happen to a friend of mine using 6.06. However maybe it won't work for you...

2. Check the file "/etc/network/interfaces". It should look like (from what you've described):
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

```

3. Check the file "/etc/resolv.conf". Does it have the address of your router? (You can't change this manually but it may be a clue.) Similarly, run "netstat -nr" for some more info/clues.

4. If 2 and 3 look "right" then maybe just reset the network, using a reboot or explicitly with:
sudo /etc/init.d/networking restart

5. Does your ethernet port (on the laptop) have a "light" that usually lights up when connected? If so, is it lit up with the cable in? Do you see any activity on the router when the laptop is plugged in?

6. This is going to sound dumb: but are you sure the ehternet cable you're using works? Have you used it on that particular router port successfully before? There are "straight" and "cross-over" ethernet cables... are you using the right one?

7. Try setting the network manually (on the commandline) instead of using the GUI tool. To do this, use "ifconfig" and "route". So for example, something like:
ifconfig eth0 inet up netmask 255.255.255.0 broadcast 192.168.0.255
route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.168.0.1 dev eth0

You may need to read about the commands to get it to work properly. See also:
[http://www.debian.org/doc/manuals/reference/ch-gateway.en.html](http://www.debian.org/doc/manuals/reference/ch-gateway.en.html)


8. Check these network troubleshooting guides:
[http://ubuntuforums.org/showthread.php?t=25557](http://ubuntuforums.org/showthread.php?t=25557)
[http://www.ubuntuforums.org/showthread.php?t=86389](http://www.ubuntuforums.org/showthread.php?t=86389)


Sorry that I can't give you a sure-fire way to fix it... but it could be any one of a thousand things going wrong. Post again if you get more info about the problem (e.g. result of the above checks).

---

### Post by jemblack on 2007-01-04
rite, i dunno how but i've got my wired network up and running now

.... now on to the wireless

cheers 4 your help

---

