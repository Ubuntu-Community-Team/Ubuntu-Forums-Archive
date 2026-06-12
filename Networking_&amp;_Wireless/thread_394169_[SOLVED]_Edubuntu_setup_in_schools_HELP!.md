---
title: "[SOLVED] Edubuntu setup in schools HELP!"
date: 2007-03-26
forum: Networking &amp; Wireless
---

### Post by tentwelveeight on 2007-03-26
I am a K-5 Technology Teacher at a charter school in San Diego, Ca. and I would like to set up several ltsp servers with about 5 thin clients using Edubuntu in the classrooms here. Unfortunately the network setup in the district is not conducive to this situation. From what I understand the computers at our school all have unique IP addresses until they go onto the web, at which point they are all routed to a single IP address. This is supposedly a common practice for large organizations (our district has several dozen schools). Until now I have been trying to set up a DHCP server on an old P4 Compaq and boot off of it with an old P3 Gateway as the thin client, but I haven't gotten it to work for some reason (maybe someone could do a REAL step-by-step on this to help out us educators?). Now I'm told it would be a bad idea to install any DHCP server of our own at all, as it would conflict with the district's own DHCP server. Is there any way I can still set up these servers and thin clients? Thanks for any help. -joe

---

### Post by Yogi3 on 2007-03-27
I am surprised nobody has tried to help, so I offer my 2p worth.

> > **tentwelveeight said:**
> I am a K-5 Technology Teacher at a charter school in San Diego, Ca. and I would like to set up several ltsp servers with about 5 thin clients using Edubuntu in the classrooms here. <

I do not get quite what you mean other than you are setting up a LAN. (Local Area Network).  I assumme only one will be an Internet server (or gateway).  What else goes on on your LAN I do not THINK is relevant to the question.

 > Unfortunately the network setup in the district is not conducive to this situation.<

I am not American and I do not undersatnd 'the district'.  You have a LAN. over which you have control, and you wish to connect this to the Internet.

  > From what I understand the computers at our school all have unique IP addresses until they go onto the web, at which point they are all routed to a single IP address. This is supposedly a common practice for large organizations (our district has several dozen schools). <

It is bog standard practice for connecting a LAN with static addresses to the Internet via an 'Internet server' or 'gateway'.  (Effectively synonimous names for the same thing.)

Excactly the same if the addresses are dynamic (i.e. controlled by a DCHP server), and the adresses must still be unique at any one  time, but they are no longer long term unique to any one node, be it a server or a client.

The gateway, or 'Internet server'  does "Network Address Translation" (NAT), making all the computers on the LAN have the same IP address to the rest of the world.  It keeps track of which traffic belongs to which computer by using different port numbers. A gateway that does not offer NAT by default would be unusual and specialized.

>Until now I have been trying to set up a DHCP server on an old P4 Compaq and boot off of it with an old P3 Gateway as the thin client, but I haven't gotten it to work for some reason (maybe someone could do a REAL step-by-step on this to help out us educators?).<

It would also be unusual to find a gateway that did not offer to be a DHCP server for the LAN, and the majority seem to come configured assumming you want this.  However, it would be an exceptionally unusual beasty it you could not switch this service off.  You don't seem to say what gateway you are trying to use!

 > Now I'm told it would be a bad idea to install any DHCP server of our own at all, as it would conflict with the district's own DHCP server. <

I repeat. I don't understand 'district'.  Just don't have two DHCP servers on one LAN!
If you have one, you are using dynamic (I.e. not static) IP addressing on your LAN.  If you don't have one, you must allocate addresses yourself, and this is called static or fixed IP addressing.  I repeat, just make sure you don't have more than one, this could be your problem.  'Servers', be they Internet gateways, or  ones primarily put there for other things tend to offer DHCP services, and you MUST switch this off in all but one.  Which one probably does not matter.  I can feel all the dye hard network administrators now going 'Tut tut, it should be the Internet gateway.'.  However, if there are reasons not use it e.g. you don't want to always switch it on, or you don't want to interfere with the present LAN setup, then don't.
The primary downside would be causing confusion to others who may work on your LAN by being unconventional. 

 > Is there any way I can still set up these servers and thin clients? Thanks for any help. <

Yes, services on LANS tend to function moderately independently, unless two devices are trying to control exactly the same service.

-joe

Yogi3

---

