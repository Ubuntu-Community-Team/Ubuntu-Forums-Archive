---
title: "Changing Hosts List"
date: 2008-07-03
forum: Networking &amp; Wireless
---

### Post by Windsurfer619 on 2008-07-03
One of my machines acts as a home server, for which I have a DNS. When I am at home on my laptop, I can either type in the local IP, or add the local IP+DNS to my hosts list to access it remotely. When I am remote, I can type in the DNS, but then I'd have to delete my hosts file entry.
So what I would like is to have my hosts list change depending on where I am so I don't have to type in my local IP for everything when I am at home, and type in the DNS when I am away.
Is this possible? Am I just really lazy? Is it normal to have two bookmarks for everything on your home server?

Thanks!

---

### Post by jimv on 2008-07-03
What you can do is just use the server's external IP to access it...the one that lets you get to it from the net.  That way you never need to change your hosts file.

Of course, a better way to do this would be to use DynamicDNS to give your server a domain name out on the net.  My server can be accessed from any machine, anywhere with the domain server.gotdns.com, which I signed up for at dyndns.com for free.

Also, you could install the DD-WRT firmware on your router and enable the lan DNS server that is included with that.

---

### Post by Windsurfer619 on 2008-07-03
Yeah, I can't install that firmware. I have a DI-524.
And I do use a dynamic DNS. The issue is that my ISP doesn't route my own IP back to me indirectly, so I can't just use that DNS from everywhere. It would only work when I'm away.

---

### Post by Windsurfer619 on 2008-08-25
I partly solved this issue using a perl script I wrote:
[http://ubuntuforums.org/showpost.php?p=5661181&postcount=2](http://ubuntuforums.org/showpost.php?p=5661181&postcount=2)

---

