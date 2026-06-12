---
title: "Inspiron E1705 wireless (Dell Wireless 1390 802.11g Mini Card)"
date: 2006-09-27
forum: Networking &amp; Wireless
---

### Post by gigiya on 2006-09-27
I installed Ubuntu 6.06 on my Inspiron E1705 yesterday.  I've had (really) bad luck with Linux on past computers, most recently with Ubuntu a year or two ago.  From what I read on the forums, it made me want to give Linux another shot.  My biggest problem has been my wireless card.

Ubuntu doesn't detect it.  I checked the wiki and read about getting Ndiswrapper.  This is the part with which I've (so far) had trouble.  I can't enable the multiverse and universe repositories.  I go to Administration -> Software properties, choose Ubuntu 6.06 LTS (Source), choose +Add, check multiverse and universe, and again click add.  When I click close, it makes me reload and says it downloads 22 files.  When I reopen Software Properties, the multiverse and universe repositories are not checked.  I am logged into the adminstrator account (root/su/whatever you call it).  I then tried the command line method in the wiki, but I can't edit sources.list.  When I try to change permissions to be able to save it, it says operation not permitted.  I am logged in as root in the terminal.  I have no idea why it's doing this.

I posted this in wireless support despite the problem not being directly related to wireless because I figured that once the file permissions problem is solved, I'll end up having trouble with Ndiswrapper too.

I'd appreciate some help.

---

### Post by gigiya on 2006-09-27
I got my wireless internet working through a method posted on the forums.  I still have the repository problem, though.

---

### Post by cataphrac on 2008-01-08
What method did you use?  I have the same laptop and gutsy isn't detecting my wireless card.

---

