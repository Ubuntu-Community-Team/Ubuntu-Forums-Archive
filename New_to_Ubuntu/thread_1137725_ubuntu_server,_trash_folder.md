---
title: "ubuntu server, trash folder?"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by lmlypfan on 2009-04-25
I accidentally deleted a file on my ubuntu server. 
Is it gone, or is it moved to a "trash bin" type folder?

Thanks

---

### Post by pytheas22 on 2009-04-25
If you deleted it using the 'rm' command, it's gone, unfortunately.  If it was an important file, there are various methods you can use to [recover it]("https://help.ubuntu.com/community/DataRecovery"), though.  photorec is probably the easiest option, but it will only work if the file was of a popular format (.txt., .doc, .pdf, .iso, etc.).

---

### Post by lmlypfan on 2009-04-25
thanks, i'll just have to re-download it.

---

### Post by MrWES on 2009-04-25
> **lmlypfan said:**
> thanks, i'll just have to re-download it.

You might want to consider placing this alias in your .bash_aliases file:

```
alias rm='rm -i'

```

I'll prompt you for confirmation the next time you delete any files.

Bill

---

