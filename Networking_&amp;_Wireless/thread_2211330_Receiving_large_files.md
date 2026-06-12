---
title: "Receiving large files"
date: 2014-03-15
forum: Networking &amp; Wireless
---

### Post by asearle on 2014-03-15
Hi everyone,

This might be a little bit off-topic but I'm sure that someone out there has a tip for me ...

I need to receive large files from contacts who will be logging in in various internet cafés without any locally pre-installed software.  Can anyone give me tips on how to receive these files?  Simply via e-mail?  Or facebook?  Or is there a more elegant way?

I was investigating "Dropbox" and FTP but software seems to need to be installed locally and for people visiting random internet cafés this is not possible.

And I was pondering having a web-site with an "upload" or "receive" option but that might start getting complicated and there must be a service which already offers something like this(?)  Yes, I don't want to re-invent the wheel  :-)

Any tips would be a great help.

Many thanks,
Alan Searle

Cologne, Germany

Happily using Ubuntu 13.10 on my Samsung Series 5 (ultrabook-style laptop)

---

### Post by howefield on 2014-03-15
How big is "large files" ?

---

### Post by tgalati4 on 2014-03-15
Set up a google drive account (gmail email) and send links to your friends.  They can then share stuff to your google drive account.  All they need is a browser and a flash drive with the content to share.  I'm sure there are file size limits, so you will have to research that.

---

### Post by bapoumba on 2014-03-15
Dropbox can be accessed from a browser. If you all have dropbox accounts and share a folder, all files within this folder will be available to everyone.
From a browser, dropbox file size limit is 10GB or your available space under 10GB.

---

### Post by coldraven on 2014-03-15
Attachments to Gmail are limited to 25MB. That is larger than most e-mail providers but may not be big enough for your needs.
Also anybody logging into Gmail from an internet café will most probably have their login details stolen.

---

### Post by JKyleOKC on 2014-03-16
> **asearle said:**
> I need to receive large files from contacts who will be logging in in various internet cafés without any locally pre-installed software.  Can anyone give me tips on how to receive these files?  Simply via e-mail?  Or facebook?  Or is there a more elegant way?As others have asked, how large are the files?

Anything up to 10 MB or so can probably be handled as binary attachments to Email. Some Email servers can accept even several GB, but not all of them do.

I have need to receive files as large as 4 GB from customers of my database recovery service, although most that I get are only a few hundred MB. To deal with this situation, I've installed a private FTP server on a local machine, and created a Windows application (since the customers all use Windows) that has the security features and FTP transmission software built into it. The customer must install that application at his end, then connect to the internet and just run the application to send me his file.

Since such database information is extremely sensitive, I've locked down the server to the best of my ability. Incoming files go to a directory that is write-only so far as the outside world is concerned, and does not even show up in a directory listing from any FTP client. There's a public directory that contains a copy of my application, and that directory is read-only to the outside world. Thus the only practical way to get a file into the server is to use the application (since the only directory that can accept files from outside is hidden from any view but my own), and no file that gets in can be seen from outside unless I actually move it to a visible read-only area. That prevents the server from being used by anyone for child porn or warez distribution.

The server is configured **NOT** to allow any FTP commands except those absolutely necessary (i.e. EXEC is not recognized, nor are any users except "anonymous" which is hard-coded into my application), since my one and only security breach stemmed from allowing login for my backup user ID.

This may be overkill for your situation, but it has worked nicely for me over the last half-dozen years. I do use "*fail2ban*" to discourage invasion attempts, and every now and then get a few hundred such efforts showing up in the logs, but that's just the price of doing business over the net. If you're interested, I'll be happy to pass along some of the tips on configuring *PostFix* that I've come up with along the way.

---

