---
title: "Faxing from Ubuntu - NO CARRIER"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by jsdegard on 2009-10-20
Hello, 

I have a fax server set up using Ubuntu 8.04, efax, and a Conexant modem.  I acquired a driver and all seems to work well most of the time; I can send faxes.  I am having a problem with one fax number, though.  I get a dial command failed, and a "NO CARRIER" error.  If anyone has seen this any idea of why this phone number doesn't work would be great.  Here's a look at the log file:

jsdegard@mu:/$ efax -s -vewinchmartfx -d /dev/modem -t T12819734926 /var/www/My
PartDisplay/SO/acks/10000122030.001
efax: Tue Oct 20 13:46:38 2009 efax v 0.9a-001114 Copyright 1999 Ed Casas
efax: Tue Oct 20 13:46:38 2009 efax v 0.9a-001114 Copyright 1999 Ed Casas
efax: 46:38 compiled Oct 15 2009 22:20:10
efax: 46:38 TIFF version 4.2 file (little-endian)
efax: 46:38 TIFF directory at 8 with 20 tags, last image.
efax: 46:38 page 1 : /var/www/MyPartDisplay/SO/acks/10000122030.001 + 338 : 1728
x2292 @ 204x196 dpi TIFF/FAX
efax: 46:38 argv[0]=efax
efax: 46:38 argv[1]=-s
efax: 46:38 argv[2]=-vewinchmartfx
efax: 46:38 argv[3]=-d
efax: 46:38 argv[4]=/dev/modem
efax: 46:38 argv[5]=-t
efax: 46:38 argv[6]=T12819734926
efax: 46:38 argv[7]=/var/www/MyPartDisplay/SO/acks/10000122030.001
efax: 46:38 opened /dev/modem
efax: 46:38 command  "Q0V1"
efax: 46:38 waiting 2.0 s
efax: 46:38 .942 [<CR><LF>OK<CR><LF>]
efax: 46:38 response "OK"
efax: 46:39 command  "E0"
efax: 46:39 waiting 5.0 s
efax: 46:39 .072 [<CR><LF>OK<CR><LF>]
efax: 46:39 response "OK"
efax: 46:39 command  "I3"
efax: 46:39 waiting 5.0 s
efax: 46:39 .202 [<CR><LF>hsfmodem-7.80.02.04full<CR><LF>]
efax: 46:39 .202 [OK<CR><LF>]
efax: 46:39 response "OK"
efax: 46:39 command  "+FCLASS=?"
efax: 46:39 waiting 5.0 s
efax: 46:39 .342 [<CR><LF>0,1,1.0<CR><LF>]
efax: 46:39 .342 [<CR><LF>OK<CR><LF>]
efax: 46:39 response "OK"
efax: 46:39 command  "+FCLASS=1"
efax: 46:39 waiting 5.0 s
efax: 46:39 .452 [<CR><LF>OK<CR><LF>]
efax: 46:39 response "OK"
efax: 46:39 using hsfmodem-7.80.02.04full in class 1
efax: 46:39 command  "+FTM=?"
efax: 46:39 waiting 5.0 s
efax: 46:39 .582 [<CR><LF>3,24,48,72,73,74,96,97,98,121,122,145,146<CR><LF>]
efax: 46:39 .582 [<CR><LF>OK<CR><LF>]
efax: 46:39 response "OK"
efax: 46:39 dialing T12819734926
efax: 46:39 command  "DT12819734926"
efax: 46:39 waiting 120.0 s
[B]efax: 47:33 .812 [<CR><LF>NO CARRIER<CR><LF>]
efax: 47:33 response "NO CARRIER"
efax: 47:33 Error: dial command failed[/B]
efax: 47:33 failed -> /var/www/MyPartDisplay/SO/acks/10000122030.001
efax: 47:33 command  "Q0V1"
efax: 47:33 waiting 2.0 s
efax: 47:33 .952 [<CR><LF>OK<CR><LF>]
efax: 47:33 response "OK"
efax: 47:34 command  "H"
efax: 47:34 waiting 5.0 s
efax: 47:34 .062 [<CR><LF>OK<CR><LF>]
efax: 47:34 response "OK"
efax: 47:34 done, returning 2 (unrecoverable error)

---

### Post by jsdegard on 2009-10-20
By the way, i did send the document using the good old fax machine and it sent, so it is a good fax number.

I'm thinking it has something to do with their modem being class 2 or something, maybe?

---

