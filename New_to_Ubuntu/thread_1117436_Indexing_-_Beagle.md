---
title: "Indexing - Beagle"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by dunbrokin on 2009-04-05
I switched from Ubuntu to Kubuntu at the weekend. My Beagle desktop search was working fine in Ubuntu (as far as I am aware)...however in Kubuntu it will not index my home folder or Documents folder (yes it is ticked)....is there a bug?

---

### Post by ronocdh on 2009-04-06
> **dunbrokin said:**
> I switched from Ubuntu to Kubuntu at the weekend. My Beagle desktop search was working fine in Ubuntu (as far as I am aware)...however in Kubuntu it will not index my home folder or Documents folder (yes it is ticked)....is there a bug?
No bug with KDE afaik... you can, however, remove the .beagle directory from your home directory which will force a full reindex.

Another, perhaps safer, option is to force a full reindex at high speed. Read the [Beagle FAQ]("http://beagle-project.org/FAQ") for how to do this.

Just make sure that in the settings for Beagle, you have the directories declared which you want to index!

---

### Post by dunbrokin on 2009-04-06
Thanks - removing .beagle worked.....however, it does not seem to be indexing Thunderbird...even though the FAQ says that it does....strange.

---

