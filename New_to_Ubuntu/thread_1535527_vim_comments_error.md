---
title: "vim comments error"
date: 2010-07-21
forum: New to Ubuntu
---

### Post by Chris1274 on 2010-07-21
I thought that text editors like vim took the # to indicate a comment and pass over those lines.

Here's the content of my ~/.vimrc file:
```
# Testing comments
set nocompatible

# Testing comments
set number
```

But when I run vim, I get this:

Error detected while processing /home/user/.vimrc:
line    1:
E488: Trailing characters: # Testing comments
line    4:
E488: Trailing characters: # Testing comments

When I remove the comment lines it works fine, but I should like to be able to add comments to my text files without it fouling things up. Does anyone know what I'm doing wrong?

---

### Post by DaithiF on 2010-07-21
Hi,
use " not # to indicate a comment line for vim

---

