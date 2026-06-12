---
title: "Where will the type of modem I use be located in the scanmodem folder?"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by gymophett on 2009-01-30
Scanmodem did the scan on my computer. It made an extra folder called modem. Supposedly one of the text files in there say what type dial up modem I have so I can install it. Which one is it?

---

### Post by cariboo on 2009-01-30
How many files are there?

Check what your modem is by running in a Applications-->Accessories-->Terminal:

```
lspci | grep modem
```

This will search through the list of pci devices in your computer, but will only output the lines with the word modem in them. This might give an indication what file you may want to look in.

Jim

---

