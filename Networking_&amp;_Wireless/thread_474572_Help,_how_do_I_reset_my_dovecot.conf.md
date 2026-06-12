---
title: "Help, how do I reset my dovecot.conf?"
date: 2007-06-15
forum: Networking &amp; Wireless
---

### Post by squinter on 2007-06-15
I was playing around trying to set up dovecot-imapd when I accidentally did something to my dovecot.conf. And now dovecot won't  run at all. I tried to remove and reinstall dovecot, but it wouldn't recreate dovecot.conf. Please help! :(

---

### Post by disasm on 2007-06-15
try apt-get --purge remove

That will wipe out all config files.

Sam

---

### Post by squinter on 2007-06-15
Thank you that fixed it :D

---

