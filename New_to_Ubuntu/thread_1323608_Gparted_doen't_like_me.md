---
title: "Gparted doen't like me"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by Pikzilla on 2009-11-11
Hey, sorry if this ends up being a double post- not sure whether the first attempt was posted. Anyhow, Gparted won't let me format a (Windows) ntfs partition into another ntfs. Any idea what's going on?

---

### Post by Aearenda on 2009-11-11
You probably need to install ntfsprogs as well for this.

---

### Post by Pikzilla on 2009-11-11
Huh. Where exactly do I get it?

---

### Post by mchecca on 2009-11-11
sudo apt-get install ntfsprogs

---

### Post by praveesh on 2009-11-11
> **Pikzilla said:**
> Huh. Where exactly do I get it?

this site might help you [http://www.linux-ntfs.org/doku.php](http://www.linux-ntfs.org/doku.php)   . Did you try searching in the Synaptic for ntfsprogs . System ->synaptic package manager->search type ntfsprog and press enter.

---

### Post by Tman5293 on 2009-11-11
Gparted by default doesn't manage ntfs partitions. So yeah you need to install an ntfs partitioner for that.

---

### Post by wilee-nilee on 2009-11-11
I think you have to use a gparted cd or a live Ubuntu Cd to change any partition and you may have to turn off swap to do this.

---

### Post by tommynz1975 on 2009-11-11
I think before you fire up gparted again. one needs to know if your on xp vista or win7

as vista and am guessing win7 also have its very own tools for splitting/growing a ntfs drive.
due to the fact MS don't play nice with no one, unless on their terms.

---

