---
title: "how to copy all of the data on one partition to another"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by energy. on 2009-04-26
I have a partition that I use for data storage.  it is called /space it is ext3

With the transition to 9.04 I want to store my data on an ext4 partion.  I have created an ext4 partition and called it /storage

I want to copy everything that is on /space to /storage

I will then delete /space and resize /storage to take its space

is copying all of the data on /space to /storage as easy as

```
sudo cp /space /storage
```

there are some hidden files on /space (porno directory) will these be copied as well?

---

### Post by Spiritous on 2009-04-26
SUDO - Root, Root = Admin, Admin Can see all files as its the system manager. So yes, It will move your pr0n. I'd say use ```
sudo cp /space /storage
``` As you said.

---

### Post by ddrichardson on 2009-04-26
You want to do:```

sudo cp -p -r /space /storage
```Or root will own the files on the new drive.

---

### Post by Spiritous on 2009-04-26
Sorry, Should of left it to the Ubuntu gurus :)

---

### Post by energy. on 2009-04-26
> **ddrichardson said:**
> You want to do:```

sudo cp -p -r /space /storage
```Or root will own the files on the new drive.

-p means don't change permissions?

---

### Post by ddrichardson on 2009-04-26
Yes and -r means recursive.

---

### Post by energy. on 2009-04-26
what does recursive mean?

---

### Post by ddrichardson on 2009-04-26
> **Spiritous said:**
> Sorry, Should of left it to the Ubuntu gurus :)
I thought it was another thread I was following where someone wanted to know how to set everything back to user:user from root:root - bizarre how similar questions seem to come up the same day.

---

### Post by ddrichardson on 2009-04-26
Recursive means it follows the folder tree. If you have /folder/folder1 and you type cp /folder /folder3 then you'll only get /folder3/folder. If you do it recursively you'll get /folder3/folder/folder1

---

### Post by energy. on 2009-04-26
thanks for your help.  the files are copying over now.  I wish that cp gave some info about the proportion of files that have been copied or estimated time until completion.

---

### Post by ddrichardson on 2009-04-26
It does - when you get the prompt back its done!

---

