---
title: "[SOLVED] Help with pppd [restore pppd]"
date: 2008-02-26
forum: Networking &amp; Wireless
---

### Post by sadeghi on 2008-02-26
Hi
i made a mistake and deleted /usr/sbin/pppd executable and now when i try to configure my VPN using pptpconfin or while try to connect usin "pon" command i get an error that says "/usr/sbin/pppd not found".
I really need to repair this and restore the executable file to configure pptp.
Thanks in advace for any kind of help

---

### Post by SpaceTeddy on 2008-02-26
open synapic, find the package called ppp and mark it for reinstall. that should place the pppd exectuable back where it was (i think). otherwise, go into the repos manually, download the ppp package, open it with the archive manager and copy out the pppd file manually.

---

### Post by sadeghi on 2008-02-26
> **SpaceTeddy said:**
> open synapic, find the package called ppp and mark it for reinstall. that should place the pppd exectuable back where it was (i think). otherwise, go into the repos manually, download the ppp package, open it with the archive manager and copy out the pppd file manually.

Thank you Space Teddy. It worked fine and now pppd executable is in right place. I try to configure my ubuntu and start developing.
thanks a lot :):)

---

