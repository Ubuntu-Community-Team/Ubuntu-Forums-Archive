---
title: "Executing Files in Terminal"
date: 2009-05-27
forum: New to Ubuntu
---

### Post by GaretJax on 2009-05-27
There is an executable file that I can double-click to execute in the File Browser and it runs like expected.

But when I try to execute the file in the Terminal window it doesn't work because it says "command not found".

The file name is four words long separated by spaces.  I tried enclosing the file name in double and single quotes.  I even copied and pasted the file name so I know that I am not typing it incorrectly.

I assume this is a syntactical problem.  Any help?

---

### Post by blueridgedog on 2009-05-27
You can attempt to run it with back slashes before the spaces:

```
 ./a\ file\ with\ spaces 
```

---

### Post by ecmatter on 2009-05-27
Are you in the right directory?

---

### Post by blueridgedog on 2009-05-27
Note the "./" in front of my sample command implies you are "there" as in the directory that contains the file you want to run.  Otherwise you could enter a full path as in /full/path/to/my/file\ with\ a\ space

---

### Post by Volt9000 on 2009-05-27
In summary:

To reference a file with spaces in the name, you can enclose the file with quotes

"just like this"

or escape the space with a backslash

just\ like\ this


Note that Linux works differently than Windows. When you type a filename in the terminal, it doesn't always by default look in the current working directory; it looks in the path.

You can view the current path by typing:

```

echo $PATH

```

In order to access a file in the current directory, prepend a dot-slash to the front of the filename, thusly:

./file

It takes a bit of getting used to at first, especially when coming from a Windows background.

---

### Post by Tibuda on 2009-05-27
you can also use the interpreter executable like
```
sh myscript.sh
```
or
```
python myscript.py
```

---

### Post by ecmatter on 2009-05-27
Or, you can add the directory the file is in to your path by adding the following to your .bash_profile.

```
export PATH=$PATH:directory_name
```

---

### Post by GaretJax on 2009-05-29
> **ecmatter said:**
> Are you in the right directory?

Yes, I'm in the right directory.

---

### Post by GaretJax on 2009-05-29
Wow, thanks for all the suggestions everyone.  I took the direct approach to this and followed Volt9000's instructions.  I typed ./"file with spaces" and it ran.

---

### Post by Mornedhel on 2009-05-29
You could have tried tab-completion.

Just type ./first_few_letters_to_your_executable, press TAB, and the name will be completed as far as the shell can guess. This includes special characters, so spaces are escaped with backslashes, etc.

---

### Post by el.numbre on 2009-06-03
> **Volt9000 said:**
> In summary:

To reference a file with spaces in the name, you can enclose the file with quotes

"just like this"

or escape the space with a backslash

just\ like\ this


Note that Linux works differently than Windows. When you type a filename in the terminal, it doesn't always by default look in the current working directory; it looks in the path.

You can view the current path by typing:

```

echo $PATH

```

In order to access a file in the current directory, prepend a dot-slash to the front of the filename, thusly:

./file

It takes a bit of getting used to at first, especially when coming from a Windows background.
thanks that was really helpful :)

---

