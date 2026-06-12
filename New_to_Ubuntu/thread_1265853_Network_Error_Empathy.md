---
title: "Network Error Empathy"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by k33bz on 2009-09-13
I have set up Empathy on my Daughter's NetBook. No matter how I try, and everything I have found on the subject, I keep getting network error on Empathy. Can anyone help me with this?

Thanks


Update: It works as should with Gtalk. However I need it working with Yahoo, and that is where I am getting the network error.

---

### Post by k33bz on 2009-09-14
<BUMP>

So am I to guess no one knows how to work around this issue?

---

### Post by misfitpierce on 2009-09-14
What IM protocol are you trying to connect to? EX... AIM, MSN, etc.etc.

---

### Post by k33bz on 2009-09-14
> **misfitpierce said:**
> What IM protocol are you trying to connect to? EX... AIM, MSN, etc.etc.

With Yahoo, that is the one I am getting a Network error on. Just to see if it was a bad install or I had done something wrong I tried with my Gtalk account and it worked with that easily.

---

### Post by misfitpierce on 2009-09-14
Try changing the port of the yahooIM that it connects to EX: switch to 5192 or so.... Perhaps change port to 5192 or whatever you want and if still getting problems make sure that port is open in IPTables which is easiest done with firewall tool Firestarter.

Well I have not used empathy for awhile... Can't remember... Is it possible to change ports in empathy as well like on pidgin when logging into a specific protocol? Yahoo usually choose 5050 for pager login port.

---

### Post by k33bz on 2009-09-14
> **misfitpierce said:**
> Try changing the port of the yahooIM that it connects to EX: switch to 5192 or so.... Perhaps change port to 5192 or whatever you want and if still getting problems make sure that port is open in IPTables which is easiest done with firewall tool Firestarter.

Well I have not used empathy for awhile... Can't remember... Is it possible to change ports in empathy as well like on pidgin when logging into a specific protocol? Yahoo usually choose 5050 for pager login port.

I had tried with port 80, that didn't work, so I just tried with port 5192, that didn't work either.

I dont have a firewall running on my daughters netbook.

---

### Post by scrooge_74 on 2009-09-14
Haven't use empathy yet, for what is worth


A friend using the Remix on a netbook 2 days ago had problems using his yahoo account while using Pidgin, all his other msn or gtalk accounts worked no problem. Yahoo just refused to connect, a day latter no changes made to config, it was logging to the yahoo account with no problems.

So I guess Yahoo is the one still giving us troubles

EDIT: About the firewall, yes you have one running, is iptables, you just dont have a GUI manager for it, install firestarter so you can config it. By default all client applications should be able to go out, just server apps are not allowed

---

### Post by misfitpierce on 2009-09-14
That is a negative. I just connected to Yahoo in pidgin 5 seconds ago. It works fine in Pidgin on default port. You may not be running a firewall per-say but linux/ubuntu is running IPTables regardless which is not configured to open that port. Or you could be running a router which has a firewall built onto it as well or a DSL modem. If need Yahoo that badly, why not give Pidgin a try and see if you can connect using Pidgin perhaps?

If not installed hit Add/Remove and install Pidgin or terminal sudo apt-get install pidgin, because like I said... I just tested my yahoo account in pidgin and it connected flawlessly without having to change port or anything and that port is not even open on my firewalls and it worked fine.

---

### Post by k33bz on 2009-09-14
> **scrooge_74 said:**
> Haven't use empathy yet, for what is worth


A friend using the Remix on a netbook 2 days ago had problems using his yahoo account while using Pidgin, all his other msn or gtalk accounts worked no problem. Yahoo just refused to connect, a day latter no changes made to config, it was logging to the yahoo account with no problems.

So I guess Yahoo is the one still giving us troubles

EDIT: About the firewall, yes you have one running, is iptables, you just dont have a GUI manager for it, install firestarter so you can config it. By default all client applications should be able to go out, just server apps are not allowed

She also has Pidgin, Gyache, and Kopete running her yahoo, those work just fine.

I will install firestarter then. Thanks for that

---

### Post by misfitpierce on 2009-09-14
No problem. If you configure the port for yahoo which is usually 5050 to be open on incoming and outgoing and it still does not work in Empathy then you may need to use Pidgin until it is resolved in Empathy. It may be a Empathy/Yahoo error in the app that may be fixed in next update of the app. Can also check to make sure you got newest version and not just one from repo's. Can add the new PPA into the repo easilly by getting Ubuntu Tweak and hitting third party app's in there. Thats a useful app so you don't manually have to add it with the key and everything. Does everything for you. Enjoy.

---

