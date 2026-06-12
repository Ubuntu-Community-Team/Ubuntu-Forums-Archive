---
title: "Firewall: DO I NEED ONE??"
date: 2010-12-02
forum: New to Ubuntu
---

### Post by maryalesia on 2010-12-02
Hokay. Fourth thread in two days. I'm on a roll. 

A brief history: my first computer was an eMac. The family computer was a pc, but I didn't really get into computers until I got my own. (when I say "get into" ... I basically mean feel the need to have one. at all times.) 

While I loved my eMac, it was extremely slow. The poor guy only had one gig of RAM. I never had virus protection installed.

Then I got my laptop with vista and I got really, I mean REALLY paranoid about viruses. I watch a lot of TV online ... on sites of ... queeestionable legality ... and I would scan for viruses almost every day.

So when I switched to linux, this whole idea that I didn't even have a firewall kind of blew my mind. I still go to video-hosting sites that post copyrighted material (the kind where right next to the play button is a big green DOWNLOAD button to trick people into downloading some scary executable file onto their computer) and I torrent the sh*t out of this thing. 

SO: do I need a firewall? And if so ... how do I even ... dooo that?

(sorry for long post and thanks oodles in advance!)

---

### Post by Zzl1xndd on 2010-12-02
Ubuntu already has a Firewall built in called ufw (I believe there is a GUI tool for managing it in the Software centre.) 

Also if you are behind a NAT router I wouldn't worry too much as it basically acts as a firewall as well.

For me I use the Shields Up tool over at GRC to test my configuration.

[http://www.grc.com/intro.htm](http://www.grc.com/intro.htm)

---

### Post by Frogs Hair on 2010-12-02
I use firewall configuration found in the software center , as said it is the front end for the Ubuntu firewall . It is handy if you have a need to set a rule for a port or enable an disable logging.

---

### Post by maryalesia on 2010-12-02
> **tweakedenigma said:**
> Ubuntu already has a Firewall built in called ufw (I believe there is a GUI tool for managing it in the Software centre.)

Didn't realize that. I've seen the GUI tool but it always takes me a while to figure out what to do. Sometimes things in linux are soooo simple that I completely miss how they work. Is that weird? 

> **tweakedenigma said:**
> Also if you are behind a NAT router I wouldn't worry too much as it basically acts as a firewall as well.

I have no idea what a NAT router is. O.o 

> **tweakedenigma said:**
> For me I use the Shields Up tool over at GRC to test my configuration.

[http://www.grc.com/intro.htm](http://www.grc.com/intro.htm)

Thanks for the help! It should be noted, however, that when you say "test my configuration" I have absolutely no idea what on earth you mean. I'll figure it out. Probably. If not ... I'll be back. ;)

---

### Post by Zzl1xndd on 2010-12-02
> **maryalesia said:**
> 
I have no idea what a NAT router is. O.o 

Thanks for the help! It should be noted, however, that when you say "test my configuration" I have absolutely no idea what on earth you mean. I'll figure it out. Probably. If not ... I'll be back. ;)

If you have a home router its Likely a NAT (network address translation) Router. 

When I say test the configuration you can use shields up to "scan" all service ports and it will show you what status (Stealth, Open, Closed) they are in and if they replay to pings. I am normally satisfied when everything comes back stealth.

---

### Post by Dragonbite on 2010-12-02
> **tweakedenigma said:**
> Ubuntu already has a Firewall built in called ufw (I believe there is a GUI tool for managing it in the Software centre.) 

Actually I think the Firewall is IPTables, and **ufw** is a tool for editing the firewall.

I always leave the firewall on my systems because it really doesn't hurt (and is probably very beneficial for my laptop which may be used in places outside my home network).

At my home, I have off of my modem an old P3 CPU running IPCop as a firewall, followed by the router with it's built-in firewall so it's probably a bit redundant to leave the firewall on my home desktops but what the hey?

---

### Post by Zzl1xndd on 2010-12-02
> **Dragonbite said:**
> Actually I think the Firewall is IPTables, and **ufw** is a tool for editing the firewall.


You are correct Dragonbite :) pardon the slip on my part.

---

### Post by oldos2er on 2010-12-02
> **maryalesia said:**
> SO: do I need a firewall? And if so ... how do I even ... dooo that?


You might want to read [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by maryalesia on 2010-12-02
> **oldos2er said:**
> You might want to read [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

THIS ... is *extremely* helpful. Much thanks!

---

