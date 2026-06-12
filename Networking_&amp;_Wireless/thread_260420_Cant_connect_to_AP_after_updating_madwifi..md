---
title: "Cant connect to AP after updating madwifi."
date: 2006-09-18
forum: Networking &amp; Wireless
---

### Post by BlazeJay on 2006-09-18
Hi everyone, i just updated my madwifi drivers and now I cant connect to any access points. I see them in wlassistant but it always fails to connect. I have a Atheros AR5006XS minipci card.

---

### Post by tturrisi on 2006-09-18
how did you update them?
see
[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)
[http://madwifi.org/wiki/UserDocs](http://madwifi.org/wiki/UserDocs)
[http://madwifi.org/wiki/UserDocs/MiniPCI](http://madwifi.org/wiki/UserDocs/MiniPCI)

---

### Post by BlazeJay on 2006-09-18
i followed the HowTo on madwifi.org The card worked fine when I first installed ubuntu, i couldnt get the card to get into monitor mode so i thought maybe updating the driver would fix it. Unfortunatly now I cant connect to any of the access points. They show up fine but I cant connect
thnx for the help

---

### Post by tturrisi on 2006-09-19
Did you backup the old drivers?
Monitor mode works just fine w/ madwifi.  Why monitor mode?  Kismet?

---

### Post by BlazeJay on 2006-09-19
I didnt backup the old drivers. I wanted to get monitor mode to work to play around with kismet, but everytime I ran kismet it gave me errors. I guess I'll just have to reinstall ubuntu again.

---

### Post by dimethroxy on 2006-09-22
I have the same exact problem !

but my card work ONLY in monitor mode !

I can't get it to work in sta mode

STA mode:

```
cgskill@cglaptop:/usr/src/madwifi-ng$ wlanconfig ath1 create wlandev wifi0 wlanmode sta
wlanconfig: ioctl: Operation not permitted

```

MONITOR mode:

```
cgskill@cglaptop:/usr/src/madwifi-ng$ sudo wlanconfig ath2 create wlandev wifi0 wlanmode monitor
ath2
```

i'm using the latest madwifi-ng cvs, I can scan for network but couldn't connect to them, monitor mode work perfectly but it's pretty useless if i can't connent to an AP !

need help, thanks!

---

### Post by BlazeJay on 2006-09-23
> **dimethroxy said:**
> I have the same exact problem !

but my card work ONLY in monitor mode !

I can't get it to work in sta mode

STA mode:

```
cgskill@cglaptop:/usr/src/madwifi-ng$ wlanconfig ath1 create wlandev wifi0 wlanmode sta
wlanconfig: ioctl: Operation not permitted

```

MONITOR mode:

```
cgskill@cglaptop:/usr/src/madwifi-ng$ sudo wlanconfig ath2 create wlandev wifi0 wlanmode monitor
ath2
```

i'm using the latest madwifi-ng cvs, I can scan for network but couldn't connect to them, monitor mode work perfectly but it's pretty useless if i can't connent to an AP !

need help, thanks!


Youre missing a sudo command in the standard mode, i destroyed mine and recreated it "sudo wlanconfig ath1 create wlandev wifi0 wlanmode sta" now the card can associate with the ap, but i cant get an ip. I set up a static ip and it still doesnt work :(

---

### Post by tturrisi on 2006-09-23
fyi:
To use use kismet w/ madwifi-ng you must edit the file /etc/kismet/kismet.conf to this:

```
# User to setid to (should be your normal user)
suiduser=YOUR UBUNTU USER NAME

# Sources are defined as:
# source=sourcetype,interface,name[,initialchannel]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=madwifi_ag,wifi0,madwifi
```:

---

### Post by dimethroxy on 2006-09-24
> **BlazeJay said:**
> Youre missing a sudo command in the standard mode, i destroyed mine and recreated it "sudo wlanconfig ath1 create wlandev wifi0 wlanmode sta" now the card can associate with the ap, but i cant get an ip. I set up a static ip and it still doesnt work :(

even with the sudo it doesn't work :(

```
sudo wlanconfig ath2 create wlandev wifi0 wlanmode sta

wlanconfig: ioctl: Input/output error
```

the only mode that work is Monitor

auto,master,managed doesn't work ! 

maybe it's a problem with my card ? i'm using an pcmcia ubiquiti SRC.

---

### Post by BlazeJay on 2006-09-24
try destroying all wifi devices first then recreate them. Mine still doesnt work but now in the NetworkManager applet it connects to an AP but the internet doesnt work, and i cant even ping the access point?! :confused: When i try to connect using wlassistant it doesnt connect at all. arrggh

---

### Post by BlazeJay on 2006-09-24
i just uninstalled and reinstalled the drivers. I have a problem while following the madwifi howto on how to uninstall the drivers. After doing "cd scripts
./madwifi-unload.bash
./find-madwifi-modules.sh /lib/modules/
cd .. " nothing happens, and when i install the drivers it says that there are still madwifi drivers on my system. Am i supposed to change something in that code ^ ?

---

### Post by BlazeJay on 2006-09-24
ok one quick thing, i just ran the make command in root, and im missing the builds, how do i download them? blaah

---

### Post by duren on 2006-10-07
I've run into the same issue..

I want
- packet injection
- WPA support

I can't use dapper's restricted madiwifi - no injection

I can't use madwifi-ng because dapper's stock kismet doesn't work, nor does wpa_supplicant, which is the backend for networm-manager-gnome. When you try to invoke wpa_supplicant manually as a test, you'll notice an error with the madwifi driver: argument list too long

I recompiled wpa_supplicant along after getting all this extra crap and this time i didn't have that problem but network-manager-gnome said that when it sets AP_SCAN to 1 it receives back UNKNOWN COMMAND (as shown in /var/log/daemon) and so it bails and I can't connect to ANY network.

using the recompiled wpa_supplicant manually was fine, I could associate wirelessly.

I'm gonna try madwifi 0.92 again because I can't remember what the results were the last time i tried using that version.

---

### Post by tturrisi on 2006-10-07
> **duren said:**
> I've run into the same issue..

I want
- packet injection
- WPA support

I can't use dapper's restricted madiwifi - no injection

I can't use madwifi-ng because dapper's stock kismet doesn't work, ...
Not sure about injection but the Dapper Kismet works just fine.  What kismet errors do you get?  I'll bet you had the kismet.conf misconfigured.  The Dapper Kismet is the latest release of kismet that's available:  2006-04-R1

---

### Post by duren on 2006-10-07
Yeah Dapper's kismet works fine but stops working once you patch madwifi source with injection support.

The error is simply that the source drivers are way too new for the kismet included in the repositories.

I have finally reached my goal - a madwifi setup that does everything I want:

- packet injection works
- no random madwifi lockups
- WPA connectivity support
- kismet works

It only took me a few days, recompiling madwifi, wpa_supplicant, kismet and upgrading to the newest kernel.

The problem is that as soon as you get the latest madwifi drivers, everything goes to hell (kismet, wpa supplicant, nm-applet/Network manager) because they don't understand how to use the new madwifi drivers.

For anyone having stupid issues like never connecting to access points / constantly trying to connect etc etc, I'm confident it's because the wpa_supplicant included with Dapper is causing the problem. Even the latest stable release (0.49) didn't work. I needed to get the newest snapshot (yesterday's actually) for everything to finally start working.

And all because I wanted new network drivers ;)

---

