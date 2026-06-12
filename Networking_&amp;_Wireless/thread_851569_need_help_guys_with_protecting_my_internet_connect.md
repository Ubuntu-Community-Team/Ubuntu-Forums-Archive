---
title: "need help guys with protecting my internet connection"
date: 2008-07-06
forum: Networking &amp; Wireless
---

### Post by temocrow on 2008-07-06
[B][COLOR="Blue"]first of all i must apologize for every one in the forum  for my intrusion ...
but i didn't know any way els to ask for help... guys iam using a normal pc machine and [COLOR="Red"]**i'am new to the linux world**[/COLOR].. i recently tried a ubuntu 7.04 and i loved it i was willing to let go of the windows system and all of its programs and  and its PS..
after i installed the ubuntu i tried to connect to the internet .. i was first perfect better than i ever hoped for .. but the problem that iam sharing a network with other users and they use a software call net cut and i can not connect to the internet via the ubuntu because of it..:confused:
they use it to direct the connection to there pc's
when i used the windows i used to deal with these people but now i'am like a blind guy in a racing track.. i need your help how to prevent them from attacking me with any kind of arp attack .. i also heard that they can lestining to my connection and steal my passwords via the arp protocol kind of software  [/COLOR][/B]

---

### Post by tamoneya on 2008-07-06
I am  looking at net cut and it doesnt exactly seem like it would be able to do much to protect you from an arp attack.  In order to encrypt traffic you would need to do stuff both client side and server side.  This is just a client side solution.  As for encrypting passwords you need to watch sites and make sure that it starts with https not http.  net cut will not effect this in any way as far as I know.  If you are seriously worried about things like this you should look into PGP encryption.  You could also do direct ssh tunnels if you have ownership of the servers which you are connecting with.  ssh tunnels encrypt all of your traffic.
EDIT: if you seriously cant live without netcut just run it in wine. ([http://www.winehq.org/](http://www.winehq.org/))

Also there is no need for blue text

welcome to ubuntu/linux

---

### Post by temocrow on 2008-07-06
thank you my friend for your replay... but
you didnt think what i was saying .. i said the the users in my network use netcut or ( net cut ) to cut me off using the internet... when i used the windows system there was a couple of tricks i used to do to hipe my ip or mac address so that they dont attack me..and there was a software called  " AntiARP " it used to help protect me from there attacks.. when i started ubuntu i'am defencless against them.. so..my question is this .. can i use antiarp on ubuntu .. is there a way of protecting my pc from attacks viw my network.. can i hide my ip from my local network...
please if u have advise for me .. i am waiting for it..!!
and please let me tell you  again that i am [COLOR="Red"]not[/COLOR] a professional linux user .. [COLOR="Red"]**iam just beginning to learn linux**[/COLOR]

---

### Post by tamoneya on 2008-07-06
you cant hide your IP address from other users.  I can just run a nmap scan on all local IPs and I will see your computer even if you disable SNMP (ping responses).  The site i found for antiarp is this:[http://www.antiarp.com/English/e_index.htm](http://www.antiarp.com/English/e_index.htm).  Provided we are now talking about the same product I would like to point out that that product appears rather sketchy to me and I wouldnt trust anything on it.  Here are the main reasons I dont trust it:
1. It has a gmail account as its main contact email
2. It is primarily Chinese and who knows what other stuff is in there.  I do not mean to offend anyone of Chinese descent but point out that I wouldnt exactly trust the Chinese government.  I dont think I would trust the US government much either though.

If you really care about security to you should look into ssh and PGP encryption.  Also watch out for https sites as opposed to http when sending passwords.

As for netcut I am still a little confused.  From what I am understanding you are being attacked by users on your own network by a program called net cut.  Why dont you just tell the administrator of this network and get them banned.  I cant imagine they like the idea of users attacking each other on their network.

---

### Post by temocrow on 2008-07-07
will thank you a gain tamonya ..
but i really dont know what is  " PGP encryption. Also watch out for https sites as opposed to http when sending passwords.
 " ... and what does that mean..
and i dont tell my network administrator cause he is using it him self .. greedy little ***.. :D any way ..
net cut is really annoying i think if i have a gun i would be able more to make them stop doing that easier than trying some softwares .. as for anti arp yes i noticed its chines .. & i was not comfortable with that .. but after i tried it it is clearly the best solution for the arp and netcut attacks...
if you please explain whatis PGP encryption.. and how can it help..

---

### Post by tamoneya on 2008-07-07
PGP encryption will encrypt your internet traffic.  This means that people will be able to see that you are using the internet but to them it will look like a big mess.  The thing about PGP though is you need to get whoever (or whatever in the case of a server) you are talking with to use PGP as well and you need to swap keys.

Honestly the best thing you could do for yourself is get a better provider.  what is this network exactly.  Is it a network at the office? school? because honestly whether or not the network admin allows and or participates in the attacks it is illegal given the amount you told me.  If the network admin wont help you just keep working your way up or just dump them all together.

[http://en.wikipedia.org/wiki/Pretty_Good_Privacy](http://en.wikipedia.org/wiki/Pretty_Good_Privacy)

---

### Post by Franc88 on 2008-07-07
It seems to me that he is trying to use wireless connection on a network that the users don't want him on.  I also get the impression that this is not paid by that individual but by someone else or a company or university.

If the other users on your network, including the administrator, are "attacking" you, can't you get your own internet connection and router and be done with the issue?

What you are describing sound very dubious and shady.

---

### Post by temocrow on 2008-07-08
for the 4th time tamoya thank you man for you advise ..:)
will .. its a network a local network started by a number of guy in my neighborhood trying to offer a service to a limitid guys like 
me who needs the internet and cannot afford to install a private ADSL .. but after a while the number of the people in the network grew as it gave him more profite we are now 32 .. (on a speed of 1024 ).
its not wireless we use the routers gateway to inter the internet
and i still dont know how to use PGP or how to do it

---

### Post by temocrow on 2008-07-08
finnaly if i could afford to have my own router & own connection i would have done that along time ago

---

### Post by tamoneya on 2008-07-08
take a look at this post which talks about how to prevent against arp poisoning.

[http://www.governmentsecurity.org/archive/t14083.html](http://www.governmentsecurity.org/archive/t14083.html)

---

