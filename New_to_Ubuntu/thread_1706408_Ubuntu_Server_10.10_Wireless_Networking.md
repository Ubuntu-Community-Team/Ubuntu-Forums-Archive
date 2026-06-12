---
title: "??Ubuntu Server 10.10 Wireless Networking??"
date: 2011-03-13
forum: New to Ubuntu
---

### Post by GeissT on 2011-03-13
Hey,

So ive recently tried out Ubuntu Server 10.10, install went well except for configuring with DHCP, for some unknown reason, so i chose configure later.

So now I have no idea on how to configure wireless devices via the command line.

The ifconfig command produces the following device:

lo

It does not yield any eth0 or wlan0 so im stumped.

Any help would be greatly appreciated with no flamers or trolls if possible. Thanks in advance.

GeissT

---

### Post by grahammechanical on 2011-03-13
I do not know if this will help but

sudo ifup eth0    = switch on eth0

sudo ifdown eth0  = switch off eth0

sudo ifconfig wlan0 up = switch on wireless 0

sudo ifconfig wlan0 down  = switch off wireless 0

Here is a link to a trouble shooting guide

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

There is a section on commands.

Regards.

---

### Post by GeissT on 2011-03-13
sudo ifup eth0

The above command showed the following results

Ignoring unknown interface eth0=eth0

Whilst this command:

sudo ifconfig wlan0 up

Returned: 

wlan0: ERROR while getting interface flags: No such device

NOTE: I have checked and the laptop i am working on has wireless turned on, but. I tried pressing the button to disable and then again to enable and i got:

ipw2200: Failed to send CARD_DISABLE: Command timed out.

It is a really old laptop (Maybe 6 years) should i try downloading and installing 9.10 because I have had 9.10 running on there fine....

Thanks for your help.

GeissT

---

### Post by GeissT on 2011-03-13
Never mind now, i'm just going to use ubuntu desktop and put a whole bunch of server software on there.

Thanks guys.

---

