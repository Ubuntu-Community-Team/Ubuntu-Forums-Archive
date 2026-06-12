---
title: "How do I delete locked folders?"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by TerminalWhimsy on 2010-10-11
I was copying the contents of a CD (Orange Box) to my home directory so I could install it via wine, but my touchpad was messed up and I was forced to restart before the transfer was finished. Now, there's a folder with all of the files, but I don't have permission to alter or use them and it has a padlock insignia on it. When I try to delete it it says "Unable to trash file: Permission denied". Any suggestions/solutions?

Things I've tried:
Just deleting it: permission denied
Running nautilus and deleting it as root: unable to access home directory
Running variations of ```
sudo rm -Rf /home/Andrew/Orange Box
```: did nothing

---

### Post by Temposs on 2010-10-11
Press Alt-F2 and type the command:

```
gksudo nautilus
```

This is a root file browser. See if you can deal with the files with that :-)

---

### Post by TerminalWhimsy on 2010-10-11
Worked! Thanks a lot. :)

---

### Post by Norabunny on 2011-04-13
Works a charm, thanks!

---

### Post by crispy_420 on 2011-04-14
Might have also been an issue that Orange Box was two separate words. The command you issued would have failed because it was technically looking for a folded called Orange and not 'Orange Box'. Just an observation.

---

### Post by prashanthds96 on 2012-04-14
Thanks man worked like a charm !!!

---

### Post by mauleshjani on 2012-08-14
thanks a lot sir, really it works fine, thanks again

---

