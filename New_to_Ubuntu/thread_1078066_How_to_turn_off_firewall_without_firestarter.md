---
title: "How to turn off firewall without firestarter"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by Mitch9654 on 2009-02-22
Anybody know how?


mitch9654

---

### Post by llamabr on 2009-02-22
How are you starting your firewall?

---

### Post by Mitch9654 on 2009-02-22
I dunno.
My Frostwire thingy is just proclaiming that I have one, and I want the firewall ***_DOWN!!!!_***


Mitch9654

---

### Post by T2manner on 2009-02-22
I'm pretty sure Ubuntu doesn't come with a firewall...

---

### Post by llamabr on 2009-02-22
Unless you've started one, your system is probably not running a firewall.  There may be one in your router.

Try messing with your settings for firewire, to tell it there's no firewall.

---

### Post by Mitch9654 on 2009-02-22
thanks I guess this is solved... I dont have control for my router (thats probably it)


mitch9654   [solved]

---

### Post by HermanAB on 2009-02-22
Thr command iptables contrls the Linux packet filter.  So you can flush all rules with:
$ sudo iptables -F

Read 'man iptables' about five or ten times and then you'll have some idea...

Cheers,

Herman

---

### Post by pdtpatrick on 2009-02-22
Linux ships with iptables which is the firewall but most times it's not blocking everything unless you have SeLinux or use NetBSD.

In any case you can do this:

sudo apt-get install ufw (commandline tool)

or since you seem like you might be new, install this

sudo apt-get install gufw

and then type:

gufw 

it will start the tool and you'll be all set. 

Have fun.

---

