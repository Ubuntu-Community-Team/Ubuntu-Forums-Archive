---
title: "How to connect pidgin behind firewall"
date: 2007-12-08
forum: Networking &amp; Wireless
---

### Post by bc040401056 on 2007-12-08
im a new user of gutsy gibbon. im using internet on nwtwrk behind firewall im toatlly messe up now is there any firewall client for ubuntu if so please tell me the name and method of it i install dante-client and fireflier-client-gtk too but i dont able to use it pleasse help this new guy
Abbas  :(

---

### Post by Emerzen on 2007-12-08
The simplest firewall interface is Firestarter IMHO.  Lokkit is also popular.  However, the default iptables for Ubuntu shouldn't prevent you from using Pidgin (which sends an outgoing connection).  What specifically is the problem with Pidgin

---

### Post by bc040401056 on 2007-12-08
thank u emergen for answering me than what should i do to talk on messenger what messenger will be best for it

---

### Post by bc040401056 on 2007-12-08
when i try to log in in pidgin it says http proxy connection error 502 and when i try it with socks than it says server did not allow u some timeit when i change is theand please tell me what is the stun server

---

### Post by vac on 2007-12-08
r u trying log in on msn/hotmail account or others account.?because each account has different set up

---

### Post by bc040401056 on 2007-12-08
im trying to get login in yahoo account behind firewall

---

### Post by Emerzen on 2007-12-09
Hey bc... - why are you connecting through a proxy?  Did you allow Pidgin to detect your settings automatically.  

I suggest you try Kopete, which is a very find IM client designed for KDE.  It's in the repo's and can be found through the Add/Remove section under Applications.  I've never had a problem w/ Pidgin in Ubuntu, but it gives me some trouble at work on Windows.  If you run into similar problems with Kopete, then you no it's a problem w/ your network settings.  Anyway, I think you'll find Kopete a better experience.

---

### Post by bc040401056 on 2007-12-09
i tryed emerzen too but it dont work i got the same problem with that too now i installed amsn which is only working fine beacuse i just typed htp proxies in network and it work great

---

### Post by Emerzen on 2007-12-10
Hmm...well, in my Pidgin I have my AIM and Google Talk accounts set up.  In both accounts, under add/edit-->Modify-->advanced, I have the proxy set to "use Gnomeproxy settings."  How about you?  Does it work if you change it to this?

---

