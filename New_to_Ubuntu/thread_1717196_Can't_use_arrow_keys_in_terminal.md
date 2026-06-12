---
title: "Can't use arrow keys in terminal"
date: 2011-03-29
forum: New to Ubuntu
---

### Post by quartaela on 2011-03-29
hi there. i am using ubuntu for 2 weeks and trying to learn it. but i have problem.after i creating a script file i can't use right left up and down arrow keys. when i try use them terminal displays some meaningless characters. for ex. if i press left arrow terminal displays "^[[D";

#!/bin/sh
#
#Script that demos, command line args
#
echo "Total number of command line arguments are $#"
echo "$0 is script name"
echo "$1 is first argument"
echo "$2 is second argument"
eho "All of them are:-$*"
^[[A^[[C^[[A^[[D^[[B^[[D

i can't go to up and write "echo" over "eho" : ).

i am waiting for your help...

---

### Post by kellemes on 2011-03-29
And you have this script opened in..?
From terminal you cannot edit files, you may use the terminal to run the script but for editing you use an editor like gedit, vi, geany etc..

Or do I misunderstand the situation?

---

### Post by quartaela on 2011-03-30
well in tutorial it says;

For e.g. now will write script to print command ling argument and we will see how to access them
$ cat > demo
#!/bin/sh
#
# Script that demos, command line args
#
echo "Total number of command line argument are $#"
echo "$0 is script name"
echo "$1 is first argument"
echo $2 is second argument"
echo "All of them are :- $*"

i wrote this codes. but when i writing i can't go to upper line if i want to change someting so when i try to use arrows it displays something like this "^[[A^[[C^[[A^[[D^[[B^[[D".

---

### Post by nothingspecial on 2011-03-30
> **quartaela said:**
> well in tutorial it says;

For e.g. now will write script to print command ling argument and we will see how to access them
$ cat > demo
#!/bin/sh
#
# Script that demos, command line args
#
echo "Total number of command line argument are $#"
echo "$0 is script name"
echo "$1 is first argument"
echo $2 is second argument"
echo "All of them are :- $*"

i wrote this codes. but when i writing i can't go to upper line if i want to change someting so when i try to use arrows it displays something like this "^[[A^[[C^[[A^[[D^[[B^[[D".

Start again.

Type ```
nano demo
```

Forget the first line - cat > demo

Type the rest into nano, you will be able to move about with your arrows.

When it's done press CTRL-O then Enter to save it. Then press Ctrl-X to close nano.

To make it executable type ```
chmod +x demo
```

Then to run it type ```
./demo
```

---

### Post by quartaela on 2011-03-30
well ok it works! so can u tell me the difference between using cat and demo_?. cause our lab. assistant gave a homework about using script file. and thanks for your help : )

---

### Post by JKyleOKC on 2011-03-30
The "cat" command simply types the content of the file to the display; that is, it lists the file but is not an editor. However "nano" is a text editor, so that you can make changes to a file and then save it.

---

### Post by nothingspecial on 2011-03-30
Yes, if using cat, you have to type it right first time. You can cat to the file and edit with nano later though.

---

### Post by quartaela on 2011-03-30
> **JKyleOKC said:**
> The "cat" command simply types the content of the file to the display; that is, it lists the file but is not an editor. However "nano" is a text editor, so that you can make changes to a file and then save it.

but in tutorial it says

To create text file       cat > { file name }    $ cat  > myfile
NOTE: Press and hold                             type your text
CTRL key and press D to                          when done press
stop or to end file                              ^D
(CTRL+D)

---

### Post by quartaela on 2011-03-30
> **nothingspecial said:**
> Yes, if using cat, you have to type it right first time. You can cat to the file and edit with nano later though.

i guess that is the reason why i couldn't go upper lines or left for change any code.

---

### Post by nothingspecial on 2011-03-30
I think you've got it.

This is homework though :-$

---

### Post by JKyleOKC on 2011-03-30
> **quartaela said:**
> but in tutorial it says

```
To create text file       cat > { file name }    $ cat  > myfile
NOTE: Press and hold                             type your text
CTRL key and press D to                          when done press
stop or to end file                              ^D
(CTRL+D)
```Well, that will work, but only if you don't make any errors. The "cat" command takes arguments to tell it which file to list and if no filename is given, takes its input from "stdin" which is usually the keyboard (but might be the output of another command, which you may not have gotten to yet). The output from "cat" goes to "stdout" which is usually the monitor but can be redirected to a file or piped to another command.

Thus the tutorial's instruction lets you type anything into "cat" and the output gets written to "myfile" -- but "cat" has no provision at all for correcting typing mistakes. If you misspell something on the last line, as in your original post, then you have to go back to the beginning and do it all over again!

As homework, it's a good illustration of how to get by with nothing other than what's built into the basic system -- but as a tutorial, it teaches you an error-prone and very unfriendly way to do things! Hopefully, this will be corrected later in the course...

Note that I added the code tags to make the tutorial excerpt display the way you originally formatted it...

---

