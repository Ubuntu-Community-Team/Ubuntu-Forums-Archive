---
title: "Network name resolving trouble"
date: 2006-12-19
forum: Networking &amp; Wireless
---

### Post by Loffe_ on 2006-12-19
Hi

I have a trouble I cannot understand. Hope I can get some help...

I have a small private network (Windows & Ubuntu mixed)

However from one of my ubuntu machines I cannot access the webserver (running on the other ubunt computer) by entering it's name. I have to enter its ip adress.

I tried and I cannot ping any of the other computers name, but their ip
Cannot even ping localhost

The weird is that nmblookup finds the ip of a name!?

Any idea of what is wrong?

Thanks,
    Loffe

---

### Post by ScreemingBlue on 2007-07-17
Same problems here, can ping ip okay, nmblookup returns name okay, but cannot ping name.
The other box is a linux box with wins enabled using samba.

I don't want to use hosts file and have also tried the winbind solution but it seems to resolve names waaaay too slow.

---

### Post by netztier on 2007-07-18
> **Loffe_ said:**
> 
However from one of my ubuntu machines I cannot access the webserver (running on the other ubuntu computer) by entering it's name.

Is that an *external* name you possibly have registered with DynDNS or some other Internet-based DDNS provider?

If that were the case, the local resolver on the machine would get the externally reachable IP addresses and would try to connect to that one. Most DSL/Broadband routers forbid such "looping back in" connections - and rightly so.

Solution: tweak name resolution in your LAN, with either of these variants:

[LIST]
[*] run an internal DNS server that gives back th internal IP address when queried for the external Hostname. 
[*] sychronise **/etc/hosts** on all your internal hosts to have the proper entries.
[/LIST]


If however you have the problem when using the *internal* hostname, you'll have to provide some form of DNS in your LAN. **DNS is the name resolution system that is native to IP networks.**

[COLOR="Green"]**Simpler alternative:** keep the **/etc/hosts** file on all systems in that LAN synchronized and make sure that it contains all host entries for your systems. As a plus, this method will also resolve the problem with the external hostname. It is easy if you have just a handful of systems - but soon gets tedious when the network grows.[/COLOR]

Samba and nmblookup have other means to resolve a name: they just send a name request to the local subnet's broadcast address, and all NetBIOS-enabled systems must process it. The one system concerned will answer it - possibly. I consider such a name resolving mechanism a horrible kludge and a leftover from the times when a network was one flat broadcast domain, didn't have a clue about what IP is and consisted of a few segments of 10base5 cabling with a handful of bridges and repeaters.

And it continues to bother us today, because it misleads users (even System Administrators) to "just want to type a hostname" - without considering how it is resolved to an IP address. 

And the most worrying thing is: a Windows computer will use NetBIOS-broadcast or WINS name resolution when you enter "http://yourhostname/" into a browser or do a "ping -a hostname" on the command line. I've seen many a case where support desk people and system admins claimed that DNS was not workung until they finally understood that their programs were using NetBIOS broadcast or WINS-resolution when they should've been using DNS.


best regards

Marc

---

