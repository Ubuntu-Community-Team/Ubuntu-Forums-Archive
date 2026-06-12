---
title: "[SOLVED] Simple question about networking."
date: 2008-10-04
forum: Networking &amp; Wireless
---

### Post by gali98 on 2008-10-04
I just need to confirm this will work.
I have a tx2000z laptop with ubuntu on it. And then I have an Xbox with some softmod stuff on it.
Basically I need to ftp into the xbox. Can I just stick a network cable into the xbox and the laptop, and set up static ips on both (such as 192.168.0.1 and 192.168.0.2) then ftp into that ip? (ftp from the laptop into the xbox)
It would make sense to me but I just wanted to check.
The reason I am asking and not trying is because the power cord on my xbox is fried, and they are sending me a new one. If this won't work, while I am waiting for it I can find a way that does.
Thanks guys!
Kory

---

### Post by lswb on 2008-10-04
I don't really know anything about the OS on an xbox, but I'd be extremely surprised if it has an ftp server running by default! If id does, though, your idea will work but you may need a crossover ethernet cable or crossover adapter. Some ethernet ports will automatically recognize when a crossover connection is required and adjust accordingly, but don't count on it. 

If you can ftp _from_ the xbox to an ftp server, however, it isn't hard to install one on a linux system. Again, I'm just guessing, but I imagine the xbox uses some proprietary protocals for its connections.

---

### Post by gali98 on 2008-10-04
The xbox is running homebrew stuff, so it does have ftp on it. What I did before was plug the xbox into our router then connected the laptop in the router and did it like that. The problem is that I don't have an ethernet cord long enough and it made a big mess. This way would be much easier. What do you mean by a "crossover cable?" Is this different than a standard cat5e cable?

---

### Post by lswb on 2008-10-04
A crossover cable has one of the wire pairs reversed from their normal positions in the connector. It is something like a null modem cable but for ethernet instead of serial ports. You can get one for a few dollars, or get a crossover adapter that one end of a standard ethernet patch cord plugs in to. It's a handy thing to have, I keep one in my laptop bag. It's possible, though, that you won't need one, it depends on the capabilities of the ethernet hardware in you computer and/or xbox.

---

### Post by gali98 on 2008-10-04
Thanks so much for your help! I am marking this as solved.
Kory

---

### Post by cariboo on 2008-10-04
Have a look here if you want to build your own network cables:

[http://www.incentre.net/content/view/75/2/](http://www.incentre.net/content/view/75/2/)

If your crossover cable isn't long enough, you can always use an rj45 connector to join the crossover and a regular cable together to make ip the length.

Jim

---

### Post by gali98 on 2008-10-04
Bookmarked! Thanks,
Kory

---

### Post by gali98 on 2008-10-04
double posted on accident :)
Kory

---

