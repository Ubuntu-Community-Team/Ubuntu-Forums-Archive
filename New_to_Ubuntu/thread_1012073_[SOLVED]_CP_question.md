---
title: "[SOLVED] CP question"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by corp.linux on 2008-12-15
I'm new to the UNIX Command Line and would like to use copy (CP) to copy a file (lets say first.txt) to a new file (lets say first.txt.trial) using wildcards.  In Windows the following works:
copy *.txt **.trial

this results in the orignal first.txt being copied to the same directory as first.txt.trial

Question: How to accomplish this in Ubuntu?

Clarification: How to accomplish this in Ubuntu using wildcard for input and output file name like example above in Windows.

---

### Post by Titan8990 on 2008-12-15
cp *.txt first.txt.trial

---

### Post by corp.linux on 2008-12-15
OK, but how to do it by using wildcards on the output (filename2)?

---

### Post by kaibob on 2008-12-15
Although not exactly what you want, the following will work:

```
for file in *.txt ; do cp "${file}" "${file/%/.trial}" ; done
```

If this is something often used, and if no one has an easier solution, you could place the above command-line in your bashrc file and use command-line arguments for the extension of the original files and for the extension that will be added. So, you would only have to type something like:

```
cpbak txt trial
```

Hopefully, someone will know how to do this with wildcards as can be done in Windows.

---

### Post by Titan8990 on 2008-12-15
Yeh, I was pondering it myself, I was thinking using find -name *.txt and putting it in an environment variable, but I can see a lot of issue with that.


This will be an interesting topic.

---

