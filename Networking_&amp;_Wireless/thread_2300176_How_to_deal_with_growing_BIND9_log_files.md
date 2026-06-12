---
title: "How to deal with growing BIND9 log files"
date: 2015-10-24
forum: Networking &amp; Wireless
---

### Post by papakota on 2015-10-24
My DNS server's logs are the text files that growing too fast and one of  them is already over 30 MB in size. I didn't set up the max. file  sizes. I would prefer just to manually delete the lines inside the  files. Let's say, my log contains entries for the last 10 days.The  entries that refer to 9 days I would manually delete and leave there  just the last day's entries. Is it something that's not gonna cause any  damage to anything, I hope???

---

### Post by Skaperen on 2015-10-24
30 MB is not that much, though it is a lot to read.  how much space do you have left?  how big is your storage space?

---

### Post by SeijiSensei on 2015-10-24
You might be logging more than you need to.  Do you have a logging {} stanza in named.conf?  Here's mine:
```

logging {
        category lame-servers { null; };
        category security { null; };        
        channel default_debug {
                file "data/named.run";
                severity dynamic;
        };
};

```
The "lame-servers" directive cuts down a lot of unnecessary traffic.  To see the categories available read this: [http://www.zytrax.com/books/dns/ch7/logging.html](http://www.zytrax.com/books/dns/ch7/logging.html).  The "size" directive can be used to roll the log over after it reaches a certain size.

---

### Post by papakota on 2015-10-24
> **Skaperen said:**
> 30 MB is not that much, though it is a lot to read.  how much space do you have left?  how big is your storage space?

My / partition is about 20 GB in size. About 10 GB is free. Right now the size of my named logs stands at around 56 MB. It might not sound like much, but it takes time even to open the file.

---

### Post by papakota on 2015-10-24
**SeijiSensei**, Thanks for your help, but right now I won't get into learning about logging. It's a topic of a separate thread. It requires a separate discussion. Definitely worth it later down the road for me.

---

### Post by papakota on 2015-10-24
I'm assuming that it's safe to delete manually since you haven't said otherwise.

---

### Post by JKyleOKC on 2015-10-24
You may have to stop the DNS server in order to do the deleting; some servers keep their log files open at all times while others open then only as needed and then close them. The few times that I have attempted to prune log files down on the fly, the writes have been rejected because "the file is busy" and I've not researched this in depth.

Even though you don't want to get into the details of logging at this time, you'll be time ahead to do a "man logrotate" from the command line to see how to deal with your situation. Logrotate is a program that runs periodically to trim back the size of the /var/log directory, and can easily be changed to keep more or fewer log files available.

---

### Post by papakota on 2015-10-24
Thanks for your reply! Yes, I first stopped BIND before deleting parts of its logs. So I haven't got any issues deleting... Had to use SHIFT key, otherwise just by pulling down the mouse, it would've taken me hours probably...
Yes, there's no alternative, but to learn how to manage logs to keep the situation under control. Something I would do when I'm freer.

---

