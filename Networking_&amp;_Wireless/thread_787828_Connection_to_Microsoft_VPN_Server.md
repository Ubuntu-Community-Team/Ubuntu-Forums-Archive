---
title: "Connection to Microsoft VPN Server"
date: 2008-05-09
forum: Networking &amp; Wireless
---

### Post by AlastairBrown on 2008-05-09
Trying to use nm-applet to configure and connect to a Win 2003 server instance of VPN.  Ive seen loads of articles suggesting different clients and params but had no joy.  There are two distinct patterns :-
With Require MPPC unset I see traffic to the VPN server but none back from the VPN server (Wireshark) then get this "Could not start the VPN connection 'name' due to a connection error VPN Connection failed.

Articles have suggested that "Require MPPC Compression" is needed, with this set there is no traffic to or from the VPN server and the message "Could not start the VPN connection 'name' due to a connection login failure Bad Username or Password" as there isnt a single packet sent or received from the VPN server find this hard to believe.

Any ideas greatly appreciated.  Been racking my brain for a couple of months now!

Dont know if it's significant but wireless often drops out after connecting with MPPC set!

---

### Post by Orestez on 2008-05-15
Ive basically got the same problem, the error coming up sporadically. Sometimes it helps if I enter the same login informationa again, lately it doesn tho. Im connected to the internet via a wired 802.1x connection...

---

### Post by ibaquez on 2008-06-04
Same problem here with MPPC, found this in my syslog:
Jun  4 00:57:53 Pavillion pppd[8703]: unrecognized option 'require-mppc'

As my VPN requires MPPC it shows exactly:
VPN failed for service 'org.freedesktop.NetworkManager.ppp_starter', signal 'LoginFailed', with message 'Bad Username or Password'. 

Why is the option "Require MPPC" in the network applet but pppd is not prepared to handle it!!!

Ive read that is a thing about copyright, Ill try to apply a patch and post the result, but I'm skeptical

---

