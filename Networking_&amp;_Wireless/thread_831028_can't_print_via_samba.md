---
title: "can't print via samba"
date: 2008-06-16
forum: Networking &amp; Wireless
---

### Post by herbert tamayo on 2008-06-16
Hi, recently I've installed samba, this morning I've created a new client account in the server, all correct here, when I set up the printer at the client pc(windows) all was ok but If I tried to send a print jobbut It didn't work, at the client I didn't received any error. but checking in the log of samba I found this:

```

[2008/06/16 09:25:13, 0] printing/print_cups.c:cups_job_submit(643)
  Unable to print file to HP2100tn - client-error-not-possible

```

I'm pretty sure that it doesn't a connectivity problem, in fact, the other clients can print well to samba, so my questions are:

1. how can I debug this problem?
2. is there a monitor software to samba?
3. cups and samba works together?
4. I created another account in the server, but my windows client didn't release the previous profile, how can I use the new profile?

thanks a lot

---

