---
title: "Remote desktop crossing router with dynamic IP"
date: 2007-03-19
forum: Networking &amp; Wireless
---

### Post by dummybert on 2007-03-19
Hi

I've tried using the remote desktop with my Ubuntu accesing from XP with RealVNC and it works fine in a local network. I'd like to do the same from job using public networks (internet). I guess I should do something like this:

1 Config NAT in the router so the packets adressing the VNC port should be redirected to my Ubuntu machine address
2 Add some kind of security and encryption, as I'm using public networks
3 Connect to the public IP address from the router with VNC

Questions:
1 Which port is used for the remote desktop application?
2 I've only seen the "Ask confirmation" and "Passwd" in the remote desktop configuration in Ubuntu, can I add some kind of encryption to the connection?
3 How can I know the router's public IP from job?

If anyone has already done this and can help I'd be really thankful. Thanx in advance.

---

### Post by dmizer on 2007-03-19
i wouldn't suggest trying to go through the trouble of making that work via internet for several reasons, not the least of which is security.  but, even though you can pipe the vnc through an encrypted tunnel via vpn, the effort is beyond what i have ever felt the need to put into it, so i don't know how.

also, (more likely than not) speed is going to be unbearably, painfully, and almost unusably slow.  unless you have a super highspeed connection on both ends, with low net traffic, you're going to experience some tortuously bad lag.  (depending on the size of your office) you'll also probably end up showing red flags on the network monitoring equipment for the gigantic increase in your bandwidth usage.

finally, if you're connecting from a work pc, you're likely to find that most outgoing ports are going to be blocked, so even though you can configure your home router and ubuntu server to listen on a different port than default, you may have difficulty finding one that works.

what is it that you are trying to do from work that causes you to desire a direct gui connection to your ubuntu machine?  there may be an easier and more secure method than vnc.  for example, if you just want to listen to music, you can connect via ssh, and get a command line prompt, open rhythmbox (or your music player of choice) and have it run on your work computer as if it were a program you opened on your work computer.

instead of trying to learn your ip address from work, i suggest setting up a free dynamic dns domain for your server at home.  you can set that up here: [http://www.dyndns.com/services/dns/dyndns/](http://www.dyndns.com/services/dns/dyndns/) ... then instead of trying to connect to an ip, you can connect with a url just as you would with a website.  also, most modern routers support automatic updating of dyndns domains, so if your ip address changes, your router should be able to update your dyndns account automatically.

---

