---
title: "Word search in files using Bash"
date: 2010-10-09
forum: New to Ubuntu
---

### Post by nnjond on 2010-10-09
Hi,
Can someone help me please/

I'm trying to use Bash to search some directories for a word in one of documents. I've tried:

```
$ grep -R Brzeninski ///Dual_Data/
```

---

### Post by Vaphell on 2010-10-09
if these documents are not plain text, grep won't help you. IIRC document types from MSOffice and OpenOffice are zipped xml files or something, there is no way to grep their content

---

### Post by nnjond on 2010-10-09
Thanks for telling me. Could you advise me on finding a word that Is in an.odt?

---

### Post by bodhi.zazen on 2010-10-09
> **nnjond said:**
> Thanks for telling me. Could you advise me on finding a word that Is in an.odt?

See this post :

[http://ubuntuforums.org/showpost.php?p=8531314&postcount=17](http://ubuntuforums.org/showpost.php?p=8531314&postcount=17)

---

### Post by jtarin on 2010-10-09
[Here]("http://www.linuxforums.org/forum/programming-scripting/66539-grep-binaries.html") are some solutions that work for some.

---

