---
title: "Cisco VPN connecting to network"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by cierin on 2008-12-22
I realize that there are a lot of threads about Cisco VPN issues, but I looked through a bunch of them and couldn't find anything that addressed the problem I'm having.

I downloaded the VPN fine, with the patch and everything, but I can't figure out how to connect to the network.

In Windows, the client says:
Connection Entry: hcvpn
Host: vpn1-public.haverford.edu
Transport IPSec/UDP

When I click on it (in the windows client), it then asks me for my username and password.

How do I go about connecting in ubuntu? Apologies if some of the above info is useless, I don't know anything about VPN, so I wanted to give all the info I had.

---

### Post by Benic on 2009-02-20
What you need is a pcf file containing the connection information. You can probably download this file from the university website. Then you put the pcf file in your vpn profile folder, which is /etc/CiscoSystemsVPNClient/Profiles in my case. 

To connect, you need to start Cisco VPN first:

```
sudo /etc/init.d/vpnclient_init start 
```

Then you use your connection profile:

```
vpnclient connect <your profile>

```

After that Cisco VPN asks you to type your user name and password. If you're using a firewall, you will have to find the right settings to enable PPTP tunnelization and be able to use internet. I use guarddog, so I can help you with it if you're having trouble.

---

