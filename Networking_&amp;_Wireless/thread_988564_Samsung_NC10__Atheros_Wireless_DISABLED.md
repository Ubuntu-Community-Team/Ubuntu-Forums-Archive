---
title: "Samsung NC10 / Atheros Wireless DISABLED"
date: 2008-11-20
forum: Networking &amp; Wireless
---

### Post by jesuspresley on 2008-11-20
EDIT | UPDATE: Solution below, this was actually a hardware problem.

Hmmmm... I had my wireless card up and running on my Samsung NC10 netbook, incl. all the Wifi networks visible in the notification area of my Gnome panel. I have installed Ubuntu 8.10.

Then, after trying to activate Gsynaptics for my touchpad and restarting the machine, I realized that the connection had gone and the wireless network is disabled.

I consulted the Wireless troubleshooting guide:
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

...and here are my results:

Check for Device Recognition:
```
sudo lshw
```

gives this output regarding wireless:

```
....
           *-network DISABLED
                description: Wireless interface
                product: AR242x 802.11abg Wireless PCI Express Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wmaster0
                version: 01
                serial: 00:21:63:89:25:ee
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
....
```

And actually now I am stuck - the driver is properly installed, everything worked fine. 
Everything else works fine, including cable ethernet:

```
root@ordenacito:~# ifconfig
eth0      Link encap:Ethernet  Hardware Adresse 00:13:77:ad:e3:f4  
          inet Adresse:192.168.1.100  Bcast:192.168.1.255  Maske:255.255.255.0
          inet6-Adresse: fe80::213:77ff:fead:e3f4/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:16053 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8893 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:10320405 (10.3 MB)  TX bytes:1359910 (1.3 MB)
          Interrupt:18 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:772 errors:0 dropped:0 overruns:0 frame:0
          TX packets:772 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:38600 (38.6 KB)  TX bytes:38600 (38.6 KB)

```

I tried  ```
networking restart 
``` but no results.

To check wether the module is loaded I used lsmod:
```
root@ordenacito:~# lsmod
Module                  Size  Used by
....
arc4                    9984  2 
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
ath5k                 108420  0 
lbm_cw_mac80211       211248  1 ath5k
lbm_cw_cfg80211        42260  2 ath5k,lbm_cw_mac80211
led_class              12164  1 ath5k
parport_pc             39204  0 
lp                     17156  0 
....
```

I guess that means it is loaded? 
Now I am stuck - as I said. 

I am not a total newbie, but unable to solve deeper problems myself - I still have to look up forums and tutorials, and I am not always aware what the commands I use exactly result in... 

Can anyone help what to do next?

---

### Post by jesuspresley on 2008-11-20
Hold it folks. 

It seems to be a matter of the WiFi hardware: I booted into Win XP, and the WiFi was not available. 
I deactivated wireless in BIOS and booted into Ubuntu and got the same result from lshw as above.

Maybe I hit a secret switch on the front panel or something - but I assume the NC10 doesn't have one.
Hope it didn't went down the drain.

EDIT: 
After one day, my wireless chip worked again, after switching it OFF in BIOS, booting, then switching it ON again. 
Very quirky.

---

### Post by Jon Bradbury on 2008-11-26
The Bios has three settings for wifi : Always on, Always off, Restore last state.

Mine's set to restore, so that it comes on if I left it on when I last shutdown. The problem is, I can only change that state in XP, as there is no fn-key that Intrepid recognises to turn on / off the wireless card.

It's reasonably easy to define a fn-key to do this, but I don't know how to ask Linux to tell power the card up/down.

---

