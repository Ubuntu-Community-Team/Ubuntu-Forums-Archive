---
title: "Is anybody able to connect to MSN Network over Pidgin?"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by Kosimo on 2009-01-12
Hey guys, I can't access to my MSN network using Pidgin 2.5.3. Is anybody else having this issue?

---

### Post by freak42 on 2009-01-12
I can't either:

"Unable to retrieve MSN Address Book" (in Pidgin 2.5.2 though.)

I am sure they are working on it already.

---

### Post by Kosimo on 2009-01-12
I can connect using aMSN. Maybe Microsoft is banning some "old" MSNPx to connect to their network. Pidgin 2.5.3 uses MSNP15 if I'm not mistaken, then we should all move forward to MSNP16 or newer.

---

### Post by Brynster on 2009-01-12
MS has updated its service, at the moment the new service is supported in Pidgin. (no doubt it will be shortly)

I have Empathy installed and that is connecting fine as well as aMSN

Both are available in Synaptic

---

### Post by Kosimo on 2009-01-12
> **Brynster said:**
> MS has updated its service, at the moment the new service is supported in Pidgin. (no doubt it will be shortly)

I have Empathy installed and that is connecting fine as well as aMSN

Both are available in Synaptic

Bug reported in launchpad: [https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/316350](https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/316350)

---

### Post by ww711 on 2009-01-12
> **Kosimo said:**
> Hey guys, I can't access to my MSN network using Pidgin 2.5.3. Is anybody else having this issue?

Yes, I'm experiencing the same problem...

---

### Post by halitech on 2009-01-12
I have Pidgin 2.4.3 and it was connected last night, I just disconnected and reconnected with no problems.

---

### Post by Kosimo on 2009-01-12
> **halitech said:**
> I have Pidgin 2.4.3 and it was connected last night, I just disconnected and reconnected with no problems.

Maybe 2.4.3 uses MSNP14 which is not experiencing any problem...

---

### Post by binbash on 2009-01-12
yah 2.5.3 not working...

---

### Post by theozzlives on 2009-01-12
2.5.2 not working

---

### Post by halitech on 2009-01-12
> **Kosimo said:**
> Maybe 2.4.3 uses MSNP14 which is not experiencing any problem...

possibility. I also have aMSN 0.97.2 and it is working as well. Is there a way of checking which version of MSNP it uses?

---

### Post by kellemes on 2009-01-12
2.5.3 not working.

---

### Post by fiona-conn on 2009-01-12
I think it's a server issue, folks. >.>;

I can't connect today on Windows Live Messenger (when on Vista), or via Emesene or Pidgin (on Ubuntu).

---

### Post by Kosimo on 2009-01-12
So, it's the MSNP15 the one that looks to be locked

[http://ezmiezmi.blog.hu/2009/01/12/error_unable_to_retrieve_msn_address_book](http://ezmiezmi.blog.hu/2009/01/12/error_unable_to_retrieve_msn_address_book)


During the meantime you can use aMSN, which works perfectly.

Edit: Or using Pidgin with msn-pecan plugin ;)

---

### Post by Caraibes on 2009-01-12
Same problem... I am now installing Emesene to use for a while...

Installed... Logged in... Works perfectly, thanks Emesene...

I simply disabled MSN in Pidgin (still using Yahoo, Facebook and Googletalk in Pidgin)

---

### Post by moofang on 2009-01-12
Try this quick fix:

> sudo apt-get install msn-pecan
Then change the account type in Pidgin to ‘WLM’ from ‘MSN

I didn't come up with the fix btw :) See

[http://ubuntuforums.org/showthread.php?t=1037694](http://ubuntuforums.org/showthread.php?t=1037694)
[http://yuenhoe.co.cc/blog/2009/01/pidgin-msn-woes/](http://yuenhoe.co.cc/blog/2009/01/pidgin-msn-woes/)

---

### Post by Caraibes on 2009-01-12
> **moofang said:**
> Try this quick fix:



I didn't come up with the fix btw :) See

[http://ubuntuforums.org/showthread.php?t=1037694](http://ubuntuforums.org/showthread.php?t=1037694)
[http://yuenhoe.co.cc/blog/2009/01/pidgin-msn-woes/](http://yuenhoe.co.cc/blog/2009/01/pidgin-msn-woes/)

Works perfect indeed, thanks !

---

### Post by makro on 2009-01-12
emesene works fine too!

---

### Post by Kosimo on 2009-01-13
Everything is fixed with the new Pidgin version: 2.5.4

Get it from [Getdeb]("http://www.getdeb.net/app/Pidgin")

---

