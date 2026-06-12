---
title: "Terminal: Permission Denied (cat)"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by Max_Mackie on 2010-01-01
I don't think the cat command needs any privileges, but I gave it some anyways. This still isn't working, I'm attempting to merge files.

I've tried:
```
sudo cat surnames >> names
cat surnames >> names
```

My output is:
```
bash: names: Permission Denied

```

If I use the sudo prefix, this shouldn't happen right?

---

### Post by Rayve on 2010-01-01
My first thought is that "cat" is not where your permission issues lie - it's in the file called "names". Test this by just running ```
 cat surnames 
``` and see if you get what you expect.  If so, then the issue is that you can't append the results of "cat surnames" to the "names" file.  In the directory where the file is located, you can do
```
 ls -l 
``` to list all the permissions of the files there. If you do not have access to the file, you can ```
 chmod +x 
``` to give execute permissions, and chmod +r / +w for reading and writing, respectively.

---

### Post by CharlesA on 2010-01-01
Post the output of:

```
pwd
``` and ```
ls -l
```

---

### Post by falconindy on 2010-01-01
You're applying the elevated permissions to the read part of the command, and not the write part. If you want to be able to write in this manner, you have 2 options:

```
sudo bash -c 'cat file1 >> file2'
```
or
```
cat file1 | sudo tee -a file2
```
Both will accomplish the same goal.

---

### Post by Max_Mackie on 2010-01-01
[falconindy]("http://ubuntuforums.org/member.php?u=863375"), that worked great :) thanks
However, so I understand well, what does "bash -c" and "tee" do?

Thanks to the other who helped too!

---

### Post by spiderbatdad on 2010-01-01
man pages are very helpful.
```
man tee
man bash
```
Tells you basically tee redirects output in two directions...to the screen and to a file. bash -c reads from standard input or file and the -c option causes commands to be read from the string, namely to append the output file in this case.

---

### Post by Max_Mackie on 2010-01-01
Many thanks to all of you :)

---

