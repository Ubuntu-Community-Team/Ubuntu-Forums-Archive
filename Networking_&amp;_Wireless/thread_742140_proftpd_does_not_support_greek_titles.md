---
title: "proftpd does not support greek titles"
date: 2008-04-01
forum: Networking &amp; Wireless
---

### Post by psychobeauty on 2008-04-01
IS there a way that i can have  my ftp server to show the greek titles of some files??
 because it does not show it.its shows somethink that cant be read like (gfhftfyrtsdf......gf222jhuyu)

---

### Post by Eiríkr on 2008-04-01
Poking around on the proftpd.org site, I found mention of a new (!) option to allow UTF-8 filenames (in the 1.31rc3 notes [here]("http://www.proftpd.org/docs/RELEASE_NOTES-1.3.1rc3")), but there are no indications of how to use this option, or where in the conf file it should go.  I suspect there is currently no full-blown way of using Unicode in ProFTPD filenames.  I'd suggest you either switch FTP server programs if possible, or prepare to wait a while until the full 1.31 version is released, and then a while longer for someone to write the documentation.  

Good luck!  I sympathize, as I deal with with Japanese, and the half-baked UTF-8 support in a number of software packages (both FOSS *and* proprietary) has caused me no end of grief.  

Cheers,

Eiríkr

---

