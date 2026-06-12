---
title: "volatile WiFi"
date: 2005-04-21
forum: Networking &amp; Wireless
---

### Post by benplaut on 2005-04-21
as hard as i try, and as many utilities i download, i still can't get it to work without problems.

I have a laptop with an atheros chipset that i use to switch, primarily, between 3 different networks. Two use 64bit WEP, and the other is open (no encryption)

1. To connect to one of the WEP networks, i have to manually, each time, go to Network Config and put in the essid's and WEP keys of the networks. Note to Gnome developers: there needs to be a network profile switcher built in. The utility had no knowledge whatsoever of what had previously been connected to- it simply tried to connect to the network that it had connected to last. The indicator said Idle, but in reality, it had no clue what it was doing.

2. Except for the first time i tried, i have not been able to connect to the insecure network. I will manually enter the essid of it, and press Activate, but it will never successfully finish. Sometimes it goes on perpetual hold at the "activating ath0" box. This might be the fault of the router (some friends of mine also have trouble connecting), but i think the network manager (or lack thereof) is part of the problem.

3. Whenever i use a network profile manager ("Wireless Connection Manager and "Wifi Radar" are the two i've gotten to install), it shuts off my internet, does not manage to scan for networks. For some odd reason, in terminal, if i "iwlist ath0 scan", it will show results (about half of the time), but if i "sudo iwlist ath0 scan", it errors out, saying it doesn't support scanning. 

4. When my internet shuts down, the wifi led turns off, and i can't figure out how to get it back on (Fn+F5 doesn't do anything). I have to reboot to get it back on.

Any suggestions?  ](*,)  ](*,)  ](*,)  ](*,)  ](*,)

---

### Post by benplaut on 2005-05-15
bump?

any help?

so far, i have since figured out that the card has some dependancy on the Gnome network applet, and only works with it. GTKwifi doesn't work, either. the card, being so new, should support scanning, but it can only seem to scan and find the network that i am connected to (?). If i'm not connected, then it can't find anything (there are five networks in my area). iwlist scan provides "no results", but sudo iwlist scan says "no results: invalid argument"... and i am not arguing with it  :^o 

did i order a bad wireless card, in terms of linux compatability?  ](*,)

---

### Post by dave9191 on 2005-05-15
I gave up on the graphical tools in gnome and kde. I wrote several script files for each network that I connect to. When I want to connect to it, i pull down a little from my panel and select the icon of the network I want. The icon then runs the connection script and configures my network for me.

---

### Post by benplaut on 2005-05-16
[QUOTE=dave9191]I gave up on the graphical tools in gnome and kde. I wrote several script files for each network that I connect to. When I want to connect to it, i pull down a little from my panel and select the icon of the network I want. The icon then runs the connection script and configures my network for me.[/QUOTE]

yeah... i think i'm going to resort to that  ](*,)  (you have an Atheros A/B/G?)

---

### Post by dave9191 on 2005-05-16
Nopez, I have a Centrino laptop with an IPW2200 in there.

---

### Post by daenney on 2005-05-16
Hey
About those scripts, could you post a sample version?
I'm kinda new to Linux but I'm very satisfied with Ubuntu. I have the same problem though with wireless networks...
So could you post some kind of sample script which I can then adjust to fit my network?

---

### Post by dave9191 on 2005-05-16
Wireless connection script example. Sets up AP details and waits for connection before it asks for DHCP. Replace all YOUR_ESSID, YOUR_MAC_ADDRESS, YOU_WEP_HEX_KEY. 

```
#!/bin/bash
#
# Set up Scooby Access DHCP
echo "Please enter your password"
sudo echo "Setting essid to YOUR_ESSID"
sudo iwconfig eth1 essid YOUR_ESSID
echo "Adding encryption key"
sudo iwconfig eth1 key YOUR_WEP_HEX_KEY
sudo iwconfig eth1 key restricted
sudo iwconfig eth1 ap YOUR_MAC_ADDRESS
iwlist eth1 scanning
echo "Waiting for association ..."

# Set the value of a - result of cmd
A=`iwconfig eth1 | grep YOUR_ESSID`
A=`expr substr "$A" 11 12`
# set the value of b - value we dont want to see
#B='eth1      unassociated  ESSID:"YOU_ESSID"'
B='unassociated'

if [ "$A" != "$B" ] ; then
        echo "strings not equal"
fi

# loop while wireless not ready
echo "Comparing"
while [ "$A" = "$B" ]
do
        echo "Device not ready - waiting (Check Wirless Switch)"
        A=`iwconfig eth1 | grep YOUR_ESSID`
        A=`expr substr "$A" 11 12`
        sleep 5
done

echo "Requesting IP using DHCP"
sudo /sbin/dhclient eth1

```

Example of a config script for wired network. Needs for the resolve.conf with network details to be copied over as this one doesnt get DHCP. 
```

# !/bin/bash
#
# Configure network devices for uni access

echo "Setting up network interface eth0"
sudo ifconfig eth0 128.16.80.79 broadcast 128.16.80.255 netmask 255.255.255.0 up
echo "Setting up gateway route"
sudo route add default gw 128.16.80.1
echo "Copying over new resolv.conf"
sudo cp /opt/scripts/resolv.conf /etc/resolv.conf

```

You can read more about wireless networking throught the command line here. [http://ubuntuforums.org/showthread.php?t=30671](http://ubuntuforums.org/showthread.php?t=30671)

Dave

---

### Post by daenney on 2005-05-16
Yay, thank you very much!

---

### Post by dave9191 on 2005-05-16
No probs :) Ill be working on refining those scripts and making a howto about this sometime in the next few weeks for other users. 

Dave

---

