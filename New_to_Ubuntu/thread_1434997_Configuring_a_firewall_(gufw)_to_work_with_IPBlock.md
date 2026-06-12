---
title: "Configuring a firewall (gufw) to work with IPBlock and Vuze"
date: 2010-03-21
forum: New to Ubuntu
---

### Post by josephuser on 2010-03-21
I'm using Ubuntu 9.10 along with downloading torrents in Vuze. To secure my connection, I'm running IPBlock with all the relevant blocklists, AND I'd like to use a firewall (here, gufw). It appears to me that when I start gufw and open the port Vuze is listening on (here, 29165), Vuze is still reporting a NAT/Firewalled problem.  Testing port 29165 ...  NAT Error - Connect attempt to X.X.X.X[I deleted IP address for this thread]:29165 (your computer) timed out after 20 seconds. This means your port is probably closed.  The problem is that I'd like to have both IPblock AND a firewall working together, and I'd like to make sure that IPblock is blocking properly.  My gut is that it is the firewall setting that is causing the problem because when I disable the firewall and reload IPBlock, the torrents begin to download again in Vuze and the NAT problem goes away.  The rule I had in my gufw firewall was "Allow both: [blank]  29165 [blank]  29165  Which yielded the rules in the firewall to say: To            Action        From 29165         ALLOW         29165  This just doesn't seem to be working.  What am I doing wrong?  Please help.  I don't have a particular set of IP addresses to put into gufw; only the port Vuze wants to listen on.

---

### Post by 3rdalbum on 2010-03-21
I'm just trying to figure out why you want a personal firewall running on your computer. Presumably, the only service listening to incoming connections on your computer will be Vuze. Your computer will only respond to connections coming in on the Vuze port, so a personal firewall will not be doing anything that your computer is not already doing.

The other thing is that IPBlock configures IPTables (netfilter) firewall, and so does gUFW. My gut says that both of these firewall configuration utilities will step on eachother's toes.

In short, turn gUFW off unless you are in the extremely unlikely use-case of "I want to run a server on my computer that nobody can access". You are just as safe without it as with it.

EDIT: Just realised you posted to another thread. The person who started the other thread was running two firewalls - one in his ADSL/cable modem, and another 'personal' firewall (configured with Firestarter). The ADSL modem would only let in ports that the person had explicitly specified as being safe, and so Firestarter would only ever see those incoming connections that the modem had allowed - so Firestarter might as well not be there.

---

### Post by josephuser on 2010-03-21
It's interesting that you say I don't need a firewall (gUFW) running.  One of the first things I remember doing to prevent hacker "attacks" on my XP box (before I switched over to Ubuntu) was to install Comodo's firewall software to prevent bad things from getting in or going out.  Here on Ubuntu, I assumed that every user should have a firewall up and running; browsing the web, downloading torrents, posting on forums, it is the kind of thing that a firewall would come in useful if a hacker tried to enter one of your open ports.  I have the standard settings (nothing fancy) running on my Ubuntu box, including Samba, and now i2p (where I'm playing around with IRC and its other tunnel services), and since many things on Ubuntu leave open ports (e.g., installed apache/php which left open a port), it's a smart idea to fire up a firewall to shut these ports down. In other words, I thought running a firewall is the safe thing to do even if you're not doing anything fancy.  What are your thoughts?   Lastly, I kind of figured out the gUFW firewall issue.  If you set the firewall to accept the connections to Vuze's port (here, 29165) *FROM ANYWHERE* (meaning you leave the "from" option blank), gUFW lists the rule output as "To: 29165; Action: ALLOW; From: Anywhere," and Vuze works like a charm without NAT / Firewall issues.  I'd still like to hear your thoughts on the firewall issue re: whether it is recommended or not for the security-minded user.

---

### Post by 3rdalbum on 2010-03-21
A firewall is essential on Windows because by default Windows will listen to a number of incoming ports. Even Windows Firewall will dramatically help with security.

If you are using any sort of ADSL/cable/broadband modem-router, it will already contain a firewall that will protect your whole network. It will prevent incoming connections from reaching into the network, which means that you don't need one on the computers.

Merely "browsing the web" or posting on forums will not cause your computer to listen to incoming connections, only to outgoing connections (which is no danger; or at least, no danger that a firewall would help with).

Your Apache and Samba are safe if they are protected by a firewall at your modem. Some people use Mobile Broadband, where the modem dongles typically don't have a firewall. In those instances, if you are using Apache for personal testing then you would want a personal firewall. If you're behind the firewall in your home network, then you don't need another firewall at your computer.

It's the same as electricity: If you have a residual current device in your electricity meterbox, you don't need one in your powerpoints as well, because the one on the house will protect everything behind it.

A good test to perform would be to turn off gUFW and IPBlock, and try the scanner at [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2). If it shows all "closed" or "stealthed" ports even with your firewall turned off, then you either already have a firewall in your modem-router, or your computer is not listening to any incoming connections. In either case, you do not need a personal firewall.

---

### Post by josephuser on 2010-03-21
It appears as if you're right.  With the gUFW firewall turned off (and IPblock disabled -- it wouldn't even allow me to connect to the grc.com site with it enabled), all the ports on my Ubuntu box appear to be closed (although not stealthed).  So it appears as if I have no specific need for a firewall on my machine.  On another note, the ports were all closed, but not stealthed.  Someone looking for information on my computer could see that there is a port, but that it is closed.  Is there a firewall for Ubuntu that would allow me to have my ports stealthed as reflected on the grc.com ShieldsUP! web site?  PS - In my younger days, ZoneAlarm for XP used to do the trick nicely, but 1) I'm running a Ubuntu box these days, and 2) last time I checked, ZoneAlarm was purchased by Checkpoint which ruined the software making it bulky and buggy.

