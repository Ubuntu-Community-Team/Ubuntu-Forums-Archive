---
title: "Uni, WPA wireless, PEAP, LEAP and utter confusion"
date: 2006-10-03
forum: Networking &amp; Wireless
---

### Post by Flamekebab on 2006-10-03
I've seen a couple of topics on this, but they seem to have gone under, so I think I'll create my own.

I've just started uni in Edinburgh (although at Napier uni) and I've found that they have pretty good wireless coverage. There's a slight problem though.

They support OSX and WinXP (SP2) but not Linux. No surprises there!

However, I figured I'd be able to get things up and running without too many problems. Turns out, they have a rather complex system, compared to what I've seen elsewhere.

It seems they use either PEAP or LEAP, or both. To be honest, it's got me a bit confused..

They have a guide to setting up their wireless [here]("http://www.napier.ac.uk/depts/citservices/Documents/wireless.PDF"), which may yield some clues.

I'm rather surprised that Dapper doesn't have support for this sort of thing OOTB. Can anyone help me?

---

### Post by tribaal on 2006-10-03
Hum, unfortunately your Uni doesn't use exactly the same process than mine... But I guess I can give you a little pointer anyway: Did you install "NetworkManager"? Becaus ethis allowed me to use a WPA-PSK and PEAP authentication system pretty easily...

To get it just "apt-get install NetworkManager" as usual... it's a gnome applet, allowing to scan for and connect to available networks. Select your Uni's, and then a pretty massive form should pop up. Give it a try with several configurations... 

Be confident, give it a little work, and it'll be fine I'm sure :)

Hope this helps any

- trib'

---

### Post by Flamekebab on 2006-10-03
Isn't the network manager applet installed by default?

It didn't seem to have any WPA options at all..

Perhaps I'm thinking of something different though, could you clarify things for me?

---

### Post by tribaal on 2006-10-03
Sure!

Well there is an applet installed by default that does manage network connections, but I think you'll want to install the package named "NetworkManager". I upgraded from Breezy (previous ubuntu version), so I'm not so sure if it's installed by default or not... The best way to find out is to:

"sudo apt-get install NetworkManager" (or use "aptitude" instead of apt-get, either way).

If the command does nothing, then you have it installed... otherwise you need to add the "NetworkManager" applet to your gnome panel and let it manage your network connections for you. 

I think that all I needed to do to get my WPA PEAP working.

Here's a screenshot of the Networkmanager applet, maybe it will be faster for your to figure out if you have the same thing installed or not :)

Don't hesitate to ask more questions :) (even by PM if you feel the need)

- trib'

---

### Post by lptr on 2006-10-03
Using KnetworkManager
Two days ago I could enter a ESSID WPA passwd etc. Networkmanager seemed to have found that hidden network (that works fine with WPA/PSK under XP and same card here on notebook). But I could not ping into alive subnet when running under Linux.

Now, I tried things again and cannot even reenter a new network. That menu-item in that tray util simply has gone. Knetworkmanager tells me there are no network devices and connections are disconnected.

Any hints what could be broken?

rob*

---

### Post by Flamekebab on 2006-10-05
Has anyone had any success with PEAP and LEAP?

---

### Post by ZylGadis on 2006-10-06
I don't know how helpful that is, but the CS department of my university uses LEAP authentication through a RADIUS server. There is a great package called xsupplicant that does everything EAP (no WPA), and I used it to connect to their wireless network in Breezy. Unfortunately Dapper's xsupplicant is broken for some reason (it segfaults), so you will need to compile the newest version yourself (Dapper's xsupplicant is also a few versions behind).
Hope that helps.

---

### Post by Flamekebab on 2006-10-06
xsupplicant doesn't seem to segfault for me, but it does seem to want some sort of complex configuration..
Could you give me any tips on how to configure it?

---

### Post by UltraMathMan on 2006-10-06
From a quick scan of your University's Setup Guide, it looks identical to my University's. I managed to get wireless working with wpa supplicant, you can check you the details [here]("http://ubuntuforums.org/showthread.php?t=249654").

-Hope this helps :)

---

### Post by ubuntu_demon on 2006-10-10
> **Amaranth said:**
> My /etc/network/interfaces looks like this:```
auto lo
iface lo inet loopback
```

Make sure your interfaces look like that.

Make sure everything except lo is unconfigured :
$ifconfig
$sudo ifdown eth*A*
$sudo ifdown eth*B*
$sudo ifdown eth*C*
....

And install network-manager-gnome or network-manager-kde :
$sudo aptitude install network-manager-gnome

OR

$sudo aptitude install network-manager-kde

logout and login again

now start playing with network-manager

Good luck! (this is about all I know about this :D)

---

### Post by wirelessmonkey on 2006-10-10
When using .1x authentication, you must use one of the supplicants.  wpa_supplicant is well documented, xsupplicant is heavily touted by industry users.
You should really take the time to read the configuration documentation for whichever client you choose to use.  Example configs are included with each app, and are also available on each projects site, with many user examples in various other places...

i.e. [http://www.it.utah.edu/services/connected/wireless/installation/linux.html](http://www.it.utah.edu/services/connected/wireless/installation/linux.html)


Good Luck

---

### Post by Flamekebab on 2007-02-16
I know this is an old topic, but hey, I wanted to make it easier for any other Napier students to get online using linux as I finally got it working just now (I'm typing this from inside a rather boring lecture..).

I used [this guide]("http://ubuntuforums.org/showthread.php?t=318539") and this is my config file:
```
auto eth1
iface eth1 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid NapAir
wpa-ap-scan 1
wpa-eap PEAP
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-EAP
wpa-identity <username>
wpa-password <password>
wpa-phase2 auth=MSCHAPV2
```

I've tried it at Craiglockhart and it seems to work. It should work at the other campuses too, but I don't give any guarantees!

I'm using my laptop's built-in wireless which is an intel card, I think.
I'll see if I can get it working on my netgear card next week.
I hope someone finds this useful.

---

