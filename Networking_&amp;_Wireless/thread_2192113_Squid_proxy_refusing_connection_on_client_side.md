---
title: "Squid proxy refusing connection on client side"
date: 2013-12-06
forum: Networking &amp; Wireless
---

### Post by primejarvis on 2013-12-06
hi guys,

Need help with zorin lite,  I have already installed squid3 and configured it as a proxy 192.168.1.1 & port 3128 ... the big bang the client ip 192.168.1.2 can ping google.com, yahoo.com, rediff.com ... but cannot open any website firefox showing error  (proxy refusing connection )

i learned from one website we should wait for 24 hours 

What should i do ?

thankx in advance ....

---

### Post by Lars Noodén on 2013-12-06
Check your squid configuration file's ACLs.  It should allow your local network to access it and have something like this:

```

...
acl localnet src 192.168.1.0/24 # RFC1918 possible internal network
...
http_access allow localnet
...

```

Then also check your browser's settings to make sure you are pointed at the proxy.  (I'm not sure how to do system-wide proxy settings.)

ping will work regardless because it goes directly and is several layers below HTTP in the network stack.

---

### Post by primejarvis on 2013-12-06
this is the link which helped me for squid proxy [http://community.linuxmint.com/tutorial/view/1163](http://community.linuxmint.com/tutorial/view/1163) .... 

I put the google public dns on the windows xp sp2 pc (client)
8.8.8.8 
8.8.4.4

And now the google/youtube/gmail/ website is opening (but slow) but many other websites are not opening like filehippo/rediffmail/yahoo etc etc ...

what might be the problem  ?

Thankx in advance

---

### Post by Lars Noodén on 2013-12-06
That tutorial looks like it is set up to make an intercepting proxy.  (Formerly known as transparent proxy)  For that to work as described you have to have it positioned on the network *in between* your clients and the Internet.  Is that the case?

Precisely which version of squid are you running and how is that machine in relation to the others on your network?

---

### Post by primejarvis on 2013-12-06
Yes you got it right its a transparent proxy.

the version of squid is 3

I am just trying to make a cache server to cache http and p2p traffic

Trying to test it with two pc

one linux box with squid (main server) 
2nd windows pc (client)

Could you please help me out  

Thankx in advance

---

### Post by Lars Noodén on 2013-12-06
Squid should be able to cache HTTP traffic but not P2P.  The P2P software usually caches data locally so that will not be an issue.  You can see which version of squid you are running like this in the terminal:

```

apt-cache policy squid

```

or by searching for "squid" in the software center.    If your network looks like the following then you can set up an intercepting proxy.

```

client---+
         |
client---+---squid---Internet
         |
client---+

```

If it looks more like the following then you can set up a regular proxy.

```

client---+
         |
client---+---Internet
         |
squid----+

```

---

### Post by primejarvis on 2013-12-06
For caching purpose i have not yet installed anything .... right know i was just trying to share internet connection with my linux box(server) to windows xp(client) 

After that was thinking of the tutorial [http://aacable.wordpress.com/2012/01/19/youtube-caching-with-squid-2-7-using-storeurl-pl/](http://aacable.wordpress.com/2012/01/19/youtube-caching-with-squid-2-7-using-storeurl-pl/) 

client---+
                 |
client---+---bandwidth controller----squid---Internet
                 |
client---+

---

### Post by Lars Noodén on 2013-12-06
Would this fit?

[http://wiki.squid-cache.org/ConfigExamples/Intercept/LinuxLocalhost](http://wiki.squid-cache.org/ConfigExamples/Intercept/LinuxLocalhost)

I'm rusty on iptables having set up my intercepting proxy using PF instead.

---

### Post by primejarvis on 2013-12-06
Most probably will see to it 

Even i am a little confused about public ip and private ip .... will definately see to it tomorrow.

please be in touch for more guidance....

---

