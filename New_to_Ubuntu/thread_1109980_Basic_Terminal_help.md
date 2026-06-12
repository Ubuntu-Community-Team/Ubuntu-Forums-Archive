---
title: "Basic Terminal help?"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by Xero Xenith on 2009-03-29
Hello, I'm using a tool called pdf2ps. I have 100 PDFs named numerically, from 101.pdf to 200.pdf.

Typing this:
```
pdf2ps 101.pdf
```
...results 101.ps, which is exactly what I need, for that particular one. However, typing this:

```
pdf2ps *.pdf
```
...does not batch process all of them.

How would I get it to process every single one?

---

### Post by hyper_ch on 2009-03-29
use "find"

---

### Post by Xero Xenith on 2009-03-29
No worries, I got it :)

```
for i in `ls *.pdf`; do pdf2ps $i; done
```

---

