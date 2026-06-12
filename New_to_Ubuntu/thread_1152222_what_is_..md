---
title: "what is ./"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by helstreak on 2009-05-07
i know if i want to run a compiled c program i need to do something like:

./my_program

so what is ./

Thank you :)

EDIT
Thanks for all the help.  Isn't there a way to mark the post as solved?

---

### Post by jacksinn on 2009-05-07
It's a way of telling Linux to execute the program that is in the current directory and not to look for commands matching that name.

---

### Post by _Purple_ on 2009-05-07
. means this directory. So ./my_program will run my_program from your current directory.

---

### Post by ddrichardson on 2009-05-07
The period is the current folder. If you don't specify the path to the command then the $PATH variable is checked for the command.

./filename just means starting from the current folder run the file /filename.

This is similar to the .. which means the parent folder.

[http://www.linux-tutorial.info/modules.php?name=MContent&pageid=17](http://www.linux-tutorial.info/modules.php?name=MContent&pageid=17)

---

### Post by geirha on 2009-05-07
./ is the path where the binary is located. You can specify the path either absolute (beginning with a /, like "/usr/bin/vim") or relative (like "../bin/vim" or "./my_program"). Each directory has two special directories;
. - self
.. - parent directory.

There's yet another way to execute a binary, which is providing no path at all (like just "vim" or "my_program"). If you try to execute a binary that way, it will search through all directories listed in $PATH. (do "echo $PATH" to see it). By default, . is not in PATH, but if it was, you could do "my_program" instead of "./my_program". But it is considered a security risk to have . in path, so its not recommended. Just get used to prefixing the binary with the relative path ./ ...

---

### Post by Nycticorax on 2009-05-07
It's a shorthand for "the current directory". Just like ".." is a shortcut for the parent directory. Try listing the files with

```
ls -a
```

and you'll see those two, together with the normal files (They're normally hidden, which is why you need the -a).

The reason you type 
```
./my_program
```

is that you need to tell the OS the location of the program you want to run. An alternative would be to give the full path, e.g.

```
~/my_code_directory/my_program
```

If you just type 

```
my_program 
```

the OS doesn't realise you're expecting it to look in the current directory. There is, of course, a way to tell the OS which directories to look in when you type a program name -- google for $PATH. That's why you can just type 

```
firefox
```
in whatever directory and it will know you're referring to /usr/bin/firefox, and will start up firefox.

---

### Post by Therion on 2009-05-07
Not to be confused with [Slashdot](http://slashdot.org/)



/.

---

### Post by doas777 on 2009-05-07
> **Therion said:**
> Not to be confused with [Slashdot]("http://slashdot.org/")



/.

you beat me too it. cheers

---

