---
title: "Cant md5sum in terminal"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by shires on 2009-12-30
I've tried to install a iso on atnother laptop, but this needed a patch that came later. My problem is that Ubuntu will not md5sum in terminal. I write md5sum and drag the file over to the window and press enter but nothing happens... I'am trying to find the md5 sum because checking that its not a corrupt file and to check that the patch worked. 

And is there another way for my to install the patch to the iso without going through terminal?

---

### Post by ugm6hr on 2009-12-30
Post a copy of what you are typing in Terminal and the response.

e.g.

```
md5sum ~/file.iso
```

---

### Post by Hallvor on 2009-12-30
> **shires said:**
> I've tried to install a iso on atnother laptop, but this needed a patch that came later. My problem is that Ubuntu will not md5sum in terminal. I write md5sum and drag the file over to the window and press enter but nothing happens... I'am trying to find the md5 sum because checking that its not a corrupt file and to check that the patch worked. 

And is there another way for my to install the patch to the iso without going through terminal?

Move the file to your home directory, then open the terminal and type md5sum and the name of your file. Assuming your file is called ubuntu.iso, type:

```
md5sum ubuntu.iso
```

---

