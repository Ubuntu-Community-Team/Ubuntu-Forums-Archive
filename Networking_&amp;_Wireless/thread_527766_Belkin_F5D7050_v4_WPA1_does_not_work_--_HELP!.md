---
title: "Belkin F5D7050 v4 WPA1 does not work -- HELP!"
date: 2007-08-17
forum: Networking &amp; Wireless
---

### Post by tak1150 on 2007-08-17
Hi,
I have a Belkin F5D7050 v4000 (lsusb give 050d:705c) and am using zd1211rw driver (the one that comes with the feisty kernel).

[SIZE="3"]I am able to use this USB wireless card if there is** no WPA or WEP** authentication and SSID broadcast is enabled.
[/SIZE]
I have tried a bunch of other drivers such as:
[LIST]
[*]ndiswrapper with BLKWGU.inf (that came w/ the CD)
[*]zd1211 found [here]("http://zd1211.wiki.sourceforge.net/VendorBasedDriver")
[*]rt73
[*]rt83 -- tried to find it, but couldn't (no longer at sourceforge.net)
[/LIST]

With ndiswrapper, the kernel crashes and Ubuntu becomes completely non-responsive
zd1211, zd1211b, rt73 do not even recognize the wireless card (when I do iwconfig nothing appears except eth0 and lo)

So it seems that the best driver to go with is zd1211rw (back to where I started :( )

When I boot the computer, a pop-up window asks for the WPA password, but entering the password and clicking "Login to network" does not work; Network Manager shows that it's trying to login w/ the little animation thing.

I have messed with the /etc/wpa_supplicant.conf file a bit with no luck. I had the following (this info I got from [here]("http://ubuntuforums.org/showthread.php?t=518272&highlight=ndiswrapper+guide+1.48")):
```
ctrl_interface=/var/run/wpa_supplicant

network={
       ssid="<your networks essid>" <--Keep the quotes
       proto=WPA
       key_mgmt=WPA-PSK
       pairwise=TKIP
       group=TKIP
       psk="ASCII Password"  <---Keep the quotes
}
```
For PSK, I had the password and not the key.

On another machine, I am able to connect w/ WPA. I have not modified any config file on this machine. I just have to type in the WPA password, which is stored under keyring.

Sorry for the long post, but if you've read this far, please help!:p

---

### Post by tak1150 on 2007-08-17
um, bump.

---

### Post by tak1150 on 2007-08-23
shameless bump!

---

### Post by emergingtechnologies on 2007-10-28
I am having a problem with mine as well.

---

