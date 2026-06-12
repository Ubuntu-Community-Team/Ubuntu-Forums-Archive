---
title: "Open Files and Display Them"
date: 2010-06-28
forum: New to Ubuntu
---

### Post by c0nrad on 2010-06-28
Hey,

This is probably really easy, but if I had a list of files in the form:

one.txt
two.txt
three.txt
...

how could I write the contents of each file to stdout?

I was trying to use cat, but it would just relist the files without opening them.

Thanks,
c0nrad

---

### Post by endotherm on 2010-06-28
well you have to provide a full path if they are not in the directory you are in, but it shoudl work.
```

Lucid:~$ echo 'Hello1' > test1
Lucid:~$ echo 'Hello2' > test2
Lucid:~$ echo 'Hello3' > test3
Lucid:~$ cat test1 test2 test3
Hello1
Hello2
Hello3


```

---

### Post by c0nrad on 2010-06-28
Well, the thing is, I don't know which files are there before hand, I use

```
 ls *.cpp *.h | cat
```And it just gives me a list of files, not the contents.

---

### Post by endotherm on 2010-06-28
> **c0nrad said:**
> Well, the thing is, I don't know which files are there before hand, I use

```
 ls *.cpp *.h | cat
```And it just gives me a list of files, not the contents.
I think you may need to run a find loop for that
[http://www.softpanorama.org/Tools/Find/find_mini_tutorial.shtml](http://www.softpanorama.org/Tools/Find/find_mini_tutorial.shtml)

use find to iterate over the files performing your action. the problem you are having now, is that LS does not return files, but their names, so cat is getting a list of text, not a set of files.

---

### Post by lukeiamyourfather on 2010-06-28
> **c0nrad said:**
> Well, the thing is, I don't know which files are there before hand, I use

```
 ls *.cpp *.h | cat
```And it just gives me a list of files, not the contents.

Just do this.

```

cat *.cpp

```

---

### Post by c0nrad on 2010-06-28
Wow.
I knew I was being stuipid. 

Here's the way I just found:

```

ls *.cpp *.h | xargs cat
```But, thanks a lot! I'll use yours.
c0nrad

---

### Post by ajgreeny on 2010-06-28
Perhaps I completely misunderstood what you want, but why doesn't ```
cat one.txt two.txt three.txt
```from the folder containing those files work for you?  It does for me, or I can of course, direct the output to a new txt file.

As I say, maybe I don't understand properly what you are trying to do.

---

### Post by lukeiamyourfather on 2010-06-28
> **ajgreeny said:**
> Perhaps I completely misunderstood what you want, but why doesn't ```
cat one.txt two.txt three.txt
```from the folder containing those files work for you?  It does for me, or I can of course, direct the output to a new txt file.

As I say, maybe I don't understand properly what you are trying to do.

If I understand correctly that won't work for the original poster because you have to know what files are in the directory. Using *.ext you get all of the files and don't have to know ahead of time what files are in the directory. Specifying each file technically works but its not what the original poster was looking for. Cheers!

---

