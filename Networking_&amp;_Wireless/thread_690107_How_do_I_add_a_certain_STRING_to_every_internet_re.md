---
title: "How do I add a certain STRING to every internet request or URL?"
date: 2008-02-07
forum: Networking &amp; Wireless
---

### Post by wakkerakker on 2008-02-07
I have a Problem... I am behind a firewall, and this firewall searches for string thing inside every request. I need to find out how to get it attached to every request... How would I do this?

Whats more, I need to use this server as a proxy, say 176.0.0.1




Every request needs a string at the end, something like /your.string/ otherewise the firewall blocks the request. How do I go about adding this string to every request without having to add it manually.

[www.google.com/](www.google.com/)                            {blocked}
[www.google.com/your-string/](www.google.com/your-string/)         {allowed}
ubuntuforums.org                            {blocked}
ubuntuforums.org/your-string/        {allowed}

etc. etc.

I have a program in windows which can do this, however im a newbie to Linux, and havent figured it out yet.

Any help on this one?

---

### Post by kirsche on 2008-02-07
I guess some sort of proxy would do the trick. One which would chain to your real proxy and alter the request before.
Have a look here:
[http://redhanded.hobix.com/inspect/mousehole11InPlainView.html](http://redhanded.hobix.com/inspect/mousehole11InPlainView.html)

Not sure if tinyproxy can do it. But you could also try to write one in Perl ;)

---

### Post by wakkerakker on 2008-02-08
Thanks for the link. Mousehole dont work for me.... however im trying to edit the source in ruby.
The problem is im not familiar with ruby. the internet here in zambia drives me nuts, this is my 3rd attempt to reply.

Any other ideas? anyone?

---

