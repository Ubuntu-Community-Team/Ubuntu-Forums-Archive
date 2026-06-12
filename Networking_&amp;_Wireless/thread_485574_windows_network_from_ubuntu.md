---
title: "windows network from ubuntu"
date: 2007-06-27
forum: Networking &amp; Wireless
---

### Post by mosaic2s on 2007-06-27
friends,
using dapper on one pc with 2 others running non linux os. the dates of the non-linux files comes at 1 jan 1970 when accessing through ubuntu network server.

can someone advise ?

sandeep

---

### Post by mosaic2s on 2007-06-27
another issue -

i changed the non-linux workgroup to dome from home. ubuntu seems to be stuck in home and i cannot make it change to dome workgroup. what is to be done?

sandeep

ps. changed it back to home. no issue to be resolved except reading of date as 1970 in non-ubunutu os.

---

### Post by conjur3r on 2007-06-27
Can't help you re the first question but the second one should be related to Samba.  Check /etc/smb.conf, specifically the line **workgroup**.  Make your changes and restart samba:

# sudo /etc/init.d/samba restart

---

### Post by mosaic2s on 2007-06-27
thanks. will keep it for future use.

---

