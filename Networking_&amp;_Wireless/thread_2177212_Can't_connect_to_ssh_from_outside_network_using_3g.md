---
title: "Can't connect to ssh from outside network using 3g"
date: 2013-09-27
forum: Networking &amp; Wireless
---

### Post by Michael_Kolonay on 2013-09-27
I have been working on connecting my android powered phone to my home network via ssh.  I have the server up and running working with public keys, and I am able to connect to if from the phone using connectbot.

From outside the network I have the phone pointed at my router using dlinkddns.com; however, when I try to connect I get an error message:
[B]Connection Lost
failed to connect to [myddnsserver].dlinkddns.com/[the-ipaddress-of-my-servercomputer] by port 22: connect failed:  ENETUNREACH (Network is unreachable)


[/B]I have tried: **sudo tcdump -n -nn -tttt -i wlan0 port 22** and seen that no traffic is coming through during my log in attempts.

Then I tried entering the external ip manually instead of relying on the ddns and the connection worked.  However, when I log into my account on dlinkddns.com I see that the ip listed for my account is correct.
[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]The strange thing is that the whole thing was working yesterday and this morning without any problems.  Any ideas what my issue could be?  [COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]

---

### Post by Lord Nelloz on 2013-09-27
Did you set up port forwarding in your home router?

---

### Post by Michael_Kolonay on 2013-09-27
Yes. Forgot about that bit; I have port 22 open and directed to port 22 using TCP.

---

### Post by Michael_Kolonay on 2013-09-27
Update: I have been doing some more digging and I have come up with a little more information:

By using various apps I have determined that I can ping the external ip address of my home router, that port 22 is indeed open on that address and that my dlinkddns address is pointing at the right internal address.

I will also add that when I successfully connect to the ssh server over the wifi from the home network I am still using the ddns address.

---

### Post by 7182818 on 2013-09-27
I think the problem is with your DNS entry.  Your internal address is probably not a routable one (like 192.168.x.x) so the traffic outside your network won't know how to reach your home network.  Instead, the DNS entry should resolve to the public IP address of your router, and then from there you will have configured your port forwarding such that everything coming in port 22 on your router gets mapped to the internal IP address of your server, so the router will do NAT and get the packets to your server.  So, I would try changing your DNS entry and see if that works.

---

### Post by Michael_Kolonay on 2013-09-27
Hockeyplayer363,

Sorry, I can see how I was unclear.  The DNS entry is referring to the external ip.  What I meant to say is that the address must be being reached since it is aware of and reporting the internal ip and port it is supposed to be forwarded to by the router.  As far as I know until my phone reaches the router it is unaware of its final destination.

---

### Post by Michael_Kolonay on 2013-09-27
Actually, sorry again.  Turns out you were right.  The interface on the dlinkddns website confused me.  It wasnt until I logged onto it using my phone on 3g that I noticed what I thought was the address it was uasing was actually the address I was using to connect to the site (until then I had always seen the address of my router -- which is exactly what I wanted). Silly mistake indeed.

---

