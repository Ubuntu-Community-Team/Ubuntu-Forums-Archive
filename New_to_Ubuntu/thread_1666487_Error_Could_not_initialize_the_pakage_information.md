---
title: "Error Could not initialize the pakage information"
date: 2011-01-13
forum: New to Ubuntu
---

### Post by Ron Roy on 2011-01-13
Hello again,
Experiencing some problems with ubuntu 9.10. Went to install fonts using the terminal and got an error that the file/var/lib/dpkg/ could not be open, permission denied. Then a red circle with white line appeared and the error says the package list or staus file could not be parsed or open. Don't have a clue as to what to do.
Tried to sudo chmod 700 /var/lib/dpkg and nothing is happening. Sure could use some help. Getting tired of re-installing the entire system.
Thanks Ron

---

### Post by yeats on 2011-01-14
Could you post the full command you're using and the output (as code, using the # button when composing)?

That will give someone enough information to troubleshoot.

It's not a good idea in general to change permissions on anything that's owned by root, especially something as vital as dpkg :-).

---