### Post by shappie on 2008-12-08
I have exactly the same problem but i really cant fix this. It just happened while starting up ubuntu and i wasnt pressing any keys or something. But once i bootup ubuntu it cant find any wireless networks any more and that is not that worse. But the real problem is it ruins my XP an Vista wireless to. I really cant find a solution for this problem :(. Hope someone can explain me what to do!

---

### Post by jesuspresley on 2008-12-27
You are right, after deleting my Ubuntu partition, the wireless worked like a charm again in windows. So I reinstalled Ubuntu and the wireless was found again. 

Really strange.

I presume that the error occurs when you right-click on the network manager icon and toggle the "Enable wireless network" checkbox.

---

### Post by Auraomega on 2009-01-02
> **Jon Bradbury said:**
> It's reasonably easy to define a fn-key to do this, but I don't know how to ask Linux to tell power the card up/down.

I'm not sure how helpful it is, but theres a command that can turn the wireless on and off that I use it with my laptop so as to save battery life, but I don't have my NC10 at the moment so I can't test if it works on there also.

Type 'iwconfig' and check the device name, then type 'ifconfig [device name] up/down' to turn it on and off.

You'll have to let me know if you manage to fix it as I plan on using Ubuntu on my NC10 when it arrives :P

-Aura

---

### Post by jesuspresley on 2009-01-03
> **Auraomega said:**
> I'm not sure how helpful it is, but theres a command that can turn the wireless on and off that I use it with my laptop so as to save battery life, but I don't have my NC10 at the moment so I can't test if it works on there also.

It's *Fn + F9*, but yet it does not work in Intrepid.

Actually I did not have any problems with that issue anymore for about a month now. 
Maybe some update fixed it?

---

### Post by Jon Bradbury on 2009-01-05
I tried 'sudo ifconfig wlan0 down' but it has no effect (measured using Powertop). The wifi card stays on.

---

### Post by Psyman on 2009-01-10
I've had a similar issue on my NC10 where the wireless just appears to stop working all together. I ran dmesg and got loads of stuff about the wireless hardware, but to be honest didn't really understand what it meant. Like you, i rebooted to XP where there wireless also didn't work. The first time this happened I removed drivers under XP and had it reinstall drivers which fixed it, however on subsequent occasions I've just turned the machine off and took the battery out for 5 mins which also sorts it. Seems to be a hardware issue rather than OS specific. 
If it happens again soon i'll post my dmesg output, but from what i gathered the wireless hardware wasn't responding to the driver

---

### Post by hasanm on 2009-10-26
It just happened to me in Jaunty. I am using the Ubuntu Netbook Remix. 

I was working in Ubuntu, then all of a sudden, the wireless stopped working. 
I booted  into XP, and but it was not working there too. I tried Fn+F9 (in XP) , verified the settings in the Bios, but nothing worked. I thought my wireless card broke or something. 

After 5 minutes, I booted into XP again. Voila, it is working again. And it is also working in Jaunty. 

One thing I noticed that, the system was responding very poorly, (like the windows sound events were jittery) while the wireless was having problem.

I am still not sure what happened. :???:

---

### Post by mcsnizzle on 2010-12-19
So glad to have stumbled across this thread!

I'm actually using a Samsung N110, which is a netbook similar to the NC10 but didn't seem to have the same distribution.. for all intensive purposes, they are the same. 

Anyway, my wireless problems are identical. I thought I'd post my experience for the benefit anyone else using the Samsung N110 who has the same wifi problem.

In the 14 months I've been using the N110 (dual-booting Windows XP and Ubuntu [actually the netbook variant called "easypeasy]) I have occasionally gotten this problem where I boot into Ubuntu and the wireless doesn't work.  However, a simple reboot had always fixed this...

until now.  For some reason, no matter how many times I reboot into Ubuntu or XP, the wireless refused to work in either. 

I tried the first kludge, taking the battery out and waiting five minutes. This didn't seem to work.

This is what I did to get it to work again:
1. load the BIOS and turned off the Wireless.
2. booted into XP
3. then rebooted again, and turned on the wireless ("always on"setting) in the BIOS
4. booted into XP. Noted that the wireless worked again.
5. Rebooted, this time into Ubuntu.  The wireless didn't work! And the same error as always--you click on the wireless icon, and it says there are no networks.  Wireless comes up as "disabled" when you look into it in terminal.
6. Rebooted again into Ubuntu, hoping it had reverted to its aforementioned ways, where occasionally a reboot would solve things. Success! :D Wireless is working again. 

If this is a hardware problem, I hope we can find some way of resolving it in the future. It may be worth noting that I also have Moblin on my computer--another Linux-flavor operating system designed for netbooks--and it seems to always be able to resolve the wireless issue.  Strange... Maybe a clue as to what's going on?

---

