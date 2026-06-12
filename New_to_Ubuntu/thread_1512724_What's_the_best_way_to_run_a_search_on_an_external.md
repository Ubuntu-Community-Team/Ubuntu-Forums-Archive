---
title: "What's the best way to run a search on an external HD attached to another PC?"
date: 2010-06-18
forum: New to Ubuntu
---

### Post by diablo75 on 2010-06-18
I have a computer setup that functions as a server for a few different things (SSH access to other computers for sharing media, hosting media to my PS3, blah blah).

So I have nautilus bookmarks setup to automatically connect to this computer via SSH.  There is an external hard drive attached to this server with a lot of stuff on it and I'd like to be able to run searches against it from time to time.  I'm used to using the "locate" command in terminal, but I'm pretty sure this tool relies on an indexing daemon that doesn't monitor the contents of other computes, much less their external HDs.

What's the best way to do file name searches on a hard drive that's attached to another PC?

---

### Post by John Bean on 2010-06-18
I'd use "find" in a terminal. Do a "man find" for info.

---

