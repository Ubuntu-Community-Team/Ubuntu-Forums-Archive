---
title: "Can samaba freak out windows??"
date: 2007-08-15
forum: Networking &amp; Wireless
---

### Post by lsutiger on 2007-08-15
I had some freaky deaky stuff happen in our network over the last couple of days. Here is a synapses:

I installed Ubuntu on my office machine, which in windows logs on to a domain, which is widows server 2003. I installed samba on my machine in order to access network shares om the server.

Now, I do not know if this has anything to do with the price of wheat in russia, but....
My sidekick here and I seem to have had the same exact problem. The day after I installed samba and accessed the network shares, the server gave us an error message that there had been a 'security breach' (while in windows) and we could not access any network shares. 

I have seen this happen maybe twice in my life before. In order to fix it, I just remove the computer from the domain, then rejoin, and all is fine. It just seems a little odd that, after I installed samba, this happened. 

Is it possible that having an ubuntu machine access shares on a network server with AD installed could 'freak out' the server?

Just a wondering...

---

### Post by ihristov on 2007-08-17
I seriously doubt it.
Even if in your particular setup you have this problem the only way to find out for sure is to repeat the same thing and see if it will occur again. I would not worry too much. Just keep a mental note of the fact.

---

### Post by HermanAB on 2007-08-17
Yes, for a number of reasons:
a. DHCP - if Linux runs a second DHCP server, then it will clash with the one running on Win2003.
b. DNS - If Linux runs a DNS, then it can clash with the one on 2003.
c. Time - If Linux supplies NTP then it may confuse kerberos on Win2003.
d. WINS - Linux Samba can provide a WINS service which can clash.
e. WinBIND - Linux Samba can confuse the SMB system on Windows
...

Maybe you should start by reading this guide:
[http://aeronetworks.ca/LinuxActiveDirectory.html](http://aeronetworks.ca/LinuxActiveDirectory.html)

That will give you some idea of all the pitfalls.

Cheers,

Herman

---

### Post by lsutiger on 2007-08-17
WOW! Thanx Herman for the info and the link!

---

