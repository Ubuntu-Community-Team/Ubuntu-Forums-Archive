---
title: "Can't connect. Wait for signal???"
date: 2005-08-11
forum: Networking &amp; Wireless
---

### Post by steddy on 2005-08-11
I've just installed ubuntu in an old AMD.
I can't connect to the internet with my modem.
I try to do this, it seems that the modem try to start the connection, I can hear the line but the modem doesn't compose the number.
May be that there's something like 'Wait signal before compose' setted but I can't find it?
What can I do?
Thanks for help
Ed

---

### Post by heimo on 2005-08-11
Hmm... Is there some place to put initialization AT commands? If there is, try adding X0 - for example: [i]atx0
[/i]That should switch off dialtone waiting.

---

### Post by steddy on 2005-08-12
[QUOTE=heimo]Hmm... Is there some place to put initialization AT commands? If there is, try adding X0 - for example: [i]atx0
[/i]That should switch off dialtone waiting.[/QUOTE]
 > Is there some place to put initialization AT commands?

If there's, I could not find it!!!
I've looked everywhere but with no success
Where can I find modem properties?

---

### Post by heimo on 2005-08-12
Have you seen this?
[https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto)

There's also example of how to edit speaker volume using AT commands, same should work for dialtone detection.

---

