---
title: "Local Network with SMB and ethernet crossover"
date: 2005-10-19
forum: Networking &amp; Wireless
---

### Post by migueljacq on 2005-10-19
Hi all,

Sorry if this has been posted before, but I was wondering if someone could assist me with the following:

I have a local network set up with SMB between two computers both running Ubuntu.

'Sirius' is the main box, connected to the internet by dialup modem. 
'Procyon' is the secondary box, connected to Sirius by ethernet crossover cable.
The connection is fine: Procyon's gateway address is Sirius' IP number, and I have also been instructed to set Procyon's DNS to match that of Sirius' (i.e, my ISP's dns), which I have done, no problem.

My question is: Is there a way for Procyon as the secondary computer, to access the internet through Sirius? i.e can it browse using Sirius' modem connection, through the ethernet cable.

Thanks in advance

---

### Post by migueljacq on 2005-10-20
Problem solved: if anyone comes here with the same question, I solved it by installing Firestarter and enabling internet connection sharing.

---

