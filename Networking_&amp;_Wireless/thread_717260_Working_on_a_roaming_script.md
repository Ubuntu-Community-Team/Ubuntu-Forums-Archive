---
title: "Working on a roaming script"
date: 2008-03-06
forum: Networking &amp; Wireless
---

### Post by abeowitz on 2008-03-06
I found this works for me quite well, but could use some tweaks.  (Hint hint.)

So, to help you all, and to improve my bash scripting, here's what I've got so far.  

Any improvements/suggestions would be awesome!  Thanks!

-=-=-=-

/etc/network/interfaces allows you to map different 'profiles' to an interface and then select one by calling an external script:

> auto lo wlan0

iface lo inet loopback

# SO I CAN BYPASS WIRELESS FOR FASTER CAT-5
allow-hotplug eth0


# CAT-5 LAN
iface eth0 inet dhcp


# CHOICE OF WLAN
mapping wlan0
  script /usr/local/sbin/detect_wlan
  map Home_ESSID wlan0-Home_ESSID
  map Work_ESSID wlan0-Work_ESSID


iface wlan0-Home_ESSID inet dhcp
  wireless-essid Home_ESSID
  wireless-key Home_key


iface wlan0-Work_ESSID inet dhcp
  wireless-essid Work_ESSID
  wireless-key Work_key


So, when /etc/init.d/networking is started, my detect_wlan script is called.  detect_wlan is passed the mapping parameters of wlan0. 

Since I used my ESSID's to name the 'profiles', I can also use these to search the airwaves.

If I grep out one of these ESSID's, I pass it back and networking picks the right profile to set things up.  :D

Here is detect_wlan:
> 
#!/bin/bash

IFACE="$1"

# BUILD GREP STRING TO FIND MATCHING ESSID'S
# FROM "iwlist <IFACE> scanning" OUTPUT
i=1;
while read NAME MAP; do
    if [ $i -gt 1 ] ; then
        GREPSTRING="$GREPSTRING\\|$NAME"
    else
        GREPSTRING=$NAME
    fi

    i=`expr $i + 1`
done

# SOMETIMES NEEDED TO RESET STATE OF WLAN0
# SOMETHING BREAKS IWLIST FUNCTION FOR ME
# wlan0     Interface doesn't support scanning : Network is down
/sbin/ifconfig $IFACE 192.168.1.250

# CHECK WIRELESS SCAN OUTPUT
ESSID=`/sbin/iwlist $IFACE scanning | grep ESSID | grep -o -m1 \"$GREPSTRING\" | sed 's/\"//g' | sed 's/ //g'`

echo $IFACE-$ESSID

exit 0



So, anyway, this is proof of concept.  I'm looking into making it do more...

1)  If no known ESSID is found, I want to find a public open WiFi router to attach to.  -OR- Any way to force network-admin into roaming mode, then?  Perhaps the user can then pick one from the GUI.

2)  If the eth0 link is alive, and has an IP, I want to skip the WiFi scan and setup, as Cat-5 is probably faster.  ethtool fools me sometimes, where I'll have a cable in, but until I do an ifconfig eth0, it thinks the link is down.  Hotplug seems to detect that though.  Is there a reliable way to see if a live cat-5 cable is connected?

3)  At work I have several WiFi hot spots.  I might look into choosing the strongest one, unless the driver does this already?

4)  Any bash scripters out there?  I struggled with this one, as I'm more of a Perl junkie.  I didn't want the overhead of Perl in my bootup.  Perhaps there are better ways to code this?

5)  Seems my wireless card gets in a bad state and iwlist fails.  I found that by attempting to assign an IP to it, it will then respond to iwlist commands.  This could be related to the GUI problems I was having with network-manager...?

---

### Post by abeowitz on 2008-03-07
Oops, found this.  This one is much better than mine:

[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

---

