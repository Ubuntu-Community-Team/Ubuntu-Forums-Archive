---
title: "Advice: Ubuntu Fileserver in Windows environment"
date: 2006-11-22
forum: Networking &amp; Wireless
---

### Post by _axiom_ on 2006-11-22
I was approached about setting up a Linux file server for a small company, because they are having problems with their current Windows based one.

One of the problems they had was dealing with date stamps, and the server wanting to update the datestamp of every file open their hd, really slowing things down.

I could probabbly set this up with samba, but one of thing they are interested it is weather the NTFS metadata will play nicely with a linux fileserver. (I have no illusions of setting up NTFS on ubuntu, I would probably just use ext3, or whatever the default is.)

The specifically wanted to know about the last modified dates on the files.  Would it show when they were actually last changed, or when they were saved to the server.  I didn't know.  

Anybody out there doing this?  Any other advice is welcome too.

---

