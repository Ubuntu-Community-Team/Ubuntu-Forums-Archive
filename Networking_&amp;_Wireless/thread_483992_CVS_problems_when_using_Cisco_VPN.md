---
title: "CVS problems when using Cisco VPN"
date: 2007-06-25
forum: Networking &amp; Wireless
---

### Post by tempest on 2007-06-25
I am using Feisty and Cisco's VPN client. I can connect to my company's VPN and use most of the necessary tools to do my job. I use pidgin to instant message. I use Firefox to browse the company's intranet sites. Where I have trouble is in two places. I can connect with Evolution or Thunderbird to the exchange server and retrieve mail, but when I try to send mail, I get a message saying that an error occurred. Another problem is that I can check out source code all day long from CVS and I can do a cvs status, or cvs log on a single source file in a directory by itself, but if there are more than a few files in the directory those commands hang and I never get a response. If I try to do a cvs update I get the same hang with no response.

kernel: 2.6.20-16-generic
vpn: Cisco vpn client (vpnclient-linux-x86_64-4.8.00.0490-k9.tar.gz)

I am also using a patch to the vpn client that I got from elsewhere in these forums, it is 
vpnclient-linux-2.6.19.diff.

Any help is appreciated. Thanks,

---

### Post by Maxtorm on 2007-06-25
Have you tried replicating the problem using vpnc (available via the repos)?

---

### Post by tempest on 2007-06-26
I went ahead and unplugged my machine from my Linksys befsr81 router and plugged it directly to the cable modem. Now the vpn works fine and I can do everything. I am not sure what is going on. I had the machine set up as a DMZ through the router, I thought that would have fixed the problem. The really strange thing is that I do not have any problems behind the router when using the windows Cisco VPN on the same machine (dual boot). Any thoughts?

---

### Post by qubithaze on 2007-06-28
I'm having exactly the same problem, but with a belkin F5D7230-4 6000.  Bypassing the router and plugging directly into my cable modem fixes the problem.

I can only get vpnc connections to stay up for about 15 minutes,  so it's not really usable for me.

---

### Post by Maxtorm on 2007-06-28
Now this is ringing some bells.  I had a vpnc connection that was connecting, but would not stay up for very long.  The problem was that after a certain amount of inactivity, the router (a cheapo Linksys) was breaking the NAT, which in turn broke the tunnel.

The solution was to use the --nat-keepalive option with vpnc.  As you might guess, the option forcibly sends data every x seconds to keep the NAT ..well.. alive.  **If** this is the solution, then there is a problem because --nat-keepalive is not an option with vpnc in the most recent version.  My solution, at the time, was to roll back to version 0.3.x.

However, I just installed the most recent version of vpnc and it has a DPD (Dead Packet Detection -- which is apparently responsible for the behaviour I was experiencing) option.  Sooo...  assuming you are running 0.4.0, add
```
--dpd-idle 10
```
to your vpnc invocation line and see if that solves it.

---

### Post by tempest on 2007-06-28
Just an update. My Linksys befsr81 router is a very old version 1.0 of that model. I checked the Linksys website and they had a firmware update so I installed it. Now my cisco vpn client connects with no trouble at all. Here is a clip from the release notes on the firmware update:

Here are the notes from the firmare release:
[http://www.linksys.com/servlet/Satellite?blobcol=urldata&blobheadername1=Content-Type&blobheadername2=Content-Disposition&blobheadervalue1=text%2Fplain&blobheadervalue2=inline%3B+filename%3Dbefsr81v2_fw_ver.txt&blobkey=id&blobtable=MungoBlobs&blobwhere=1130776253046&ssbinary=true&lid=7527927648B09](http://www.linksys.com/servlet/Satellite?blobcol=urldata&blobheadername1=Content-Type&blobheadername2=Content-Disposition&blobheadervalue1=text%2Fplain&blobheadervalue2=inline%3B+filename%3Dbefsr81v2_fw_ver.txt&blobkey=id&blobtable=MungoBlobs&blobwhere=1130776253046&ssbinary=true&lid=7527927648B09)

Now if I could only get the cisco vpn client to work wihtout having to disable firestarter.

---

