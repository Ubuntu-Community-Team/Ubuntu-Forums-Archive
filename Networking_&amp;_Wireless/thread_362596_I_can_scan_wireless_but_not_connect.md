---
title: "I can scan wireless but not connect?"
date: 2007-02-15
forum: Networking &amp; Wireless
---

### Post by renegade1029 on 2007-02-15
I recently installed Ubuntu for the first time. Now, having a Broadcom bcm4306 wireless card, I knew I would have some work to do to get it working, but a I have a problem, and I haven't seen the solution yet.

I followed [this]("http://ubuntuforums.org/showthread.php?t=340689") ndiswrapper guide (kudos to maclenin for helping a lot with it), and almost everything is fine. I can scan the wireless networks using both wifi-radar and "sudo iwlist wlan0 scan" in the terminal. However, I can't connect to any network using wifi-radar.

I tried forcing my card to my network's ESSID like this :

```
sudo iwconfig wlan0 essid "My_essid"
```

but nothing happens. I can change every iwconfig setting BUT the ESSID.

Anyone knows what my options could be? I would consider using the bcm43xx driver with fwcutter, but I would like the ndiswrapper way to work, since it seems more stable.

---

### Post by Floppyjoe on 2007-02-15
Have you tried editing your /etc/network/interfaces file?
```
sudo gedit /etc/network/interfaces
```
add stuff like this:
```
wireless-essid   MYNETWOTK
wireless-key     FEFEFEFEFE
wireless-channel 11
wireless-mode    managed
```
Where you change the info to your particulars.

---

### Post by jiminy on 2007-02-17
I'm in a similar boat---trying to get things working with Ubuntu Edgy on AirPort Express and a Mac PowerBook G4, also with a BCM4306 card. I used fwcutter, and while the machine can "see" my wireless network it can't connect to it, with wifi-radar, dhclient or anything else. I tried editing the /etc/network/interfaces/ file as suggested abve (setting up all the options listed in the example, and no others---I don't know what syntax to use to force it to use a particular MAC address, for example) but it's still not connecting.

In one word: help!

---

### Post by hicksy on 2007-02-17
Just speaking as a total newby, have you tried switcihng any security off before you try and connect? I remember reading somewhare that Linux doesn't get on with 128bit WEP at all. This information could of course be totally wrong, and should be treated with the appropriate dgree of caution....

---

### Post by Cloudane on 2007-02-17
Same boat here.  I've seen an insane amount of threads about this since I posted mine.  Basically, wireless is broken in Edgy IMO.

---

### Post by jiminy on 2007-02-17
> **hicksy said:**
> Just speaking as a total newby, have you tried switcihng any security off before you try and connect? I remember reading somewhare that Linux doesn't get on with 128bit WEP at all. This information could of course be totally wrong, and should be treated with the appropriate dgree of caution....
Indeed I did (though I had been working with WPA, not WEP).

> **Cloudane said:**
> Same boat here.  I've seen an insane amount of threads about this since I posted mine.  Basically, wireless is broken in Edgy IMO.
Really? Did you (or anyone else reading this) have any more luck with Dapper? I might just try downgrading, if so . . .

---

### Post by chili555 on 2007-02-17
This reply, and 80 or so more, is being postted with 128-bit WEP. I have another lappy upstairs that works perfectly, as well. One uses ndiswrapper and the other native orinoco_cs drivers.

Check your settings, especially in /etc/network/interfaces. Here is the wireless part of mine, for example.
```
auto wlan0
iface wlan0 inet dhcp
wireless-essid GBR1
wireless-key 096cxxxxxxxxxx4afe restricted

```

I use the word "restricted" because my router is set to Shared Key under Advanced Wireless Settings -> Authentication Type. If yours is set up as Auto, then you do not need to mark your WEP key "restricted."

Now, let's check our work, try again and hook up!

---

### Post by punkmonkey on 2007-02-18
I too am having this exact problem.  The really frustrating part is that when I first got my card working, it connected (to my neighbor's network) like a dream, and worked perfectly for a few hours.  Then I tried disconnecting from the neighbor and connecting to my own router, and now I can't connect to *anything*, though I can still scan half a dozen networks in range via wifi-radar and iwlist.  If I try to connect to any network via wifi-radar, I get as far as "Acquiring IP address" and it fails.

I have gnome-network-manager installed, and oddly it doesn't seem to recognize that I have a wireless interface.  It recognizes the wired ethernet fine. If I go to admin/networking, both my interfaces are listed.

ETA: I've also noticed that I have no wireless card light coming on, though I did earlier when my connection was working.

---

### Post by jiminy on 2007-02-19
I'm posting from a finally-functional WEP 802.11b connection (faster  and more secure would be nice, but I don't feel like pushing my luck . . . ) Here's how it worked:

I found a walkthrough [here]("http://www.ubuntuforums.org/showthread.php?t=319402&highlight=broadcom+4306+airport") , and followed it, with a couple of quibbles: most important, the WEP key had to be the full-length hexadecimal key---using a password didn't work. (AirPort users can get the key by looking up the network on the AirPort Admin Utility in OS X---not sure about Windows---and clicking the "password" button.) If in doubt, check "iwconfig eth1" against "iwlist eth1 scan" and try and make sure the Access Point and ESSID match, and that if iwlist says the network is using an encryption key, that iwconfig is too. Using the Networking program under Administration only made things worse, and the Network Manager icon in the corner of the screen was still telling me it couldn't find a network while I was chatting happily on Gaim. :???:  Afterwards, I found wifi-radar *would* work, and it even seems to be reconnecting me automatically at startup.

---

### Post by renegade1029 on 2007-02-19
Problem solved.

I changed the content of /etc/network/interfaces to this :
```
auto lo
iface lo inet loopback


iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

iface wlan0 inet dhcp
wireless-essid Powers
wireless-channel 11
wireless-mode managed
auto wlan0
```

And I can connect when my router is not protedted. I am going to try it when I have WEP encryption.

---

