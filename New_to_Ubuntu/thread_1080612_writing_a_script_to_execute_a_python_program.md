---
title: "writing a script to execute a python program"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by lyratzis on 2009-02-25
Hey

So I wrote a pseudo-random text generator in python, and I thought it would be fun if I could feed the output from this program into the built-in speech synth. I am pretty new to Ubuntu, so I don't rightly know, but my guess was that the best way to do this would be to write a script that executes the python program and takes the output and runs the speech synth command using it. I have never written a script before; is this what I want to do in this case? and can I just execute the python program (how?), assign the output to a variable, and run the echo command?

---

### Post by llamabr on 2009-02-25
py script.py | synthesizer

that doesn't work?  Depending on how the synth program takes input, it might be

py script.py | exec synthesizer

---

### Post by The Cog on 2009-02-25
A script should always start by specifying the interpreter on the first line. For a shell script this would probably be:
**#!/bin/sh**
and then the commands themselves. You can collect the output from a program into a variable like this:
**a=$(python makerandomtext.py)**
note no spaces round the = sign.
Then you can recall variables by putting a dollar sign in front like this:
**echo $a**
so the whole script might look like this:
> #!/bin/sh
rubbish=$(python makerandomtext.py)
espeak $rubbish
You need to make the script executable with the chmod command:
**chmod +x myscript**
then execute it. You must say which direvtory it's in ike this:
**./myscript**

---

### Post by lyratzis on 2009-02-26
thanks very much!

---

