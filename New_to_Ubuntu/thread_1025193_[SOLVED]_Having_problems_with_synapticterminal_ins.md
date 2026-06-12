---
title: "[SOLVED] Having problems with synaptic/terminal installation.."
date: 2008-12-29
forum: New to Ubuntu
---

### Post by MrJoeyUK on 2008-12-29
Okay so whenever I open synaptic I get the following.. 

```
dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

And I also get the same thing in terminal when I use 'sudo apt-get install xxxx'

What's causing this? And how do I fix it? Thanks for any help you can offer.

Joey.

---

### Post by fooman on 2008-12-29
open a terminal and try:

```
sudo dpkg --configure -a
```

then:

```
sudo apt-get update
```

see if that helps.

---

### Post by MrJoeyUK on 2008-12-29
> **fooman said:**
> open a terminal and try:

```
sudo dpkg --configure -a
```

then:

```
sudo apt-get update
```

see if that helps.

That worked a treat, thanks. Guess it was the most obvious thing to try yet not the first thing to pop into my head :(

PS: Could a mod delete my duplicate thread? I clicked submit thread once, I get a white 'server error' page, so I go back and try again and got the same thing, then I realise I made two threads anyway. Sorry.

---

