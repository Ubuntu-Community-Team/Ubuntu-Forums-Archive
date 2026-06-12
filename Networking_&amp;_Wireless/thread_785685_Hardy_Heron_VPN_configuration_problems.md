---
title: "Hardy Heron VPN configuration problems"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by sanjarjalilov on 2008-05-07
Hello,

have recently downloaded the Hardy Heron Desktop CD and had a chance to try it today on brothers PC.
The task was to establish a VPN connection a local wifi ISP.
The configuration looks like this:

[PC] o----ethernet---o [black-box (wifi-modem?!)] o-----radio---o [ISP]

Done fresh install of Hardy Heron Desktop.
Downloaded and installed network-manager-pptp (+pptp etc. etc.) as described here [http://tipotheday.com/2008/04/29/connect-to-windows-vpn-server-pptp-with-ubuntu-hardy-heron/]("http://tipotheday.com/2008/04/29/connect-to-windows-vpn-server-pptp-with-ubuntu-hardy-heron/")
But somehow the "VPN Connections" does not even show up in Network management applet. There is only "Manual configuration" setting available.
In windows it was very easy - just run the wizard new "create VPN connection" - fill in the values and voila. Now, after 6hrs of struggle and no VPN I am completely lost.

Any advice would be helpful!
:confused:

---

### Post by Tamerz on 2008-05-07
Same problem here. I noticed other people posting about the same thing. One person said rebooting fixed it but that hasn't helped me out. The packages are installed, I just don't get the VPN option in connection manager.

---

### Post by sanjarjalilov on 2008-05-07
Hi,
I have found someone mentioning to put "Wired connection" to "Enable Roaming" flag on and that "VPN connection" menu will show up.
Can anyone check it if it works?

[update]
Current Network Manager in Hardy Heron does not support "Static IP". Setting static IP will not show "VPN Connections" menu in the Network Manager applet.

What to do if the ISP has provided a static IP with which VPN connection should be made?

---

### Post by sanjarjalilov on 2008-05-08
With static IP
Setting Wired Connection to "Enable roaming" helps.
VPN setting appears in the Network Manager and in two steps MS PPTP VPN can be established successfully.

---

### Post by Tamerz on 2008-05-08
Both my wireless and wired interfaces are set to roaming. The menu doesn't show up either way. I've rebooted, everything else I can think of.

I created a bug report:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/228256]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/228256")

---

### Post by Tamerz on 2008-05-08
Not sure what changed but it shows up now for me.

---

