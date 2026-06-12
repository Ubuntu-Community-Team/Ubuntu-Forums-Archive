---
title: "rsync suddenly not working"
date: 2015-07-07
forum: Networking &amp; Wireless
---

### Post by mick.cannon on 2015-07-07
I've been using rsync to backup to second computer on my home network successfully for over a year using the following command:  rsync -ruv --delete /home/mickl 192.168.1.3: /home/   Today it's stopped working and says "Unexpected remote arg: 192.168.1.3:"   The only changes that have been made to either of the computers since the last time I backed up are the system updates.  Something must have been changed but I haven't a clue what or where to look. Can anyone help please.

---

### Post by hakermania on 2015-07-07
I notice a space between```
[COLOR=#000000]192.168.1.3:[/COLOR]
``` and ```
[COLOR=#000000]/home/[/COLOR]
```.

Although I haven't used rsync in a while, are you sure that there should be a space between those 2?

---

### Post by mick.cannon on 2015-07-07
Thanks for that hackermania. You're right there shouldn't be a space between those two. It was a typo when I wrote the message, so that's not my problem.

---

### Post by mick.cannon on 2015-07-07
In desperation re-booted both machines and it now works.  Have no idea what caused the problem but glad it's fixed.

---

