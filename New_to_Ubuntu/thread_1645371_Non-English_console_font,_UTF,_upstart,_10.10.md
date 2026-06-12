---
title: "Non-English console font, UTF, upstart, 10.10"
date: 2010-12-14
forum: New to Ubuntu
---

### Post by tkzv on 2010-12-14
How to change Linux console font in version 10.10? Currently I get white squares for all non-ASCII characters. I have packages console-setup, console-terminus and fonty-rg installed. How to check whether necessary daemons have started?


Forgot to mention:
**locale** command shows every environment variable to be "ru_RU.UTF-8", except LC_ALL which is empty.

But **set** command shows any LC_ only inside _get_cword () function.

LANG variable is correct: "ru_RU.UTF-8".

---

