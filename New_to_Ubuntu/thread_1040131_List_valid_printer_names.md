---
title: "List valid printer names"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by Mariane on 2009-01-15
Please, is there a command which lists valid printer names? I'm on a network here, I did not install the printers so I have no idea what they are called. 

The "file/print" command just does nothing. 

lpr file.pdf 
says:
lpr: Error - no default destination available

pdftops file.pdf 
produced an openable and readable file.ps, so 
I think the file is OK. 

Mariane

---

### Post by cmnorton on 2009-01-16
lpstat -a

---

