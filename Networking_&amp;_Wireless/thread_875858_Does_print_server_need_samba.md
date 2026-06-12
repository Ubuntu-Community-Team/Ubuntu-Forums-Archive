---
title: "Does print server need samba?"
date: 2008-07-31
forum: Networking &amp; Wireless
---

### Post by VenisonMogambi on 2008-07-31
Hi,

I just installed Ubuntu (Hardy Heron) and I've got my HP PSC1315 all-in-one printer hooked up via the USB port. For my next project I'd like to make the Ubuntu PC a network print server for the other two Windows XP laptops in the house (connected via wireless). So I guess I have two questions:
1. Should I use CUPS to set the Ubuntu PC up as a print server for the other two PCs?
2. Should I set up samba first? In other words, is CUPS dependent upon samba networking?

Any comments or suggestions are appreciated. 

Thanks.

---

### Post by BobMUK on 2008-07-31
I use CUPS with Samba and it works a treat.  Never tried CUPS on it's own...

2 seconds on google turned up [http://gentoo-wiki.com/HOWTO_Linux_Cups_printserver_Windows_clients_without_samba]("http://gentoo-wiki.com/HOWTO_Linux_Cups_printserver_Windows_clients_without_samba")

So:
1. yes.
2. Don't have to but it's easier.

---

