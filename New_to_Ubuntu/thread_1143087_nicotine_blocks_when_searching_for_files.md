---
title: "nicotine blocks when searching for files"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by Cozze on 2009-04-29
I upgraded to 9.04 and ever since nicotine blocks after a few seconds once I start searching for files. Anyone an idea how to resolve this problem?

Thanks, Cozze

---

### Post by robine on 2009-12-09
I just switched to Ubuntu and got the same thing. I was really looking forward to downloading music again!

Any suggestions?

---

### Post by Chesamo on 2009-12-09
1. I wouldn't mention that in a public forum, rob ;)
2. Try this:
```
rm -r ~/.nicotine
sudo apt-get purge nicotine
sudo apt-get install nicotine
```
This should, in theory, remove Nicotine from your system and reinstall it. It sounds like it broke during the upgrade -- this should fix it.

---

### Post by Soul-Sing on 2009-12-09
Nicotine blocks/stops sometimes when your "searchword" is too general, you get to many info/hits from nicotine, and as a result nicotine stops working.

---