### Post by Yogi3 on 2007-03-28
Sorry I get verbal diarrhoea when I'm 99% asleep waiting for my wife to come to bed, or did you like my lesson?  Anyway, get a bog standard ADSL to Ethernet gateway. If it has not enough holes get an ethernet switch. Connect each computer to it, leave everything in default.  Leave off anything that might have been a DHCP server. Open a browser and the gateway asks for your username and password, as got from your ISP.  (If it does not default to doing this I'm afraid its a bit of RTFM) You have just followed the path taken by millions before you.  What's the problem?  Something you left left off because it  was a DHCP server also did something useful?  You will have to say what.

Yogi3

---

### Post by Yogi3 on 2007-03-28
Perhaps I am confused over what you want when you say 'ITSP' servers and 'Thin clients'.  AFAIK ITSP refers to early days of what has become VOIP (Voice Over Internet Protocol) and we are talking about telephones not Linux.  Linux can, of course, host VOIP, but that is hardly 'thin'. If that is regarded as some sort 'server' its 'clients' surely must look like telephones???? I am completely confused.  In any event, whilst a LAN may transport the packets, this is not a lot to do with LAN addressing.  Have I missed the plot completely?  Please describe what you mean.

Yogi3

---

### Post by hboshoff on 2007-03-28
> **tentwelveeight said:**
> I am a K-5 Technology Teacher at a charter school in San Diego, Ca. and I would like to set up several ltsp servers with about 5 thin clients using Edubuntu in the classrooms here. Unfortunately the network setup in the district is not conducive to this situation. From what I understand the computers at our school all have unique IP addresses until they go onto the web, at which point they are all routed to a single IP address. This is supposedly a common practice for large organizations (our district has several dozen schools). 

Your individual computers probably keep their unique IP addresses (possibly in the private range) for local communication on the LAN. The Internet gateway only shows a single public IP address to the outside, doing NAT translation for Internet traffic between local computers and the outside. This should not affect the LAN traffic or addressing.

One possibility is using a computer with two network cards for the Edubuntu server. One card gets its address from the upstream DHCP server, and both the server and clients have Internet access through that interface. On the other card, your server offers DHCP service and LTSP access to the thin clients. Isolate the clients on separate network segment; you will need a separate network switch for that.

> **tentwelveeight said:**
> 
Until now I have been trying to set up a DHCP server on an old P4 Compaq and boot off of it with an old P3 Gateway as the thin client, but I haven't gotten it to work for some reason (maybe someone could do a REAL step-by-step on this to help out us educators?). Now I'm told it would be a bad idea to install any DHCP server of our own at all, as it would conflict with the district's own DHCP server. Is there any way I can still set up these servers and thin clients? Thanks for any help. -joe

It would indeed be a problem if you have two competing DHCP servers on the same network segment. Are you using Edubuntu on the Compaq, or doing it another way? Booting thin clients involves a number of steps, all of which are taken care of by the Edubuntu server. You may want to do your tests off the school network, until you are satisfied that your setup works. Please involve the network administrator in planning to integrate your thin client clusters with the school LAN.

---

### Post by Yogi3 on 2007-03-28
DUH!!!, the Linux Terminal Server Project, how stupid of me not to think I had mis read a letter.  Now your thin clients make sense.

AFAIK each 'Server' is at the centre of its own networked cluster of clients. Also the servers can also be networked together, and be clients of what _I_ will call a 'mother' network.  However, each LTSP network must be logically isolated (In practice read physically isolated), and also be similarly  isolated from the 'mother' network.  The only real solution to this is to have two network cards in each LTSP server, one for being a client on the 'mother' network, and one to serve its thin LTSP clients.  (Via its own ethernet switch.) As these networks are isolated, each can have its own DHCP server.  By the way LTSP has been made to work each LTSP server _will_ be DHCP.  The way the 'mother' network functions is completely independant of this, each LTSP server simply appears as a 'computer' (even if it has got several users!) and as a client it simply obeys the mother network rules.  (I.e. the mother network is unaware of the LTSP network, let alone its DHCP properties). Presumably the Internet comes in through the 'mother' network, from a source independant of the LTSP concept.

Yogi3

---

### Post by tentwelveeight on 2007-03-29
Yogi and hbo, thank you for all the time you have spent on my problem. I appreciate it very much. Let me clarify my situation a bit before I proceed. 

In America each school (primary and secondary) is grouped together into a district of schools. My district happens to be a very large district with many schools besides mine in the district. Our school, and all schools in our district, gets Internet service from an office somewhere far away at a district building. 

I do not have access to the gateway server nor do I have the ability to add smart switches to the network. These privileges are restricted for district employees only. I only have the power to change things "on the outside of the walls".

What I would like to do is set up 15 different LTSP servers in 15 different classrooms, with 2 network cards in each server, one to connect to the "upstream" district network and one to connect the "downstream" thin clients. Since I would like each server to serve 6 thin clients in every classroom, this means a total of 105 different machines running in 15 different classrooms. This will let every teacher in the school have a station of 6 thin clients and 1 server that their students can use.

