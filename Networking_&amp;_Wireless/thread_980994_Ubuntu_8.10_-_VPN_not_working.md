---
title: "Ubuntu 8.10 - VPN not working"
date: 2008-11-13
forum: Networking &amp; Wireless
---

### Post by jshair on 2008-11-13
I previously had ubuntu 8.04 installed on an external HD and was using kvpnc to VPN into the office. Life was good...but a little slow booting from the HD.

After my trial w/ 8.04, I decided I wanted to take the dive and completely remove XP from the laptop and install ubuntu. Yea!!!! Upon reading mixed reviews on 8.10, I still decided to move forward installing 8.10. Everything to date has been working great....minus VPN.

After installing a vpn client (sudo apt-get install network-manager-vpnc), I imported the same pcf file via the network manager UI (quite nice!). Every time I tried to connect, it just failed with only a message stating that it failed.

I then tried to install kvpnc and import the same pcf file that worked on 8.04. Kvpnc said that it connected. However, I was not able to reach any internal sites AND kvpnc would automatically disconnect after a certain length of time...with again, not real error message.

I've read the forums and so far, nothing reported in the forums has worked for me. How can I debug the situation to find out where the problem truely lies? Has anyone gotten VPN working successfully in 8.10?

Help! I don't want to revert back to 8.04 and this is my only & very large stumbling block.

---

### Post by Muflon on 2008-11-13
Hi jshair

I don't know if yours is exactly the same problem but you may wish to contribute to this thread.

[http://ubuntuforums.org/showthread.php?t=974092](http://ubuntuforums.org/showthread.php?t=974092)

Muflon

---

### Post by jshair on 2008-11-13
Thanks Muflon. I reviewed the post. If I could get connected, I might experience the same problem. However, using Cisco VPN, I can't even get connected.

When adding the route, sounds like the IP is to be that of the VPN or IPs accessible via the VPN. Is that correct? 192.168.1.x is within my local network.

Otherwise, any clue how to debug why Cisco VPN is not working? After I attempt to login, all I get is 'VPN connection failed'. I don't even know where to begin to find the 'true' error or root cause.

---

### Post by gjkuijn on 2008-11-14
I have the same problem as JSHair: VPN won't connect at all. Connecting & not being able to ping would be a huge improvement.
The error message is a very general "connection failed", which suggests some setting-problem. Like incorrect username or password. But I'm using exactly the same settings as I did with Ubuntu 8.04.

---

### Post by Jakonavitch on 2008-11-14
Hey,

i am experiencing the same problem, i spoke to the folks at work who run the VPN Shop and they said that my user or ip wasn't being denied and hadn't even registered in their logs.  so the VPN isn't even reaching the server. thought that might be useful for debugging.

---

### Post by gatman3 on 2008-11-29
I am having problems with kvpnc in 8.10 as well, but only on the 64-bit install.  The 32-bit 8.10 works fine.  When I import a .pcf file, it does not seem to make use of the encrypted group password, so it prompts me for a group password (which I don't have) whenever I try to connect.

Note that I have had success with the command line vpnc-connect.  But it would be nice to connect with two mouse clicks instead of a shell.  In any case, you might see if you have the same problems with the command line.

---

### Post by DocForbin on 2008-12-28
FWIW, I had to enable point-to-point encryption (MPPE) in advanced to connect to my office. Don't recall doing that in previous versions of ubuntu, maybe it used to be the default for pptp.

---

