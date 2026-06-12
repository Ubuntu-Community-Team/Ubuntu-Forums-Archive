---
title: "UBUNTU ndiswrapper problems"
date: 2007-03-13
forum: Networking &amp; Wireless
---

### Post by kickerkeeper on 2007-03-13
Hi all, I'm very new to Linux and I just installed Ubuntu on my new computer. I have a Belkin Wireless G Desktop Card and from what I've read I need to get ndiswrapper bc it isn't seeing the card. However, when I after I do the lines: make distclean, make and make install I get ndiswrapper:command not found. When compiling and installing I see a few lines that say "make: warning: Clock skew detected. Your build may be incomplete" and a couple other warnings about modification time in the future. I need some serious help getting this network card installed. If I don't even need ndiswrapper (seeing how though I don't know what it does) please let me know. Thank you anyone who can help.

- Jay

---

### Post by The Weather Underground on 2007-05-13
bump

I am getting this same message

---

### Post by James.Hoffman on 2007-05-13
When running the make install command are you doing it as sudo?

If not that is your problem, because you need to have root permissions to install ndiswrapper.

So it should be

"Sudo make install"
Without quotes

---

### Post by The Weather Underground on 2007-05-13
Yes, i'm doing it with Sudo, and I'm not getting permission errors, but the Clock error I am getting...

---

