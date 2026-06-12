---
title: "NetworkManager is not running..."
date: 2009-09-14
forum: New to Ubuntu
---

### Post by rippedpaperbox on 2009-09-14
I shut my machine down for a minute or two and when I resumed, my NetworkManager said it stopped running. When I hover over the icon, it says "network disabled" though I never disabled it myself. I ran nm-applet and got this:
 
** (nm-applet:3404): WARNING **:<WARN> applet)_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.
Return: 3
 
I tried sudo /etc/init.d/NetworkManager start and nothing happened. I`ve looked at other threads on this subject and that didn't help either. Am I missing something?
Thanks.

---

### Post by earthpigg on 2009-09-14
is another user logged in?
```

users
```

---

### Post by rippedpaperbox on 2009-09-14
No, I only have one account logged on. The other one exists but isn't used for anything.

---

### Post by t0p on 2009-09-14
Have you tried *ulp* logging out and back in again?  Or even *double ulp* restarting?  As you're being told that the NetworkManagerUserSettings service is already taken, maybe logging out or restarting will free up the NetworkManagerUserSettings service.

You tried running nm-applet.  You've got the Network Manager on your panel though, right?  Have you tried right-clicking on it and ticking Enable Networking? Sometimes all that's needed is the simplest of things...

---

### Post by rippedpaperbox on 2009-09-14
I have restarted it, several times now. Shut it down for a few hours. The "Enable Networking" is ticked and the only account logged into is my current one. :(

---

### Post by JBAlaska on 2009-09-14
Try accessing it through= System, Administration, Network. If you have it set to manual config it may not act right from the panel.

---

### Post by rippedpaperbox on 2009-09-14
Network Tools? If so, which tab? Devices, Ping, Netstat, Traceroute, Port Scan, Lookup, Finger, Whois. I'm using ubuntu 9.04

---

### Post by JBAlaska on 2009-09-14
Not network tools, you should have an entry called Network that will access Network Manager

---

### Post by rippedpaperbox on 2009-09-14
I looked in Administration and Preferences, and there's Network Proxy, Network Connection and Network Tools. Nothing with just "Network."

---

### Post by rippedpaperbox on 2009-09-14
bump!

---

### Post by Rebootkid on 2009-09-14
As I said over in LJ-Land...

Lets start with some basics.

the output of the following:

ifconfig -a
iwconfig (if it's a wireless link)

dhclient eth0 (or eth1, wan0, etc.. again, depending on the interface in question.)

If you're at a loss as to what I'm talking about, then just start by opening up a terminal window (applications, accessories, and click on terminal) then type
ifconfig -a and hit enter. Give us the output of that, and we'll go from there.

Oh, and also, a general description of the computer in question and how it is supposed to connect to the network will be helpful.

---

### Post by Chris Grk-O-Matic on 2009-09-15
I have the same error message when I run nm-applet:

** (nm-applet:3726): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


My network manager taskbar applet is also missing and I tried sudo apt-get install network-manager-pptp (as per someone's advice) and the applet is still not there after a reboot.


I did ifconfig -a and got this:

chris@chris-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0a:95:88:7f:d8  
          inet addr:192.168.1.38  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:95ff:fe88:7fd8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1881 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1585 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1149702 (1.1 MB)  TX bytes:254143 (254.1 KB)
          Interrupt:41 Base address:0xe800 

eth1      Link encap:Ethernet  HWaddr 00:30:65:28:2f:55  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:57 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:206 errors:0 dropped:0 overruns:0 frame:0
          TX packets:206 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14484 (14.4 KB)  TX bytes:14484 (14.4 KB)

pan0      Link encap:Ethernet  HWaddr 06:26:61:65:c6:27  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


Do you guys know how I can get the applet back as I heavily relied upon it?


[B]1Ghz Titanium Powerbook
Ubuntu 9.04[/B]


Thanks,
Chris

---

### Post by ShetlandJohn on 2009-09-16
I had this problem last night.  Fixed it this morning!

Open a Terminal.
type:

```
sudo stop network-manager
```
(then enter your password)

```
sudo start network-manager
```

And that brought mine back up and running.

The fact that it's died on reboot is nothing to do with this, I'm sure!

---

### Post by Chris Grk-O-Matic on 2009-09-16
I'll keep this in mind if it happens to me again;

but,

Who would of thought... the applet that contains Network Manager is called *Notification Area*. 

I never would have realized this until I dug it up somewhere. I was looking at all sorts of posts with many different possible solutions on this issue. 

This should be considered as a future fix in an upgrade, in my opinion. Maybe make an applet called, oh I don't know, *Network Manager*. [IMG]http://ubuntuforums.org/images/icons/icon12.gif[/IMG]



My sincere thanks to the Ubuntu Community for Ubuntu and all of their support.

Chris

---

### Post by earthpigg on 2009-09-16
> **Chris Grk-O-Matic said:**
> 
Who would of thought... the applet that contains Network Manager is called *Notification Area*. 

...

This should be considered as a future fix in an upgrade, in my opinion. Maybe make an applet called, oh I don't know, *Network Manager*. 

the notification area is where ***all*** notification-type applets hang out. the power monitor also hangs out there. pidgin can be configured to display an icon in the notification area. notification area is also called 'system tray' and a couple other things.

***nm-applet*** is the name of the applet that hangs out in the notification area. if it doesn't have a notification area to hang out in, it wont display.

you may have been confused because, on your particular setup, the only thing that is ever shown in the notification area is nm-applet -- the network manager applet.

---

