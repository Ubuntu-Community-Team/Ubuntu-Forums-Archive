---
title: "GFTP with SSL"
date: 2006-11-16
forum: Networking &amp; Wireless
---

### Post by dmsn on 2006-11-16
Hey atm this is my dream gftp with SSL working.
Can you help me to get this working maybe a mini guide for me
would be so nice.
I have tested alot but i didnt got it worked.

Thanks for help.

---

### Post by Wim Sturkenboom on 2006-11-16
I assume you want to setup a secure ftp server yourself and next use gftp to connect. If so, read on.

First you need a ftp server that is configured for SSL. I use vsftp on my slackware box and followed instruction from [Miles Brennan's home server howto](http://www.brennan.id.au/) to set it up (there is a page dedicated to vsftpd).

The alternative is to configure the SSH daemon for ftp. I did not do that as it sounded too complicated to jail users to their homedirectories at the time that I tried (things might have changed).

Next you can configure gftp on the client machine. I'm NOT connecting from a box running Ubuntu, so can't help you with that.

I use FileZilla on a Windows machine to connect to my Slackware server. The important thing is to use the correct server type (and something similar will apply to gftp); in my setup I have to use *ftp over ssl (explicit encryption)*

---

### Post by dmsn on 2006-11-16
Hey i have a ftp server already with SSL.
And i can conncet to it from windows machines but i want it too from my ubuntu linux pc.
Gftp with SSL would be nice.

---

### Post by Whoopie on 2006-11-16
Hi,

you could this repo: [http://seveas.imbrandon.com/](http://seveas.imbrandon.com/)

Seveas is an Ubuntu dev.

Best regards,
Whoopie

---

### Post by dannyboy79 on 2006-11-16
> **dmsn said:**
> Hey i have a ftp server already with SSL.
And i can conncet to it from windows machines but i want it too from my ubuntu linux pc.
Gftp with SSL would be nice.

are you using proftpd version 1.3? did you compile it yourself cause the one in the repo's doesn't have mod_tls compiled in by default. a bug has been filed already about this.

---

### Post by timrichardson on 2007-05-01
the KDE app KFTPGrabber works great with explicit SSL FTP with a self-signed certificate. I have Ubuntu 7.04 and the KDE app looks very good. I had my ftp connection to a Filezilla server on a Windows box working first time (< 30 seconds setup) which was nice after the experience with gFTP.

---

### Post by dannyboy79 on 2007-05-02
the problem isn't with the client, it's with the server and since you're stating youre using Filezilla on Win 2000 that really doesn't help here. but thanks for the info, Filezilla is way better than the stupid free FTP server that Windows XP Pro provides.

---

### Post by sceo on 2008-01-24
The problem with the Seveas repo version is that update-manager nags you to install the newer version of gftp from the repo's.  Any way to prevent that?

---

### Post by dannyboy79 on 2008-01-24
> **sceo said:**
> The problem with the Seveas repo version is that update-manager nags you to install the newer version of gftp from the repo's.  Any way to prevent that?

within command line, I thought you could use aptitude or apt-get to "hold" a package, meaning don't update it. Not sure how the update-manager daemon will handle that though. you could just ignore the little orange thingy or click, "view updates" and then uncheck the gftp one.

---

