---
title: "Problems conecting via SSH using the teminal"
date: 2007-06-04
forum: Networking &amp; Wireless
---

### Post by NiceGuy on 2007-06-04
Hi all, confusing one this....

I've got a server on my local network (running dapper if your interested) which I'm trying to connect to via ssh.

All was working fine then I upgraded my machine (the client) to Fiesty and now I can't connect to my server using the terminal.

The command I'm using (as I always have) is: ssh 192.168.1.64

After a few mins it just times out :-(

I know that this is not a server-side issue as I can still connect fine using my laptop (running Edgy) and, perhaps even more bizzarly, I can connect using nautilus and gFTP on the client machine - just not the (gnome) terminal.

I'm really at a loss with this one!

If anyone can shead any light on the situation, or offer any suggestions as to how to fix it I'll be most greatful - having to boot my laptop everytime I want to do anything on my server is a pain!

---

### Post by merlinus on 2007-06-04
Try ssh username@IP address

-merlin

---

### Post by NiceGuy on 2007-06-04
Thanks for the quick reply.

I tried what you said and after about a minute (far longer than it should take) it worked?!

But after I disconnected, it wouldn't let me do it again (timed out).

Then in desperation I went to the system monitor (a good standby in windows - old habits are hard to break) and killed ssh and ssh-agent. I then tried it again and to my surprise it worked, not only that but typing just: ssh <ip address> - works too!

Restarted my desktop and they both still work so I'm keeping my fingers crossed now... still confused mind but at least its working.

---

