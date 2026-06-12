---
title: "Hoary and Ndiswrapper"
date: 2005-04-01
forum: Networking &amp; Wireless
---

### Post by bottledwater on 2005-04-01
I installed the ndiswrapper-utils package from the CD and set it up by following [http://www.ubuntulinux.org/support/documentation/howto/ndiswrapper](http://www.ubuntulinux.org/support/documentation/howto/ndiswrapper). Whilst following the instructions I recieved no errors. My wireless network card is a Belkin F5D7000ea and the driver I'm using is bcmwl5.inf from the install CD. I setup the IP address, subnet mask, gateways and preferred/alternate DNS servers up in the network settings. The card is being recognised it's just not able to connect to the internet. I would appreciate any help that anyone can give.

Thanks!  :D 

Darren

---

### Post by tmowerman on 2005-04-01
I had to use the bcmwl5a.inf from the cd. (Note the a)

i also had to manually add a section to /etc/network/interfaces

```
iface wlan0 inet dhcp
name Wireless Lan Card
wireless_essid <youressid>

```

Then you should be able to configure from the networking in system menu

Tim

---

### Post by bottledwater on 2005-04-01
[QUOTE=tmowerman]I had to use the bcmwl5a.inf from the cd. (Note the a)

i also had to manually add a section to /etc/network/interfaces

```
iface wlan0 inet dhcp
name Wireless Lan Card
wireless_essid <youressid>

```

Then you should be able to configure from the networking in system menu

Tim[/QUOTE]

I don't have that file, would you mind sending it to me? (bottledwater@gmail.com)

Thanks

---

### Post by bottledwater on 2005-04-01
I got it working  :-D All I had to do was change a 1 to a 0 in a config file  :shock:  Easy as that

---

### Post by shayan on 2005-04-15
I'm having the same problem.
1) did you have to use the bcmwl5a.inf? or was bcmwl5.inf enough
2) which config file did you use to change and what exactly did you do to bring it up again?

Thanks!

---

### Post by spd106 on 2005-04-16
This is a common problem with the belkin wireless cards, there are various howtos on this site that are a good starting point.
First I suggest looking at 

[http://www.ubuntulinux.org/wiki/HardwareSupportComponentsWirelessNetworkCards](http://www.ubuntulinux.org/wiki/HardwareSupportComponentsWirelessNetworkCards)

This isn't complete by any means but it provides a lot of different solutions found by people with similar setups.
check to see if the light on the card comes on. If not you may have to edit the /etc/ndiswrapper/bcmwl5/xxxxx.conf file by changeing the radiostate from 1 to 0.

This works for me in Hoary.

In Warty the bcmwl5.inf driver didn't work so I found another driver from the information on the above link. This one was for the dell truemobile 1350 and called bcmwl5a.inf.

Sorry if i've just confused the issue.

---

### Post by topicalanalgesic on 2005-05-02
I have the rev.3 model of the Belkin 7000 card which had previously worked perfectly under several other distros.  When I installed Hoary though, it would not function.  The card was detected with "ndiswrapper -l" and even "lspci", but it wouldn't turn on.  I tried both the drivers from the belkin cd as well as the Dell drivers from their website.  Neither of them seemed to do the trick.

I literally was pulling my hair out trying to get this thing to work correctly.  So as a last ditch effort, I tried changing the 1's to 0's in the .conf files within the /etc/ndiswrapper/XXX directory as suggested in this forum.

That did the trick nicely!!!

Thanks guys!

---

