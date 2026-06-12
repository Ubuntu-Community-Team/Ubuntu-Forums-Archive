---
title: "&quot;open with&quot; a shell script"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by tracerbullet on 2009-05-10
This may be a case of a backwards approach to the problem, but regardless:

I have a fairly simple command which I use on a daily basis

```
unrar e <filename>
```

Now this is not a problem to type for a small filename, but when the file has a long name including a long string of numbers (a version number for example) and it located within a folder of the same name inside another folder and so on, it becomes a pain to type it out every time.

Thus I would like to create a script with which I can open said file, yet I am completely lost as to how I would do this.

I can already make a basic shell script to the effect of

```
echo "something"
cp file file2
```

and so on, which works fine. But I could use some pointers when it comes to making the shell script interact with a file in the "open with" manner.

And I know there are GUIs for a lot of archive applications and such, this is not what I am looking for, I am both trying to learn as well as create this specific function. :)

Thanks in advance!

---

### Post by kerry_s on 2009-05-10
what you want is called a nautilus-script, i'll try to talk you through it.

open nautilus and press ctrl+h to show hidden files/folders go into .gnome2/nautilus-scripts

right click create file
you can name it what ever you want, i'll just use "unrar".
open it with gedit and put:

```
#!/bin/sh
unrar e "$@"

```

now right click the file> properties> permissions
check execute

that's it should be ready for you to use in your right click> scripts

---

### Post by 3rdalbum on 2009-05-10
Why not type:

```
unrar e
```

And then drag the file to the terminal? That will automatically fill in the filepath for you.

---

### Post by tracerbullet on 2009-05-10
> **kerry_s said:**
> what you want is called a nautilus-script, i'll try to talk you through it.

open nautilus and press ctrl+h to show hidden files/folders go into .gnome2/nautilus-scripts

right click create file
you can name it what ever you want, i'll just use "unrar".
open it with gedit and put:

```
#!/bin/sh
unrar e "$@"

```

now right click the file> properties> permissions
check execute

that's it should be ready for you to use in your right click> scripts
Thanks! Works like a charm! Any way to make it open in a terminal though, so I can see the progress? :)
> **3rdalbum said:**
> Why not type:

```
unrar e
```

And then drag the file to the terminal? That will automatically fill in the filepath for you.
Yup, I know. But this is still more operations than I'd like it to be (open a terminal and type the command, open nautilus and browse to the file then drag it into the terminal). I prefer doing it either the terminal way or the right click way. :)

---

### Post by kerry_s on 2009-05-10
sure, make the command:

```
#!/bin/sh
gnome-terminal -x unrar e "$@"

```

it might be:

```
#!/bin/sh
gnome-terminal -e unrar e "$@"

```

can't remember what the execute is, check> man gnome-terminal
sorry, i'm a xterm user for me it's "xterm -e command". :)

---

### Post by tracerbullet on 2009-05-10
-x does the trick. Thanks kerry!:D:D

---

