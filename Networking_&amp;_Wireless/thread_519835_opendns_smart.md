---
title: "opendns smart?"
date: 2007-08-07
forum: Networking &amp; Wireless
---

### Post by tocleora on 2007-08-07
A coworker of mine (we're both in IT) wants to use OpenDNS for our company's network because of it's reporting capabilities.  We do a lot of credit card transactions and such (hundreds a day).  Is this a smart thing to do?  Thanks in advance.

---

### Post by david_ulevitch on 2007-08-07
> **tocleora said:**
> A coworker of mine (we're both in IT) wants to use OpenDNS for our company's network because of it's reporting capabilities.  We do a lot of credit card transactions and such (hundreds a day).  Is this a smart thing to do?  Thanks in advance.

Of course it is.  And if you give us feedback, we'll make the stats better.  We need to know what users want.  Plus, we're more reliable than your ISP and let you see detailed insights into your traffic that is otherwise a PITA to get.  Oh, not to mention you can block any hostname from resolving on the fly -- like the next big botnet or worm that uses DNS. :-)

---

### Post by tocleora on 2007-08-08
I guess my concern is, every thing we do on the internet is stored on opendns, no?  every request we make small or large hits opendns before it goes anywhere else, correct?  So a 3rd party stores all of our data on their server, or I guess, your server. ;)  Does that make sense why I'm concerned?  I *am* the overparanoid one in our company... lol How secure are we in that manner?

---

### Post by kevdog on 2007-08-08
opendns breaks winbind if you are using this in combination with samba to identify computers by name rather than ip address.

---

