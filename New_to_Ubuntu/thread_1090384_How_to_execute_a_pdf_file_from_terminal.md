---
title: "How to execute a pdf file from terminal"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by amrutayan on 2009-03-08
i want to open a pdf file from terminal without double clicking on the pdf file so wht should be my command in the terminal???

---

### Post by ugm6hr on 2009-03-08
```
evince name_of_file.pdf
```

---

### Post by amrutayan on 2009-03-08
thanks dude

---

### Post by lswb on 2009-03-08
Also, the command "xdg-open filename.ext" will open a file using the same program that is used when double-clicking on a file in your default file manager.

---

### Post by ugm6hr on 2009-03-08
> **lswb said:**
> Also, the command "xdg-open filename.ext" will open a file using the same program that is used when double-clicking on a file in your default file manager.

I'd forgotten that.

gnome-open does the same (in Gnome).

---

