---
title: "Key code problem with TB 3 download/Ubuntuzilla"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by gnometorule on 2010-01-21
I followed the instructions of the Ubuntuzilla TB 3 download:

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation)

I got TB 3 installed; however, whenever I try to confirm the key code as per this command on the page:

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29

[FONT=Verdana]my connection times out prior to actually confirming (for installation I've
simply confirmed the download manually). I've tried over a period of
one hour yesterday, and again several times today; so I doubt that this is 
a 'server down' issue. Questions:

(1) Any idea what's happening? 
(2) Any idea how to achieve confirmation?
(3) Absent that, any idea of stopping  sudo apt-get update to show this
warning (if I can't confirm keycode I'll just trust this page in the future 
(I'd hope I can) and will manually accept downloads):

W: GPG error: [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CCC158AFC1289A29

Many thanks for any help. 
[/FONT]

---

### Post by gnometorule on 2010-01-21
...was a firewall issue (/blush). 

As a new forum user, what's the etiquette if you later find errors in your own post: should i have just deleted it?

---

### Post by nanotube on 2010-01-21
> **gnometorule said:**
> ...was a firewall issue (/blush). 


exactly what i was going to suggest ;)

> 
As a new forum user, what's the etiquette if you later find errors in your own post: should i have just deleted it?

just post the solution to your own problem, as a lesson to others - precisely what you did. :)

---

### Post by J V on 2010-01-21
And mark it solved!

---

