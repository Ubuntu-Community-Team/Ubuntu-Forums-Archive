---
title: "Cisco VPNC"
date: 2010-03-23
forum: New to Ubuntu
---

### Post by golfnut324 on 2010-03-23
New-new-newbie here. Trying to make the "big" move away.

I am running Ubuntu 9.10 and have set up a Cisco vpn connection by using Network Connections and importing the .pcf file. It works nicely but with two problems: 1) Once I initialize a session, I can't run any other wireless networking tasks (i.e. web browser or email client) and 2) After I close the vpn session, I can't re-establish another vpn connection without rebooting. Note: closing the vpn session does resolve issue #1.

Does anyone have an idea on how I can fix these issues. Please go slow with lots of details since I'm still groping in the dark here.

Thanks all, very much!

---

### Post by rickzoll on 2010-03-25
VPN creates a tunnel to your chosen site.  I think you will find that you can get to your office site (assuming you connected to your office), and from your office site you can get to what you normally get to from there.  That's just the definition of Virtual Private Network.  If other sites were in the mix, it would not be a private network.  So - turn it on when needed and off when you are done.

---

### Post by jimv on 2010-03-25
What's happening is that your IP routes are getting messed up by the VPN client.  To fix this, configure the VPN connection --> Edit --> IPv4 Settings --> Routes --> Tick “Use this connection only for resources on its network”

---

### Post by golfnut324 on 2010-03-26
> **jimv said:**
> What's happening is that your IP routes are getting messed up by the VPN client. To fix this, configure the VPN connection --> Edit --> IPv4 Settings --> Routes --> Tick “Use this connection only for resources on its network”
 
 
 
Thanks for the guidance. I will try that out. unfortunately I committed the big noob sin! I tried to run update to install Ubuntu 10.04 and have messed the system. I'm starting new thread to see if I can get help. When fixed I'll try the "tick".
 
Thanks again.
 
and yes, I've learned my lesson. wait for several weeks _after_ distro release!

---

### Post by golfnut324 on 2010-03-28
> **jimv said:**
> What's happening is that your IP routes are getting messed up by the VPN client.  To fix this, configure the VPN connection --> Edit --> IPv4 Settings --> Routes --> Tick “Use this connection only for resources on its network”



Feedback for anyone that comes across this thread with same problem: 

First - jimv's solution (quoted above) was spot on! I thank you for that.

Second - after I figured out that I installed Ubuntu 9.10 using wubi, I simply rectified my earlier sin of trying to update to 10.04 by running wubi again.

Third - I followed the instructions at link below to install the Cisco client. It's a simple and fast matter now to launch my vpn connection.

Thanks again for the help.


[http://www.lamnk.com/blog/vpn/how-to-install-cisco-vpn-client-on-ubuntu-jaunty-jackalope-and-karmic-koala-64-bit/](http://www.lamnk.com/blog/vpn/how-to-install-cisco-vpn-client-on-ubuntu-jaunty-jackalope-and-karmic-koala-64-bit/)

---

### Post by sandeepy on 2010-03-28
you could alternatively use "route" command to modify the system routing tables. Just set the default route to the gateway of your home LAN.

E.g.

route add default gw 192.168.1.1 dev wlan0

---

