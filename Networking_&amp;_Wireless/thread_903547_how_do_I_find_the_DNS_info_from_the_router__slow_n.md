---
title: "how do I find the DNS info from the router?  slow nets"
date: 2008-08-28
forum: Networking &amp; Wireless
---

### Post by Bubs on 2008-08-28
I'm having trouble with a super slow internet as soon as I fresh installed hardy.  I never found a solution but this one looks like it may work.  [http://ubuntuforums.org/showthread.php?t=152637](http://ubuntuforums.org/showthread.php?t=152637)

the question I have is How do I find the DNS info with my 2wire router?  I looked all around and found that the router sets up DNS info automatically and doesn't display the results...

And if anyone else has a better idea on how to speed up the nets I'm all ears.  This is the only computer that is slow in the whole house.  we have 5 going at different time throughout the day.  this one is always on.  I can bring my laptop in set it down right on top of the box and the laptop still gets good speed and the ubuntu box is still slow.  so location isn't a problem.  I disabled IPv6.  everything is slow like firefox, email, bittorrent it's not like I'm getting slowdowns in FF only.  that why I thought about giving the above solution a try.

bubs

ps.  wireless connection, 2wire router, ubuntu hardy

---

### Post by mellowd on 2008-08-28
```
cat /etc/resolv.conf
```

What's the output?

---

### Post by Bubs on 2008-08-28
The output is this

search gateway.2wire.net
nameserver xxx.xxx.x.xxx  (IP address)

is the IP the DNS?

---

### Post by mellowd on 2008-08-29
Yeah, but it could just be pointing to your router itself. 

If it's a public IP address you know it's your DNS. If it's private it means it the router's IP.

In that case you'll need to log into your router and check there. It should list it's DNS somewhere

---

### Post by Bubs on 2008-08-30
I found it..  I'm such an idiot, I was looking for a label named DNS but it was labeled domain name server so skipped over it when I was searching for it... :)

so I tried the "fix" listed on the post an I'll let you know if it seems to speed anything up.

bubs

---

### Post by mellowd on 2008-08-30
good to know :)

---

