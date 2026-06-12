---
title: "ls - shows more folders/files than I can see"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by jordanguyoflove on 2009-07-06
See for yourself:
Can you explain why this is happening and how to solve this problem? Thanks.

---

### Post by Tyke91 on 2009-07-06
those aren't problems.

Many text editors make a swap files with a '~' on the end of the file name in order to buffer.

you can remove them if you'd like using ```
rm *~
``` but you don't really need to.

---

### Post by Revolutionary101 on 2009-07-06
I think it is because terminal shows hidden files. 

What you are seeing on your desktop are only non-hidden files.

Open a Nautilus and go to your Desktop folder. Then make hidden files visible by pressing Ctrl+H. That should show all of the files that showed up in terminal.

---

### Post by Celauran on 2009-07-06
> **Revolutionary101 said:**
> I think it is because terminal shows hidden files. 

What you are seeing on your desktop are only non-hidden files.

Open a Nautilus and go to your Desktop folder. Then make hidden files visible by pressing Ctrl+H. That should show all of the files that showed up in terminal.

At the risk of being pedantic, xxx~ aren't hidden files, they're backups. Nautilus treats them the same as hidden files, the terminal does not (hence why they show up without using -a or -A)

---

### Post by Revolutionary101 on 2009-07-06
> **Celauran said:**
> At the risk of being pedantic, xxx~ aren't hidden files, they're backups. Nautilus treats them the same as hidden files, the terminal does not (hence why they show up without using -a or -A)

Thanks for the info.

---

### Post by Tyke91 on 2009-07-06
> **Celauran said:**
> At the risk of being pedantic, xxx~ aren't hidden files, they're backups. Nautilus treats them the same as hidden files, the terminal does not (hence why they show up without using -a or -A)

I always wondered about that...

thx :)

---

### Post by poosietgp on 2009-07-07
take note that files starting with "." example .foo by default will be hidden graphically.

---

