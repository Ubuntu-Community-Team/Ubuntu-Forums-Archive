---
title: "CUPS, Samba, TCP/IP and Authorization"
date: 2007-12-10
forum: Networking &amp; Wireless
---

### Post by jharadie on 2007-12-10
A WinXP shares a printer on the LAN (Canon i560).  CUPS found it (shows as a Samba printer, smb://xpmachine/Canoni560), works OK.  CUPS lets this printer accept TCP/IP ([http://mydomain:631/printers/Canoni560](http://mydomain:631/printers/Canoni560)), family and friends around the US can send me stuff.  So far so good.

The problem is authentication.  Right now I must Allow All, which is not acceptable.  BUT, making ANY change (System -> Printing -> i560 -> Access Control) creates a Deny All situation.  I would like to use "Deny printing for everyone except these users:" but when I add a user name (one registered on Ubuntu), it denys even that user.  Should I be inputting "user password" (or some variant) instead?  I've read CUPS documentation, Ubuntu Forums, and Googled every keyword combo I can think of.

FWIW, I went to xpmachine printer properties for that printer, but could find no security.  Went to xpmachine Help and Support (aka Waste of Time), followed instructions for getting to security tab, no luck.

Running Ubuntu 7.10.  Long story as to why I can't move printer to Ubuntu machine.

Is this a bug, or am I the one that's buggy? :)  All help appreciated.  Thanks.

---

