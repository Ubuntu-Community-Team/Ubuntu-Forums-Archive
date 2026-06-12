---
title: "symbolic links"
date: 2010-03-08
forum: New to Ubuntu
---

### Post by woodsonoversoul on 2010-03-08
Hello all,
    I've got a compiler I'd like to be able to reference from any directory on my system by just using the file's name and not it's whole directory path. I think what I'm talking about would be called a symbolic link. How can I set this up?

---

### Post by steindor2 on 2010-03-08
ln -s

---

### Post by woodsonoversoul on 2010-03-08
Thats what I thought, but when I enter:
```
ln -s /home/dan/go/src/cmd/8g/8g 8g

```
to make it so that I just have to type 8g <filename> to compile, wherever I am, I get:
```
8g: command not found

```

What gives?

---

### Post by r-senior on 2010-03-08
Are you sure you want a symbolic link and not an update to your path?

Do you want to be able to run your compiler program from within a terminal, regardless of the current directory? That sounds more like a path update. A symbolic link makes a file or directory appear in a different place or under a different name.

---

### Post by woodsonoversoul on 2010-03-08
yes, then that's what I want to do, update my path...

---

### Post by r-senior on 2010-03-08
In that case, try:

$ export PATH=$PATH:<path_to_your_program>

If that works, there are a multitude of ways of making it permanent, depending on what you want.

Adding the above line to ~/.bashrc is a start, then read the options here:

[http://ubuntuforums.org/showthread.php?t=2793]("http://ubuntuforums.org/showthread.php?t=2793")

---

### Post by woodsonoversoul on 2010-03-08
Will I need to restart the terminal?

---

### Post by woodsonoversoul on 2010-03-08
I added:
```
$export 8g=$HOME/go/src/cmd/8g/8g

```

to the end of ~/.bashrc

---

### Post by r-senior on 2010-03-08
Sorry, I perhaps didn't make it completely clear. PATH is the variable that defines the path. So you need something like:

$ export PATH=$PATH:$HOME/go/src/cmd/8g/

That assumes your program 8g is in the directory $HOME/go/src/cmd/8g.

Then you should just be able to type:

$ 8g

I'm assuming that the 8g file is already executable. If not, go to $HOME/go/src/cmd/8g and type:

$ chmod u+x 8g

---

