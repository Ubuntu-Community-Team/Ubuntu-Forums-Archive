---
title: "Firewall Rules for VPN Connection Only?"
date: 2014-02-24
forum: Networking &amp; Wireless
---

### Post by genivasla on 2014-02-24
I'm trying to use GUFW to setup firewall rules that only allow browsing when connected to an OpenVPN connection. So far I'm not having much luck. I have the Income and Outgoing settings to Deny, and have tried various rules to allow the VPN ports and/or IP.

Funny thing is I'm able to establish a VPN connection through Network Connections when I add the rules, but I am unable to browse. Without the rules, I'm unable to make the VPN connection... so it is working at some level. I just can't browse :(

Anyone have a working solution to deny browsing when the VPN connection drops or isn't established?

---

### Post by tomearp on 2014-02-24
Your traffic is directed over the VPN via the routing table and will be checked by the firewall. You will need to open outgoing port 53 UDP for DNS lookups and outgoing ports 80/443 TCP for HTTP/S.

I'm not familiar with OpenVPN but I'm assuming there is some way that a script can be executed when the VPN connects and disconnects. To achieve your desired effect you would need to open the ports above when the VPN connects and close them again when it disconnects.

---

### Post by genivasla on 2014-02-24
That's it! I had all of that except Port 53 UDP. Now just need to figure out how to close those ports when VPN is disconnected like you said.

---

### Post by genivasla on 2014-02-25
Does anyone know how to create a script that will close these ports when the OpenVPN connections disconnects or drops? Thanks!

---

### Post by SeijiSensei on 2014-02-25
I don't know how NetworkManager does it, but the standard configuration file for OpenVPN includes a ["down" directive]("http://askubuntu.com/questions/28733/how-do-i-run-a-script-after-openvpn-has-connected-successfully") that runs a script when the connection is closed.  In your case, you would probably want two sets of firewall rules and run the one with the ports closed after disconnecting.

I couldn't immediately determine where NM writes its OpenVPN configuration file.  Perhaps someone else might chime in here.

---

### Post by genivasla on 2014-02-27
> **SeijiSensei said:**
> I don't know how NetworkManager does it, but the standard configuration file for OpenVPN includes a ["down" directive]("http://askubuntu.com/questions/28733/how-do-i-run-a-script-after-openvpn-has-connected-successfully") that runs a script when the connection is closed.  In your case, you would probably want two sets of firewall rules and run the one with the ports closed after disconnecting.

I couldn't immediately determine where NM writes its OpenVPN configuration file.  Perhaps someone else might chime in here.

Oh nice! Thanks for the tip. I'm a linux noob, so not sure how to go about making that script. If anyone can point me in the right direction, I'd appreciate it.

Thanks!

---

