---
title: "IP blocking"
date: 2009-10-25
forum: New to Ubuntu
---

### Post by shadowlands on 2009-10-25
what IP blocking software is good and works with Ubuntu?

---

### Post by vinutux on 2009-10-25
Do U mean firewall ?

---

### Post by vinutux on 2009-10-25
Check this link [http://www.cyberciti.biz/faq/how-do-i-block-an-ip-on-my-linux-server/]("http://www.cyberciti.biz/faq/how-do-i-block-an-ip-on-my-linux-server/")

---

### Post by vinutux on 2009-10-25
Just found a gui one called ipblock **[http://onlyubuntu.blogspot.com/2007/08/ipblock-graphical-ip-blocker.html]("http://onlyubuntu.blogspot.com/2007/08/ipblock-graphical-ip-blocker.html")**

---

### Post by shadowlands on 2009-10-25
Thanks for the replies.  I typed in IP blocking in the search feature and got no hits on this site.  I googled IP blocking+ UBUNTU AND GOT THIS HIT [http://ubuntuforums.org/showthread.php?t=530183](http://ubuntuforums.org/showthread.php?t=530183) 


*Jumping up and down doing the happy dance*

---

### Post by lovinglinux on 2009-10-25
There is [iplist](http://iplist.sourceforge.net/) and [moblock](http://moblock-deb.sourceforge.net/). I personally prefer moblock, but if you are acquainted with PeerGuardian, then you might prefer iplist. If you want a graphical interface then use iplist or add [mobloquer](http://mobloquer.foutrelis.com/) along with moblock. You cannot install both.

Be aware that if you are using a firewall manager like Firestarter or ufw, then you need to launch it before the ip blocker, otherwise the firewall manager overwrites the ip blocker rules. Moblock also has the ability to launch iptables scripts, so you can use it to completely replace other firewall managers, if you are familiar with iptables commands.

---

### Post by shadowlands on 2009-10-26
When you say lunch the fire wall first you mean go online then click on the IP block?  I have never used this type of software before so I will be asking a lot of questions.  I have IPblock installed  it automaticly blocks certain snoops right?  > **lovinglinux said:**
> There is [iplist](http://iplist.sourceforge.net/) and [moblock](http://moblock-deb.sourceforge.net/). I personally prefer moblock, but if you are acquainted with PeerGuardian, then you might prefer iplist. If you want a graphical interface then use iplist or add [mobloquer](http://mobloquer.foutrelis.com/) along with moblock. You cannot install both.

Be aware that if you are using a firewall manager like Firestarter or ufw, then you need to launch it before the ip blocker, otherwise the firewall manager overwrites the ip blocker rules. Moblock also has the ability to launch iptables scripts, so you can use it to completely replace other firewall managers, if you are familiar with iptables commands.

---

### Post by lovinglinux on 2009-10-26
> **shadowlands said:**
> When you say lunch the fire wall first you mean go online then click on the IP block? 

Yes, if you use a firewall manager like Firestarter or UFW, then start the ip blocker after the firewall manager rules are already loaded. If you decide to change some firewall manager rules while the ipblocker is running, then you need to restart the ip blocker.

Here is a better explanation form moblock site. I don't know about iplist, but as far as I remember, it works in a similar way.

> WARNING: Users with firewall (iptables rules)

MoBlock (since version 0.9) and NFBlock do not conflict with other firewalls (iptables rules). But if you use them, you have to take special care to avoid severe conflicts. Make sure the following three conditions hold:

   1. The IP block daemon marks non-matched (IP is not in the blocklist) packets. (The marking feature is on per default.)
   2. Other firewalls do not mark packets.
   3. blockcontrol is started after other firewalls. If other firewalls are started/reloaded after blockcontrol, then you need to restart blockcontrol again. You will be fine, if the iptables rules which send traffic to the iptables chains (blockcontrol_in, blockcontrol_out and blockcontrol_fw) stand before all other iptables rules which ACCEPT traffic. To help you achieve this, blockcontrol.watchdog restarts blockcontrol if it detects any problems. But it's still recommended, to restart blockcontrol manually, whenever another application changed 

> **shadowlands said:**
> I have IPblock installed  it automaticly blocks certain snoops right?

It blocks whatever IP you put in the blocklists, but keep in mind this is not an anonymity tool. It doesn't hide your IP or prevents a third-party from seeing what you are doing. It just prevents bad known IP addresses from connecting to your machine. There are several blocklists available from [iBlocklist](http://iblocklist.com/lists.php) or [Bluetack](http://www.bluetack.co.uk), each one serves a different purpose.

---

### Post by shadowlands on 2009-10-26
What can I use to keep third parties from seeing what I am doing?> **lovinglinux said:**
> Yes, if you use a firewall manager like Firestarter or UFW, then start the ip blocker after the firewall manager rules are already loaded. If you decide to change some firewall manager rules while the ipblocker is running, then you need to restart the ip blocker.

Here is a better explanation form moblock site. I don't know about iplist, but as far as I remember, it works in a similar way.





It blocks whatever IP you put in the blocklists, but keep in mind this is not an anonymity tool. It doesn't hide your IP or prevents a third-party from seeing what you are doing. It just prevents bad known IP addresses from connecting to your machine. There are several blocklists available from [iBlocklist](http://iblocklist.com/lists.php) or [Bluetack](http://www.bluetack.co.uk), each one serves a different purpose.

---

### Post by lovinglinux on 2009-10-26
> **shadowlands said:**
> What can I use to keep third parties from seeing what I am doing?

There is not much you can do. You could use [TOR](http://en.wikipedia.org/wiki/Tor_%28anonymity_network%29) or a [VPN](http://en.wikipedia.org/wiki/VPN) service. Keep in mind that both services have their own [weaknesses](http://en.wikipedia.org/wiki/Tor_%28anonymity_network%29#Weaknesses). For instance, a VPN would probably log your connections and they require your personal data to provide the service. Additionally, unless you are paying for a decent VPN service, download speeds will probably not be optimal and it is considered impolite to use TOR for large data transfers.

> **Bandwidth hogging**
    It is considered impolite by Tor community members to transfer massive amounts of data across the Tor network – the onion routers are run by volunteers using their own bandwidth at their own cost.

**BitTorrent**
    Due to the high bandwidth usage caused by the use of this protocol, it is considered impolite and inappropriate by Tor community members to use the Tor network for BitTorrent transfers. By default, the Tor exit policy blocks the standard BitTorrent ports.

If you use TOR, then don't use iplist, otherwise you will block tor nodes and since all connections will be tunneled through TOR, it doesn't make much sense to use iplist.

---

### Post by lovinglinux on 2009-10-26
BTW, take a look at [http://www.eff.org](http://www.eff.org) for some info on Internet privacy.

---

### Post by sliketymo on 2009-10-26
> **shadowlands said:**
> What can I use to keep third parties from seeing what I am doing?

:( Depends on what your doing.

---

### Post by shadowlands on 2009-10-26
give me a list of things that will protect me and I can chose the program that I need.> **sliketymo said:**
> :( Depends on what your doing.

---

### Post by cranecreek on 2009-10-26
I think Shadowlands is still looking for a way to hide his ip which I don't think is within the scope of this forum. I suggest to you that you find a nice hacking forum and you will get plenty of answers. If you have a question related to a problem with Ubuntu then that would be differrent.

---

### Post by sandyd on 2009-10-26
just 
```

gksudo gedit /etc/hosts

```
then at the top of the file, map the ip addresses you want to localhost.

---

### Post by shadowlands on 2009-10-26
They have hacking forms, sounding like the hobbit who find out beer comes in larger sizes.  I do not want to steal or break anyone's stuff. Nor do I deal in kiddy stuff. If that puts anyone's mind at ease. > **cranecreek said:**
> I think Shadowlands is still looking for a way to hide his ip which I don't think is within the scope of this forum. I suggest to you that you find a nice hacking forum and you will get plenty of answers. If you have a question related to a problem with Ubuntu then that would be differrent.

---

