---
title: "Empathy history"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by UpSignal on 2010-10-12
hello guys, i'm currently using:

Ubuntu Maverick Meerkat
Empathy 2.32.0

When i open a contact to chat (live messenger account), empathy displays the last lines of conversation i had with him. How do i prevent that history?
I have disabled "log conversations" in preferences. Yet, id didn't help.

Thanks

---

### Post by UpSignal on 2010-10-12
also, is it possible to maintain my custom message when i start empathy again?

---

### Post by fleachy on 2010-11-28
Regarding deleting the logs you should remove files from this directory:

./.local/share/Empathy/logs/

If you check the files in there is quite easy to find what you specifically need to remove.

---

### Post by vene-ubu on 2011-02-21
I have this same problem, but I cannot find that folder.  after /share , I cannot find Empathy

---

### Post by davidbanez on 2011-03-07
> **fleachy said:**
> Regarding deleting the logs you should remove files from this directory:

./.local/share/Empathy/logs/

If you check the files in there is quite easy to find what you specifically need to remove.

You can also delete the account from Empathy, then add again that account.

Example:

1. Remove Yahoo account
2. Re-add Yahoo account

This should delete all logs on Yahoo account. You cannot however delete logs for specific user with this method.

This worked for me using Empathy 2.32.1

---

### Post by GWBouge on 2011-03-07
Empathy now keeps logs in:

~/.local/share/TpLogger/logs

---

