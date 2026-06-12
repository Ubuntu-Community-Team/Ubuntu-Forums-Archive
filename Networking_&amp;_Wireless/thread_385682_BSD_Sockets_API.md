---
title: "BSD Sockets API"
date: 2007-03-16
forum: Networking &amp; Wireless
---

### Post by haricharan on 2007-03-16
Hi

Where can I download the BSD Sockets API from? I googled but couldn't find it!

Thank you

---

### Post by gradedcheese on 2007-03-16
Um... Linux comes with it.  Perhaps you're missing the man pages?  Try...

```

man socket

```

To get more man pages:

```

sudo apt-get install manpages-dev

```

now run...

man select
man bind
man connect

...and so on

---

### Post by haricharan on 2007-03-16
can you tell me the packages which constitute to BSD sockets API. I am trying to get it work on my friend's laptop who is using OpenSUSE and it doesn't come by default in that. I tried to run the same code in my Ubuntu laptop and it works...but couldnt find the packages

---

### Post by gradedcheese on 2007-03-16
I don't know anything about SUSE or how their packages work, you should ask some SUSE people (or search his package manager software).  All Linux distros come with BSD sockets, however he's just missing the header files most likely.  These are included as linux-headers-name_of_kernel in Ubuntu, and there's probably a similar "Linux headers" or "kernel headers" package in SUSE.

---

### Post by haricharan on 2007-03-16
ok thank you...lemme try that....:)

---

