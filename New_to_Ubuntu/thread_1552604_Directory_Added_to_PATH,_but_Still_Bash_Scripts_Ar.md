---
title: "Directory Added to PATH, but Still Bash Scripts Aren't Found"
date: 2010-08-13
forum: New to Ubuntu
---

### Post by linux4me on 2010-08-13
I'm using Lucid. I'm a longtime Ubuntu user, but still an absolute beginner to bash.

I have a directory in /home/myusername called Scripts in which I have a number of bash scripts that I would like to run from various directories without typing in the path. The scripts all run fine when I'm in the Scripts directory. 

I added the Scripts folder to the PATH by editing ~/.bashrc and adding the following to the end of the file:
```
# add extra paths
export PATH=$PATH:~/Scripts
```
and then ran
```
source ~/.bashrc
```
When I run the command:
```
echo $PATH
```
I get the following:
> /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/myusername/Scripts

So far so good. However, when I go to some directory other than Scripts, say Desktop, and execute a script without the path like this:
```
./myscript.sh
```
I get the error:
> bash: ./myscript.sh: No such file or directory

What am I doing wrong?

TIA

---

### Post by jtarin on 2010-08-13
Leave off the ./ and see if that will run.

---

### Post by wojox on 2010-08-13
Your script starts

```
#!/bin/bash
```

Try dropping the **.sh** and change it to just **myscript**

---

### Post by linux4me on 2010-08-13
> **jtarin said:**
> Leave off the ./ and see if that will run.
That was it! Thanks. I figured I was doing something dumb.

---

### Post by jtarin on 2010-08-14
> **linux4me said:**
> That was it! Thanks. I figured I was doing something dumb.
Your welcom. The ./ tells it to execute in the present directory. I can remember making the same mistake....once upon a time.

---

