---
title: "Bittorrent traffic, how can I run http tunnel under block of http proxy?"
date: 2009-09-05
forum: New to Ubuntu
---

### Post by sebjob on 2009-09-05
Hi 
Am a victim of a internet provider that promised me unlimited access, though only allows ssh 22, domain 53 and http port 80. Plus blocks all bittorrent traffick so it gets incredibly slow. What I understand I need to do, from reading on the internet, is to create a tunnel to an external ip server that will help me tunnel the http traffic to allow bittorrent. Found the program httptunnel, but extremely confused from it all. Do the server need to be Linux(running Easypeasy)? Does anybody have the knowledge to save me out of this frustration (bittorrent 5kb s)?:confused: How can I create an http tunnel to avoid the scam of my provider?

---

### Post by halitech on 2009-09-05
what bit torrent client are you using? With most, there is an option to change what ports it uses. just change it to different ports. (I use the 50000 - 60000 range and get good speeds)

---

### Post by lovinglinux on 2009-09-05
Switch to another ISP.

---

### Post by falconindy on 2009-09-05
> **lovinglinux said:**
> Switch to another ISP.
I'm with this. Are you sure you weren't mislead? Is there anything in your contract about **only** these ports being available? In 2007, Comcast was sued for blocking ports when they promised unlimited access to customers.

Source: [http://www.wired.com/threatlevel/2007/11/comcast-sued-ov/](http://www.wired.com/threatlevel/2007/11/comcast-sued-ov/)

---

### Post by sebjob on 2009-09-06
yeah, not a complicated contract, so was mislead. On the test of ports in network tools in Easypeasy, and on sites that provide it on the internet. Tried open ports and also in firewall;
sudo iptables -A INPUT -p tcp --dport 61500 -j ALLOW
sudo ufw allow 61500

---

### Post by sebjob on 2009-09-06
halitech, using transmission bittorrent client and been trying amule

lovinglinux, its an african thing. Internet traffic bought per megabyte from the us, so internet traffic sold per megabyte. Would have no problem with them limiting my traffic if they said so in advance, though they did big commercials to pay a bit extra to get unlimited. checked speed through speed tester, and its fine but blocks bittorrent traffic to make it slow to the extreme...

oh, and of course general slower speed than promised in average, but still quite high, but that one I expected. Its the bittorrent speed that is extremely frustrating

---

### Post by sebjob on 2009-09-06
thanks for the swift reply guys

been trying httptunnel, though confuses me, and been reading lots on proxies and tunnels...gSTM and differrent VPN tunnel programs offered by Ubuntu...also changed port to the ranges recommended, and tried to ignore unecrypted peers, though no luck

---

