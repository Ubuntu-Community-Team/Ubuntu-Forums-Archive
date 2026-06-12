---
title: "&quot;Best&quot; Instant messegaing app [Pidgin vs rest]"
date: 2009-06-27
forum: New to Ubuntu
---

### Post by Andy06 on 2009-06-27
**EDIT: Poll added, you can select more than one option. Please note the poll is for what you will use in the future from 9.10 onwards once Empathy is default and not for what you are currently using.**

Pidgin is awesome but it does not support facebook chat, has been having trouble recently connecting to yahoo and will be replaced in Ubuntu 9.10 with Empathy.

All of this got me searching for a new IM app so which one do people recommend? I especially need compatibility with a large number of networks, especially the common ones like: 

MSN/Live and Yahoo which all seem to support
Gtalk which some of them support
Facebook chat which very few seem to support

If the same app can be used on Windows (like pidgin, carrier, Digsby), that would be awesome. It would also be great if any of them have the out-of-the-box polish in terms of looks of the latest Windows Live Messenger. To be frank the latest gen Live and Yahoo messengers look light years ahead of others.

Currently, I am looking at:
SIM-IM
Gossip 
Gajim
Pidgin - When will it implement facebook chat?
Carrier - pidgin fork that offers almost no extra worthwhile features?
Digsby - not open source, shady activities on computer?
Empathy - It will be default for Ubuntu

Also include things like rate of development, current development status (active/dormant), features etc when you recommend one over another.

Thank you very much

P.S Why is there such a wide range to choose from. I know Linux is all about choice but too much choice is baad, I wish there were 2 or 3 I could try and choose from.

---

### Post by SunnyRabbiera on 2009-06-27
Actually windows has more IM clients then Linux has, thanks to its monopoly over everything.
For me right now Kopete seems to be a big winner, as for facebook chat I dont know of any current linux IM client that works with it.
Telepathy I am unsure of, it intends to replace Pidgin for where its been lacking for many but still I didnt think it was all that thrilling.

---

### Post by siryuhan on 2009-06-27
Bitlbee!

