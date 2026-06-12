---
title: "Rsync hangs and all connections become very slow"
date: 2008-08-07
forum: Networking &amp; Wireless
---

### Post by edouardp on 2008-08-07
Hi everyone,

I'm using Ubuntu 8.04 Server Edition and make backup to it using Rsync. The problem is that after a random number of files transferred, rsync hangs, and I can't access the server from the network (ssh often timeouts, 1 ping in 10 is successful ...) however if I login physically on the server and restart the network connection (ethernet) everything come back to normal. I searched about this issue and didn't find anyone with this specific problem. In most cases rsync hangs, but the server on the other hand is fine. I don't know if it's coming from the ethernet controller but there are no messages in /var/log/messages other than the boot messages. I don't think it comes from the rsync on the client end, because I tried with multiple linux distribution (ubuntu included) and the same problem arises everytime.
Any help would be appreciated !
Thanks :)

---

### Post by revanb on 2008-10-28
Hi terminator446

I have the issue that rsync hangs after a number of files and then I have to manually restart it. It's not good since I'm using it for backups, so this hanging is not helping. I'll try it again after I upgrade in November to new Ubuntu.

Anyway, I also want to try using it without the z (compression option).

---

### Post by edouardp on 2008-10-28
Since then I switched to another server, and rsync is working great. I think the problem come from the ethernet card that can't handle long and big transfers (realtek on a Via motherboard). I'm not sure but I didn't find anyone using rsync with ubuntu and having this specific problem. And restarting the network was working that's why I came to this conclusion ...

---

### Post by RgnKjnVA on 2009-05-06
> **terminator446 said:**
> Since then I switched to another server, and rsync is working great. I think the problem come from the ethernet card that can't handle long and big transfers (realtek on a Via motherboard). I'm not sure but I didn't find anyone using rsync with ubuntu and having this specific problem. And restarting the network was working that's why I came to this conclusion ...

I'm a bit late to the party but I have the exact same issue in Intrepid using rsync+ssh to backup about 5G worth of /home data from my Ubu laptop to my Ubu pc. Works great until about 85% then is so slow it's basically not functional. Interestingly, this is only true going from my laptop (Intel Pro/Wireless BG2200 on my Dell Latitude D610) to my Dell Dimension pc (don't have it in front of me to id the network card), rsync+sshing from the pc to laptop does not hang. Weird eh?

Thanks for the tip about restarting the network though. I'll give that a shot when I get home to at least finish the backup. I presume this won't be an issue on subsequent syncs once the data is copied over.

Forgot to mention, this is true whether I have checksumming and/or compression enabled or not.

---

