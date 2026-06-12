---
title: "blocking web sites"
date: 2009-08-11
forum: New to Ubuntu
---

### Post by Mariane on 2009-08-11
Hi, 

I tried 2 programs to block ips, the first one I couldn't get to run at all (Debian packages) and the second, Mobloquer, runs but does nothing. 

I just want something to which I can tell "if the request comes from such a web site, don't answer, if a packet comes such a web site, ignore it". 

I'm afraid Mobloquer is too complicated for me. There is a thread here with 20 pages about it, but people are asking how to do things much more advanced than what I want to do. 

Does anyone know a simple program which does that, please? 

Mariane

---

### Post by kpkeerthi on 2009-08-11
[http://www.opendns.com/how/safer/content-filtering/]("http://www.opendns.com/how/safer/content-filtering/")

---

### Post by akarkor on 2009-08-11
The most simple way is , redirect the unvanted website to localhost.

```
sudo gedit /etc/hosts
```

and put inside

127.0.0.1  [www.websiteblockedbyme.com](www.websiteblockedbyme.com) 


:P

---

### Post by Mariane on 2009-08-11
Looks good, I'll try that. Thank you. 
Please, does it block traffic from the web site or to the web site? Or both? 
And how can I do the other possibilities?


The opendns I found another tutorial for it:
[http://ubuntu-unleashed.com/tag/opendns](http://ubuntu-unleashed.com/tag/opendns)

It looks as though all web traffic has to go through their site, which is not what I was looking for. But thanks for the suggestion anyway. 

Mariane

---

### Post by tom66 on 2009-08-11
What the hosts file does is let you redirect domains to specific IP addresses. 127.0.0.1 is a loopback IP which refers to your own computer. You are effectively routing the traffic from [www.myblockedwebsite.com](www.myblockedwebsite.com) to your own computer and thus your computer cannot connect to it. The hosts file will still allow the website to connect your, though by default, Ubuntu closes ALL ports (and makes them stealth, meaning that Ubuntu sends no response) and thus the website wouldn't be able to connect to you, at least in Ubuntu. Other OSes vary. Additionally, you may want to add entries with and without the www and the various top-level domains (TLDs) and country-codes (like .co.uk) if the website uses them as well. 

For example, your hosts file might look like this:

```

127.0.0.1	localhost
127.0.1.1	orion

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

you can then add entries below the other 127.0.0.1 addresses:

```

127.0.0.1	localhost
127.0.1.1	orion
127.0.0.1       www.myblockedwebsite.com
127.0.0.1       myblockedwebsite.com
127.0.0.1       www.myblockedwebsite.co.uk
127.0.0.1       myblockedwebsite.co.uk

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

Usually a reboot is required for these settings to be saved. Also you will need sudo to access and edit these files.

---