Since I have no way of separating any of these computers from the main district network, I think I will need to find some other way to serve thin clients. Can you tell me:

Can Ubuntu DHCP servers be configured to only supply IP addresses to network cards based on their hardware address?

Is there a small software program that I can install on the hard drive of each thin client that tells the machine to go to a specific server and be served like a thin client?

Thanks again for all the help, I'm starting to understand more about networking and maybe soon I'll be able to solve the problem and help raise a new generation of linux users. Cheers -joe

---

### Post by bcmiller on 2007-03-29
I am sorry if Im confusing the issue... but I don't understand why you need a DHCP server to connect upstream.  

Your DHCP should dole out IPs to your thin clients and translate thier packets to be passed upstream as if they came from your computer.  

The thin clients are just separate accounts all running from your host computer with thier own monitors, keyboard and mice.  Your computer goes upstream like always with the thin clients tagging along.  

I am also trying to set up LTSP using Edubuntu, but at my home so my daughters ancient computer can be reborn.  Again If Im wrong please disregard.  

Good luck, what you are doing is very important.  I'd love to have a whole crop of kids whose first and lasting experience with computing is linux.

P.S.
You may also look for help at [www.linuxquestions.org](www.linuxquestions.org) it's a great forum for all distros and I have seen a lot of LTSP help on there.

---

### Post by tentwelveeight on 2007-03-29
BC, thanks for the reply. I hope you are right, this would be wonderful if it could work! I think the default setting in edubuntu is as a DHCP server, so I guess I would have to change that to some other kind of server?

Also, how could I test this? Right now I have two NIC cards on the server (is this redundant?), with eth0 on the motherboard and eth1 on the PCI slot. Then I have eth0 connected to the Net and eth1 connected to a hub that connects to the thin client. In "Network Settings" if I set eth0 to DHCP I get the Web on the server. No matter what I do with eth1 though (DHCP or static address), I can't get the thin client to boot up. I can ping the server from the thin client in DOS so I know they can see each other, but I have never got the thin client to fire up, I'm not sure what I'm doing wrong.

Let me know how you get your daughter's system up and running if you have the time. I'm off to check out your link. Thanks again -joe

---

### Post by Yogi3 on 2007-03-30
Tentelveeight,

 > In America each school (primary and secondary) is grouped together into a district of schools. My district happens to be a very large district with many schools besides mine in the district. Our school, and all schools in our district, gets Internet service from an office somewhere far away at a district building. <

Of great interest to me, thank you.  I suppose they use this to implement policies and prevent shool children accessing places they should not do they?  In this country (UK) it seems to be up to each school.  Anyway, as far as your LTSP enterprise is concerned, this is what I called your 'mother network'.  In each computer that will become a LTSP server you must set up your device for this network (i.e. eth0 in your case) just as if it never will be an LTSP server. I don't know your 'district rules' but I strongly suspect it is a DHCP _CLIENT_ (which is the default).  However, whatever it is, you appear to have done it.  Leave it. it is now completely irrelevant to your project, and if it works don't fix it.  You district will be wondering how there is enough room on its little screen for enough windows for six children, and how they magically pass the keyboard round to each other several times a second. That's their problem. (Of course they know really, and I don't know your district rules about permission to do what your doing, but do you get the drift of what I am saying?) As far as the 'mother' network is concerned you are merely adding 15 computers.

 > I do not have access to the gateway server nor do I have the ability to add smart switches to the network. These privileges are restricted for district employees only. I only have the power to change things "on the outside of the walls". <

You are not going add anything or do anything to the 'mother' network other than put 15 computers onto it just as if the LTSP never existed.

> Since I have no way of separating any of these computers from the main district network, I think I will need to find some other way to serve thin clients. Can you tell me:

Can Ubuntu DHCP servers be configured to only supply IP addresses to network cards based on their hardware address? <

It works through the concept of devices, but ultimately the Interfaces are distinguished by the MAC addresses. The answer is yes.  However, you don't worry about that.  Your job is to attach 'eth1' to the LTSP project, then connect the associated card, via a common or garden switch or hub, to your six thin clients. You altimately let the project worry about addresses. It should NEVER interfere with the 'mother' network or eth0, and you don't have to work out why.

> Is there a small software program that I can install on the hard drive of each thin client that tells the machine to go to a specific server and be served like a thin client? <

Each thin client should go to a hub or switch that goes to 'eth1' on its LTSP server. It must not have any physical contact with the 'mother' network, it does not know about the mother network, and will never find out anything about it.  It does not need any such software. 

 > Right now I have two NIC cards on the server (is this redundant?), <

