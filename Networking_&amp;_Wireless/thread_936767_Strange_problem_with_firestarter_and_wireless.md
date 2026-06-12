---
title: "Strange problem with firestarter and wireless"
date: 2008-10-03
forum: Networking &amp; Wireless
---

### Post by cdyson37 on 2008-10-03
Hi. I have my wireless networking configured using the following /etc/network/interfaces
```
auto lo eth1
iface lo inet loopback

iface eth1 inet static
address 192.168.1.253
netmask 255.255.255.0
gateway 192.168.1.1
wpa-psk ***********************************
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid Badger

iface eth0 inet dhcp
```
which worked perfectly well until I installed firestarter. Now for some reason after bootup all the ifconfig stuff is done (correct IP, netmask etc) but iwconfig has not been run (no SSID etc set).

This is easily rectified by running
```
$ sudo ifdown eth1
$ sudo ifup eth1
```

but it's becoming a bit tedious to have to do on every boot! Any ideas folks?

---

### Post by Chas_E_Erath on 2008-10-04
Hi.

It is likely considered cheezy, but you can add those two commands to the end of your /etc/rc.local script (without the 'sudo', of course...). 

Hope that helps.
Chas.

---

### Post by kforum on 2008-10-05
why not use the network manager, its so simple...

---

### Post by cdyson37 on 2008-10-05
> **kforum said:**
> why not use the network manager, its so simple...

This is a static wireless configuration - no roaming required - and I'd like it to connect on boot rather than login (since it will sometimes be unattended). In any case such a move would be defeatist and leave the mystery unsolved :-P

---

### Post by kforum on 2008-10-05
isee... well i dont use ubuntu(i use gentoo), and i have the same spirit as you, but from what i know...

ifconfig at startup is nto sufficient, you need iwconfig set so you can have it locked on to a specific essid, also...
"iface eth0 inet dhcp" this seems contradicting to the fact that you want static ip...
i'd recommecnd reading around some docs, maybe you've done it wrong so far.

another, thing i assume you ARE using WPA security or otherwise it is broken.(if its wep you gotta config it for wep :p)

anyways, i dont know much about the specifics but maybe you should check teh firestarter docs.

firestarter only starts at login(unless you did somethign different), so it shoudnt bother anything in root time, but maybe it changed something inn the iptables...
also, maybe if you set a 'timeout' variable in the interface config, to a larger strech then standard it might help.

i dont know the proper syntax for such variable but im sure it exists.


cheers.

---

### Post by kevdog on 2008-10-05
Possibly something is not getting initialized.  At the top of your statements for eth1, what if you add a 

pre-up sleep 10

Does this solve the problem?

---

### Post by cdyson37 on 2008-10-07
> **kevdog said:**
> 
pre-up sleep 10

Indeed it does solve the problem! (Though I cut it down to 5 seconds because I am impatient!) The question is... why?

Many thanks!

---

### Post by cdyson37 on 2008-10-07
kforum: eth0 stuff isn't relevant as that's the wired interface (not being used). I leave it as dhcp in case I ever have to plug it in should the wireless fail.

Firestarter starts on bootup on ubuntu if it is installed and configured. There's an init script but that's just used to shut it down at the end. It's actually started in /etc/network/if-up.d. Quite why the sleep command would fix things I don't know... maybe firestarter is started too early or too late for iwconfig to do its magic?

Many thanks!

---

### Post by cdyson37 on 2008-10-14
I had to do ifdown/ifup again today after a hard disk check which appeared to be running simultaneously during boot (even though CONCURRENCY=none is set). So clearly there's something funny going on with the order in which things are run...

---

