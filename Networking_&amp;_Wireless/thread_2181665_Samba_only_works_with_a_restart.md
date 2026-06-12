---
title: "Samba only works with a restart"
date: 2013-10-18
forum: Networking &amp; Wireless
---

### Post by bobblex on 2013-10-18
Running Lubuntu 13.10 now, had the same problem on Lubuntu 13.04.  After a re-start Samba says it is running, but I can't connect from other computers on the network until I open up a terminal and do 

```

sudo restart smbd

```

If I do 

```

sudo start smbd

```

I'm told smbd is already running.

Any ideas on what is going on?  Why is it necessary to do a restart on the Samba daemon?

Thanks

---

### Post by houstonbofh on 2013-10-18
How about name services?

sudo start nmbd

---

### Post by bobblex on 2013-10-19
Starting nmbd results in the message that nmbd is already running.

I spent a large part of today re-reading all of the Samba and CIFS manuals, How-Tos and FAQs that I can find and I'm still stumped.  I went through all of the log files in VAR/LOG and still can't see anything that shows what the problem might be.

Anyone with an idea on why after booting and verifying that smbd has loaded and is running that I have to do a Samba restart before the other machines (all MS W7) on the network can browse and open the Lubuntu shares?

Thanks

---

