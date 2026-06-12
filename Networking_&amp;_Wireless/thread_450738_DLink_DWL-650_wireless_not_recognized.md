---
title: "DLink DWL-650 wireless not recognized"
date: 2007-05-21
forum: Networking &amp; Wireless
---

### Post by hodad on 2007-05-21
I just bought a wireless card to get my older Dell Latitude (Pentium III Coppermine approx 2001 vintage) connnected to wireless networks. I tried "Administration-Networks", but only saw "modem" listed. 

 I then went to documentation support and found the wireless network support page.  Tried suggested actions, saw the card listed with lshw command, but got bogged down when I tried to Gedit the /etc/pcmcia/config.opts file.   I don't know what to "bind" the card to.  In the example given, they say "bind ATH ..." or somethng like that, and ask you to fill in what you want to bind to, but I don't know what I'm supposed to bind to, or where to find out.  Anyone have any ideas?? 

Thanks in advance!

---

### Post by hodad on 2007-05-21
...A little more info:

I loaded "Feisty" on the laptop after having no luck in Dapper.

I tried sudo lshw -C network.  Result:

Password: 
  *-network               
       description: DWL-650 Wireless PC Card RevP 
       product: ISL37101P-10 
       vendor: D-Link 
       physical id: 0 
       version: A3 
       slot: Socket 1 
dave@dave-laptop:~$ sudo ifconfig eth1 up 
eth1: ERROR while getting interface flags: No such device 
dave@dave-laptop:~$ sudo ifconfig eth0 up 
eth0: ERROR while getting interface flags: No such device 

Still no recognition of the card under "System-Administration-Network Settings"...

---

### Post by grgzfla on 2007-05-23
I have an older Dell OptiPlex GX1 450MHz Pentiium-III with 640MB running Feisty Fawn 7.04.
I have a working wired network connection.  I'd like to install a Syba PCI to PCMCIA controller so I could use my DLink DWL-650+ wireless adapter.

After poking around the internet for the better part of a day, I thought "This is doable".

Physically installed the Syba controller and rebooted.  Device Manager (System -> Preferences -> Hardware Information) correctly identified it as a Ricoh RL5c475.

Inserted the DWL-650+ and restarted Device Manager.  It correctly identified my wireless adapter under the Syba controller as a TI ACX 100 device.  Under the Advanced tab it even lists it as a DLINK DWL-650+ Cardbus adapter!

I thought I was home free...  But wait, System -> Administration -> Network only shows entries for  Wired and Modem connections!  Where's the Wireless???  Rebooted again (old habits die hard)...  No joy!  Still no Wireless connection.

Ok.  I've clued into the fact that the DWL-650+ uses a non-open ACX100 driver.  And I'm resisting setting up an ndiswrapper using a M$-Windows driver as most of the older postings have suggested.  (It's a matter of principle issue.)  Back to more poking around...

What's this Restricted Drivers Manager under System -> Administration?...  It says it needs linux-restricted-modules-2.6.20-15-generic to run.  Ok, use System -> Administration -> Synaptic Package Manager, find the module, and install it along with a few other required packages.

Wahoo!  The light on the wireless adapter is flashing!  It's alive!...  Almost.  I haven't setup my SSID or WEP key yet.  Now how do I do that?...

I remember some posts talking about a WiFi Radar utility that might be useful.  Ok Mr. Synaptic, lets install the wifi-radar package (version 1.9.7-0ubuntu4).

Now I have Applications -> Internet -> Wifi-radar to configure my connection.  Very slick; it lists all the networks in range and their signal strengths!  I configure my SSID and WEP key.  It tells me I'm connected!  I'm getting warm fuzzy's!

System -> Administration -> Network now has a Wireless entry!  I wonder if it found that before or after WiFi Radar?  I forgot to check.  Anyway, I disabled the Wired connection.  And rebooted again.  (Sorry, old habit.)

Now I'm happy to share my success with others via my wireless connection!  :popcorn:

My only low point is the double computer network icon in the panel at the top of the screen doesn't seem to know I have an active wireless connection.  Oh well, that I can live with.  I have a wireless internet connected Linux system, unencumbered with M$ cruft!

All for the cost of the Syba controller, two 256MB SDIMMs, and keyboard and mouse.  The base system and screen were rescued from a discard pile.  The DLink adapter was leftover from a previous home network upgrade project.

Thanks for reading.  Hope it helps!  :)

---

### Post by soulglo83 on 2007-06-02
I too have a D-Link dwl-650 and have identical output from the lshw command as the thread starter.  His output indicates he is using the dwl-650 revision P which is what I too am using.  grgzfla you are referencing a card that does not use the same drivers.  The DWL-650+ is an entirely different card.  Adding the restricted modules may be necessary to make the 650 work, but it is not the only step.

Is anyone aware of what step we are missing? the dwl-650 is recognized by lshw however it is not bound to an eth interface.

---

### Post by -Phi- on 2007-06-12
This worked brilliantly for me for the DWL-650, even if it is ndiswrapper: [https://help.ubuntu.com/community/WifiDocs/Device/RTL8180L](https://help.ubuntu.com/community/WifiDocs/Device/RTL8180L)

Apparently the issue has to do with the old driver getting blacklisted in Feisty. More details: [http://ubuntuforums.org/showthread.php?t=422198](http://ubuntuforums.org/showthread.php?t=422198)

- Phi

---

