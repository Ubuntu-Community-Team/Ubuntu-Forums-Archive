---
title: "Sh: secured solution to get the filename without extension and extension ?"
date: 2010-11-02
forum: New to Ubuntu
---

### Post by honeybear on 2010-11-02
this solution is not necessarily working all the time?

Bash favors it, sh not :( 

```
#!/bin/sh

a='testfile.test.txt'

echo "Filename: ${a%.*}"
echo "Extension: ${a##*.}"

```

---

### Post by Vaphell on 2010-11-02
how is this not working?

---

