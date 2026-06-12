---
title: "Firestarter working properly?"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by Primus1 on 2010-06-01
Hi, 

New Ubuntu user.

There are no 'events' to be seen in Firestarter (ever) while I have been using it, can this be correct?

Do I understand right that Firestarter is a front end for iptables which runs whether Firestarter is present or not?

Thanks :)

---

### Post by HereInOz on 2010-06-01
If your computer is behind a NAT router of some description - most broadband modem/routers are such devices - and there is no one else on your network attempting to connect to your computer, then it is quite possible that you would see no events at all.

If however you are somehow directly connected to the Internet, using a dialup or wireless broadband device, then you would expect to see some events, as it is the firewall which is facing the Internet directly.

If you are using a fairly recent version of Ubuntu, the recommended firewall is ufw, and the gui for it is gufw.  It is in the repositories.

---

### Post by Primus1 on 2010-06-01
Thanks, I have a modem router, connected using ethernet to Homeplug adapter. Using Lucid, when I used windows xp and zonealarm I saw intrusions with that firewall. Will have a look at ufw, thanks.

---

### Post by new_tolinux on 2010-06-01
> **HereInOz said:**
> If you are using a fairly recent version of Ubuntu, the recommended firewall is ufw, and the gui for it is gufw.  It is in the repositories.
For what I've seen, gufw is missing some options which are present in Firestarter.
Firestarter is more user-friendly in my opinion.
But to be fair, the development of Firestarter seems completely discontinued, so it can be a bit out-of-date. I don't know if I should consider that a real problem, since Firestarter isn't the firewall, it's only configuring the firewall.

---

### Post by Soul-Sing on 2010-06-01
> **Primus1 said:**
> Hi, 

New Ubuntu user.

There are no 'events' to be seen in Firestarter (ever) while I have been using it, can this be correct?

Do I understand right that Firestarter is a front end for iptables which runs whether Firestarter is present or not?

Thanks :)

give ```
sudo iptables -L -n
```
activity?

Firestarter is old and no longer maintained by the devs. and "we" don't recommend using it. I suggest UFW or GUFW if you insist on having a (software) frontend firewall.

---

### Post by Primus1 on 2010-06-01
give      Code:
     sudo iptables -L -n 
activity?

What do you make of this please * leoquant*?

---

### Post by Soul-Sing on 2010-06-01
I don't know if firestarter works properly,there are known bugs showing firestarter being buggy working with networkmanager.: [http://ubuntuforums.org/showthread.php?t=1463755&highlight=firestarter+bug](http://ubuntuforums.org/showthread.php?t=1463755&highlight=firestarter+bug)
```
sudo /etc/init.d/firestarter status
```
will show it is running/"up"
It seems to being working though....

---

### Post by egalvan on 2010-06-01
> **Primus1 said:**
> New Ubuntu user.

Do I understand right that Firestarter is a front end for iptables which runs whether Firestarter is present or not?


Absolutely correct. Firestarter is just a front-end.
And as others have stated, Firestarter is also old, and un-maintained.
Use UFW and/or it's ilk.


BUT iptables is a set of rules, not a program that "runs".
They are read and acted upon by other software.

---

### Post by Primus1 on 2010-06-02
Code:
 	sudo /etc/init.d/firestarter status 
will show it is running/"up"
It seems to being working though....

"firestarter is running"
Thanks.
I see around the forum some say firestarter and some ufw, I'll look at ufw till I learn enough about iptables to use it directly.

---

### Post by 3rdalbum on 2010-06-02
> **Primus1 said:**
> Thanks, I have a modem router, connected using ethernet to Homeplug adapter. Using Lucid, when I used windows xp and zonealarm I saw intrusions with that firewall. Will have a look at ufw, thanks.

Why bother?

Your modem router already contains a firewall that's protecting your whole network. Why do you need a firewall on your client as well? The client's firewall will not receive any incoming connections, as you've just seen, because all incoming connections are being blocked by the router.

The only thing a personal firewall would protect against is attacks originating from your own network; and if that's happening, then you've got more immediate problems.

---

### Post by Primus1 on 2010-06-02
Thank you for your contribution. I am not the only person on the forum using a firewall with ubuntu so it clearly isn't that outlandish.

---

### Post by 3rdalbum on 2010-06-02
> **Primus1 said:**
> Thank you for your contribution. I am not the only person on the forum using a firewall with ubuntu so it clearly isn't that outlandish.

It's very common (Windows mentality, methinks) but it's simply not necessary as no incoming connections will ever reach your inner firewall. And besides, you're probably not running anything on Ubuntu that would listen for incoming connections anyhow.

Believe me, a lot of people out there don't really know what a firewall does. A popular idea on Ubuntu Brainstorm about a year ago was a firewall that "Opens up when you access the Internet (for instance, when you check your mail) and then closes again straight afterwards". ](*,)

---

### Post by Primus1 on 2010-06-02
Yes 3rdalbum, it's my Windows mentality :). Quite a shock coming from Bills os where the first thought is to get a Firewall and anti virus installed quick.

Im sure I don't know what a firewall is either, not properly :mrgreen:. It will take me a long time to learn that and many other things but hope I can get the help here as I have done already.

Cheers.

---

### Post by oldos2er on 2010-06-02
You might want to read [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by Primus1 on 2010-06-02
> **oldos2er said:**
> You might want to read [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Just had a quick look, interesting and of course it has lots of other links in it. As a new Linux user I find I'm reading ( I do read up before posting :) ) a page and a link sends me on to another item somewhere and I lose track. I'll give it a proper read tomorrow though.
Thanks.

---

### Post by dvwolfman on 2010-06-05
So which is a firewall app that has a gui that is good for newcomers to Linux security, like me, I tried Firestarter, is there another Linux software firewall that might be more appropriate for a home user with a small LAN? For now I will read up on UFW and GUFW...

running Ubuntu 10.04 

> **leoquant said:**
> give ```
sudo iptables -L -n
```activity?

Firestarter is old and no longer maintained by the devs. and "we" don't recommend using it. I suggest UFW or GUFW if you insist on having a (software) frontend firewall.

---

### Post by Primus1 on 2010-06-05
Hi dvwolfman, like you I am learning. One thing I have learnt is Firestarter is not a firewall, just a more user friendly way of configuring iptables. Like leoquant says, such things are software front ends.

---

