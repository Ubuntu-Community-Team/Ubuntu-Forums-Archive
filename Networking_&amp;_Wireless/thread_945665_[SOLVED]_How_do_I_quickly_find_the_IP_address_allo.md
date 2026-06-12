---
title: "[SOLVED] How do I quickly find the IP address allocated by my ISP?"
date: 2008-10-12
forum: Networking &amp; Wireless
---

### Post by bwallum on 2008-10-12
IS there a quick and easy command to get the IP address my ISP uses to connect to my router? It is not a fixed IP address and changes everytime the router is switched off and on. I want this to find out the ip address of a remote router to connect to it. 

I can find out by accessing the router. However I am trying to get somebody to do it remotely with even less knowledge than me...if thats possible.

---

### Post by forger on 2008-10-12
```
sudo apt-get install curl
ip=$(curl -s www.whatismyip.org)
echo "My current IP is: $ip"
```

Don't use it too much, otherwise:
> Error: 5 requests received from your IP address in the last 60 seconds (current max is 3 but automated agents should not query more often than once every 10 minutes)

---

### Post by bwallum on 2008-10-12
> **forger said:**
> ```
sudo apt-get install curl
i=$(curl -s www.whatismyip.org)
echo "My current IP is: $ip"
```

Don't use it too much, otherwise:

What have i done wrong here?

> bob@bob-desktop:~$ i=$(curl -s [www.whatismyip.org](www.whatismyip.org))
bob@bob-desktop:~$ echo "My current IP is: $ip"
My current IP is: 
bob@bob-desktop:~$ 
 Nothing was returned?

---

### Post by twisted_steel on 2008-10-12
> **bwallum said:**
> What have i done wrong here?

 Nothing was returned?

It was just a typo in forger's original post.  It should be:

```
ip=$(curl -s [www.whatismyip.org]("http://www.whatismyip.org/"))
echo "My current IP is: $ip"
```

It was missing the "p" in "ip" for the initial assignment.

---

### Post by kevdog on 2008-10-12
See this thread -- there are a lot of one liners in this thread. I personally prefer my one liner, however there are a bunch of creative solutions:

[http://ubuntuforums.org/showthread.php?t=526176](http://ubuntuforums.org/showthread.php?t=526176)

---

### Post by ww711 on 2008-10-12
Can use various sites e.g [whatismyip.com](whatismyip.com) , [www.ipchicken.com](www.ipchicken.com)

---

### Post by bwallum on 2008-10-12
> **twisted_steel said:**
> It was just a typo in forger's original post.  It should be:

```
ip=$(curl -s [www.whatismyip.org]("http://www.whatismyip.org/"))
echo "My current IP is: $ip"
```

It was missing the "p" in "ip" for the initial assignment.

Bingo! Thanks for that.

---

### Post by cariboo on 2008-10-12
There are two other ways  to find the ip address assigned to you by your isp. If you are using a router, just log into the management interface and check the status page, or if you are directly connected in a trminal type:

```
ifconfig
```

Your ip address will be listed in the interface you connect to the inter net with.

Jim

---

