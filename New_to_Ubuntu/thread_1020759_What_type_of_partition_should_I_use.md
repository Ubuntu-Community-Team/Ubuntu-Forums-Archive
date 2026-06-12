---
title: "What type of partition should I use?"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by innmate1436394 on 2008-12-24
Im going to dual boot Vista/Ubuntu and I need to know what type of partition should I use to have access to my Vista partition files. I couldn't find a good place that explains the different types.

---

### Post by snova on 2008-12-24
I'm not sure what you mean...

Ubuntu can access Vista's NTFS partitions without difficulty, it that's what you wish to know. In addition, Vista can't normally access native Ubuntu partitions.

I don't understand what you're trying to accomplish. Could you elaborate, please?

---

### Post by innmate1436394 on 2008-12-24
Yes thats what I need to know, I just wanted to know if I had to use any extra software to read Windows files from Ubuntu because I knew it was neccessary to read them the other way around.

---

### Post by kansasnoob on 2008-12-24
> **innmate1436394 said:**
> Yes thats what I need to know, I just wanted to know if I had to use any extra software to read Windows files from Ubuntu because I knew it was neccessary to read them the other way around.

I always add ntfsprogs to Ubuntu for simplicity in mounting NTFS partitions. It's in the repos so it can be installed either from synaptic or:

```
sudo apt-get install ntfsprogs
```

[http://www.linux-ntfs.org/doku.php](http://www.linux-ntfs.org/doku.php)

---

