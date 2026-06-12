---
title: "How can I sort a file and save the changes to the same file"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by techfish on 2010-02-07
How can I sort a file and save the changes to the same file

I use this line but it removes all the contents of the file
```
sort fileA > fileA
```

---

### Post by HermanAB on 2010-02-07
```
sort fileA > fileB;cp fileB fileA;rm fileB
```

---

### Post by Bachstelze on 2010-02-07
```
cat fileA | sort > fileA
```

---

### Post by falconindy on 2010-02-07
You'll need to use a temporary file or use another program to sort it in place. Vi can do this...

```
vi filetosort -s ':%!sort' -s ':wq'
```

But you're probably better off just doing...
```
sort FileA > FileB;mv File{B,A}
```

---

### Post by falconindy on 2010-02-07
> **Bachstelze said:**
> ```
cat fileA | sort > fileA
```

You just blew my mind... now you've got me wondering if process substitution would work as well since it creates a new FD in the process.

edit: joy. it does.
```
sort <(cat FileA) > File A
```

---

