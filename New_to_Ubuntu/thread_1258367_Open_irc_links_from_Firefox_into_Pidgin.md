---
title: "Open irc:// links from Firefox into Pidgin"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by hanzj on 2009-09-04
Hello,

When I'm in the firefox browser, how can I have "irc://" links open up in pidgin?

Currently, when I click an "irc://" link, I see a "launch application" window open up. The 2 options are: purple-url-handler, which does nothing; and "Mibbit" which I prefer not to use.
I tried adding pidgin to the list (by selecting /usr/bin/pidgin), but nothing happens.

Please help.

---

### Post by coldReactive on 2009-09-04
> **hanzj said:**
> purple-url-handler, which does nothing

[http://developer.pidgin.im/ticket/3692](http://developer.pidgin.im/ticket/3692)

---

### Post by hanzj on 2009-09-04
if I can summarize that pidgin.im page that coldReactive linked to, a request to have URI handling in Pidgin was submitted, but so far, there is none of this yet.

---

### Post by coldReactive on 2009-09-04
> **hanzj said:**
> if I can summarize that pidgin.im page that coldReactive linked to, a request to have URI handling in Pidgin was submitted, but so far, there is none of this yet.

Just like how passwords saved are not encrypted: Both it and this IRC thing are set to "patches welcome."

---

### Post by gasull on 2009-11-29
It works for me adding```
 /usr/bin/purple-url-handler
``` to the list.

---

### Post by ubunaut on 2010-04-30
> **gasull said:**
> It works for me adding```
 /usr/bin/purple-url-handler
``` to the list.

This works although you must first set up an account in Pidgin for the IRC server.

---

