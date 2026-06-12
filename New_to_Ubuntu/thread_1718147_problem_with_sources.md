---
title: "problem with sources"
date: 2011-03-30
forum: New to Ubuntu
---

### Post by ramjeesaradi on 2011-03-30
hi I'm getting the following error while running update manager or Synaptic package manager. 
Can some one please provide me the solution
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/repo.palatinus.cz_stable_Packages
E: The package lists or status file could not be parsed or opened.
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/repo.palatinus.cz_stable_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by wolfen69 on 2011-03-31
Do:
```
sudo rm /var/lib/apt/lists/* -vf
```
then
```
sudo apt-get update
```

---

### Post by ramjeesaradi on 2011-03-31
Thank You very much.:D [wolfen69]("http://ubuntuforums.org/member.php?u=3744")
can you also please tell me what the problem about..

---

### Post by wolfen69 on 2011-03-31
Suffice it to say your /apt/lists/ file needed to be purged. Glad it worked for you.

---