[http://www.bitlbee.org/main.php/news.r.html](http://www.bitlbee.org/main.php/news.r.html)

---

### Post by unknownPoster on 2009-06-27
> **Andy06 said:**
> Pidgin is awesome but it does not support facebook chat, has been having trouble recently connecting to yahoo and will be replaced in Ubuntu 9.10 with Empathy.


A plugin is in the repos that will allow facebook-chat.

[PHP]sudo apt-get install pidgin-facebookchat
[/PHP]

---

### Post by binbash on 2009-06-27
There is a facebook chat plugin for pidgin : pidgin-facebookchat

---

### Post by Andy06 on 2009-06-27
Thanks everyone,

SunnyRabbiera,

Unfortunately, Kopete is qt4/KDE-based, so I am not currently considering it. What's the closest GTK+/GNOME messenger? Is there one using the same back end?

A number of linux IM clients claim to work with FB chat like SIM IM, Empathy, Gossip etc

siryuhan,
I dint really know who actually used Internet relay chat was :D. No one I have ever seen, guess my crowd is just not so advanced, but yeah, I don't really need IRC features, would prefer something more "mainstream" :D

binbash,
Yeah I've tried it, heard from lots of people that it was very unstable and then experienced it myself.

I am trying to wean myself away from pidgin, its a resource hog, lacks new features and even though it has a massive user base, all that will change the moment Empathy becomes Ubuntu's default IM. It will see a exponential increase in number of users.

Keep the comments coming

---

### Post by Andy06 on 2009-06-27
> Telepathy I am unsure of, it intends to replace Pidgin for where its been lacking for many but still I didnt think it was all that thrilling.

Hadn't heard of telepathy. Searched a bit and found out that the default 9.10 IM app, Empathy is based on telepathy. Is there a standalone telepathy app as well?

You weren't thrilled with telepathy or empathy? And how long ago did you try it? Perhaps its improved since then, else the Ubuntu team would not make it default.
Three advantages it has over Pidgin is out of the box FB chat (and more chat protocol compatibility in general), less system resource intensive and voice and video chat! :D

---

### Post by Andy06 on 2009-06-27
Do aMSN and emesene connect to anything apart from the Windows Live network? I wasn't considering them so far.

---

### Post by Sef on 2009-06-29
> Do aMSN and emesene connect to anything apart from the Windows Live network? I wasn't considering them so far.
No.  They strictly connect to Windows Live.

---

### Post by Andy06 on 2009-06-29
hmm...anyway I can add a poll to this thread now?
I tried editing first post, doesn't give me the option.
Would be nice to see what everyone is using.

Thanks

EDIT: Never mind, figured it out, there was an option in thread tools.

---

### Post by hufferd on 2009-06-29
> **Andy06 said:**
> Pidgin is awesome but it does not support facebook chat, has been having trouble recently connecting to yahoo and will be replaced in Ubuntu 9.10 with Empathy.

All of this got me searching for a new IM app so which one do people recommend? I especially need compatibility with a large number of networks, especially the common ones like: 

MSN/Live and Yahoo which all seem to support
Gtalk which some of them support
Facebook chat which very few seem to support

If the same app can be used on Windows (like pidgin, carrier, Digsby), that would be awesome. It would also be great if any of them have the out-of-the-box polish in terms of looks of the latest Windows Live Messenger. To be frank the latest gen Live and Yahoo messengers look light years ahead of others.

Currently, I am looking at:
SIM-IM
Gossip 
Gajim
Pidgin - When will it implement facebook chat?
Carrier - pidgin fork that offers almost no extra worthwhile features?
Digsby - not open source, shady activities on computer?
Empathy - It will be default for Ubuntu

Also include things like rate of development, current development status (active/dormant), features etc when you recommend one over another.

Thank you very much

P.S Why is there such a wide range to choose from. I know Linux is all about choice but too much choice is baad, I wish there were 2 or 3 I could try and choose from.


Update I use the newest pidgin --- from their web site and it supports FB chat

---

### Post by Mornedhel on 2009-06-29
I'll be using Empathy if it works as well as Pidgin does now. I have no use for FacebookChat, wasn't even aware there was such a feature, don't have a Facebook account, won't get one.

My second IM client of choice is ERC (IRC in emacs).

GTalk is supported by about everyone. It's XMPP after all. I configured Pidgin to access GTalk as an XMPP account right when the feature came out in Google Labs and Pidgin didn't have an explicit GTalk plugin.

As for Pidgin and others being lightyears behind WLM and YM, I'll keep my IM clients ad-free, thankyouverymuch. I consider Pidgin to be a fairly polished app in terms of UI, although it does suffer from the Gnome syndrome of hiding configuration options.

---

### Post by Andy06 on 2009-06-29
By default or using a plugin?

I never got why pidgin doesn't auto update with the update manager....

What about voice and video chat support?

Thanks

---

### Post by Mornedhel on 2009-06-29
> **Andy06 said:**
> By default or using a plugin?

I never got why pidgin doesn't auto update with the update manager....

What about voice and video chat support?

Thanks

Sorry, are you talking about GTalk support ?

If you are, then yes, support for XMPP (GTalk, Jabber...) is available out of the box.

Pidgin *does* auto update with the update manager. If yours is a few minor versions behind, it's because packaging is a complicated process which does not include pulling the very latest every day and repackaging it for a released distribution, although if you use the Pidgin PPA you probably won't be further behind than a few days.

Still no voice and video chat support for GTalk in Pidgin AFAIK, but I never tested those features, I don't use them.

---

### Post by LiamWilson on 2009-06-29
Yeah, I'd like to know what IM Clients support Video/Vioce chat fo MSN. I think Empathy does, doesn't it?

---

### Post by Andy06 on 2009-06-29
> Sorry, are you talking about GTalk support? 

No about facebook :)

> Pidgin *does* auto update with the update manager. If yours is a few minor versions behind, it's because packaging is a complicated process which does not include pulling the very latest every day and repackaging it for a released distribution, although if you use the Pidgin PPA you probably won't be further behind than a few days.

