---
title: "How to cat a file without its 2 first lines ?"
date: 2010-09-25
forum: New to Ubuntu
---

### Post by honeybear on 2010-09-25
Tail and head are cool but I am looking to "cat" a file without its 2 first lines

Any commmand exists for that in our Ubuntu?

---

### Post by Rinzwind on 2010-09-25
cat {file} | (read; read; cat)"

skips 2 lines.

---

### Post by da burger on 2010-09-25
A slightly cleaner way to do that is to use tail with a slightly different syntax.

```
tail -n+X filename
``` where X is the number of lines you want to skip at the top.

Alternatively (and i prefer this method because I think it is more readable) ```
cat file | tail -n+X
``` uses a pipe from cat with tail.

Which you chose is up to personal preference.

Hope that helped
Angus

EDIT Just so you know, one of the benefits of this is that it is a lot more scalable, imagine you wanted to use Rinzwind's method to skip 150 lines of a file :S

---

### Post by honeybear on 2010-09-25
> **da burger said:**
> A slightly cleaner way to do that is to use tail with a slightly different syntax.

```
tail -n+X filename
``` where X is the number of lines you want to skip at the top.

Alternatively (and i prefer this method because I think it is more readable) ```
cat file | tail -n+X
``` uses a pipe from cat with tail.

Which you chose is up to personal preference.

Hope that helped
Angus

EDIT Just so you know, one of the benefits of this is that it is a lot more scalable, imagine you wanted to use Rinzwind's method to skip 150 lines of a file :S


I tried 
```
cat file | tail -n+1 
``` but I got whole file line ... :(

---

### Post by da burger on 2010-09-25
My apologies. From those examples X should be the line number of the line you want to start from. So to start from the 3rd line as in your example you would use tail -n+3 not -n+2 as a recommended previously.
Hope I actually got it right this time :)
Angus

---

### Post by honeybear on 2010-09-25
> **da burger said:**
> My apologies. From those examples X should be the line number of the line you want to start from. So to start from the 3rd line as in your example you would use tail -n+3 not -n+2 as a recommended previously.
Hope I actually got it right this time :)
Angus

but one shall now before the number of line of the file. This could be relatively using the CPU:
- first seek in file for how much lines
- second , store and display with tail

a skip while catting would be simpler for shorter coding ... I know that is not required since now we have big machines. But check into the bible of linux and it is said that coding programs shall be made the best way, and not loosing resources

check here the video:
[http://www.youtube.com/watch?v=8utW0ecx7es](http://www.youtube.com/watch?v=8utW0ecx7es)

---

### Post by Jitse on 2010-09-25
Use ```
cat myfile | tail -n +N
``` which prints all lines except the first N-1

---

