---
title: "pidgin"
date: 2010-02-24
forum: New to Ubuntu
---

### Post by DarinB on 2010-02-24
I am new to IM can i with an AIM account contact a yahoo person that gave me her account name???
when i added her in and try to IM her i get refused by client is that my pidgin that is refusing or hers. not sure how this whole thing works to i need an email address??? or something???

---

### Post by theozzlives on 2010-02-24
> **DarinB said:**
> I am new to IM can i with an AIM account contact a yahoo person that gave me her account name???
when i added her in and try to IM her i get refused by client is that my pidgin that is refusing or hers. not sure how this whole thing works to i need an email address??? or something???

You need a Yahoo acct to talk to Yahoo people. AIM is for AOL people.

---

### Post by DarinB on 2010-02-24
wow i figured it was cross platform thanks.

---

### Post by Rex Bouwense on 2010-02-24
> **DarinB said:**
> wow i figured it was cross platform thanks.

Now I am confused.  The previous default client GAIM was cross-platform.  So Pigeon is not cross platform.  That doesn't make sense.

---

### Post by ubudog on 2010-02-24
Pidgin is cross-platform, you can run it on windows and ubuntu and some others like OSX.

---

### Post by DarinB on 2010-02-24
who knows i created or started using an old yahoo account i had to change the server to 66.163.181.181 and found a web page that gave me a bunch of others to choose from but it still does not connect. no idea what to do????

---

### Post by ubudog on 2010-02-24
> **DarinB said:**
> who knows i created or started using an old yahoo account i had to change the server to 66.163.181.181 and found a web page that gave me a bunch of others to choose from but it still does not connect. no idea what to do????

I remember this...  Pidgin wouldn't connect to any yahoo account of mine in 9.04.  You will need to install empathy.  To do this, open a terminal (Applicatons, Accessories, Terminal) and type ```
sudo apt-get install empathy
```  This will install empathy.  To open empathy, go to Applications>Internet>Empathy IM Client.  Enter your details after that.  It should work then.  Good luck!:D

---

### Post by DarinB on 2010-02-24
i am using LinuxMint8 build on Karmic. can i use empathy on it?

---

### Post by ubudog on 2010-02-24
> **DarinB said:**
> i am using LinuxMint8 build on Karmic. can i use empathy on it?

Yes, you can.  Just follow the same instructions I gave previously, it should work on Mint too.

---

### Post by DarinB on 2010-02-25
thanks but she opened an aim IM account, so i will hold off on any change just yet
thanks again. with i could get pidgin to work.

---

### Post by shihkster1015 on 2010-02-25
I dont know if you guys checked, but there's a new version of pidgin and it's multiprotocol. I have a hotmail account and now i can see my yahoo contacts :)

---

### Post by ubudog on 2010-02-25
> **shihkster1015 said:**
> I dont know if you guys checked, but there's a new version of pidgin and it's multiprotocol. I have a hotmail account and now i can see my yahoo contacts :)

It has been multiprotocol ever since I started using ubuntu 3 years ago on Ubuntu 7.04.

---

### Post by gallifrey on 2010-02-25
Pidgin is cross platform, and it is multi-protocol, but it is not cross-protocol. To contact a Yahoo user, you must have Yahoo account, to contact AIM, you need an AIM account, etc. The only exception MIGHT be with MSN, who's own messenger can contact Yahoo messenger users, etc. It all depends on the protocol really.

---

### Post by DarinB on 2010-02-25
all this conversation is great but it sure as heck don't work with yahoo. i made a yahoo account and it will not connect. so if anybody knows how to do that it would be interesting.

---

### Post by ubudog on 2010-02-25
Did you ever install empathy?

---

### Post by DarinB on 2010-02-25
I may end up doing that but i find it a cowards way out. just use something else. that often does not end well with ubuntu. just fix the problem. that is all.

---

### Post by texaswriter on 2010-02-25
Pidgin is MULTI PLATFORM + MULTI CLIENT... BUT, you have to have a yahoo accounter ENTERED to be able to chat with other yahoo people.. same goes for AIM, same goes for MSN, etc. Though, MSN people can add yahoo friends and vice versa.. I wouldnt' recommend it though.. It never shows when they are online. 

I run pidgin with my MSN account + yahoo account. 

Hope that clears things up. 

Pidgin has been this way since it was GAIM... GAIM was always that way as far as I know... 

It's intended to be that way.

---

### Post by zeroseven0183 on 2010-02-25
> **DarinB said:**
> all this conversation is great but it sure as heck don't work with yahoo. i made a yahoo account and it will not connect. so if anybody knows how to do that it would be interesting.

What's the error message in Pidgin?

---

### Post by shihkster1015 on 2010-02-25
It was the recent update that enabled pidging to be fully multi-protocol capable. A while back, it was capable of signing into different messenger service, but it wasn't capable of detecting more than one at a time. like yahoo contact in msn

---

### Post by DarinB on 2010-02-26
i figuered out that the default account used by pidgin is the first on added. (not totally sure on that) 
but by default the account was the aim account not the yahoo one. 
once i changed that it worked
thanks for not letting me give up and go to empathy LOL

---

### Post by Tibuda on 2010-02-26
> **gallifrey said:**
> Pidgin is cross platform, and it is multi-protocol, but it is not cross-protocol. To contact a Yahoo user, you must have Yahoo account, to contact AIM, you need an AIM account, etc. The only exception MIGHT be with MSN, who's own messenger can contact Yahoo messenger users, etc. It all depends on the protocol really.

XMPP is also an exception. Google Talk can talk to Jabber, and any other server using XMPP.

---

### Post by prashantkumarha on 2010-05-10
> **ubudog said:**
> I remember this...  Pidgin wouldn't connect to any yahoo account of mine in 9.04.  You will need to install empathy.  To do this, open a terminal (Applicatons, Accessories, Terminal) and type ```
sudo apt-get install empathy
```  This will install empathy.  To open empathy, go to Applications>Internet>Empathy IM Client.  Enter your details after that.  It should work then.  Good luck!:D


This Also doesn't work boss.

I have tried so many things like

1)changing server address to cn.scs.msg.yahoo.com, scsa.msg.yahoo.com. both ping from my terminal

2) gyachi, Empathy.

3) open port addresses 80 and 5050 manually.

4)sudo gedit /etc/hosts   ...............    66.163.181.184 scs.msg.yahoo.com

both did not ping.


Please help me boss.

---

