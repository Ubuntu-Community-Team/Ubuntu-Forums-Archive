---
title: "What does %s do?"
date: 2010-09-16
forum: New to Ubuntu
---

### Post by nrogers64 on 2010-09-16
I read on [this blog post]("http://www.liberiangeek.net/2010/07/automatically-start-programs-ubuntu-10-04-lucid-lynx-ubuntu-starts/") that if you want to add Firefox to the list of startup programs, this is the command you should use:

firefox %s

What is the "%s" for? In my tests, it appears that the "firefox %s" command is no different than the "firefox" command.

Thank you!

---

### Post by ubunterooster on 2010-09-16
It appears to be "start" which is redundant and pointless. I have no idea why it was said to add that

---

### Post by sisco311 on 2010-09-16
%s is not a valid field code. 

The .desktop specification website has [the full list of special field codes and description]("http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s06.html").

---

