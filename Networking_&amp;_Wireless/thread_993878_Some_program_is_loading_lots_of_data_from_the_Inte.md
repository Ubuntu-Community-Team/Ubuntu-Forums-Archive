---
title: "Some program is loading lots of data from the Internet"
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by Paddy Landau on 2008-11-26
Since putting the network icon on my panel, I've noticed occasionally that my computer is receiving -- and sending -- loads of data to and from the Internet. :confused:

This morning, I noticed that it had already sent 14Mb of data, and was busy sending data as I watched, even though I was not using the Internet at the time.

How can I find out what programs are accessing the Internet, so that I can figure out whether it's something I should have expected, or something that I need to attend to?

---

### Post by TFX360 on 2008-11-26
Look [here]("http://www.debianadmin.com/network-traffic-analyzer-for-your-ubuntu-system.html")!

---

### Post by Paddy Landau on 2008-11-26
Thanks, TFX360, for the link.

I've installed Darkstat and Wireshark, and run them. However, I really don't know how to interpret the results. Wireshark just has me scratching my head in puzzlement :(. (I'm not a clever chap with networking -- I really just need to know which program is sending all that data.)

Etherape and Ethstatus don't look as though they will point me in the right direction.

Do you have any advice as to how to interpret the data?

---

### Post by TFX360 on 2008-11-26
Look at the protocol. If it is something you would not expect (FTP/SSH/HTTP) look at wich IP-Address is generating this data.


In a Terminal:

```
netstat -natp
```

Shows wich ports are opened. In my case only cupsd, port 631, which is printer support and, port 5561, for Vodafone Wireless 3G.


Regards,


TFX

---

### Post by Paddy Landau on 2008-11-26
OK, so to make sure that I understand...

Next time that I see this happening, I run darkstat to see which ports are being used.
Then I look at netstat -natp to see which program it is.

Is that correct?

---

### Post by TFX360 on 2008-11-26
Yes, and combine the logical things. You can always use this thread here or create a new one!

---

### Post by Paddy Landau on 2008-11-27
Thanks for the advice, TFX360.

I'll do this next time I have the problem.

---

