---
title: "Search for file when folder name unknown"
date: 2011-07-18
forum: New to Ubuntu
---

### Post by FredVanH on 2011-07-18
Hi.  How do I search for a file by partial name when I do not know what folder it resides in (that's why I'm searching)?  I thought I downloaded TrueCrypt in Ubuntu 11.04 but when what I downloaded did not open automatically, as I had asked for, and I could not find it in the Home directory, I wanted to see where it went.  Any clues as to how to (universally) search when I don't know the folder name would be appreciated.
Thanks,
Fred

---

### Post by Grenage on 2011-07-18
In the GUI, and with Nautilus, go to your top level and press *ctrl-f*; you can enter your file name and search.

In the CLI, use something like:

```
find /home/user -type f -name myfile.bin
```

---

### Post by kalimojo on 2011-07-18
i found catfish a very good search tool

sudo apt-get install catfish

---

### Post by FredVanH on 2011-07-19
Thanks guys/gals!
Fred
:popcorn:

---

