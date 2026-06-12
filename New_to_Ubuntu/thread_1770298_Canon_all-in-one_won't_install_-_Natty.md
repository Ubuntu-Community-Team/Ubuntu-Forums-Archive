---
title: "Canon all-in-one won't install - Natty"
date: 2011-05-29
forum: New to Ubuntu
---

### Post by thenudehamster on 2011-05-29
I've just upgraded to 11.04 and am having trouble getting my Canon PIXMA 6150 to work with it. So far I've only used it from a W7 or Vista machine, where it works perfectly.

I have two printers, both ethernetted directly to the router, an OKI 430dn LED (laser clone) page printer and the aforementioned Canon all-in-one. The OKI was no trouble - add new printer, find network printer, select correct .ppd file and all is sweetness and light. The Canon is not so forgiving.

To begin with, I tried the same routine, and it could not find the printer - kept asking me to log into WORKGROUP, which is not my local workgroup's name, and didn't recognise me anyway. So I went to Canon's site, downloaded a pair of drivers, (printer and scanner) in .tar.gz archives. Now I'm not that familiar with tarballs, but I managed to get inside well enough to find the installation instructions. Fairly simple - open terminal, extract files, change to .deb directory, run install script - except if fails with an error of: "package management system unrecognised".

Now what? am I missing something, or is it that the Canon driver installer is incompatible with the new Software Centre? Canon do have source code files available, but I'm wary of trying to compile code on the fly without help; I'm a user not a programmer - that's was my late wife's talent - but I'll try it if someone can tell me how.

That apart, if anyone has any useful ideas, I'm all ears.

---

### Post by yeats on 2011-05-30
> Fairly simple - open terminal, extract files, change to .deb directory, run install script - except if fails with an error of: "package management system unrecognised".

Can you try again and paste the full output here (within CODE tags - clicking the # symbol while composing will provide them)?

Also, which Canon site did you install from?  Can you provide the link you used?

---

