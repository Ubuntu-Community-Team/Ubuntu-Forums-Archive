---
title: "Why am I getting - No such file or directory?"
date: 2011-02-05
forum: New to Ubuntu
---

### Post by mjaytee on 2011-02-05
I needed to get into a specific directory to use mp3wrap (of which, I will post a noob buck-naked to fully clothed tutorial soon, I know I could have used one) to combine a set of mp3s.  However, when I tried to change directory using: cd ~/Music/Unity    

I get the message:

bash: /home/mjaytee/Music/Unity: No such file or directory   

Although, it is clearly there. The Music prompt shows if I leave off "Unity", and "ls" will list "Unity" at the Music prompt.

I solved the problem by using: sudo apt-get install nautilus-open-terminal   and right clicking "Open in Terminal" within the 'Unity' folder.

Although I accomplished what I set out to do, I'm still curious as to why this above change directory (cd) did not work or if it is supposed to work at all.  Thanks

---

### Post by Old *ix Geek on 2011-02-05
Please post the output of **ls -l** while in /home/mjaytee/Music

---

### Post by asmoore82 on 2011-02-05
or even better:
```
ls ~/Music | cat -A
```

`-A` tells `cat` to represent all non-printing characters in some way.

It's most likely that you have an extra space or 2 on the end of the name.
The fix for that will look something like this:
```
Music $ mv "Unity " Unity
```
or a more fun option that will fix even wilder possibilities:
```
Music $ mv Unity* Unity
```

---

### Post by mjaytee on 2011-02-06
> **Old *ix Geek said:**
> Please post the output of **ls -l** while in /home/mjaytee/Music


mjaytee@ThinkPad-Z60m:~/Music$ ls -l
total 4
drwxr-xr-x 2 mjaytee mjaytee 4096 2011-02-05 23:12 Unity
mjaytee@ThinkPad-Z60m:~/Music$ 
 
Thanks for the response.  I had to reinsert the folder.

---

### Post by mjaytee on 2011-02-06
> **asmoore82 said:**
> or even better:
```
ls ~/Music | cat -A
````-A` tells `cat` to represent all non-printing characters in some way.

It's most likely that you have an extra space or 2 on the end of the name.
The fix for that will look something like this:
```
Music $ mv "Unity " Unity
```or a more fun option that will fix even wilder possibilities:
```
Music $ mv Unity* Unity
```

Yes that was it.  Man, you guys are sharp.  Thanks a lot.

---

### Post by bluntz on 2011-02-07
Glad it helped you however It does not fix mine

---

