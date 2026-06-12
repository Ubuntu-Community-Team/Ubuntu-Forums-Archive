---
title: "remove &quot;link to&quot; from multiple files"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by Archer Troy on 2009-01-10
i have alot of link in a folder, they all have "link to" in front of them. Short of going through everyone of them,anyone know how I can remove the "link to" in front of all of them.

---

### Post by stanz on 2009-01-10
If you did not create all these 'link to' files, they may be system files that are needed.

What version do you have installed & where are you going in the directory - to see these files?

Offer more information...don't just delete !!

---

### Post by Archer Troy on 2009-01-10
haha. no i created them. Its for my mythbuntu box. All of my movies have their own separate folder, so instead of listing every single folder i just made links to all of the movies in a separate folder, but they all show up as "**link to** whatever" and id rather not delete all 500 separately. although i will if theres no quick way to do it.

sorry, probably should have explained my situation a bit better. thanks for the reply

---

### Post by lswb on 2009-01-10
If these links and the files they point to are in the same directory, they cannot have the same name, as would happen if "link to" was just removed from the remaining portion of the name. 

If the links point to files in other directories, you could do something like this at the cli or in a script: 

WARNING: Untested code! for proof of concept only! TEST BEFORE USING!
```

for FILE in "link to"*
do
mv "$FILE" "${FILE:7}"
done

```

If any of the links point to directories they may need special handling.

---

### Post by Archer Troy on 2009-01-23
i found a pretty easy way... Its a program called bulk renamer. really easy, really effective for renaming multiple files quickly.

---

