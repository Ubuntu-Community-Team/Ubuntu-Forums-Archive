---
title: "rm command (with warning)"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by kwacka on 2011-06-28
I had a directory containing some duplicate files, with the filename containing (copy), e.g. **a4-prices.PDF** and **a4-prices (copy).PDF**

To get rid of the copies, I ran the command (**don't try this at home, kids!**)```
rm * (copy) *
```

which deleted all files in the directory (leaving directories).

My question is, why?

---

### Post by sanderd17 on 2011-06-28
because of the spaces. you delete *, (copy) and again *. So with the first *, everything is deleted. You need to escape spaces with a backslash:

```

rm *\ (copy)\ *

```

or by using quotes

```

rm "* (copy) *"

```

Maybe you need to escape the brackets too, I don't know that for sure. But you can always try a rm command by using ls instead of it.

---

### Post by kwacka on 2011-06-28
Stupid, stupid, stupid - of course it's the spaces.  :oops:

(That's me, not you, BTW)

Thanks.

Aren't backups wonderful?

---

### Post by texaco on 2011-06-28
I think, you will need backlash for "(" and ")" characters.

Anyway, 

```
rm "*copy*"
```It must be work.

---

### Post by FormatSeize on 2011-06-28
> **kwacka said:**
> I had a directory containing some duplicate files, with the filename containing (copy), e.g. **a4-prices.PDF** and **a4-prices (copy).PDF**
```
sudo rm -rfvi /this/directory/*(copy).PDF
```
would have been the safer choice. I've made it a practice to identify things like this with a few of the last characters and the file extension to make sure rm doesn't remove something that I want to stay there. Too, the -i flag is there to make sure I am absolutely sure that I want to delete the things that the command thinks I do. 
 
Another safe choice would be to use the mv command before using rm. That way, you can move all the files to a dummy directory, and then inspect the files there to make sure everything that you targeted was correct. Then you use rm to remove that directory.

---

### Post by kwacka on 2011-07-03
Good suggestions - thanks for those.

---

