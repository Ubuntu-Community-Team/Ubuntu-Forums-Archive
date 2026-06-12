---
title: "Limited HOSTS file size?"
date: 2008-11-13
forum: Networking &amp; Wireless
---

### Post by puckskraper on 2008-11-13
Hi all, this is my first post.  First off, thanks to everyone in these forums!  I've resolved most of my issues just by searching this forum and documentation.

Coming from XP it's said that a HOSTS file larger than 135kb should have DNS disabled.  Is this needed in Ubuntu/Linux?  I prefer to use the list at mvps.org vs. adblock etc.

Thanks in advance.

---

### Post by jonobr on 2008-11-13
Eh?

Could you explain a bit more what your doing?
I would have figured a hosts file that larger should actually be suing DNS more?

---

### Post by puckskraper on 2008-11-13
Sorry for not being clear.  I've copied the list from [http://www.mvps.org/winhelp2002/hosts.txt](http://www.mvps.org/winhelp2002/hosts.txt) and saved it to my /etc/hosts.  Everything is working fine.  When I ping an address in the list it reports as 127.0.0.1 (loopback).  My question is, as this list grows could it slow down the machine like it does in W2000/XP/Vista.  If so, is disabling DNS the solution?


Quote taken from [http://www.mvps.org/winhelp2002/hosts.htm](http://www.mvps.org/winhelp2002/hosts.htm)
"Editors Note: in most cases a large HOSTS file (over 135 kb) tends to slow down the machine. This only occurs in W2000/XP/Vista. Windows 98 and ME are not affected."
Their solution is to disable DNS.

---

### Post by jonobr on 2008-11-13
Originally in the 1970s, (you probably werent even born then :) )
all name resolution was handled using hosts files,

The list were maintained and distributed by stanford.
Hosts files got huge,
maintaining the hosts files was difficult and and as the number of connected hosts grew it became impossible to manage

thats why DNS started to do lookups in a distributed fashion.

System usually use hosts files then dns if deinfed to find a machine or other host.

From what I know, the host file on startup is loaded into memory and I do know an excessively huge file will slow things up a bit .

I have heard disabling the DNS client in windows works, however, I am not sure of the equivalent in this os.

I believe once you get that big where it is impacting service, you need to start consider using a pac file.

I have not seen any hard figures on size versus mem usage versus speed,

---

### Post by bswilson on 2008-11-13
> **puckskraper said:**
> Sorry for not being clear.  I've copied the list from [http://www.mvps.org/winhelp2002/hosts.txt](http://www.mvps.org/winhelp2002/hosts.txt) and saved it to my /etc/hosts.

It sounds like you're trying to configure your **/etc/hosts** file so that you can avoid browsing the Web with advertisements.  If this is the case, you can probably achieve your goal by using Firefox with the [Adblock Plus]("http://adblockplus.org/en/") extension.

---

### Post by puckskraper on 2008-11-13
jonobr - The 70's, you mean when disco was polluting the airwaves, thankfully no :)  Thanks for the tip about pac files.  I'm not familiar with them but a quick google shows that all browsers support them.

bswilson - Thanks but I'm not a fan of adblock and I don't always use Firefox.

I'm new to Ubuntu/Linux (1 week to be exact) but I'm bit surprised there's not more info about Linux hosts file limitations.  If this weather keeps up I'm might just see about running some tests on my own.

---

### Post by jonobr on 2008-11-13
Were you checking out the wiki on the 80's :lolflag:

---

