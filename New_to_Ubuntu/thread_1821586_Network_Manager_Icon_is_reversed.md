---
title: "Network Manager Icon is reversed"
date: 2011-08-09
forum: New to Ubuntu
---

### Post by landersohn on 2011-08-09
I have a curious behavior of my network manager icon in the panel on ubuntu 10.04.
I changed my wireless router and now when I am connected the icon shows "disconnected". When I actually disconnect, the icon shows me all bars and indicates that I am connected.
Does anybody know how to get this back to the way it should be?

Incidentally, at my other wireless network at home it works fine.

---

### Post by amjjawad on 2011-08-09
> **landersohn said:**
> I have a curious behavior of my network manager icon in the panel on ubuntu 10.04.
I changed my wireless router and now when I am connected the icon shows "disconnected". When I actually disconnect, the icon shows me all bars and indicates that I am connected.
Does anybody know how to get this back to the way it should be?

Incidentally, at my other wireless network at home it works fine.

Not very sure if this what you mean but I think you need to remove the old Network from your Wireless Tab. You need to Click on "Edit Connections".

---

### Post by landersohn on 2011-08-09
Thanks for the reply, but that is not it.
Deleted all old networks, even complete uninstalled network-manager-gnome and re-installed, still the same thing: it displays the opposite item:

when I turn my router off, I get the icon indicating that I am connected, when it actually is connected, I get the icon showing that I have no connection.

---

### Post by landersohn on 2011-08-09
I forgot: when I hover the mouse pointer over the icon, the little tool tip that appears shows the correct connection status. It's just the icon.... (almost as if the icon file names got switched).

---

### Post by amjjawad on 2011-08-09
> **landersohn said:**
> I forgot: when I hover the mouse pointer over the icon, the little tool tip that appears shows the correct connection status. It's just the icon.... (almost as if the icon file names got switched).

I understand now but unfortunately I'm not sure how to fix that?

Try to search here, perhaps you'll find similar issue:
[http://www.googlubuntu.com/](http://www.googlubuntu.com/)

---

### Post by landersohn on 2011-08-09
I found a thread from 2009 with a solution: the /etc/network/interfaces file got out of sync. Fixing that file did the trick: I manually removed the "#" in front of the lines with active and connected interfaces and rebooted, problem fixed.
Thanks for your help

---

### Post by amjjawad on 2011-08-09
> **landersohn said:**
> I found a thread from 2009 with a solution: the /etc/network/interfaces file got out of sync. Fixing that file did the trick: I manually removed the "#" in front of the lines with active and connected interfaces and rebooted, problem fixed.
Thanks for your help

That's very interesting to know and glad you managed to fix it :)

---

