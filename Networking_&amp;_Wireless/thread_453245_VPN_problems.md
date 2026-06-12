---
title: "VPN problems"
date: 2007-05-24
forum: Networking &amp; Wireless
---

### Post by zenkaon on 2007-05-24
Hello,

I would like to connect to my University network using VPN. They use MS PPTP which requires 128 bit MPPE encryption with MS-CHAP-v2. I am using kubuntu 7.04. If I click on KNetworkManager then I get VPN options and I believe that I have setup the gateway etc correctly. However, when I try and connect I put in my username and password for the network but /var/log/syslog says that:

NetworkManager: <information>^IWill activate VPN connection 'Uni', service 'org.freedesktop.NetworkManager.ppp_starter', user_name 'john', vpn_data 'ppp-connection-type / pptp / pptp-remote / student-vpn.bris.ac.uk / usepeerdns / yes / encrypt-mppe / yes / encrypt-mppe-128 / yes / compress-mppc / yes / compress-deflate / yes / compress-bsd / yes / ppp-lock / yes / ppp-auth-peer / yes / ppp-refuse-eap / no / ppp-refuse-chap / no / ppp-refuse-mschap / no / mtu / 1416 / mru / 1416 / lcp-echo-failure / 10 / lcp-echo-interval / 10 / ppp-extra /  / ppp-debug / yes / usepeerdns-overtunnel / yes / routes /  / use-routes / no', route ''.

and then I get a bad user name or password error. The user name that I enter into the connection GUI from KNetworkManager is NOT john. That is my user name on my laptop, my university username is something different (the username that I enter into the GUI).

Can someone tell me why KNetworkManager is passing the wrong username? and more importantly, how to fix it?

Cheers
John

---

### Post by scruffyminds on 2007-05-25
The "username" entry in syslog showing your laptop username is normal....it's logging the user that started the pppd daemon, not the username used to connect to the VPN.  If your VPN login includes a Windows domain, you need to enter both the Windows domain and user name in  the dialog box like this:  MyWindowsDomain\MyWindowsUsername.   Make sure you use the '\' slash and not the '/' slash.  Also, if you are connecting from behind a home router (like Linksys), make sure the router isn't blocking the GRE packets (on my Linksys router, it's Advanced->Filters->Allow PPTP Passthru)

---

