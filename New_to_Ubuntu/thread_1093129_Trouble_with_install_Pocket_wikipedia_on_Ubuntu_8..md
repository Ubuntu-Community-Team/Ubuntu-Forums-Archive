---
title: "Trouble with install Pocket wikipedia on Ubuntu 8.10"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by plutov03 on 2009-03-11
I've downloaded  Pocket wikipedia form it's homepage.I did as it says on Readme file:"Copy Wikipedia.wi and WikipediaL files in the same directory on your disk and execute double click on WikipediaL file",but nothing happen.In windows it did well.
please help me.I spent nearly 1 hour to download it.
Thanks a lot.:(

---

### Post by skymera on 2009-03-11
Make the WikipediaL file executable

```
 chmod + x WikipediaL
./WikipediaL 
```

That should make the file executable then run it.
Use sudo if necessary

---

### Post by plutov03 on 2009-03-11
Can you make it clearer?
I'm a complete newbie.the files are in :
  /home/plutov03/Documents/Wikipedia
Can you write commands for me?:(

chmod: cannot access `x': No such file or directory
chmod: cannot access `WikipediaL': No such file or directory

---

### Post by plutov03 on 2009-03-11
Thank you.I've  done it.But it looks too ugly.
thanks again.

---

### Post by skymera on 2009-03-11
> **plutov03 said:**
> Thank you.I've  done it.But it looks too ugly.
thanks again.

oh sorry. Just noticed my typo :(

Should be +x not + x

---

