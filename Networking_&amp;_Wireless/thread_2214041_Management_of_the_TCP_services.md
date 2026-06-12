---
title: "Management of the TCP services"
date: 2014-03-30
forum: Networking &amp; Wireless
---

### Post by balubeto on 2014-03-30
Hi

In Lubuntu 13.10 how do I manage the services that open the TCP ports to the outside? 

In particular, I should add a service that is activated during loading of the X11 server (that is, before the LightDM display manager is displayed).

Thanks

Bye

---

### Post by SeijiSensei on 2014-03-30
The simplest way to start a program during boot is to add the appropriate command(s) to /etc/rc.local.  This script is run at the end of the boot process and thus before X starts.  Place the commands you need above the "exit 0" line in that file.  You'll need to edit this file as root with sudo.

---

### Post by balubeto on 2014-03-31
> **SeijiSensei said:**
> The simplest way to start a program during boot is to add the appropriate command(s) to /etc/rc.local.  This script is run at the end of the boot process and thus before X starts.  Place the commands you need above the "exit 0" line in that file.  You'll need to edit this file as root with sudo.

How do I make this script and add the appropriate command to the directory?

Thanks

Bye

---

### Post by SeijiSensei on 2014-03-31
From your original posting I assumed you already had something in mind.  Learning to program is beyond the purpose of this forum.  Writing a "daemon" that attaches to a TCP port requires understanding of system programming and typically knowledge of C.

---

