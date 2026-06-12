---
title: "firestarter im getting loads of hits being registered is that normal"
date: 2009-06-03
forum: New to Ubuntu
---

### Post by blake7 on 2009-06-03
if that is normal why does ubuntu not have it as a default setting, im getting 3 hits per seconded, could thier be antheir problem like a virus on my system

and one last thing is their a way to follow these hits back to their souces.

thank you for your time and have a nice day

---

### Post by Didius Falco on 2009-06-04
> **blake7 said:**
> if that is normal why does ubuntu not have it as a default setting, im getting 3 hits per seconded, could thier be antheir problem like a virus on my system

and one last thing is their a way to follow these hits back to their souces.

thank you for your time and have a nice day

Yes, it's normal. You are getting port-scanned by people looking for unprotected computers.

It's not the "getting hits" part that is dangerous, it's if they are getting through. The fact that you are seeing all these hits means your firewall is doing it's job and blocking them.

If you are behind a router, you've got yet another layer of protection.

If you are at all worried about it, go here

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

and run the testing on your PC. It should reassure you that everything is okay. If you do find ports open, then you can start looking at those ports and what is using them, if it isn't something you've allowed to use those ports, like, for example, a game server.

Yes, you can try and chase down the sources, but unless you are consistently seeing the same one trying to get into your PC, I wouldn't worry about it. 

When the port-scanner folks are scanning, they aren't targeting you specifically (unless you are a secret agent or an industrial spy or something ;)), they are just looking for computers that are not defended.

If yours is protected, they'll move on looking for easier prey, and since you are firewalled at least once and maybe 2X, this would put you in the safe category.

Go have a look at the GRC site, run the tests and see what you find out - it is a safe site, run by Steve Gibson, a well-known and trusted coder.

Then if you still have worries, you will be able to post again with more specific information and someone will try and help you figure it out.

Regards,

Didius

---

### Post by lovinglinux on 2009-06-04
> **blake7 said:**
> if that is normal why does ubuntu not have it as a default setting

[list][*] Ubuntu comes with a firewall installed and running by default, which is called iptables
[*] iptables will allow all traffic by default, because a hit is only a security risk if you have a program listening to a port (service) and if this program has security flaws. Since Ubuntu is shipped without any services running by default, then you don't need ipatbles rules to block any traffic
[*] Firestarter is just a tool for easy configuration of iptables, it is not "the firewall"
[*] Firestarter is not recommended anymore. You should try installing Gufw, which is available in the "Add/Remove" manager with the name "Firewall Configuration"[/list]

> **blake7 said:**
> im getting 3 hits per seconded, could thier be antheir problem like a virus on my system

There aren't any virus for Linux on the wild, but there are other types of malware that could compromise your network. Nevertheless, getting hits from several sources is a common thing and could be due to several reasons, like port-scan or simply a [ghost packet](http://ubuntuforums.org/showthread.php?p=7391948).

> **blake7 said:**
> and one last thing is their a way to follow these hits back to their souces.

System >> Administration >> Network Tools

I also recommend reading the tutorial [Ubuntu Security](http://ubuntuforums.org/showthread.php?t=765421)


*UKeywords: 649167 2009 june firewall iptables hits virus port-scan ghost packet*

---

### Post by blake7 on 2009-06-04
thankyou for all your help

but still unclaer about if i can chase any of these hits back. is thier any prgram that will do this for me


cheers and have a good day

---

### Post by LewRockwell on 2009-06-04
> **blake7 said:**
> thankyou for all your help

but still unclaer about if i can chase any of these hits back. is thier any prgram that will do this for me


cheers and have a good day

I wouldn't waste much time chasing them unless you have some sort of suspicions and a rough idea of "who" it might be.

Remember that anything and everything can be spoofed and hacked.

Never blindly assume that what you see...is actually what you're getting.

as always, your mileage may vary.

---

### Post by blake7 on 2009-06-04
please please tell me i just would love to know is i can and how

thank  you

---

### Post by LewRockwell on 2009-06-04
> **blake7 said:**
> please please tell me i just would love to know is i can and how

thank  you

[http://www.whois.com/](http://www.whois.com/)

[http://www.whois.net/](http://www.whois.net/)

[http://whois.domaintools.com/](http://whois.domaintools.com/)

[http://www.networksolutions.com/whois/index.jsp](http://www.networksolutions.com/whois/index.jsp)

[http://fosswire.com/post/2007/05/using-traceroute/](http://fosswire.com/post/2007/05/using-traceroute/)

[http://www.traceroute.org/](http://www.traceroute.org/)

[http://network-tools.com/](http://network-tools.com/)

---

### Post by cariboo on 2009-06-04
Whois is installed by default. Open an Applications-->Accessories-->Terminal and type:

```
whois 192.168.1.200
```

Substitute the ip address you want to check in the above example.

---

