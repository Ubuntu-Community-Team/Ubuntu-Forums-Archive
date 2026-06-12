---
title: "Slow firefox/Chrome. Not internet issue."
date: 2011-01-13
forum: New to Ubuntu
---

### Post by vorannon on 2011-01-13
Didn't quite know how to phrase the title.

I'm using Ubuntu 10.04 LTS on a dell inspiron 1721

Lately (past month, maybe) Firefox and Chrome have been very slow to use. They open slow, freeze for a few second loading pages, have some (not always) scrolling issues, and cannot properly stream flash videos.

It's not an internet issue. Transmission works just as well as it ever did and youtube videos load just as fast. It's also not likely a computer issue because nautilus and other programs work just fine. There might be other programs effected but firefox and chrome are the only ones I've noticed.

---

### Post by oldsoundguy on 2011-01-13
what other tabs do you have open?  Facebook is notorious for having monstrous memory leaks!

It is for that reason that I have to re-boot occasionally in order to return to point A.

---

### Post by vorannon on 2011-01-13
It happens even when I search google from the homepage after a reboot.

---

### Post by stalkier on 2011-01-13
I have experienced the slow Firefox also.I have not used any other browsers yet to test connections. Just wanted you to know you are not the only one experiencing this.

---

### Post by SteveTheRed on 2011-01-16
I don't know about Chrome, but Firefox 3.6.x is trying to resolve IPs via IPv6 and then falls back to IPv4 after IPv6 fails.

To stop this, set **network.dns.disableIPv6** to **true** on the [about:config]("about:config") page.

This helped me a quite a bit, though web pages still load more slowly than I'd like.

I don't have this problem at all using Firefox 4.0 beta in a Windows XP virtual machine on the same computer. I'm thinking about trying Firefox 4.0 in Ubuntu. I'll report my results here if I do.

---

### Post by kn0w-b1nary on 2011-01-16
Lots of addons slow firefox down.

I would recommend using:
SwiftFox
Opera

as alternate browsers that work a lot faster that those.

Hope this helps!

---

### Post by SteveTheRed on 2011-01-16
I installed Firefox 4.0 beta 9. Pages load wicked fast now.

Unfortunately, there's no deb. You have to install from tarball.

---

