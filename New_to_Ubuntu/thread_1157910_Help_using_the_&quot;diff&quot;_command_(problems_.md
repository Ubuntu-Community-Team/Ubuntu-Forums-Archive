---
title: "Help using the &quot;diff&quot; command (problems stripping whitespace)"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by Cranio on 2009-05-13
Hi all!

I'm trying to _recursively diff the files in two directories_, I'm so excited to have discovered the power of this command.
The files are **HTML/PHP source codes** for two (actually four, but let's assume two) versions of a website, and I have to sync the sites.

Now the problem, let's suppose I have a first text file **t1**:

```
<p>Marco</p>
```

and now a second file **t2**:

```
<p>

Marco
</p>
```

They are nearly identical, but the second has some carriage returns. What I want is that diff should treat these two files as equivalent and not different. Though, using:

```
diff -w t1 t2
```

wouldn't do the trick: what I expected was that every whitespace (spaces, tabs but also FF, LF and CR) would be stripped before the comparison. Instead, at least the CR's are "seen". What am I missing? Is it a wrong implementation (er, I don't think so but..) Maybe it's because diff is line-based (er, is it?)?

Are you able to suggest me some other fast solution, that is recursively suitable for whole directories (maybe with **sed** and a regexp to strip out all the whitespaces)? 

Thanks in advance, the more I use Ubuntu and the Linux shell the more I fall in love with it :)

---

### Post by lovinglinux on 2009-05-13
I f you don't need t use command-line, then I would recommend meld.

```
sudo apt-get install meld
```

It can do directory comparisons and other stuff, through a nice interface.

---

### Post by Cranio on 2009-05-14
> **lovinglinux said:**
> I f you don't need t use command-line, then I would recommend meld.

```
sudo apt-get install meld
```

It can do directory comparisons and other stuff, through a nice interface.

Yep, heard of meld, but I'd prefer to stick to the command line because it has to be done via SSH on a remote machine.

Do you know if mend can handle also remote directories and files via SSH?

OR, if there is a way to launch a local GUI with a refernce to the remote files?

---

### Post by lovinglinux on 2009-05-14
> **Cranio said:**
> Yep, heard of meld, but I'd prefer to stick to the command line because it has to be done via SSH on a remote machine.

Do you know if mend can handle also remote directories and files via SSH?

OR, if there is a way to launch a local GUI with a refernce to the remote files?

I was able to compare remote directories via SSHFS on Hardy, with some limitations. But I don't know why I'm not able to do it right now on Jaunty.

---

### Post by PGScooter on 2009-05-14
Have you considered using a filter? A filter can be written in many languages (most commonly awk sed and perl?) and takes input and then gives output, so it could take input from the file (through cat), pipe it to the filter which would output the same text without the newline characters. I don't have ubuntu to experiment with for another week, but if you still need help I can do it then.

---

### Post by Cranio on 2009-05-14
> **PGScooter said:**
> Have you considered using a filter? A filter can be written in many languages (most commonly awk sed and perl?) and takes input and then gives output, so it could take input from the file (through cat), pipe it to the filter which would output the same text without the newline characters. I don't have ubuntu to experiment with for another week, but if you still need help I can do it then.

As I wrote in the first post of the thread, I was thinking about sed, indeed; but as I am a beginner with linux I have some problems in finding the right syntax.

Maybe I can succeed in doing the filtering with sed and a very trivial regular expression to strip out all the whitespace, but the real difficult part for me would be to make the filtering and the diff-ing parts recursive on a whole directory tree.

---

### Post by kaibob on 2009-05-14
I am not familiar with the diff utility, but you can use the tr command-line utility to strip out unwanted characters. For example, the following removes new lines:

```
cat file | tr -d '\012'
```

See the man pages for tr and ascii for more detail.

---

