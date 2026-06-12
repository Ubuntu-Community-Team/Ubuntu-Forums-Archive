---
title: "Connecting to Microsoft Exchange 5.5"
date: 2007-11-13
forum: Networking &amp; Wireless
---

### Post by mesocal on 2007-11-13
I've been searching for some solution or way to connect to my works exchange server which is MS Exchange 5.5.  But so far all i found out is that there is no support.  any help would be much appreciated.

Thanks.

---

### Post by veloce on 2007-11-13
> **mesocal said:**
> I've been searching for some solution or way to connect to my works exchange server which is MS Exchange 5.5.  But so far all i found out is that there is no support.  any help would be much appreciated.

Thanks.

I'm not up with version numbers but Evolution connects to ms exchange on windows server 2000 and windows server 2003.

---

### Post by HermanAB on 2007-11-13
If Exchange has IMAP enabled, then you will have no problem.  Otherwise if only DCE/RPC is available, then you would need an Outlook Connector.

If you are responsible for the Exchange server, then do yourself and your users a massive favour and replace it with Citadel [http://www.citadel.org](http://www.citadel.org).  You can replace a whole rack full of Exchange servers with a single Citadel server - but do add a second one for backup...

Cheers,

Herman

---

### Post by mesocal on 2007-11-13
I dont have any control over the exchange server.  i can connect with IMAP but what are the pros and cons of that? would i have to have it check periodically for the new mail as oppose to automatically updating my inbox?

---

### Post by veloce on 2007-11-14
> **mesocal said:**
> I dont have any control over the exchange server.  i can connect with IMAP but what are the pros and cons of that? would i have to have it check periodically for the new mail as oppose to automatically updating my inbox?

The only downside is that you only get mail, no access to your calendar.  If you don't need that, then you are much better off with IMAP.  You should be able to set your email client to check at whatever frequency you want - same as connecting to exchange.

---

### Post by mesocal on 2007-11-14
Thanks.  I do need to be able to view my calendar and access to my contacts.  There must be some plugin or software somewhere that can solve this.  i wish i could solve this on my own, but im far from that point.

Any other ideas on connecting Evolution (or anything on linux for that matter) to Microsoft Exchange 5.5?

---

### Post by veloce on 2007-11-14
> **mesocal said:**
> Thanks.  I do need to be able to view my calendar and access to my contacts.  There must be some plugin or software somewhere that can solve this.  i wish i could solve this on my own, but im far from that point.

Any other ideas on connecting Evolution (or anything on linux for that matter) to Microsoft Exchange 5.5?

Evolution uses the exchange web interface from 2000 and 2003.  If 5.5 doesn't have a web interface then there is no public interface that can be used.

---

### Post by mesocal on 2007-11-14
Interesting, hmmmm.

But I do believe there is a web interface for Exchange 5.5.  I login once and a while from home on my webmail.company.com/owa link.  Is that the web interface that you are referring to?

---

### Post by veloce on 2007-11-14
> **mesocal said:**
> Interesting, hmmmm.

But I do believe there is a web interface for Exchange 5.5.  I login once and a while from home on my webmail.company.com/owa link.  Is that the web interface that you are referring to?

have you tried setting up evolution using that link?

---

### Post by mesocal on 2007-11-14
ive tried a few times,  but i keep on getting a message that says something to the extent of "Can only connect to MS 2000 and 2003 and that i am trying to connect to Exchange 5.5" i remember a few months ago reading about a plugin that could be purchased - even though thats against my linux beliefs.

Hmmm. there must be a solution, i know i cannt be the only one with this issue.

---

### Post by dude1981 on 2007-11-19
Hi!

I've the same problem... Either without any solution... :(

---

### Post by dude1981 on 2007-11-19
This could be a solution: [http://www.42tools.com/node/23](http://www.42tools.com/node/23)

But there isn't any version for gutsy...

---

### Post by mesocal on 2007-11-20
Thanks for that post.  I knew there was at least one program that could do it.  unfortunately,  im on a x86_64 system and im running into a lot of errors for this.  

thanks, i still havent found a solution yet.  anyone else have any ideas.

---

### Post by colding on 2007-11-21
Hi, I wrote most of the stuff at 42tools.com - mainly Brutus Server and evolution-brutus. Could you please tell me which errors you are running into? If you are struggling with evolution-brutus, then please try this:

./autogen.sh && make distfiles

With a little luck you should end up with gutsy debs. You are welcome to write me at colding AT 42tools DOT com if you continue to have problems.

HTH,
  jules

---

### Post by mesocal on 2007-11-21
Well, you are the pro.  So let me give it another shot.  Is there a step by step guide that i could follow to make sure that im doing this correctly.

---

### Post by zoro on 2007-12-05
Colding - is there any possibility of you providing a .deb for Gutsy?

---

### Post by jonallport on 2007-12-05
Off topic:

Citadel looks interesting, how does it compare to Zimbra?

---

