---
title: "Problem reading XPM files in asmail"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by wacky_keyboards on 2009-07-12
Hello,

I downloaded and installed asmail, the AfterStep mail monitor
using aptitude, and set my .asmailrc file to tell asmail to
use certain (standard asmail) XPM pixmaps to indicate the
presence or absence of mail.  However, when I launch asmail,
I get the error message,

     % asmail
     asmail: XPMError:   /var/tmp/asmail/nomail_s.xpm: could not load xpm

The XPM file exists, and it seems valid -- for example, I can
use xpmtoppm to convert it to a PPM file and then use xloadimage
to view it.

Does anyone have any suggestions on how I might fix this?

I am running on Ubuntu 9.04 (Jaunty Jackalope), on a 64-bit
machine -- uname -a gives:

     Linux testmach 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 22:12:12 UTC 2009 x86_64 GNU/Linux

Thanks!

---

### Post by lisati on 2009-07-12
.

---

### Post by Corin-EU on 2010-07-28
asmail is poor at parsing the asmailrc configuration file.

It will only tolerate one SPACE or TAB character between new, old etc and the path to the pixmap.

Please check that you do not have multiple spaces or space and tab between the old, new identifier and the path specification.

---

