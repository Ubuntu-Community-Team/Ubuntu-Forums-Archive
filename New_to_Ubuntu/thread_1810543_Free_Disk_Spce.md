---
title: "Free Disk Spce"
date: 2011-07-23
forum: New to Ubuntu
---

### Post by DaveMcC on 2011-07-23
I thought I had an app "Disk Usage Analyser" that showed what free disk space I had left, but it don't show that it shows what is on the disk

Open to suggestions, what the app is called 

Dave

---

### Post by Autodave on 2011-07-23
> **DaveMcC said:**
> I thought I had an app "Disk Usage Analyser" that showed what free disk space I had left, but it don't show that it shows what is on the disk

Open to suggestions, what the app is called 

Dave

That program is under ACCESSORIES.

Click APPLICATIONS -> ACCESSORIES -> DISK USAGE ANALYZER

---

### Post by CatKiller on 2011-07-23
> **DaveMcC said:**
> Open to suggestions, what the app is called

baobab

---

### Post by 2F4U on 2011-07-23
If you can't find the application, open a terminal and type

```
df -h
```

That will show you how much space is occupied and available.

---

### Post by DaveMcC on 2011-07-24
> **Autodave said:**
> That program is under ACCESSORIES.

Click APPLICATIONS -> ACCESSORIES -> DISK USAGE ANALYZER

For some strange reason, my copy shows 100% usage not what is free?

but df -h told me what I needed to know "free space"

thanks all

---

### Post by CatKiller on 2011-07-24
> **DaveMcC said:**
> For some strange reason, my copy shows 100% usage not what is free?

You misunderstand what the 100% is telling you. Essentially it's saying that everything that's used is used. Baobab shows you what is being used where of the space that's been used. It necessarily adds up to 100% because it's proportions of what's used rather than proportions of what's available.

---

### Post by DaveMcC on 2011-07-24
> **CatKiller said:**
> You misunderstand what the 100% is telling you. Essentially it's saying that everything that's used is used. Baobab shows you what is being used where of the space that's been used. It necessarily adds up to 100% because it's proportions of what's used rather than proportions of what's available.

Ya,, if I were a diver and the gauge told me what amount of breaths I had taken and not how many I had left
I don't think I would be diving as the gauge would let me die first...? :confused:

Looked at it again,   "Disk Usage Analyser"  it says Total file-system capacity 291gb, err no.. I know for a fact it is 100gb for ubuntu and 20gb for (winxp) "needed" wonder where it found an extra 171gb ? :confused: ?

Dave

---

### Post by CatKiller on 2011-07-24
> **DaveMcC said:**
> Ya,, if I were a diver and the gauge told me what amount of breaths I had taken and not how many I had left
I don't think I would be diving as the gauge would let me die first...? :confused:

Looked at it again,   "Disk Usage Analyser"  it says Total file-system capacity 291gb, err no.. I know for a fact it is 100gb for ubuntu and 20gb for (winxp) "needed" wonder where it found an extra 171gb ? :confused: ?

Dave

The fact that you don't understand the display doesn't change what it's displaying. It shows the location of usage in the filesystem tree. That's everything that's used, wherever it happens to be mounted.

Why would you need to see the usage of space that isn't used? It isn't used, so there's no usage.

There are other tools that show proportions of what's used against what's available. Baobab isn't one of them. It isn't really that hard to follow.

---

### Post by DaveMcC on 2011-07-25
> **CatKiller said:**
> The fact that you don't understand the display doesn't change what it's displaying. It shows the location of usage in the filesystem tree. That's everything that's used, wherever it happens to be mounted.

Why would you need to see the usage of space that isn't used? It isn't used, so there's no usage.

There are other tools that show proportions of what's used against what's available. Baobab isn't one of them. It isn't really that hard to follow.

With-out getting into a debate about this

When I go to off load my photos from the card, there is no point starting to off load / move from the card to the disk, if there is NOT ENOUGH SPACE 

 It isn't really that hard to follow

---

### Post by CatKiller on 2011-07-25
But that's not what that tool is for. It's for answering the question, "where the hell has all my hard drive space gone?" You might still want it to do something else, but it doesn't.

If it was "Disk Space Analyser," or even "Disk Management Tool," you might have a point. But it isn't.

---

