---
title: "Hey check out all this action I got going on with my firewall"
date: 2010-02-11
forum: New to Ubuntu
---

### Post by Bakerconspiracy on 2010-02-11
Where should I start? Should I just reformat at this point or what

I know the ssh is fine, but everything else... those connections on the high ports...

---

### Post by Mustard on 2010-02-11
It's a bit early for reformating.

Best to follow all leads out to their logical conclusions first.  Everything is not always as it seems, at first glance.

---

### Post by cariboo on 2010-02-11
Running firestarter as root all the time is a great way to get your system cracked. Firestarter hasn't been updated since 2005, the Debian maintainer only adds bug fixes. I would suggest you use GUFW if you need a gui interface for iptables.

Try:

```
netstat tnlps
```

To see what the connections are doing

---

### Post by Mustard on 2010-02-11
My first thought is that they are just connection attempts by computers that were previously connected to you, for example, if you were downloading a torrent earlier, but have now shut down the torrent, your IP might still be 'out there' as a place to go for a torrent, so those computers continue to look for you, despite the torrent being shut down.

There are many reasons why you get these types of hits on a firewall.

---

### Post by 2hot6ft2 on 2010-02-11
Hard for these old eyes to read all that but it looked like
a few AOL IM - Pidgin (chat)
HTTP - Firefox (web browser)
and SSH

So if you're browsing, chatting on AOL IM with pidgin, and running SSH what is unusual about it?

---

### Post by Bakerconspiracy on 2010-02-11
>  if you were downloading a torrent earlier, but have now shut down the torrent, your IP might still be 'out there' as a place to go for a torrent,

I don't think this is the case. It has been at least a week since I downloaded a torrent of any kind. The bad news is I moved, and these same connections are showing up at the new house (new IP). My computer used to be a server that hosted a simple website. It was on for the greater part of last year. For some reason I suspect foul play...

I created some new firewall rules using GUFW, and check out what happened (see attached image). Also, I pipped out "netstat tnlps" after I created the rules (see attached document).I looked up the IPs that were making the connections and some people had trouble with them too: [http://www.cimsuyu.com/cmn/pubservices/offensive_details.html?id=5268]("http://www.cimsuyu.com/cmn/pubservices/offensive_details.html?id=5268")

> So if you're browsing, chatting on AOL IM with pidgin, and running SSH what is unusual about it?

Beyond the few http, the aol connections and the ssh, there are a few connections in the higher ranges of ports that I cannot account for.


Thanks for you quick responses guys. I am trying to fix this problem tonight.

---

### Post by k3lt01 on 2010-02-11
Cariboo gave you a briliant suggestion but now I am wondering why do you have two separate firewall GUIs running at the same time. I would think that may be able to open you up to more issues.

---

### Post by Bakerconspiracy on 2010-02-11
Check out one more attachment. 

All these samba connections yet I have no other computers connected to my router and that port should not be accessible outside my network.

> Cariboo gave you a briliant suggestion but now I am wondering why do you have two separate firewall GUIs running at the same time. I would think that may be able to open you up to more issues.

Good point.

---

### Post by k3lt01 on 2010-02-12
> **Bakerconspiracy said:**
> Check out one more attachment. 

All these samba connections yet I have no other computers connected to my router and that port should not be accessible outside my network.Can I make a suggestion? Why don't you reboot and see if the connections break.

> **Bakerconspiracy said:**
> Good point.I'd be using UFW with GUFW if I were you, as Cariboo said FireStarter is not really supported anymore and can be a weak link.

---

