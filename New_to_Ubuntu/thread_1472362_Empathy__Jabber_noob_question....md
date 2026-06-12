---
title: "Empathy / Jabber noob question..."
date: 2010-05-04
forum: New to Ubuntu
---

### Post by pcal on 2010-05-04
Sorry to have to ask such a noob question - but it seems everyone assumes that everyone already knows and I can't find any info basic enough...

I've never used any sort of IM client before.

Have just upgraded my netbook to 10.04 and decided to figure out what Empathy does. Did some research which suggested Jabber was the open source system of choice for widest interoperability, and tried to open an account with jabber.org only to find they are not taking new accounts just now. So, after looking at the list of alternate servers on their site opened an account with another server.

Entered the new account details into Empathy, got an "Available" status after a few log in attempts, browsed the Room/Join option and under "+Room List" found only about 6 rooms, with nearly 4 subscribed members in total...

This was a little underwhelming.

Clearly I've not interconnected with anything and am looking only at some small backwater server's local rooms. Do I need to create an account with every server out there to make the system inter-operable (surely not!), or is there some other setting that has alluded me in Empathy that will connect me with the whole net rather than just the minute corner I've happened upon?

Thanks,

Pcal

---

### Post by madjr on 2010-05-04
hello i recommend you start with xchat:

[http://screencasts.ubuntu.com/Installing_and_Using_XChat-Gnome](http://screencasts.ubuntu.com/Installing_and_Using_XChat-Gnome)

[https://help.ubuntu.com/community/XChatHowto](https://help.ubuntu.com/community/XChatHowto)

[http://www.ghacks.net/2010/01/23/install-and-use-xchat-to-take-ubuntu-classes/](http://www.ghacks.net/2010/01/23/install-and-use-xchat-to-take-ubuntu-classes/)


you may also try pidgin (which is like xchat and empathy in 1)
[https://help.ubuntu.com/community/Pidgin](https://help.ubuntu.com/community/Pidgin)


set up both see which one works best for you. Xchat also has much more options, it's a full IRC (internet relay chat) client

---

### Post by peculiar penguin on 2010-05-04
While Jabber also supports chat rooms, that feature hasn't exactly replaced  [IRC]("http://en.wikipedia.org/wiki/IRC"). So if you're looking for public chat rooms with people inside, set up an IRC account and use that. You could try [Ubuntu's IRC channels]("http://www.ubuntu.com/support/community/chatirc") for a start.

---

### Post by pcal on 2010-05-05
Thanks guys... although I'm not really any the wiser about what exactly the point of jabber / empathy "is" (as opposed to "isn't"!). I can only assume it must be good at something in order to have been chosen for default inclusion in the ubuntu distro...

I guess it's mysteries will just have to remain for a while longer.

Pcal

---

### Post by peculiar penguin on 2010-05-05
Welp, hard to explain without a short novel...

The point of instant messaging (IM) in general is communicating (usually by text messages, but voice/video may also be possible) with other people you "know" - be it in person or just as an anonymous screen name. If you've never used IM before, your contact list is probably empty and therefore not very useful right now.

If you want to send someone an e-mail you need their e-mail address, and it's the same with IM - if you want to talk to someone directly, you need their IM name. You'd tell your IM client to add that person to your contact list, after which you should get some sort of status information from the IM network/server (i.e. if that person is online and available or not). If the person is online, you generally can double click on their name in your contact list and send messages back and forth in a window that pops up.

So far this is private communication (unless rogue server operators, ISPs, or law enforcement come into play) between specific users who know each other, resp. their IM names. As mentioned before there's also chat rooms, which are different in that they're generally considered public, since anyone who knows the room (or "channel") name can enter and take part in whatever goes on inside.

Now, Jabber (resp. XMPP, as it would like to be called these days) simply is an open instant messaging protocol. There are countless other IM protocols, most of them proprietary. Microsoft has MSN Messenger or Live Messenger or whatever it's called now, AOL has AIM (and just sold ICQ to some Russian company, IIRC), Yahoo runs Yahoo! Messenger and so on.

Empathy is an open source IM client. Unlike the proprietary IM clients made by the companies mentioned in the previous paragraph, it can talk to more than just one single IM network - that's why it is included (or in previous Ubuntu versions, Pidgin was included) by default. This saves you from having to install and use multiple, different IM clients to communicate with people on different IM networks. So if you want to talk to someone via Jabber, sign up for a Jabber account, add it to Empathy, add the contact and chat away. If you need to talk to someone on AIM, you'll still have to sign up for an AIM account, but you can also add that account to Empathy and use it there, instead of having to install another IM client just for AIM.

Sorry if this was too basic, but it's hard to tell what your exact question was...
Wikipedia also has an [article on Instant Messaging]("http://en.wikipedia.org/wiki/Instant_messaging").

---

### Post by pcal on 2010-05-06
Not too basic at all!

Just the sort of foundational understanding that is so hard to get when you're not part of the "first wave" with any new system. "Jabber = protocol" was the missing Rosetta stone. I now know enough to ask the right questions about anything further I need to know - thank you.

Pcal

---

### Post by mastablasta on 2010-05-06
> **peculiar penguin said:**
>  
If you want to send someone an e-mail you need their e-mail address, and it's the same with IM - if you want to talk to someone directly, you need their IM name. 
 
Except for at least ICQ that one used to have (probably still has) the ability to find someone (their IM name) to talk too based on their interests and such. hence the ICQ (I seek you).
 
Also IM are not anyhting new as they have been arround for quite some time now. (well over 10 years). :p

---

### Post by victorhugo289 on 2010-07-10
Hello everyone, 

hi peculiar penguin, your information is good but I already knew it, sort of, am I correct in the next: ??

-UBUNTU 10.04 --------->  EMPATHY  -----------> Jabber  ----------------> msn
----------------> gmail
----------------> yahoo

I added a Jabber account in Empathy, it's the only account, does that mean that I am able to add "msn" -"gmail"- "yahoo" contacts without adding a respective msn, gmail, yahoo account in the same Empathy??? 

If I understand correctly, jabber is ALL i need to talk to msn, gmail, and yahoo.

------------------
I think it is not working...

---

### Post by Blümchen Blau on 2010-08-04
@victorhugo289:

You're wrong. Jabber (XMPP) is a protocoll like those of "msn, gmail, and yahoo" and others.

BB

---

