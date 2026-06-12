---
title: "how to enter folders with a space in the name"
date: 2011-05-13
forum: New to Ubuntu
---

### Post by ehsango on 2011-05-13
hi friends
how can i enter folders with a space in the name? like:"my folder"

---

### Post by Perfect Storm on 2011-05-13
```
cd "my folder"
```

Use the " "

---

### Post by amanchesterman on 2011-05-13
I'm not sure from your post **where** you want to enter a folder name like that?

However when I use the terminal, I sometimes need to enter such a folder name as part of the path to a file. It works OK if I enter it with double quotes around the folder name, exactly as you have it in your post. So the path in terminal looks like:

/home/myusername/afoldername/"another folder"/folder/ ... etc.

John

---

### Post by frankbooth on 2011-05-13
Typing whatever comes before the space followed by a '\' and pressing the tab key might be more convinient.
```

cd my\<tab>

```

---

### Post by dcsoldschool53 on 2011-05-13
> **ehsango said:**
> hi friends
how can i enter folders with a space in the name? like:"my folder"

Try,```
cd my\ folder
```Use a space between\ and folder's name.

---

