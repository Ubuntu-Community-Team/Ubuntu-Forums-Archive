---
title: "How to Rename a file with ! Character?"
date: 2009-08-02
forum: New to Ubuntu
---

### Post by jrocheleau on 2009-08-02
I tried running the command 

```
sudo mv file!.jpg file.jpg
```

But it keeps giving me this weird error:

```
bash: !.jpg": event not found
```

Any idea why this would be happening? I know I can easily rename the file in the GUI, but this is more out of curiosity to prove anything can be done in the terminal.

---

### Post by credobyte on 2009-08-02
```
sudo mv "file!.jpg" "file.jpg"

```

---

### Post by j.bell730 on 2009-08-02
Actually, it would be like this:
```
sudo mv file\!.txt file.txt
```
The backslash is used for characters that could be ambiguous in meaning.

---

### Post by jrocheleau on 2009-08-03
Awesome, thanks! I tried it with the quotes and it didn't work, but the escape character worked perfectly. I know it's kind of a noob question, but thanks for the help!

---

### Post by colau on 2009-08-15
> **j.bell730 said:**
> actually, it would be like this:
```
sudo mv file\!.txt file.txt
```
the backslash is used for characters that could be ambiguous in meaning.
+1

---

