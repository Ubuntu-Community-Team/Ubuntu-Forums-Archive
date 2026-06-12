---
title: "Browser Issues"
date: 2010-04-15
forum: New to Ubuntu
---

### Post by vivek40 on 2010-04-15
Hii!
I have a couple of links which just dont seem to work on my firefox or konqueror, but the sites work on my windows system.The firefox has javascript enabled.. java test also works perfectly.. no firewalls installed.. cleared the cache .. still does not work.. any help would be deeply appreciated..
Thanks
for eg:- i just came across a site which does not open 
"http://support.mozilla.com/en-US/forum/1/518608"

---

### Post by e4uforums on 2010-04-15
Can you access the site via IP address instead of doman name?

Try:  [http://63.245.209.132/en-US/forum/1/518608](http://63.245.209.132/en-US/forum/1/518608)

If yes, then you have a DNS issue somewhere.

---

### Post by vivek40 on 2010-04-15
When i click  [http://63.245.209.132/en-US/forum/1/518608](http://63.245.209.132/en-US/forum/1/518608) I reach here...[http://www.mozilla.com/en-US/](http://www.mozilla.com/en-US/)  and this site anyway opens on my system without the IP address. By the way what is this DNS thing and how can i just check it. I was running windows on my system a few weeks back and it was running perfectly

---

### Post by e4uforums on 2010-04-15
I'm sorry, perhaps I misunderstood you.  I thought you were having trouble accessing that Mozilla support site...

DNS stands for Domain Name Service - this is the system that translates domain names (ie [www.google.com]("http://www.google.com")) to ip addresses (ie 66.249.90.104).

To view your DNS servers I believe you can use the command:

```
ifconfig
```or 

```
ifconfig -a
```I'm not a Linux pro and I'm not at a Linux box for sure so I can't tell you for sure.  Hopefully someone will come in and bail me out....  :)

---

### Post by vivek40 on 2010-04-15
somone bail ME out!!!

---

### Post by lovinglinux on 2010-04-15
Try to disable ipv6 in Firefox

1. Type about:config in the address bar, press Enter.

2. Find **network.dns.disableIPv6** in the list.

3. Right-click -> Toggle.

4. Restart Firefox and try again.

You can also disable ipv6 on the system. See [How to disable IPv6 in Karmic Koala](http://wojox.homelinux.net/?p=4).

---

### Post by vivek40 on 2010-04-15
Hi lovinglinux,
> Try to disable ipv6 in Firefox

1. Type about:config in the address bar, press Enter.

2. Find **network.dns.disableIPv6** in the list.

3. Right-click -> Toggle.

4. Restart Firefox and try again.does not help.. .. I have tried toggling both true and false... no does not work.......

The "SOS" is still on

---

### Post by vivek40 on 2010-04-15
bump!

---

### Post by vivek40 on 2010-04-15
Hii ! a little update here .. when i try the ip address of the site it works .. but whenever I type the name of the site it does not...... can someone help me from here

---

### Post by e4uforums on 2010-04-15
Yes, this confirms that you have a DNS issue.

Run two Google searches and you should be better off.

Google "public dns server" - you'll find some open and available dns servers you can use.

Google "update dns settings Ubuntu" - you should find a link on updating your dns server settings in Ubuntu.

I would advise you further on exactly how to do this but I'm a newbie myself and I'm currently sitting at a Windows machine.

Good luck!


***Edit***
Or maybe you can just call your ISP and ask if they're having DNS problems.  That could very well be the case.

---

### Post by vivek40 on 2010-04-15
hmm thanks ..but almost 99% of the sites do open with the present settings.. will changing the dns servers hurt the working sites in any way... by the way can someone tell me how exactly to do this

---

### Post by vivek40 on 2010-04-16
bump!

---

### Post by dineshs on 2010-04-16
Try this
[http://code.google.com/speed/public-dns/docs/using.html](http://code.google.com/speed/public-dns/docs/using.html)
You can backup /etc/resolv.conf before doing this

---

