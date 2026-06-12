---
title: "Inspiron 6400 + WiFi problem"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by xtremesupremacy3 on 2008-05-03
Hey people,

Wonder if you can help me. 
I am the owner of an Inspiron 6400 by Dell. famously known for it's dissapointment lol. But anyway, wonder if anyone could lend me a hand here.

I upgraded a few weeks back to Hardy Heron through upgrade and ran my system perfectly and without any worries at all. But yesterday (Friday 2nd May '08)my system let me know that updates were available. So without even thinking about it I went ahead and did the upgrades. All went well and it asked to restart but I had a few things left to do so I opted for restarting when I was done.

Then when I restarted I was confronted by 'WHITE SCREEN OF DEATH!!!' ok, so I knew this was because there were multiple users running compiz so just uninstalled compiz. That was all sorted...but now it won't come up with my WiFi, as if it's not even in there! but I am running of 7.10 live cd at moment which detected it straight away.

Anyone got tips?
Greatly appreciated

Arthur

---

### Post by Fearghal on 2008-05-03
Just an idea but have you tried on a wired connection and through synaptic manager uninstall and then re-install bcm43xx-fwcutter.  It should prompt to re-install firmware also.  Its worth a go..

---

### Post by xtremesupremacy3 on 2008-05-03
ill give it a shot

---

### Post by Fearghal on 2008-05-03
I am running Dell 6400 also.  I only ungraded this morning to 8.04.  I didn't have any problems.  The upgrade did kill off all the hardware drivers though and did require re-install.  Everything else that were critical I had backed up just incase the upgrade went pear shaped.

---

### Post by xtremesupremacy3 on 2008-05-03
Ok well I just tried it and here's the really funny thing. I wasn't able to even get my wired connection working :confused: but never mind so i downloaded the DEB file instead using live cd and putting it into partition, but then it needs active connection to download the settings so, be honest. Is this going to be solvable problem or should I prepare for re-install?

---

### Post by Fearghal on 2008-05-03
So its more than just a wireless issue.  You will most likely have to configure your network connection manually.  When you restart your PC from HDD did you notice if the configuration is manually set or, as mine is, set to roaming.  This means it will pick up the ip address dynamically from your router.  If it is manually set then you have to ensure the ip address, the host etc are all exactly right or else it cannot connect and complete handshake with the router.
You should restart the PC and go to System/Administration/Network, unlock the applet and firstly click on the wired icon and select properties and set to roaming.  Save this and plug in the cable.  It should now pick up an address from the router.

---

### Post by xtremesupremacy3 on 2008-05-03
Well I see nothing unusual on boot but it throws loads of errors on shut down with Network Manager

---

### Post by Fearghal on 2008-05-03
Well if the system is set up dynamically and it stll does not connect maybe you should look at the setup you currently have using the live CD.  Look at the network manager settings for the wired setting.  If all else fails start from HDD and when system has started select Applications/Accessories/Terminal and enter,

sudo apt-get remove network-manager-gnome

Then,

sudo apt-get install network-manager-gnome

This will remove network manager and re-install a fresh version.

Again you should look at the connection settings and ensure roaming is set for wired and wireless settings.

---