NO!!! your are doing it perfectly correctly.

  > with eth0 on the motherboard and eth1 on the PCI slot. Then I have eth0 connected to the Net and eth1 connected to a hub that connects to the thin client. <

The way round everything is is actually up to you, but you have chosen the obvious 'default' and for clarity I am wording messages assumming this.

>  In "Network Settings" if I set eth0 to DHCP I get the Web on the server. No matter what I do with eth1 though (DHCP or static address), I can't get the thin client to boot up. I can ping the server from the thin client in DOS so I know they can see each other, but I have never got the thin client to fire up, I'm not sure what I'm doing wrong. <

You are doing EVERYTHING correctly and you have finger problems with the LTSP
project.  I am afraid the only way I can help further is to get dirty hands and dig into the depths of the project.  What I want to emphasise at this stage is that this is a case of us both RTFM of the project, and that it has NOTHING WHATSOEVER to do with your district, its rules, its protocols, or 'eth0'.

Yogi3

---

### Post by tentwelveeight on 2007-03-30
Yogi, I can't thank you enough for your help and time, this is very encouraging for me.

You are correct that the main purpose of the district here is to centralize decision making processes, one of which is indeed how the porn filter functions, etc. Of course it goes much further than that as well, the district handles all hiring applications, background checks, salary schedule, etc. They even handle our central heating! Of course most of the time their actual function seems to be to make our jobs more difficult than they should be. Yesterday I tried to download OpenOffice 2.2 and was blocked from the site because it was "militant, extremist, terrorist-related". Seriously.

So it seems like I had the right idea all along, which makes me wonder what I was doing wrong in the first place. Why couldn't I get the thin client to boot up? I was mostly following the documentation on the ubuntu wiki and [this site]("http://www.freesoftwaremagazine.com/articles/linux_terminal_server"), but now I suspect it has something to do with [this article]("https://help.ubuntu.com/community/ThinClientHowto"), specifically the "Tips" section at the bottom that tells how to have the thin client boot off of a specific server. Perhaps the thin client was trying to boot off of my district's DHCP server and not getting what it needed because their server is not configured for LTSP?

Besides being a K-5 technology teacher I am also a graduate assistant at San Diego State University in the educational technology department. On Tuesday my boss will be back in the lab and I plan on having him help me out with the problem. I've already dragged the server and a client to the campus so he can work on it in real time. I'll be sure to post here if we solve the problem though if you have any more ideas I welcome them with open arms. You've already been a huge help and I am very thankful for your time and advice. Once again -joe

---

### Post by tentwelveeight on 2007-04-03
SOLVED!!!!

Guys, thanks so much for your help. I think my problem the whole time was the stupid Compaq I was using for the server because I clean installed edgy on a different tower and it fired right up! No problems! This is going to be great for our school, I can't wait to get it up and running in the classrooms and show all the teachers the great offerings that Edubuntu has. Thanks again for all your help. -joe

---

### Post by Yogi3 on 2007-04-04
So glad you are sorted out!  I started several times to reply to your previous message with 'ideas' but (complex in the situation) reservations I feel about giving 'servers' 6 times the load kept bursting through, making my reply efforts too long and unhelpful.  I am particularly puzzled why this project encourages you to _want_ to boot (even thin) clients off the server.  As I am all for hardware re-use I would be very grateful if you would keep posting the success (or otherwise) of the project to the school.  Thanks

Yogi3

---

### Post by tentwelveeight on 2007-04-04
Yogi, I'll be sure to post more information about my adventures moving my school over to Linux in the future. I might resort to posting on my blog though, or the blog I keep for my school. That site is at [www.aeacs.org](www.aeacs.org). Thanks again for all your help, I think this is going to be really great for our school. The reason I'm so excited about it is because our school has really poor technology infrastructure right now. Most of our computers are something along the lines of Pentium 3s running on 128 MB of ram, although many have less than that even. We're running Windows 2000 on most of them which is so prone to viruses that we have to have an anti-virus program running at all times. This alone pretty much takes up all the system resources of the computer. Using a computer for anything other than browsing the Internet is pretty unreasonable at this point, and even browsing the Internet can be slow sometimes. What I'm hoping to do is consolidate some of the best computers we have to be the servers and then use the others as thin clients. Basically I'm hoping the shift will lead to three things:

faster computers
more secure computers
less maintenance time (as I will only have to update the servers and not the thin clients)

Thanks again for all your help and advice, I'll be sure to post here once in a while on the progress we've made. Cheers -joe

---

