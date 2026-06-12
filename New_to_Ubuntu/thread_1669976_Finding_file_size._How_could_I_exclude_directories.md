---
title: "Finding file size. How could I exclude directories?"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by Zombir on 2011-01-18
Hi all,

I'm trying to write a bash script in Ubuntu and I need the file sizes in a specified directory. I searched for it in the net but all the solutions suggested showed sizes of files *and directories*. I want the sizes of *files only,  *in my script. How can I find only the *file* sizes? Please help. (Hope this is relevant to this forum)

Thanks in advance.

---

### Post by Vaphell on 2011-01-18
```
ls -la | awk '/^-/ { print $8, $5 }'
```
or 
```
find . -maxdepth 1 -type f -exec stat -c%n\ %s '{}' \;
```

---

### Post by bleutyler on 2011-01-18
```
find . -type f -maxdepth 1 -exec ls -l {} \;
```

However, since the ls -l command is being run on each file independantly, the columns will not line up.

you can always grep your ls -l results.

```
ls -l | grep -vE "^d"
```

This will have columns lined up.

---

### Post by Zombir on 2011-01-18
Thanks both of you. It seems an awful lot of symbols to me. Sorry I'm just a starter. Anyway, I won't exhaust you asking for explanations. I'll google and see if I could decipher them. Thank you once again. :D

---

### Post by Cheezespread on 2011-01-18
I just had a quick question on the maxdepth in find. What would "-maxdepth 1" do ? .Does it consider only the files in the current directory and ignore any directories below that ?

I looked into the manpages after I noticed it in your responces and was a bit confused.

---

### Post by Vaphell on 2011-01-18
find is recursive and will go through the whole subtree if not told otherwise

maxdepth limits how deep in the tree find should go, 1 = main dir only

---

