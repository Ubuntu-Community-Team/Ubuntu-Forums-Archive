---
title: "Terminal Code"
date: 2009-08-08
forum: New to Ubuntu
---

### Post by Eumenides on 2009-08-08
It has come to my attention that there are certain commands one uses in the Terminal to access various programs, install or delete, upgrade or update. Each time i asked on the procedure to run or install a program, different combinations of code were given to me to make work of the things i needed. In so, i am wondering and asking you guys to please tell me, how and where i can learn Terminal code and command lines. I am wanting to learn the commands so i dont have to alwats inconvenience you guys and have a level of independence while using Ubuntu.

---

### Post by Tclarkie on 2009-08-08
i think this is what u need
[http://fosswire.com/post/2007/08/unixlinux-command-cheat-sheet/](http://fosswire.com/post/2007/08/unixlinux-command-cheat-sheet/)

---

### Post by Tclarkie on 2009-08-08
or maybe this
[http://www.scottklarr.com/topic/115/linux-unix-cheat-sheets---the-ultimate-collection/](http://www.scottklarr.com/topic/115/linux-unix-cheat-sheets---the-ultimate-collection/)

---

### Post by Barrucadu on 2009-08-08
'Terminal code' is just a series of programs joined together, much like how you use a combination of GUI programs to accomplish a task. I find thinking of it like that rather than as a different language makes it simpler.

You can get help for different commands with the **man** command, for example, `man apt-get`, **apt-get** being part of the package management tools on Ubuntu (along with **dpkg**, **aptitude**, etc). Here are some common commands:

**ls** - list the contents of a directory
**man** - get help on a command
**cd** - change directory
**grep** - search for text
**cat** - display the contents of a file
**echo** - display text
**sudo** - run a command as another user
**rm** - remove a file
**cp** - copy a file
**mv** - move a file
**wc** - count characters, words, and lines.

Those are probably the most used commands. Now for the next lesson, piping.

Commands can be chained together using 'pipes', where the output of one command goes to the input of another. For example, there are two ways of searching for text in a file:

```
grep TEXT FILE
cat FILE | grep TEXT
```

In the second command the **cat** command is used to get the contents of the file, which is then piped to the **grep** command, which searches for the text. It does exactly the same as the first command, which uses **grep**'s ability to open the file itself. Another example, I'll leave it as a very simple challenge to figure out what it does:

```
ls -al | wc -l
```

After piping, we have input/output redirection. This lets you send stuff to files and suchlike. For example, that grep command above could also have been written as:

```
grep TEXT < FILE
```

Here the "<" means "send the contents of FILE as input". Output is sent to a file with ">". For example:

```
echo TEXT > FILE
```

Would replace the contents of FILE with TEXT. To append, use ">>":

```
echo "Directory Listing of `pwd`" > dirlist
ls -la >> dirlist
```

That example shows something else, as well. Backticks. These allow you to run a command where otherwise you might not be able. That example runs the **pwd** command to get the current working directory and put it in the text sent to the file.

Last thing, variables.
```
hello="world"
echo $hello
```

That's as complex as they get. "VARIABLE=VALUE", referenced by "$VARIABLE". The arguments to a script are stored in $1, $2, $3, etc. All the way up to $9, at which point you have to **shift** to access the higher ones. But don't worry about that unless you plan on writing scripts with a lot of arguments. Backticks can be used in variables, of course:

```
dir=`pwd`
echo "The current working directory is $dir"
```

Google and manpages will teach the rest :)

---

### Post by CatKiller on 2009-08-08
Another thing to bear in mind, as well as the responses you've had so far, is that giving a command is the easiest way to achieve the task of *giving help to another person over the Internet using a text-based forum*. It does not necessarily follow that it is also the easiest way to achieve the task of *a user doing something to their own computer when they are sat in front of it*. Depending on the user, using the command line may still be the best way to do a particular thing, but it may be that that user would be much more comfortable using a graphical tool instead.

Learning how to use the command line is an interesting process in its own right, and some users (myself included) may find that comfort with the command line makes their use of their machine more efficient. But it isn't, in general, **necessary** to learn how to use the command line.

---

### Post by Eumenides on 2009-08-08
Thank you all.

---

