---
title: "list size of all files in subdirectory"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by flylehe on 2009-07-02
Hi,
When I use ls under some directory, how can I list the size of all files in each subdirectory?
Thanks and regards!

---

### Post by Tyke91 on 2009-07-02
in each sub directory?

```
ls -lahR | less
```l is for long file names
a is for hidden files
h makes it easier to read
R is the recusion you want
less will make it easy to manage. trust me, you want to pipe it thru less

press q to exit less

---

### Post by austinpsycho on 2009-07-02
> **Tyke91 said:**
> in each sub directory?

```
ls -lahR | less
```l is for long file names
a is for hidden files
h makes it easier to read
R is the recusion you want
less will make it easy to manage. trust me, you want to pipe it thru less

press q to exit less
to put it in the same convention
|less creates a temporary file and opens it for easier browsing

well put though ;)

---

### Post by austinpsycho on 2009-07-02
on a side note; how do you do the neat code window thing.. *starts poking around*

---

### Post by Cheesemill on 2009-07-02
Or you can use:
```
du -h --max-depth=1
```

---

### Post by Tyke91 on 2009-07-02
> **austinpsycho said:**
> on a side note; how do you do the neat code window thing.. *starts poking around*


the [code] tag  :) end it with a backslash code tag.

---

### Post by austinpsycho on 2009-07-02
> **Tyke91 said:**
> the [code] tag  :) end it with a backslash code tag.
Ah; I just had to go into 'advance mode' to figure that out.. quickreply doesn't have a button for it (though im sure i could have just typed it in there)

---

### Post by flylehe on 2009-07-02
Thanks! 
How to not list all the files in subdirectories? I just like to have a glance at how much size each directory takes.

---

### Post by Tyke91 on 2009-07-02
hehe. why didn't you say so?
```
du -h
```

EDIT: Doh... scroll up. max depth 1 will give you only the subdirectories of the directory that you are currently in.

---

### Post by flylehe on 2009-07-02
Thanks!
When using 
```

du -h --max-depth=1

```
can I sort the results from big size to small?

---

