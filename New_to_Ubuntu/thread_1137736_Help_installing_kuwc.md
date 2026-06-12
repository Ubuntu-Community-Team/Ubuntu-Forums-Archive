---
title: "Help installing kuwc"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by mystmaiden on 2009-04-25
I've used webshots as backgrounds and screen saver for years, and  really miss it. I found someone had recommended kuwc to operate webshots in linux. I searched and did not find a deb package for it, just a tar.bz2 which I downloaded and extracted to a folder on my desktop.

The information included says the simplest way to install it is run the command:

python setup.py install

I attempted it and got:

python: can't open file 'setup.py': [Errno 2] No such file or directory


Honestly, I'm not at all sure how to go about this, but I would love to get this working. Its been years since I messed with a tar.

mystmaiden

---

### Post by cariboo on 2009-04-26
If you are in the same directory as setup.py the command should be:

```
python ./setup.py install
```

the above command will only install the program in your home directory.

---

### Post by mystmaiden on 2009-04-26
I'm a complete newbie, so I am not at all sure I understand, but I tried installing it both as a user and as root and neither worked.  I am wondering if I need to do something to get python scripting to work? Or do I need to something before  using the above command.

mystmaiden

I'm half way there - I think- I did get uwc installed and found the thread here with the work around to get webshots going. Hopefully, I can sort that out.

---

