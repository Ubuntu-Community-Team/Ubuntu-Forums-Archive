---
title: "Backup keys?"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by garthcrocker on 2009-10-14
Hi! The answer to this is probably very simple but I can't find it. I've used an answer by Sarmacid (Aug 20th, 2008) to set up encrypt/decrypt of some files of a novel I've been writing and would be embarrassed if too many people go to see it. That's working fine, but Sarmacid recommends backing up my keys. He says 'Go to Keys - Backup keyrings but for the life of me I can't find that. I'm getting the feeling there might be something in euthenasia after all. Clearly I should be taken out back and put down like an old dog! :confused:

---

### Post by dvlchd3 on 2009-10-15
Not sure how to do it graphically, but here's how to do it from the command-line

```

gpg --list-key [optional email address here]

```

Find your key, it will usually look something like:
pub   1024D/2FBEA691 2007-11-17
(The 2FBEA691 is the important part here)

```

gpg -a --export 2FBEA691 > my_key.asc

```
'my_key.asc' can be replaced with whatever filename you'd like.

To restore:
```

gpg --import my_key.asc

```

---

### Post by garthcrocker on 2009-10-15
Many thanks for that. Found it OK in GUI form under the Export facility. You've made a friend for life. That's the trouble with writing salacious pornographic novels! Lol! 

GC.

---

