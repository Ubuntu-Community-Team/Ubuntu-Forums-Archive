---
title: "Accidentally disabled wireless"
date: 2014-06-12
forum: Networking &amp; Wireless
---

### Post by SageOfSmeg on 2014-06-12
Panic!
Thanks to the tiny touchpad on my laptop (and my clumsy fingers) I accidentally unchecked the tick against "Enable Wireless Networking".
Now I cannot use the wireless.
The "Enable Wireless Networking" option has also vanished, so I can't simply re-tick the option.

Uner Network Connections the wireless entry is still there and all of the settings remain unchanged, but no wireless is available.

The entry of "wlan0" that usually appears under iwconfig or ifconfig is no longer present.

Can anybody please suggest a fix.
Thanks.

---
lubuntu 12.04

---

### Post by A Bunny on 2014-06-12
[FONT=arial][SIZE=2]Okay try this go to
[COLOR=#333333]Menu->Preferences->Default Applications for LXSession->Autostart.
then add the following
[/COLOR]nm-applet
Then reboot your computer.

If that doesn't work try adding
nm-applet --sm-disable
and then reboot your computer.

Hope this helps
A_Bunny[/SIZE][/FONT]

---

### Post by SageOfSmeg on 2014-06-12
> **A Bunny said:**
> [FONT=arial][SIZE=2]
[COLOR=#333333]Menu->Preferences->Default Applications for LXSession->Autostart.
[/COLOR][/SIZE][/FONT]

There isn't any entry matching that option. Do you know of the equivalent in terminal?

---

### Post by A Bunny on 2014-06-12
Try this link [http://askubuntu.com/questions/81383/how-can-i-add-new-autostart-programs-in-lubuntu](http://askubuntu.com/questions/81383/how-can-i-add-new-autostart-programs-in-lubuntu)

Hope this helps.
A_Bunny

---

### Post by SageOfSmeg on 2014-06-12
No, that didn't work either.
I will dig a little deeper and keep on trying.

---

### Post by steeldriver on 2014-06-12
It sounds like you may have removed the System Tray from the panel - if that's the case, you should be able to

[LIST]
[*]R. click anywhere on the toolbar 
[*]Select 'Add/Remove Panel Items' 
[*]Go to the 'Panel Applets' tab and if necessary 'Add' and then select 'System Tray' from the list of available plugins 
[/LIST]

It will probably add back at the RHS of the toolbar by default - you can use the Up/Down buttons to reposition it to the left of the clock if you want

---

### Post by SageOfSmeg on 2014-06-13
I don't think this is the problem. The panel applet for Network Connections is present, it just doesn't have the option to re-enable wireless. If I try and add a new wireless connection entry in the NC it comes up with a blank MAC ID when before there was always a wlan0 entry, so I suspect that the problem lies deeper behind the scenes.

---

### Post by steeldriver on 2014-06-13
Ah OK sorry I misread your post. If that is the case, we need to look at whether the wireless device is blocked, or whether the driver has gone AWOL:

```

sudo rfkill list

sudo lshw -C network -sanitize

```

---

### Post by SageOfSmeg on 2014-06-13
```
gjd@gjdpc3:~$ sudo rfkill list
0: eeepc-wlan: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

gjd@gjdpc3:~$ sudo lshw -C network -sanitize
  *-network               
       description: Ethernet interface
       product: L2 Fast Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: a0
       serial: [REMOVED]
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl2 driverversion=2.2.3 duplex=full firmware=L2 ip=[REMOVED] latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:43 memory:fbfc0000-fbffffff memory:fbfa0000-fbfbffff
gjd@gjdpc3:~$
```

Plus, now it appears that my wired network is failing. When I use Firefox I get this:
> Server not found

Firefox can't find the server at [www.metoffice.gov.uk](www.metoffice.gov.uk).

    Check the address for typing errors such as ww.example.com instead of [www.example.com](www.example.com)
    If you are unable to load any pages, check your computer's network connection.
    If your computer or network is protected by a firewall or proxy, make sure that Firefox is permitted to access the Web.

Although skype seems to be working, which is strange if Firefox isn't.

---

### Post by steeldriver on 2014-06-13
Let's focus on the wireless for now - does

```

sudo rfkill unblock 0

```

help? Check that it took effect by running 'rfkill list' a second time.

---

### Post by SageOfSmeg on 2014-06-13
```
gjd@gjdpc3:~$ sudo rfkill unblock 0
gjd@gjdpc3:~$ sudo rfkill list
0: eeepc-wlan: Wireless LAN
        Soft blocked: no
        Hard blocked: no
1: phy0: Wireless LAN
        Soft blocked: yes
        Hard blocked: no
gjd@gjdpc3:~$
```


Everything is working now, thanks steeldriver, even Firefox. 
I will try and be less clumsy in future.

---

### Post by steeldriver on 2014-06-13
OK that's all good - sorry we took you around the houses to get there!

---

