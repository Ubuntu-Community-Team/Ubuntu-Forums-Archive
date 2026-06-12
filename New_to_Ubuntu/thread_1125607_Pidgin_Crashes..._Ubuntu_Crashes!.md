---
title: "Pidgin Crashes... Ubuntu Crashes!"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by LesterPalooza on 2009-04-14
Ubuntu crashes when I select "New Status..." in the status menu in Pidgin Internet Messenger. I am currently using a "saved" custom status and I am trying to make or edit a new one.

I am using Ubuntu 8.10 Intrepid Ibex. My friend recommended doing ctrl+alt+backspace to logout and reset the x.org. Haven't tried that yet, but based on the looks of my friend's solution, it is just temporary.

If you need more information about my system, please do tell me what to provide as to solve this problem. :)

Thanks!

---

### Post by nandemonai on 2009-04-15
> **LesterPalooza said:**
> Ubuntu crashes when I select "New Status..." in the status menu in Pidgin Internet Messenger. I am currently using a "saved" custom status and I am trying to make or edit a new one.

I am using Ubuntu 8.10 Intrepid Ibex. My friend recommended doing ctrl+alt+backspace to logout and reset the x.org. Haven't tried that yet, but based on the looks of my friend's solution, it is just temporary.

If you need more information about my system, please do tell me what to provide as to solve this problem. :)

Thanks!

Run pidgin from a terminal and record any errors it throws out at you.

If the system is hard locking then you can try restarting X as your friend suggested, this will at least let you get back to your desktop.

If it is hard crashing you then from terminal you can try this in order to record what is happening.

```
$ pidgin -d > ~/pidgin.txt
```

This will save a txt file with debugging information.

Attach it to a reply and we should be able to see what is causing the crash.

---

