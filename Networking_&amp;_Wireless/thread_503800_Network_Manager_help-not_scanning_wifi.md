---
title: "Network Manager help-not scanning wifi"
date: 2007-07-18
forum: Networking &amp; Wireless
---

### Post by ajmctaggart on 2007-07-18
Hey everyone,

Could someone possibly help me with Network Manager?  I am running Feisty on a PowerPC, and this is my /etc/network/interfaces file:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.88
netmask 255.255.255.128
gateway 192.168.1.1

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```

And this is my /etc/iftab

```
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.


eth0 mac 00:30:65:79:1B:16 arp 1
wlan mac 00:16:01:18:63:75 arp 1
#eth1 mac 00:0a:95:9b:b0:72 arp 1


```

So why is it when I click on my nm-applet it gives me a...

[ATTACH]38539[/ATTACH]

How can I use network manager to choose my wireless network?  Is the Network Manager in PPC distros of Feisty different than x86, please advise, 


Thanks,
ajm

---

### Post by ajmctaggart on 2007-07-18
bumped

I know someone has got to be able to help me with this, anyone?

Network manager applet doesn't show me available wireless networks but iwlist scanning works like a charm

What would make network manager just pull up a window of the current connection?  Where is the dialog for wifi no networks detected with a manual configuration for a static ip?  That's how it has always looked for me, unless of course PowerPC is different.

---

### Post by kevdog on 2007-07-18
There is an error in your iftab file:

> wlan mac 00:16:01:18:63:75 arp 1
Should be:
```
**wlan0** mac 00:16:01:18:63:75 arp 1
```

Network Manager _does not_ use the /etc/network/interfaces file to configure devices.  I would suggest that you actually put a # sign in front of the wlan0 lines, then

```
sudo /etc/init.d/dbus restart
```

Then try again to connect with network manager.
A reboot is always good to try if something isnt working also.

---

### Post by ajmctaggart on 2007-07-18
I am installing some updates, so I'll have to check that /etc/iftab in a minute, thanks!

Quick question, If I am using a static ip cause of my office, I DONT need to comment that out, just the wlan0, since that's what I want Network Manager running?

Have you or anyone seen a Network Manager applet open a window instead of a drop-down...

Thanks, Ill correct everything asap

ajm

---

### Post by kevdog on 2007-07-18
You can keep your wired static address in the interfaces file because you are not using network manager to make this connection.  

Hmmm, I dont know of any other interface to network manager than an applet or popup.  There are programs that are substitutes for network manager -- ie wicd, wifi radar, etc.  I know wicd works through a popup.  Not sure about the other one.  

If you are using a fixed wireless router (like the only one at your house), you could put all the wireless settings in the interfaces file.

If you are not using the ath0 interface name (for example an atheros based chipset), I would probably also delete these two lines from the interface file.

Also on the jpeg you posted, dont you want to use network manager with wlan0 rather than eth0??

---

### Post by ajmctaggart on 2007-07-18
That's just it- before this PPC laptop, I had Feisty on many x86 boxes, w/ static ip's and wifi...well when clicking on the nm-applet, it would say what networks were available (via wireless) and then it would say "Manual Configuration"  Why doesn't this happen anymore?

I want eth0 and wlan showing in the applet...wlan0 should contain the wireless (at the top) then my static ethernet should be described as a Manual Configuration

This just isn't happening on the laptop...I don't know why 

When I click on the nm-applet, what I get is that jpeg I posted...

Help Kevdog, help...

Thanks
ajm

---

### Post by kevdog on 2007-07-18
Are you using ubuntu feisty with the default theme??  My network manager applet definitely doesnt look like what you posted.  Ive never seen the popup box you pictured.  I have K,U,Xbuntu installed on my machine, and the popup looks more like an Xbuntu or Xwindow popup.  Its kind of strange.

---

### Post by ajmctaggart on 2007-07-18
Not the standard theme, no...but I've used these themes so many times now..hardly see why that's it

---

### Post by Gen2ly on 2007-07-18
That almost looks like wifi radar, a completely diff. app.

---

