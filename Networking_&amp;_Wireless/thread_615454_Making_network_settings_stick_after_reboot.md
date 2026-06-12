---
title: "Making network settings stick after reboot?"
date: 2007-11-17
forum: Networking &amp; Wireless
---

### Post by .neo on 2007-11-17
Hi good ppl,

I'm kinda of an Ubuntu n00b so any help will be very much appreciated.

I've got a problem with network settings which won't stick after reboot.

Here's the case: I've got two computers (one running Ubuntu and other one Xubuntu), both with two Ethernet network adapters... The adapters linking the two forementioned computers are 2 Diamond HomePNA cards (which have been setup so that pcnet32 loads with the homepna=1 option), with Fixed IP settings (10.10.10.1/255.0.0.0 & 10.10.10.2/255.0.0.0)...
The Ubuntu computer has another Ethernet adapter that hooks up to an ADSL modem (and that adapter is set to DHCP). Also the Xubuntu computer has another Ethernet adapter that's set to DHCP (but is not used at the moment). What is the problem? 

If I reboot either of the two computers there's not going to be a line in the routing tables that handles the 10.x.x.x subnet until I upon reboot go into the network-admin panel and fiddle with the settings for the HomePNA adapters just enough (change 'em a little, and change 'em back again) for the OS to update network settings... After that happens everything's peachy, but that's a hassle I'd like to avoid.

What's the problem, how to add a line to routing tables that sticks after reboot? Maybe it's because the HomePNA adapters are not set to be primary, and the primary adapters are setup via DHCP (even though I think I've tried setting them with fixed IP settings also, but with the same non-results after reboot)...

TIA

---

### Post by spd106 on 2007-11-17
I've had a bit of trouble with network-admin in the new Ubuntu 7.10 release too.

I would recommend that you eschew network-admin where possible and configure the connections/interfaces manually in the /etc/network/interfaces file. You can use a normal text editor, though you'll have to start it as root i.e 

```
gksudo gedit /etc/network/interfaces
```

You should see a file like this, though the names may be different.

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
address 10.10.10.1
netmask 255.255.255.0

```
In this version roaming mode is not in use at all, so Network Manger won't attempt to interfere with any of the network settings. The eth0 interface will use DHCP, the static eth1 interface should come up on boot automatically and the routes will be set up correctly.

You can also choose to use roaming mode on the eth0 by removing those two lines from the interfaces file. This probably won't make much difference though, since you aren't using wireless.

---

### Post by .neo on 2007-11-19
Hi spd106,
  Thanks for your reply, unfortunatelly the problem with my HomePNA network isn't that Network Manager messes up interfaces file (which I've noticed sometimes it does) but that with the right settings (even if they're written manually by calling sudo nano /etc/network/interfaces) the route -n won't show the HomePNA related entries after reboot.
  I've noticed though that if after reboot I manually in terminal call sudo /etc/inti.d/networking restart (which is what I guess implicitly also happens if you change things in network-admin panel), the routing table will show up the entries related to HomePNA adapters...?
  BTW, don't know if this makes a difference but I had to edit sudo gedit /etc/init.d/module-init-tools and had to add a line modprobe -r pcnet32 > /dev/null 2>&1 to make my HomePNA card work not in the default RJ-45 (ethernet wire), but RJ-11 (telephone wire) connector active mode... Also, as I said in the first post, the /etc/modules has a line pcnet32 homepna=1 added. Is there someting I need to do to make sure, the networking restarts upon login after reboot so I don't have to do it manually...

TIA

---

### Post by spd106 on 2007-11-19
You could add a custom command in System -> Preferences -> Session. This will then run every time you login to the desktop.

Does that help?

---

### Post by .neo on 2007-11-20
> **spd106 said:**
> You could add a custom command in System -> Preferences -> Session. This will then run every time you login to the desktop.

Does that help?

Hi spd106,

  Thanks again for all of your help in this matter. It seems that the problem (but for now at least unsolvable) is in the /etc/init.d/module-init-tools script. Adding that one line to unload pcnet32 module (so that it wouldn't load in the default RJ-45 ethernet mode) will in fact result in routing table not being filled with the routing data related to the homepna adapter at all.

  I can confirm this since upon restart I've ran "sudo /etc/init.d/networking restart" (which loads the routing table with routing data for the homepna adapter - which is initially after restart missing) and then running "sudo /etc/init.d/module-init-tools" (which reverts the effect of networking restart - resulting in a routing table that once again is missing routng data for the homepna adapter, same as is after restart).

  So my solution in the end: I've added the "/etc/init.d/networking restart" line to the end of the "/etc/init.d/module-init-tools" (basically what spd suggested only i didn't want to place it in the session - mostly because I need homepna to be working all the time, and also :) I couldn't find System -> Preferences -> Session in Xubuntu).

  Now I just need to get the old bt878 tv card to stream audio :( (anyone got experience in that, my guess is I've got problems mostly because my Bt878 Audio capture device is UNCLAIMED - but I'll open a new post on this in the apropriate section :) )... BTW, I stream /dev/dsp but (even though I can hear audio locally from that device) it's just streaming silence from VLC?!? Maybe I've not setup VLC right? :confused:

Thanks again spd106.

[EDIT]

Talked to some ppl and their guess is networking is being initiated in between the point when the pcnet32 module was unloaded in the module-init-tools script and the point that the pcnet32 gets loaded once again (with the correct homepna=1 mode turned on), so that's why no routing table for that adapter gets entered into the routing table (does that make sense to you???).

---

