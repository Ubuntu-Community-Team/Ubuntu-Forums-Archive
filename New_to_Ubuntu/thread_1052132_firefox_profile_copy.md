---
title: "firefox profile copy"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by arjuntank on 2009-01-27
how can i copy a profile folder into another newly made profile folder?
can i copy the contents of the older profile folder into the new one?
my profile folder is like "tjeksfng.default"
i have firefox 3.0.5

regards

arjun

---

### Post by sarpulhu on 2009-01-27
just copy the whole .mozilla folder over.

---

### Post by arjuntank on 2009-01-27
> **sarpulhu said:**
> just copy the whole .mozilla folder over.


i tried to do that last time but it doesnt work that way..
and i got some serious problems with that old default profile 
i think its a bug or may be a virus, because that profile was 3 months and costs 140Mbytes
and if i replace that way, firefox wont start giving a message that firefox is already running and i should restart my system or kill firefox to start again..and yes i searched every corner of current processes through ps and grep'd it and also did killall firefox..and firefox was nowhere to be found! that is really weird..!

Help!

---

### Post by philinux on 2009-01-27
Easiest solution is to backup/save you bookmarks. Delete the .mozilla folder and restart FF to create a new one. Then just copy your bookmarks.html file back. Then just download the addons you need.

---

### Post by stchman on 2009-01-27
> **arjuntank said:**
> how can i copy a profile folder into another newly made profile folder?
can i copy the contents of the older profile folder into the new one?
my profile folder is like "tjeksfng.default"
i have firefox 3.0.5

regards

arjun

Use this line:

```

cd ~/.mozilla
find . -depth -print0 | cpio --null --sparse -pvd <dest> 	

```

Where <dest> is the destination folder.

---

