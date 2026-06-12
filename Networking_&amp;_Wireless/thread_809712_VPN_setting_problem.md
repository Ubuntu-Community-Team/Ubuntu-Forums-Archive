---
title: "VPN setting problem?"
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by zggame on 2008-05-27
I recently put Xubuntu 8.0.4 into a Dell latitude c610 PIII w/Dell TrueMobile 1150 802.11b miniPCI.  Fortunately it works out of box.  But it does have some weird problem.  Here is one.  

I tried to connect to the campus wireless network.  I can get in with the normal unsecured connection with my ID/passwd.  Then I tried to use the VPN for that.  According to [http://www.cites.uiuc.edu/vpn/otherclients.html]("http://www.cites.uiuc.edu/vpn/otherclients.html"), it use PPTP.  So I installed the network-manager-pptp package and set it up according to the direction. (I only set the gateway and leave everything else untouched. )  According to [another page]("http://www.cites.uiuc.edu/vpn/dl-winv.html"), we used the MS-CHAP v2.  It seems the pptp package use this version 2 automatically.  Anyway, I cannot get in with VPN.  I always get the information 

"VPN Connect Failure

Could not start the VPN connection 'test' due to a connection error.

VPN Connection failed"

On the other hand, I can get through with the same VPN via wired network. So I am fairly sure that VPN is set correctly.  

I tried to find some log, but I cannot find the log of NetworkManager in /var/log.  Do I need to turn it on or is it somewhere else? 

 :confused:

Any thought on this?   Thanks.

---

### Post by zggame on 2008-05-28
Well. It seems to be the problem of Firestarter firewall. I got it through by disabling the firewall.

---