[http://www.pidgin.im/download/ubuntu/](http://www.pidgin.im/download/ubuntu/)

That page indicates it does not. 

> Yeah, I'd like to know what IM Clients support Video/Vioce chat fo MSN. I think Empathy does, doesn't it? 

I think currently empathy lacks a lot of things. Its just that it racing at breakneck speed compared to the others.

In my opinion, if you want to face the real world with a IM app, you need full MSN support and full facebook support. Everything else is secondary. The last time I checked empathy lacked basically everything that majority of people do majority of the time such as:

Rich text messages
Chatting with friend appearing offline and ivisible users on MSN
Sending and receiving offline messages
File transfers
Custom emoticons
Custom status messages

There are many IM apps around on Linux, but none can do the basics right and provide proper compatibility IMO. Hopefully all of these issues with Empathy will be sorted out before Karmic is released.

The 2 big things it has going for it are voice and video chat and facebook chat support by default.

Have a look here:
[http://pinstack.blogspot.com/2009/06/replace-pidgin-with-empathy-in-karmic.html](http://pinstack.blogspot.com/2009/06/replace-pidgin-with-empathy-in-karmic.html)

Not a very encouraging pics but even with all these faults, I am hopeful I can find my one-size-fits-all-encompassing solution with empathy :P

Waiting for new features in pidgin was sort of like waiting for the oceans to dry up :(

---

### Post by Mornedhel on 2009-06-29
> **Andy06 said:**
> [http://www.pidgin.im/download/ubuntu/](http://www.pidgin.im/download/ubuntu/)

That page indicates it does not. 


From the page : "(except for security issues and high-severity bugs)". This is the case for *all* your packages, I hope you understand this. *Nothing* gets updated except for three things :

* Security updates
* Major bug fixing updates
* Anything that might be backported from $your_distro+1 to $your_distro.

Pidgin isn't special in this.

> **Andy06 said:**
> In my opinion, if you want to face the real world with a IM app, you need full MSN support and full facebook support. Everything else is secondary. The last time I checked empathy lacked basically everything that majority of people do majority of the time such as:

Rich text messages
Chatting with friend appearing offline and ivisible users on MSN
Sending and receiving offline messages
File transfers
Custom emoticons
Custom status messages

There are many IM apps around on Linux, but none can do the basics right and provide proper compatibility IMO. Hopefully all of these issues with Empathy will be sorted out before Karmic is released.

The 2 big things it has going for it are voice and video chat and facebook chat support by default.

That's exactly that, *your* opinion. In the "real world", you'll quickly find out that outside of your friends from college and your parents, no one has serious uses for IM. Enterprise use for IM doesn't require advanced features, OR it requires using a particular client.

By the way, I like that Pidgin doesn't have support for "full" MSN features. I like that my friends can't use MSN to send me pictures or nudges or whatever. I may be old-school (my using emacs to chat on IRC certainly makes me old-school), but when I chat I use *text*. (I consider rich text support useless : when I enable it I quickly get tired of bold pink text and animated emoticons ; and my opinion is that chatting while invisible is extremely impolite, it's basically you saying "I can disturb anyone but no one better disturb me." But that's exactly it : it's *my* opinion. Also frankly, Facebook chat support ?! What the hell was wrong with every other protocol available on the face of this planet ?!)

Yup, I definitely feel old now.

---

### Post by l-x-l on 2009-06-29
Pidgin on Linux; Digsby on Windows.

---

### Post by Andy06 on 2009-06-29
> From the page : "(except for security issues and high-severity bugs)". This is the case for *all* your packages, I hope you understand this. *Nothing* gets updated except for three things :

* Security updates
* Major bug fixing updates
* Anything that might be backported from $your_distro+1 to $your_distro.

Pidgin isn't special in this.

Yes you are right. I assumed that pidgin would auto update from 2.5.6 to 2.5.7 and 2.5.8 which would be considered minor updates and then stop before updating to say v3.0. I think I have understood it wrong.

> That's exactly that, *your* opinion. In the "real world", you'll quickly find out that outside of your friends from college and your parents, no one has serious uses for IM. Enterprise use for IM doesn't require advanced features, OR it requires using a particular client.

Not exactly. It is indeed my opinion but one shared by a great majority of people. Live messenger has market share dominance in a LOT of markets and in many places in Europe it is greater than 3/4ths.

Anyway, what I am saying is that no IM app is effective unless it offers reasonable compatibility with MSN. We can use our own apps for everything in linux but unfortunately IM is a two way street and no matter how much superior open source protocols maybe, we just have to speak a common language with the people we want to communicate with. 

You seem to be making a case against IM itself rather than any one protocol or client. So then this whole question of its features is irrelevant to you. That's fine.

But the fact that 100s of millions of users around the world use IM and that 99.999% are outside my friends circle does not change. And of these users, the majority use Windows Live Messenger/MSN, especially outside USA (where AOL/AIM/Skype take more away from MSN than in other regions).

---

### Post by Mornedhel on 2009-06-29
> **Andy06 said:**
> Not exactly. It is indeed my opinion but one shared by a great majority of people. Live messenger has market share dominance in a LOT of markets and in many places in Europe it is greater than 3/4ths.

I live in Europe. About everyone has an MSN account here, including me. It *is* a necessity if you want to communicate with your friends, I'll grant you that.

> **Andy06 said:**
> Anyway, what I am saying is that no IM app is effective unless it offers reasonable compatibility with MSN. We can use our own apps for everything in linux but unfortunately IM is a two way street and no matter how much superior open source protocols maybe, we just have to speak a common language with the people we want to communicate with.

You seem to be making a case against IM itself rather than any one protocol or client. So then this whole question of its features is irrelevant to you. That's fine.

Not exactly. My point is that I consider text-only chatting a sufficient implementation for most purposes. It certainly is "reasonable compatibility" and "the basics". I don't need the nudge feature and can't really understand its point.

I regularly use IM. The first thing I do when I start my computer is start my two IM client (ok, so the first's ERC, but the second is Pidgin), unless I'm at work.

As for the question of the superiority of open source protocols, I have not examined them in enough detail that I could confidently tell you that XMPP is technically superior to MSN. I can however confidently tell you that it's by far better having open source protocols than closed protocols. It is self-evident when you observe the difficulties the libpurple developers have in reverse-engineering MSN. There is also the matter of general popular inertia to consider, obviously : everyone uses MSN because everyone has MSN, and no one uses Jabber because no one has Jabber.

I *really* feel old when people tell me being able to send custom emoticons is a basic feature of IM...

Now I've said all this, it seems like I've hijacked the thread with my get-off-my-lawn rant. I just wanted to point that "the basics" of IM was sending and receiving text and that there might be people who would consider that enough for their purposes. Let's get back on topic :

Empathy and its underlying framework Telepathy are the current effort in GNOME in IM and contact management, so it's no surprise it's being developed more actively than most. Due to this fact, Pidgin probably suffers from a lack of developers since it's not very attractive to develop for a project that's going to be scrapped as far as the main GNOME development is concerned.

(Trying to get back on topic after a rant is really awkward, it seems.)

---

### Post by Andy06 on 2009-06-30
It will be interesting to see what happens to pidgin's popularity henceforth. Currently it is extremely popular due to the familiarity since it is default for Ubuntu (and GNOME?), in fact I see plenty of people use it on windows. 

With Empathy becoming the GNOME default and perhaps more importantly, the ubuntu default, its popularity will skyrocket and if it can keep up the development pace, pidgin will have no niche to cater to since KDE use Kopete which integrates nicely, Mac OS X has Adium and ichat and virtually no MAC user uses anything else, and finally for windows we have all the proprietary clients.

BTW, is Gossip simply the predecessor of Empathy? The always reliable wikipedia page for empathy seems to imply so.

---

### Post by Andy06 on 2009-06-30
BTW, could the users voting for the "Others category" please let us know which one they use specifically. The list is by no means comprehensive and I may well have missed out a major client.

Where are the KDE users? Kopete still at 0 votes?

---

### Post by theozzlives on 2009-06-30
If you like Pigin, go to Accounts > Edit Account > Avanced Tab, and enter "cn.scs.msg.yahoo.com" as your paging server. I did that and can connect to yahoo.

---

### Post by Andy06 on 2009-06-30
They already solved the issue with yahoo in 2.5.7. No need to modify anything :)

---

### Post by ~sHyLoCk~ on 2009-06-30
Pidgin for me.

---

### Post by X1R1 on 2009-11-17
Another pidgin vote, development its pretty good and integration its too, also, if you like something you can just install it on the new version, everytime I do a fresh install on ubuntu I remove transmision and install deluge (for torrents) for example, would do the same for pidgin.

But its true, it can skyrocket empathy popularity and that can make a pretty good field of competition between pidgin and empathy, and competition are always good for users because developers tend to improve software even more and feel encouraged to beat competition :popcorn:

---

### Post by fromthehill on 2009-11-17
I use emesene 1.5 (on 1.0 some thing don't work)
used amsn for a while but don't like the interface

---

