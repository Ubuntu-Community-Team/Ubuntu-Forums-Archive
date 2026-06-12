---
title: "VPNC won't establish connection with VPN server, although it is pingable"
date: 2008-03-01
forum: Networking &amp; Wireless
---

### Post by Buzzdee on 2008-03-01
Hello, 

I'm using Gutsy x64 on a Thinkpad T61p and would like to establish a connection to a VPN server with vpnc and network-manager-vpnc. When I let network-manager try and do this, it asks for passwords, then it takes some time, then it reads
"VPN Connect Failure
Could not start the VPN connection 'xx' due to a connection error.

The VPN login failed because the VPN program could not connect to the VPN server"
My first idea was a firewall issue, so I tried to ping the server, successfully however. I'm using a Siemens SE551 router.

Does someone have an idea on how to tackle this problem?

Bastian

---

### Post by Buzzdee on 2008-03-01
My matlab also is not able to connect to the remote license server:

License checkout failed.
License Manager Error -15
MATLAB is unable to connect to the license server. 
Check that the license manager has been started, and that the MATLAB client machine can communicate
with the license server.

Troubleshoot this issue by visiting: 
[http://www.mathworks.com/support/lme15b](http://www.mathworks.com/support/lme15b)

Diagnostic Information:
Feature: MATLAB 
License path: /usr/local/matlab75/etc/license.dat:/usr/local/matlab75/etc/*.lic: 
FLEXnet Licensing error: -15,570. System Error: 115

I think there might be some networking issues with my router/pc. (Un?)fortunately, I can ping matlab's license server as well. 

Any ideas? I just don't have a clue what I could do here, I'm not into networking...

---

### Post by johnbl on 2008-03-01
Have you checked for port redirection?

I'm using tight vnc to access my MS based office system and whilst on the SAME network it's ace. But to get to my server from outside - WAN -- documentation spells out the need to enable port redirection. Could this be your problem?

I'm very much a newbie myself on these things however but if it serves the purpose, would recommend you have a look at tightvncserver

John

---

### Post by Buzzdee on 2008-03-02
There seem to be two different sorts of vpn:

Here's a translation of the information I found on the internet:
For PPTP the router has to let pass PPTP-requests. Therefore, the IP-protocol 47 (not to be confused with the TCP/UDP port 47!) and the TCP port 1723 have to be opened for access.
L2TP needs the UDP ports 500 and 1701, as well as the IP protocol 50. This combination causes trouble because it is not NAT-able.

I have no idea what these IP protocols are and can't find an option on my router to enable them.

Bastian

---

### Post by zorkerz on 2008-03-16
im using network-manager-vpnc in 64 bit hardy. As late as thursday of last week i was able to connect to my school's vpn. When i attempted today I get the same error "VPN Login Failed".

The vpn settings are all saved in a file that has not been changed. Im not sure if there was a network-manager-vpnc update or some other that could affect this.

Any ideas how I could find out what is going wrong?

---

