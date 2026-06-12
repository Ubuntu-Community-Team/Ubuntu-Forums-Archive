---
title: "strange wifi problem showed up"
date: 2005-10-09
forum: Networking &amp; Wireless
---

### Post by sd_ap on 2005-10-09
The hoary install is quite a generic one - so no quirky things to work around.

The card: aironnet 350.

The problem.

When at home I am connecting just fine to my access point; both w/out wep and w/ wep. No worries there.

I go anywhere else and I cannot connect to a single access point.  iwlist sees them, as does the default network manager in gnome.  They both see the other networks, but when I go to connect, the connection never happens.  

I have a profile saved for my home network so I do not have to re-enter that damn wep key (quite long for a 128bit key) each time I want to connect to home after going elsewhere.  

Now, when I go to connect to another AP it says it is initializing eth1 (that is correct) but never grabs an IP and never connects to the AP.  I have even created a new profile for testing that is void of any/all WEP settings...but still nothing.  It sits for a while at "chaning profiles" and eventually comes back, yet no status change in my success with connecting to any other APs.

What I can't figure out is why it seems that my home settings are hardcoded to the system and no matter what I change, it refuses to connect anywhere else.  Wired works just fine, but the pcmcia card just won't connect.

I have tried popping the card in/out, rebooting...doesn't matter.  I have used both graphical and command line methods to connect to other access points...

Does anyone have any suggestions?

Thanks!
-Sean

---

### Post by sanemadman on 2005-10-10
I've encountered the similar issues - At home, I can access my wifi network without a hitch.  However, accessing the wireless network at work seems to be a different story.  I have the network key and using the basic settings (DCHP on....) in the network setup.  I deactivated my eth0 and activated wireless - reinstalled my wireless drivers with ndiswrapper.  All out of the obvious options.  

I have fallen in love with Ubuntu's builds.... but lack of real wireless support (as opposed to Fedora Core....) is killing my 'Buntu buzz....

eep.. help!?

---

### Post by sd_ap on 2005-10-10
anyone?

surely someone has atleast a suggestion :)

---

