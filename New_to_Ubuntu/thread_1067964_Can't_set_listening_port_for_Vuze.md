---
title: "Can't set listening port for Vuze"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by white3911 on 2009-02-12
I am trying to set up port forwarding to Vuze as outlined on portfowarding.com. The first step says to set the listening port in Vuze between 49152-65535. I have tried multiple numbers in this set; however when I click "save" the number is reverted to 49151. Help a newb out!:confused:

---

### Post by white3911 on 2009-02-13
to the top!

---

### Post by pipedreamer on 2009-09-14
Hi all,

I have just encountered the same problem as the user above and wondered if anyone could help me out. 

I started to download a file last night and now have about 57% of it. When I checked again this morning, the smily faces were yellow, indicating a NAT problem.

I followed the instructions on portforward.com however I cannot put my IP address in Vuze any higher than 49151 - whereas portforward tells me I need to enter anything from 49152 upwards. 

Vuze also informs that ports 49152 and upwards are private and cannot be used.

I am running Ubuntu 8.10 Intrepid, and Vuze version 3.1.1.0-3ubuntu3, if that's any help. I really don't want to lose the torrent I'm halfway through downloading, so if anyone could help me I'd be really grateful.

Thanks all!

Rachel

---

### Post by earthpigg on 2009-09-14
hi,

intermittent problems like this could be your home router or computer's network interface card going bad. has been known to happen.

alternatively,

your ISP may be meddling in the middle and killing this connection under the ignorant assumption that "ALL TORRENTS ARE ILLEGAL PIRATING!!!!".... after you run off to bed, they can see that the only traffic going to/from your house is .torrent traffic on port X and conclude that you are in bed and they can kill it without you noticing.

this is something that has picked up in the last year or two, with more ISP's jumping on the Bandwagon of Ignorance.

one thing you could try is leaving pidgin logged in... this will create a bit of non-torrent traffic as your buddies log in and out that may or may not throw them off. maybe leave firefox with the 'reload every' addon set to reload cnn.com or something every 10 minutes while you are in bed.

another way to confirm this would be to connect to a different ISP with the exact same computer and see if things suddenly start working. if its a laptop, bring it to a coffee shop or two with wifi and try it there. if its a desktop, maybe find out if the neighbors use a different ISP and ask them kindly if you can use their wifi for a day to test it.

alternatively, you can call the ISP and try to get a direct answer from them. good luck.


EDIT: i should mention that my tin-foil hat and paranoia has been known to suddenly flip on and into overdrive from time to time with little justification. this may be one of those times, but i remain squinting my eyes and glaring at your ISP as we speak. a well-seeded torrent generally doesn't just suddenly die like that at 57% done.

---

### Post by earthpigg on 2009-09-14
[http://azureuswiki.com/index.php/Bad_ISPs](http://azureuswiki.com/index.php/Bad_ISPs)

---

### Post by pipedreamer on 2009-09-14
Thanks very much for the help - do you know of any reason why Vuze won't let me enter the port numbers recommended by portforward? It says they are private, but the portforward worked with my last PC (windows XP OS), and not here.

Thanks!

Rachel

---

### Post by earthpigg on 2009-09-14
just came across this:

[https://bugs.launchpad.net/ubuntu/+source/azureus/+bug/264950](https://bugs.launchpad.net/ubuntu/+source/azureus/+bug/264950)



> Hi,
I just wanted to say that, as goto mentions, as of 7 February 2009 many parts of the Azureus wiki seem to be really outdated. New users trying to configure their azureus/vuze should be careful when taking information from there.

In summary, even if the Azureus wiki tells you to "Choose a port from the 49152&#8211;65534 range", you should in fact choose a port not included in that range.

I make this post only for clarification, since this bug report appears as one of the first results in your favourite search engine when searching for this problem.

---

### Post by quequotion on 2010-01-12
Sorry to revive an onl thread but i think the conclusion to this is ridiculous. Basically, users are now forced to use a port that is reserved for another purpose. It's not only a bit scandalous, but also potentially disrupting to network services (you could inadvertently DOS *yourself*...)

I suppose this will have to be taken to the Vuze developers to get an explanation, but I have to wonder if the choice wasn't made to hide torrent traffic within other packets.... which will eventually lead to ISPs shutting down those services as well (and they will, trust me... customer service and standards compliance mean nothing to most of these companies; even following the **law** is less important than avoiding a lawsuit).

There should still be some way to specify a higher port manually, as there are cases in which using a reserved port is not an option.

Case in point: I connect to the internet through a cell phone. As the phone itself has very limited capabilities, only the "Well Known Ports" are open. The "Registered Ports" cannot be used **at all**. There's no way to proxy to them either as the phone features no software to connect to a proxy. However, one, and only one, of the Dynamic ports is open (for reasons unspecified, most likely to handle some service provided by my cellular provider) unfortunately it is 62078; which cannot be set in the current Vuze.

---

### Post by gtr225 on 2010-02-06
To use a higher port, just download Vuze directly from sourceforge.

---

