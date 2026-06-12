---
title: "[SOLVED] can't access internet from rc.local"
date: 2008-11-20
forum: Networking &amp; Wireless
---

### Post by eotakos on 2008-11-20
Hello, i want my computer to send me a mail at startup. The script i created works when i'm logged in, but it seems that when it is called from within rc.local, it is like there's no connection to the internet to execute the commands successfully.

Actually today, it was the first time that the email was actually sent, but the previous command didn't have internet available in order to fill in the content of the mail.

The script first calls the the w3m command, which returns
> The page cannot be displayed
Explanation: The connection to the website was closed by
the site or by one of its servers.

and the mail command when -as usual- fails, it returns that it has problem locating DNS service

It seems to me that if I could buy 3 seconds from within the script, it will work just fine. Does anyone know any "delay" commands?

Thanks in advance for any input

---

### Post by htmlland on 2008-11-20
> **eotakos said:**
> Does anyone know any "delay" commands?

You could try "sleep xx" where xx is the number of seconds you want it too pause. Might do the trick :)

---

### Post by eotakos on 2008-11-20
Oh yeah!.... it was just what i suspected. A little delay was all that was needed. 

thank you very much for the tip my friend!

---