### Post by k33bz on 2009-09-14
> **misfitpierce said:**
> That is a negative. I just connected to Yahoo in pidgin 5 seconds ago. It works fine in Pidgin on default port. You may not be running a firewall per-say but linux/ubuntu is running IPTables regardless which is not configured to open that port. Or you could be running a router which has a firewall built onto it as well or a DSL modem. If need Yahoo that badly, why not give Pidgin a try and see if you can connect using Pidgin perhaps?

If not installed hit Add/Remove and install Pidgin or terminal sudo apt-get install pidgin, because like I said... I just tested my yahoo account in pidgin and it connected flawlessly without having to change port or anything and that port is not even open on my firewalls and it worked fine.

She connects with several different apps to her yahoo account, all which work perfectly. I keep Pidgin around cause it is much better, just waiting for audio and video support for Yahoo protocol. I heard that empathy has it already for yahoo, gyache and kopete both have one of the other but not both.

> **misfitpierce said:**
> No problem. If you configure the port for yahoo which is usually 5050 to be open on incoming and outgoing and it still does not work in Empathy then you may need to use Pidgin until it is resolved in Empathy. It may be a Empathy/Yahoo error in the app that may be fixed in next update of the app. Can also check to make sure you got newest version and not just one from repo's. Can add the new PPA into the repo easilly by getting Ubuntu Tweak and hitting third party app's in there. Thats a useful app so you don't manually have to add it with the key and everything. Does everything for you. Enjoy.
Its the newest version of empathy.

---

### Post by k33bz on 2009-09-14
Ok, I have opened the ports, still no go :(

---

### Post by scrooge_74 on 2009-09-14
You got me there I dont remember, I havent use Firestarter like in 2 years, got used to the firehol commmand line config :p  

If I remember well you go to network card and then there is an option to add ports and stuff, it will let you config even from which IP you want to connect to (in case of services from a server) Toy with it and you will find is easy to config 

Emphaty could be suffering from the same problems all pidgin users had a few weeks ago when Yahoo updated their login protocols and anybody not using latest ubuntu was left out in the cold until pidgin was upgraded for the rest of us ;)

---

### Post by k33bz on 2009-09-14
> **scrooge_74 said:**
> You got me there I dont remember, I havent use Firestarter like in 2 years, got used to the firehol commmand line config :p  

If I remember well you go to network card and then there is an option to add ports and stuff, it will let you config even from which IP you want to connect to (in case of services from a server) Toy with it and you will find is easy to config 

Emphaty could be suffering from the same problems all pidgin users had a few weeks ago when Yahoo updated their login protocols and anybody not using latest ubuntu was left out in the cold until pidgin was upgraded for the rest of us ;)

ya but with that there was a work around in the meantime. However if that is what I am suffering then all empathy users using the same version should have this problem. 

But the problem is sporadic from what I have read, some with problems with yahoo, others with msn, others with jabber, and so on and so on. None of the recommendations I read have fixed my issue.

This is so disappointing.

---

### Post by bodhi.zazen on 2009-09-14
I filed a but report in Launchpad for the same problem.

[https://bugs.launchpad.net/bugs/428971](https://bugs.launchpad.net/bugs/428971)

---

### Post by k33bz on 2009-09-14
> **bodhi.zazen said:**
> I filed a but report in Launchpad for the same problem.

[https://bugs.launchpad.net/bugs/428971](https://bugs.launchpad.net/bugs/428971)

I dont know about IRC, I wont set my daughter up with one. I currently run 9.04, my yahoo dont work. Did you do anything to get it to work in 9.04 and did it work out of the box?

Havnt tested 9.10

---

### Post by bodhi.zazen on 2009-09-14
No, on 9.04 yahoo worked out of the box. I set up a new yahoo account and entered my information (yahoo user name and password).

Empathy then automatically connected.

---

### Post by k33bz on 2009-09-14
> **bodhi.zazen said:**
> No, on 9.04 yahoo worked out of the box. I set up a new yahoo account and entered my information (yahoo user name and password).

Empathy then automatically connected.

great, it does not connect for me at all on yahoo

---

### Post by bodhi.zazen on 2009-09-14
Bug report ?

---

### Post by Vevmesteren on 2009-09-17
I read that empathy is to be the new out of the box messenger app. And seeing these issues trouble me. I am having the very same issue, and did, thanks to this blog post [http://aslakjohansen.wordpress.com/2009/07/27/empathy-gives-network-error/](http://aslakjohansen.wordpress.com/2009/07/27/empathy-gives-network-error/) manage to create myself a custom launcher that auto kills butterflies on every launch (the name alone troubles me :) ) but that still means that I need to reboot empathy after essentially EVERY MSN conversation...any thoughts on this?

---

