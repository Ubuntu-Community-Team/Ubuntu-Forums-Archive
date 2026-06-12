---
title: "patches"
date: 2010-08-04
forum: New to Ubuntu
---

### Post by beelzebufo on 2010-08-04
stupid question, I know you will probably say, if you don't know, you shouldn't do it.  but I would like to learn, so can someone tell me what a patch is and how to use it? I can't seem to find any "patching for dummies" kind of stuff.  any help would be greatly appreciated.  thanks

P.S. I am trying to use a patch to enable injection in aircrack-ng (for my own network of course)

---

### Post by aeiah on 2010-08-04
patches can be thought of as find and replace scripts, i suppose. a patch will insert and/or remove code from source code to enable more functionality or correct a bug. you then compile the changed code.

if you read the patch file in a text editor, you'll see line numbers +++ signs and --- signs etc. this is basically a set of instructions that the program 'patch' will use to find and replace segments of code for you.

. look at the man pages for patch either with this command in the terminal:
```

man patch

```

or somewhere like [here](http://linux.about.com/od/commands/l/blcmdl1_patch.htm)

or maybe google for examples on how to use patch to apply a patch to your driver. incidentally, are you sure this driver isnt available somewhere pre-compiled, or pre-patched?

---

### Post by Paul820 on 2010-08-04
Read here: [http://en.wikipedia.org/wiki/Patch_%28computing%29]("http://en.wikipedia.org/wiki/Patch_%28computing%29")
If you have a patch then there should be instructions on how to apply it. Did it come with a 'readme' document?
EDIT: This might be better [http://en.wikipedia.org/wiki/Patch_%28Unix%29]("http://en.wikipedia.org/wiki/Patch_%28Unix%29")

---

### Post by beelzebufo on 2010-08-04
I am not sure if this driver (madwifi-ng) is available pre patched, it's not real easy to get instructions on it either, especially for a noob, thanks a lot for the quick responses and information, I have to check it out tomorrow, I am sure I will have more questions then, thanks again

---

### Post by t0p on 2010-08-04
As you no doubt realise by now, a patch will enable functionality that normally would not be possible.

To find out all the patches avaikable for aircrack-ng, I advise you to go check out the site at [backtracklinux.org]("http://backtracklinux.org/").  Lots of info there on what patches are available for what chipsets, where to get them from, and what to do with them once you've downloaded them.  Anything you don't understand: feel free to come back and pick our brains again.  

Happy to help!

---

### Post by Paul820 on 2010-08-04
Have you had a look at this? [http://www.aircrack-ng.org/doku.php?id=madwifi-ng]("http://www.aircrack-ng.org/doku.php?id=madwifi-ng")

---

