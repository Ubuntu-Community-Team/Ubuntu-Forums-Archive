---
title: "When adding a printer, why start with ipp:// ?"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by JDuc on 2008-12-26
I'm trying to learn a bit about why things are done the way they are in Linux.

I've successfully managed to get my printer set-up through my wireless print server (Linksys WPS54G) per this thread: [http://ubuntuforums.org/showthread.php?t=516747](http://ubuntuforums.org/showthread.php?t=516747)

However, I would like to understand why the URI format is the way it is.

For instance, why 'ipp://' ?

Why '/ipp/P1' ?

I'm guessing the P1 is printer 1?

Sorry if this seems like a simple question, I just like to understand why things are done the way they are, I tend to remember better and understand more then.

Thanks!

---

### Post by HotShotDJ on 2008-12-26
> **JDuc said:**
> Sorry if this seems like a simple question, I just like to understand why things are done the way they are, I tend to remember better and understand more then.Bravo!  It is never "stupid" to ask "simple" questions.  Better to learn all you can than to remain in the dark!  Check out this page -- I hope it helps you understand things better.

[http://www.webopedia.com/TERM/I/IPP.htm](http://www.webopedia.com/TERM/I/IPP.htm)

---

### Post by Dedoimedo on 2008-12-26
This saves you the need to specify the port, which is 631 for cups. The same way ftp:// or http:// are for these network protocols. For example, when you type http://  this means you want to use the port specified in /etc/services for the http protocol. Similarly, ipp goes for port 631.

If you run a port scan on your machine with nmap, for instance, you'll see this in action:

```

nmap localhost

```

And then, you'll see all sorts of numbers and protocol names.

Cheers,
Dedoimedo

---

