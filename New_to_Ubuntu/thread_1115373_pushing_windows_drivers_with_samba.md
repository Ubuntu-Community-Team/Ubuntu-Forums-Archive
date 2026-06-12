---
title: "pushing windows drivers with samba"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by BarryDocks on 2009-04-03
has anyone managed to push windows printer drivers via samba using ubuntu server 8.04?

I seem to run into lots of permission problems??

---

### Post by cacycleworks on 2009-04-04
Did you see this: [https://turing.phas.ubc.ca/mediawiki/index.php/Samba](https://turing.phas.ubc.ca/mediawiki/index.php/Samba)

fyi: they link to a tar.bz2 package... you need to change that host name to turin.phas in that url! Also, unzip that with bunzip2.

I've been working on trying to set up a PDF print server for about 2 days now and seriously about to just give up and accept that it can't be done. I'm real good with command line, permissions, and making linux & windblows talk. 

Nothing I do can convince printing in windows to make anything happen on the ubuntu box. I got it so it can browse to the server and find the printer, but that's about it. Nothing can make the driver share or the print job spool. :P I've tried it with 2 different ubuntu machines, too... one is my kubuntu hardy desktop and the other is my gutsy headless server. 

I've tried direct internet protocol via [http://ip_address:631/PDF](http://ip_address:631/PDF) as well as via samba. I've done all the dirty deeds to /etc/samba/smb.conf and /etc/cups/cupsd.conf as well as /etc/cups/mime.convs and mime.types

And when I'm at ip_address:631 in the browser from aforementioned windoze box, I can print a test page when browsing that printer and the guest / anonymous test page shows up in /var/spool/cups-pdf/ANONYMOUS like it's supposed to... 

When you google all over for this, you'll find where people have you make a smbclient user with group nobody and $HOME of /home/smbclient ... nope that tutorial didn't work for me. And there's another where you make /home/pdf-documents, which was a bust too.

Anyone have ideas about how folks are implementing the PDF server/spooler with modern ubuntus? 

:) Chris

---

### Post by cacycleworks on 2009-04-04
FWIW, I had the most hopes with this link:
  [http://tldp.org/HOWTO/Debian-and-Windows-Shared-Printing/sharing_with_windows.html](http://tldp.org/HOWTO/Debian-and-Windows-Shared-Printing/sharing_with_windows.html)


I'll try this one Monday... I need to go get a beer before I throw a computer out the front door of my work:
  [http://linux-sxs.org/networking/PDF_creation_using_Samba.html](http://linux-sxs.org/networking/PDF_creation_using_Samba.html)

---

