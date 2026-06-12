---
title: "Unexpected auto logout in natty"
date: 2011-08-18
forum: New to Ubuntu
---

### Post by mmasroorali on 2011-08-18
Dear All,
Recently (perhaps after I upgraded to natty), infrequent auto logout is happening in my machine. I do not find any clue regarding what is triggering this unwanted event. 

Please see the following output,


As you can see, a logout has happened at 12:53.[IMG]http://ubuntuforums.org/attachment.php?attachmentid=200259&stc=1&d=1313656310[/IMG]

While checking the logs, I found a rather unwanted situation. /var/log/messages is empty. And the last line in /var/log/messages.1 says,
```
Apr  9 09:52:41 Dell-Home kernel: Kernel logging (proc) stopped.
```


I am not sure whether there is any relationship between the two, but I thought that I should let you know.

(I am making a [separate post]("http://ubuntuforums.org/showthread.php?t=1827594") on this).

The only pattern in this logout is, it happens in my absence. Is there anything I can check?

---

