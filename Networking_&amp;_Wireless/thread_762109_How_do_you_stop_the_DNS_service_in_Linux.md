---
title: "How do you stop the DNS service in Linux?"
date: 2008-04-21
forum: Networking &amp; Wireless
---

### Post by AvalonSkies on 2008-04-21
Hi, all. I was wondering if someone could help me with some Windoze vs Linux concept translation. :)

So I'm working in Windows on my notebook right now. I have a cute little bug that sometimes decides to petrify the DNS Client service when I bring the box out of sleep mode. I'm able to go into Services and restart the DNS Client service to fix the problem.

I'm wondering--how would I do this in Linux? Linux uses the Service concept, right? Is there a services.msc equivalent for Linux?

Cheers, and thanks! [IMG]http://www.scarletsix.com/etc/sam/gw/companioncubesmiley.gif[/IMG]

--Avalon


EDIT: I thought I'd add that I don't *need* there to be a GUI. I'm just as game for command prompt stuff. It's the concept of a service manager that I'm asking about. ^_^

---

### Post by mmichalik on 2008-04-21
sudo /etc/init.d/networking restart should do the trick for you in Ubuntu

---

