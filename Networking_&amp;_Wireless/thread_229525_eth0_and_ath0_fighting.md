---
title: "eth0 and ath0 fighting?"
date: 2006-08-04
forum: Networking &amp; Wireless
---

### Post by wildseven on 2006-08-04
hello, i recently bought a wg511t and it worked literallt right out of the box. i put it in and did
```
sudo ifconfig eth0 down
sudo ifconfig ath0 up
sudo dhclient ath0
```

and it was up and i set up the rest ( ap, wep key ) through the network manager. in the network manager i deactivated eth0 and i slo clicked on the eth0 properties and unchecked 'Enable this Connection' this way ath0 was the only card i was using.

but the next day, i did 
```
iwconfig
```
and i see that they are both on. and i check the settings and eth0 is still off. yesterday when i checked iwconfig eth0 said 
no wireless extensions. Now it is telling me info as if it were on.

i tried 
```
 sudo ifconfig eth0 down 
``` but it still shows up under iwconfig as on.

any ideas?

---

### Post by stormblue on 2006-08-04
Are you having network trouble?  I ran two wireless cards eth0 and ath0 for war driving for a while with no problems.  

Maybe their set to auto in your config file. Check your config by located in /etc/network/interfaces.  Look in there for auto eth0.

---

### Post by wildseven on 2006-08-04
well it doesnt really bother me that they are both up, it's jsut a concern that they are. i mean, i tried turning eth0 off and i get
```
eth0      IEEE 802.11b  ESSID:****  Nickname:****
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:06:25:60:68:89
          Bit Rate=11 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=-36 dBm  Noise level=-81 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:68   Missed beacon:97
```
i checked the /etc/network/interface and it says ath0 is the primary network interface. 

is this a problem i should be worrying about tho? will it affect me in any way? i mean a backup is cool you know, i just dont want any interference or problems to occur later on.

---

### Post by stormblue on 2006-08-04
I don't see any reason for concern. I'd set my cards in all different modes..managed, master,ad-hac,monitor and switch it up depending on what I was doing and had no problem.  I doubt you will.

You should just be able to take the card out and not have it appear any longer.

---

### Post by wildseven on 2006-08-04
i want to use my ath0, i know i can take it out and it wont see it. but the other one is ipw2200 and its onboard so i cant take that out haha. well if i dont want the ipw2200 to be used, what mode should i put it? i usually use ath0 in managed for regular internet or monitor for wardriving/wep hacking w/e.

---

### Post by stormblue on 2006-08-04
You should be able to disable your wireless card either in the bios or with a FN key.  


So there is nothing in /etc/network/interfaces file about eth0? If there is delete it and that should fix it.

---

### Post by wildseven on 2006-08-04
nope there is nothing in there about my eth0. hmm, well with them both on managed mode, is it dangerous to my laptop? will they clash in any way? if not, ill just leave it the way it is heh~

---

### Post by wildseven on 2006-08-04
wo0ps, i just found something new interfaces.dpkg-old

i read that and it has stuff on eth0. should i edit it or something?
```
 # The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp
        # wireless-* options are implemented by the wireless-tools package
        wireless-mode managed
        wireless-essid any



iface eth1 inet dhcp



auto eth0
```

---

### Post by stormblue on 2006-08-04
No they won't clash.  At least I can't think of a situation where they would, unless you assigned them both the same static IP or something like that where you were trying to make them clash.  What's your model number for your computer?  Check to see if there isn't a way to turn it off manual.  I would think there has to be a way to turn it off either in the BIOS or with FN keys.

---

### Post by wildseven on 2006-08-04
heh oh well, i guess there really isnt anything to worry about then heh, yeh there is a switch to turn off the wireless inside my laptop ( eth0 ).
well atleast its better i think (dont know if it was even bad in the first place, just concerned )

i did ```
iwconfig
```
and this time eth0 radio is off and it is not associated to the AP.

---