---

### Post by josephuser on 2010-03-21
As a follow-up to my inquiry about stealthing ports in Ubuntu (per GRC site), I did some searching and I found a script called "Arno's Iptables Firewall," which I heard good things about on freshmeat.com's web site.  I initially installed the version on the Ubuntu Universe Repository, but I received error messages on this version (which were reported as bugs fixed in later versions).  So I went to the site and downloaded the latest version which installed very easily.  The problem is that even though the script says the firewall is running, gUFW doesn't show that it is running.  Oh, and Vuze stopped working again.  So I gave the stop command to Arno's firewall and Vuze started up again.  I guess I'm back at square one.  I suppose my goals here are 1) to secure my ports (ideally to stealth them as I used to in XP), and 2) to allow Vuze to be able to download torrents.  In short, I suppose I have to figure out how to add an exception to Arno's firewall to open the port and allow the torrent traffic through.

---

### Post by 3rdalbum on 2010-03-21
ShieldsUp says they're all closed (if you're in a suit of armour, you don't also need to wear an invisibility cloak), so (1) has been done. And you can use torrents, so that's (2).

If you really want to, you could fiddle with the settings on your router and see if you can enable its firewall - because it sounds like the router's firewall is not active. The router will probably 'stealth' (completely drop incoming packets without sending a reply) - but the benefits over simply having closed ports are very much debatable.

I'm not just sprouting theory at you :-)  I run my netbook on mobile broadband with no firewalls at all, because I know that there's nothing running on my computer that will listen to anything. Even if I was using Bittorrent on that machine it still wouldn't matter that there's no firewall, because the Bittorrent client is the only thing listening, and even if there was a firewall it would still have to listen to incoming connections.

---

### Post by lumitoro on 2010-03-22
> **3rdalbum said:**
> A firewall is essential on Windows because by default Windows will listen to a number of incoming ports. Even Windows Firewall will dramatically help with security.

If you are using any sort of ADSL/cable/broadband modem-router, it will already contain a firewall that will protect your whole network. It will prevent incoming connections from reaching into the network, which means that you don't need one on the computers.


    There's a general misconception about linux systems in the ubuntu community regarding the linux security tightness.
    Thankfully, linux desktops are growing in the general population. This means that linux desktops are increasing in numbers all over the web. All that results in yet another perfectly good platform for spreading DoS(the best example I managed to pop up out of my head). This is by no means a major security threat to you but it can cripple the cloud services you all have grown attached to(myself included). So even though you think your safe, your just another "windows" zombie in the web.
The point is:
    No matter how safe your local system is, you will allways be disrupting all the services that you depend on, and, linux viruses do exist so firewall and anti-virus are indeed necessary, no matter how you display your arguments.

P.S.: Don't post in a forum that no one needs protection in linux systems behind any kind of "secure hardware" because no system is fully secure. Besides multiple layers of security are always welcome(most of the times, it makes the balance between gain and effort not worth the trouble), and the fact that newcomers will actually learn about security issues by trying to implement them with the help of the FLOSS community is what FLOSS is all about.

P.S. 2: If you are behind a router and go through your iptables firewall logs, you can see what i'm talking about...

---

### Post by josephuser on 2010-04-09
So what do you suggest?

---

### Post by lumitoro on 2010-04-12
> **josephuser said:**
> So what do you suggest?

One thing i'm sure is that you can't have several firewalls in linux. Every single package, application, script, that you find, use ipchain/iptables as back-end, because it's the best firewall you'll have since it's in the linux kernel and it's up before you even have a network to be protected from. You should only have one IPTABLES/IPCHAIN (IPTABLES because i assume that you are using recent linux distro) frontend. Basically, if you have ufw activated then you can't have any other IPTABLES front-end activated, otherwise nothing will work. Things like, rule shadowing(this means that allowing something after it was blocked prevents you from accessing the thing you are allowing) will confuse you, and prevent you from successfully debugging your IPTABLES rules.
If you like messing around you can google for "networkmanager iptables profiles" or "fwbuider roaming"...
I'm sorry if i can't be much help because this is a matter of choice, and everyone as different setup's. Right now i'm not even using Networkmanager because it's not working with my university setup, so i resorted to /etc/network/interfaces configuration with wpa-roam features and ifupdown firewall profiles. It's not easy to give a straight answer. If you want my setup, i'm glad to post-it. Reading fwbuilder help is a good start but Firestarter is better for first encounter with linux firewall.

hope this helps you. bye.

PS: about iptables logs...i had to suppress then because they where filling my HDD and i'm behind a router that drops icmp and ping request's by default...

---

### Post by 3rdalbum on 2010-04-12
Dude. You don't need two firewalls. If you already have one in your router, and it's configured correctly, then it will drop all incoming connections and they will never be seen by the client computers. And besides, you need to tell the router WHERE you want those packets to be sent to - it can't just let them through to all the clients, that's not the way IP works.

It's not like anti-virus programs where you have to run two (on Windows) because one might not know about all the same viruses as the other one. A firewall drops ANYTHING that you haven't told it about.

Also, Linux viruses do exist - but try finding one that runs on your box today.

And finally, I can't find any iptables log file. Apparently, IPtables logs to "messages" - but this doesn't contain anything to do with IPtables as far as I can see. I'm behind a router.

---

