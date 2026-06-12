---
title: "VPN Location"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by lilredcougar07 on 2010-03-22
Hey all, I am needing a little help. I'm trying to set up my VPN for my school (they use Cisco Clean Access). After a lot of searching on the internet and school stuff, I thought I finally had it. Here's the output I got:

> haleymo@haleymo-laptop:~$ sudo vpnc-connect --enable-1des --local-port 0
Enter IPSec gateway address: vpn.truman.edu
Enter IPSec ID for vpn.truman.edu: truman
Enter IPSec secret for [EMAIL="truman@vpn.truman.edu"]truman@vpn.truman.edu[/EMAIL]: 
Enter username for vpn.truman.edu: hbe2464
Enter password for [EMAIL="hbe2464@vpn.truman.edu"]hbe2464@vpn.truman.edu[/EMAIL]: 
RTNETLINK answers: File exists
VPNC started in background (pid: 3799)...
haleymo@haleymo-laptop:~$ ls
I can't find where the VPN is though! I looked in Network and got nothing. I've looked all the obvious places I think, so if someone could just help me out real quick, I'd really appreciate. Thanks!

---

### Post by 2hot6ft2 on 2010-03-22
Have you tried Right clicking on the network-manager-applet in the top right panel and selecting Edit Connections then the VPN tab and setting it up that way?
Beyond that I don't know.

---

### Post by rickzoll on 2010-03-25
The pid is the running VPN.  If you try in a browser to get to your site, I think you will be successful.  In fact if you try to browse to other locations you will find they are not available.  The problem that you are having is the same one I am having is that the Network Connections does not show the VPN as active and you cannot shut it down (or re-start it from there).  This was all working properly in a previous release and I'm searching now for a solution.  BTW, you can sudo kill pid to close the vpn to access other networks.

---

