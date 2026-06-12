---
title: "Allowing only a few websites, all others are to be blocked"
date: 2014-08-20
forum: Networking &amp; Wireless
---

### Post by jonker2 on 2014-08-20
Hi there,

We have two old computers at my workplace. They are both slow and running on Windows XP and as the support for the latter ran out earlier this year I wanted to change them to something more up-to-date. After doing some research, I found that Lubuntu would be perfect. 

So I have Lubuntu 14.04 sucessfully installed on the first one and I am now trying to get the internet browsing right. 
My boss would like to have only a few urls allowed as: 

maps.google.com
[www.publibike.ch](www.publibike.ch)
[http://fr.wikipedia.org/](http://fr.wikipedia.org/)

Honestly I have no idea how to do this, but I guess it cant be too hard. Any suggestions?

Thanks!

Jonker

---

### Post by bizhat on 2014-08-20
How you do this in Win XP ? As far as i know, you need a proxy server or your modem need to support this. My cheap modem Dlink DSL-2750U have option to block URLS.

If you need a hacky solution, just set your DNS server to something that is not accessible (for example some random IP like 192.168.0.100). Then edit /etc/hosts of the computer, then add

```

208.80.154.224 fr.wikipedia.org

```

You will need to find IP for each site you are allowing and add it to /etc/hosts file.

With SSH access to PC, you can do this remotely as required.

---

### Post by jonker2 on 2014-08-20
> **bizhat said:**
> How you do this in Win XP ? 

Hi bizhat, thanks for the answer. No, in fact I already changed from Win XP to Lubuntu 14.04 as I think it is safer&faster to operate a Computer with an up-to-date system. So I'd like to block the standart user from browsing the internet exept from those few pages on a (L)ubuntu system. 

Any ideas on that?

---

### Post by bizhat on 2014-08-20
If i need to do this, i will edit network connection, then set a static IP for the computer along with custom DNS server. In DNS server, set it to IP of the PC itself. 

At this stage, you won't be able to access any web site as DNS resolution fail for web sites (it may work for web sites you just accessed as dns info get cached for few hours).

Now edit /etc/hosts file and add allowed web sites. 

You can read more about hosts file at

[http://en.wikipedia.org/wiki/Hosts_(file)](http://en.wikipedia.org/wiki/Hosts_(file))

Now you will be able to access sites that are listed in hosts file. Only problem with the method is, if IP of a site change, you need to edit hosts file, for large sites this won't happen frequently.

---

### Post by jonker2 on 2014-08-22
Thx. for the answer. Ill try my best to do as you said :D

---

