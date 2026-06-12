---
title: "Networking not working on boot"
date: 2005-10-20
forum: Networking &amp; Wireless
---

### Post by sisooktom on 2005-10-20
Ok, I'm having a weird problem with networking in Breezy.  I have an old Dell with a venerable 3com 3c59x NIC that sits behind a Linksys WRT54G router.  When I first boot the system, eth0 claims to be configured and UP, RUNNING, etc (according to ifconfig eth0), but there is no IP listed.  I can't get to any websites nor can I even ping my router.  It's as if DHCP isn't working but I know it's configured and the router works fine with my other computer.  If I use the network applet in the panel to bring eth0 down, back up, and select it as the default connection, it finally starts to work, but then it does the same thing next time I boot up.  Any ideas?

---

### Post by hajk on 2005-10-20
Is hotplug working? What does /etc/network/interfaces look like?
If hotplug doesn't work, you could try to add "auto eth0" to /etc/network/interfaces, on a line by itself, just preceding the "iface eth0.."
line.

---

### Post by sisooktom on 2005-10-20
[QUOTE=hajk]Is hotplug working? What does /etc/network/interfaces look like?
If hotplug doesn't work, you could try to add "auto eth0" to /etc/network/interfaces, on a line by itself, just preceding the "iface eth0.."
line.[/QUOTE]

I checked that file last night, and I believe that auto eth0 is in it already (I'm not at home right now).  My hardware is just so common, I find it hard to believe that the defaults don't work.  I never had an issue with Redhat/Fedora :???:

---

### Post by sisooktom on 2005-10-21
Ok, I double checked and auto eth0 is in my /etc/networking/interfaces file.  Also, I disabled IPv6 (why this is on by default baffles me).  But the box still doesn't seem to actually get an IP at startup.  Any ideas?

---

### Post by Tsume on 2005-10-21
I believe my issue is the same, or at least really similar.

I'm using a Broadcom adapter with ndiswrapper, and wpa_supplicant.  When I'm booting, it says tempory error resolving some website, then FAIL in red next to it.

When I boot, it shows usually something around 12 packets sent 3 recieved, and nothing internet-wise is working until I go in the network thing, press de-activate, and then press activate.  Then it works great!  Until I reboot anyway... then I have to do the same thing again.

auto wlan0 is in my /etc/network/interfaces file.

I tried moving it just above the iface wlan0 line but it didn't seem to change anything.

---

### Post by Eremit on 2005-11-01
I have the same problem on two different computers.
One is an update from hoary to breezy, the other is a fresh breezy installation.

After reboot the interfaces are up but they don't have IPs assigned, static IP or DHCP makes no difference.
After "/etc/init.d/networking restart" everythink works fine.

I can't believe nobody has a solution for that.

---

### Post by bonifacio on 2005-11-01
Same boat here.  Here is some info about my problem...

[http://ubuntuforums.org/showpost.php?p=458784&postcount=6](http://ubuntuforums.org/showpost.php?p=458784&postcount=6)

---

### Post by teaker1s on 2005-11-01
anyone know how to set the static ip and dns in konsole as the system-administration-networking in gnome is buggy as hell and randomly it looses settings after several boots and successful atempts at accessing the internet

---

### Post by Biased turkey on 2005-11-01
To set the static adress, use sudo ifconfig .... ( see the man page )
DNS edit /etc/resolv.conf

The interface showns up in the GUI network setting, but is not configured.
I think you have to click twice on it to configure it
P.S. I'm at work right now and of course my boss is so stupid that she prohibit me to use linux. But I have a "secret" drive with ubuntu on it so I'll fire it during lunch time.

---

### Post by andremarcel on 2005-11-01
My problem was the entries of pppoeconf in /etc/network/interfaces
I have deleted them out and everything is normal again.  But if you have not a router, this won't help you...

---

### Post by Eremit on 2005-11-02
I have a router but it still doesn't work.

---

### Post by Eremit on 2005-12-05
has anybody found a solution?

---

### Post by yyagol on 2005-12-24
Same here the problem is only with Breezy
with the Hoary ther was no prob with that.
after restart the eth0 is down and need to auto restart with
ifconfig eth0 up
all look fine with the configurations files and i see that many people
have the same problem.

---

### Post by yyagol on 2005-12-30
OK i found the problem
the problem for me was in the /etc/network/interfaces  file
i found out that 
[COLOR="Red"]auto eth0[/COLOR] came after 
[COLOR="Red"]iface eth0 inet dhcp[/COLOR]
after i moved it it work like magic i could not belive it was that simple
so i try to restart for 10 time to belive it. its working now.

---

### Post by Sod75 on 2005-12-30
I had the same issues setting the network via the gui. not working at boot, loosing settings...

when I checked the  /etc/network/interfaces the "auto ethx" was also not were it was supposed to be ( the line before the respective "iface ...")
the default gateway was just missing and "ifup eth" would puke because of a bad syntax (missing parameter) in the file, the culprit was an unused interface ( I added "static")

for those still struggling here is my working config file

```


# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth1

# The primary network interface
auto eth1
iface eth1 inet static
address 192.168.1.9
netmask 255.255.255.0
gateway 192.168.1.1

iface eth0 inet static


```

key learning is to ditch the GUI though, it causes nothing but troubles

---

### Post by imhoff on 2005-12-30
I don't know whether my problem is really related. 
But I noticed that my /etc/network/interfaces file became broken
after using System/Network Settings. I have an on board network card that
I don't use and which was not configured during installation.
It seems to me that the wizard does not set all necessary values
by default if you have multiple network devices but just 
edit one device. 
This resulted in a wrong line for that eth-device in my /etc/network/interfaces
and a too late auto eth0 line.
After disabling that wrong line manually and adding etho to auto
networking worked fine for me again, now with a static IP for my desktop.

If networking does not start after reboot but networking restart works. Did you 
check that networking is started on Boot in System/SystemServices for the 
default runlevel you see in /etc/inittab?

I actually don't remember whether I had to turn that on again.

you can see my working interfaces file as an example:
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo eth0
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
#iface eth0 inet dhcp
iface eth0 inet static
 address 192.168.1.23
 netmask 255.255.255.0
 gateway 192.168.1.1
#iface eth1 inet

---

