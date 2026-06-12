---
title: "Allow only certain IP Addresses in Firefox"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by CostaRica on 2009-04-10
Hi.  

- Is there a way to allow only certain IP Addresses to be visited in Firefox, in such a way that the employees can only visit, say, 4 IP Addresses and not been able to modify this restriction without a password?  

- Is /etc/hosts the way to do it? How?

Thanks!

---

### Post by Paranoid Tux on 2009-04-10
Hi CostaRica,

if yuo are dealing with a larger number of people you are probably better of setting up an ACL on your router itself, or using a distro like Smoothwall, which would also make your network more secure.

If you have more information or I can help further, let me know.

Cheers,

Paranoid Tux

---

### Post by CostaRica on 2009-04-10
It should be done in 4 different stores with only 2 users in each place, so I would like a simpler solution than Smoothwall, since I would have to install another Smoothwall computer in each location, since I see it is something like Untangle, right?

---

### Post by Paranoid Tux on 2009-04-10
That's right. I would suggest that you see if you can have an ACL on your router on eash premises. Most do allow them. Even if you can only do a patrial block that would be ahead of where you are. Logging is an option and offering immediate dismissal to anyone caught using it for non-permitted purposes. Smoothwall is much like Untangle and IPCop, etc, but blocking is usually done at the gateway level, not so much the node level, unless you are using w$, of course.:)

---

### Post by suzypeppercorn on 2009-04-10
i think setting up an ACL on the routers themselves would be much easier. Even with this few amount of computers you would have to configure, it would still be easier. Don't you think?

---

### Post by CostaRica on 2009-04-10
Thank you, Paranoid Tux.  

- Where can I learn more about ACL and how to accomplish this?

---

### Post by Paranoid Tux on 2009-04-10
No worries. The best place to look up ACLs and blocking is on the manufacturers website of your router. Cisco is easy, linksys is good, not sure about the rest, but I do know that some you can't at all. Let me know how you go and if I can be of help.

Cheers,

Paranoid.

---

### Post by lovinglinux on 2009-04-10
I'm not sure if it is a good solution, but you could use moblock with an ip blocklist range of 0.0.0.0-255.255.255.255, then whitelist only the allowed web sites IPs.

---

### Post by CostaRica on 2009-04-10
Hey, lovinglinux, sounds like MoBlock is a very good option.  I'm going to try it.  

Thank you all for the GREAT answers!

---

