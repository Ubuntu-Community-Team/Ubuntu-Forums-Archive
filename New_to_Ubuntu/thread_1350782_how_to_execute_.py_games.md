---
title: "how to execute .py games"
date: 2009-12-09
forum: New to Ubuntu
---

### Post by aaron_the_dude on 2009-12-09
Hey, I have been using Ubuntu for a few months now, but I still don't know everything that there is to know.  But I want to start making python games and I'm just starting with a simple "Hello, World!"

Here is what I did and you could tell me what I'm doing wrong.
1.  Using IDLE with python 2.6
2.  I put the thing "#!/usr/bin/python" on the very top
3.  I put in the print("Hello, World!")
4.  save it as hello.py
5.  Right click the hello.py file>Properties>Permissions>Allow executing as program.
6.  Double click the file and click run.
7.  Nothing happens after that.

Help me out please, I want to make some games and learn code.

---

### Post by m_duck on 2009-12-09
Hey,
Because the program will print "Hello World" to the command line, it will be executing, but in the background so you don't see it. To run it, first open up a terminal (Applications -> Accessories -> Terminal). Then change directory to where your hello.py file is. For example if it is in /home/aaron/pythonstuff/hello.py type:```
cd ~/pythonstuff
```The **~** simply is a short hand way of referring to "the current user's" home directory, /home/username. Once you are in the folder, as the permissions have been set to executable, you can type the following to run your program (I think):```
./hello.py
```I may be wrong with that, but as long as it is executable and begins with the "#!/usr/bin/python" it should execute. If one of those two prerequisites are not filled, it won't execute. You can then either do both of them or run:```
python hello.py
```

---

### Post by vanhelsing2009 on 2009-12-09
[SIZE="2"]ok try this :
cd directory of ur program
python program_name.py -o program_name
[/SIZE]

---

### Post by aaron_the_dude on 2009-12-09
Nope, didn't work, this is what I got:

> aaron@aaron-desktop:~$ cd ~/pythonstuff
aaron@aaron-desktop:~/pythonstuff$ ./hello.py
./hello.py: line 1: syntax error near unexpected token `('
./hello.py: line 1: `Python 2.6.4 (r264:75706, Nov  2 2009, 14:38:03) '
aaron@aaron-desktop:~/pythonstuff$ python hello.py
  File "hello.py", line 1
    Python 2.6.4 (r264:75706, Nov  2 2009, 14:38:03) 
             ^
SyntaxError: invalid syntax
aaron@aaron-desktop:~/pythonstuff$ python hello.py -o hello.py
  File "hello.py", line 1
    Python 2.6.4 (r264:75706, Nov  2 2009, 14:38:03) 
             ^
SyntaxError: invalid syntax
I tried the three ways and didn't get it to work.  And that is my output right above.  And yes, I made a new folder named pythonstuff in my home directory to test it out.

---

### Post by llamabr on 2009-12-09
Oh, it's running, that's why you're getting all that output.  Your problem isn't running it, your problem is your code.  Post your script, and we'll show you where you went wrong

---

### Post by vanhelsing2009 on 2009-12-10
my dear well the code like this :
cd Desktop
python mymodule.py -o mymodule


if that does not work can u plz make a copy of ur code of python
it said error syntax in first line
maybe this is the problem

---

### Post by HighCommander540 on 2009-12-10
> **aaron_the_dude said:**
> Hey, I have been using Ubuntu for a few months now, but I still don't know everything that there is to know.  But I want to start making python games and I'm just starting with a simple "Hello, World!"

Here is what I did and you could tell me what I'm doing wrong.
1.  Using IDLE with python 2.6
2.  I put the thing "#!/usr/bin/python" on the very top
3.  I put in the print("Hello, World!")
4.  save it as hello.py
5.  Right click the hello.py file>Properties>Permissions>Allow executing as program.
6.  Double click the file and click run.
7.  Nothing happens after that.

Help me out please, I want to make some games and learn code.

Hey, so I am kinda of a noob still with shell scripting and Python. So I was wondering, where you found the info that told you about the /usr/bin/python thing? I didn't know you could just add it to the beginning of the file to get it to run with python..

---

### Post by nothingspecial on 2009-12-10
> **aaron_the_dude said:**
> Hey, I have been using Ubuntu for a few months now, but I still don't know everything that there is to know.  But I want to start making python games and I'm just starting with a simple "Hello, World!"

Here is what I did and you could tell me what I'm doing wrong.
1.  Using IDLE with python 2.6
2.  I put the thing [COLOR="Red"]"#!/usr/bin/python"[/COLOR] on the very top
3.  I put in the print("Hello, World!")
4.  save it as hello.py
5.  Right click the hello.py file>Properties>Permissions>Allow executing as program.
6.  Double click the file and click run.
7.  Nothing happens after that.

Help me out please, I want to make some games and learn code.

If you put quotes round #!/usr/bin/python that would give you errors.

---

### Post by deathbyswiftwind on 2009-12-10
The #!/usr/bin/python part can be found in most online python tutorials. Very handy ;)

---

### Post by HighCommander540 on 2009-12-10
> **deathbyswiftwind said:**
> The #!/usr/bin/python part can be found in most online python tutorials. Very handy ;)

Oh, ok thanks. I guess I was looking at my school's Python book and its not in there. I will use online tutorials instead.

---

### Post by aaron_the_dude on 2009-12-10
Well, here is the .py file when you choose to display it instead of run it.

> Python 2.6.4 (r264:75706, Nov  2 2009, 14:38:03) 
[GCC 4.4.1] on linux2
Type "copyright", "credits" or "license()" for more information.

    ****************************************************************
    Personal firewall software may warn about the connection IDLE
    makes to its subprocess using this computer's internal loopback
    interface.  This connection is not visible on any external
    interface and no data is sent to or received from the Internet.
    ****************************************************************
    
IDLE 2.6.4      ==== No Subprocess ====
>>> #!/usr/bin/python
print("Hello, World!")

---

### Post by earthpigg on 2009-12-11
doesn't there have to be a space after the crunchbang and before the /?

ie:

```
#! /usr/bin/python
```

and not

```
#! /usr/bin/python
```

if it's a python 2.x program, you should be able to run it with 

```
python /path/to/program.py
```

when you see the 'syntax errors' and stuff, that is telling you... that there is a syntax error.

i'm not sure how to use idle, but here is a simple and correct hello world program:

```
#! /usr/bin/python
print("Hello World!!")
```

if you open it in a text editor or 'cat' it ($ cat /path/to/program.py) .... the result should look very similar to that.

---

### Post by earthpigg on 2009-12-11
o, and also:

to 'install' any python script so it can simply be run from the terminal by typing 'programname'...

rename it from programname.py to programname

right click on it -> properties. make it executable by all users. 

move it to /usr/bin.

done. :D

typing programname will now launch the program.

---

### Post by aaron_the_dude on 2009-12-11
Ok, I tried the following now.
1.  Copied and pasted Earthpigs hello world into IDLE.
2.  saved as hello.py in the /home/aaron/pythonstuff folder
3.  Went into the terminal and typed python /home/aaron/pythonstuff/hello.py
4.  Still not figureing out the whole syntax thingy, or what syntax really means.

> aaron@aaron-desktop:~$ python /home/aaron/pythonstuff/hello.py
  File "/home/aaron/pythonstuff/hello.py", line 1
    Python 2.6.4 (r264:75706, Nov  2 2009, 14:38:03) 
             ^
SyntaxError: invalid syntax


---

### Post by undecim on 2009-12-11
> **aaron_the_dude said:**
> Python 2.6.4 (r264:75706, Nov 2 2009, 14:38:03) 
[GCC 4.4.1] on linux2
Type "copyright", "credits" or "license()" for more information.

************************************************** **************
Personal firewall software may warn about the connection IDLE
makes to its subprocess using this computer's internal loopback
interface. This connection is not visible on any external
interface and no data is sent to or received from the Internet.
************************************************** **************

IDLE 2.6.4 ==== No Subprocess ====
>>> #!/usr/bin/python
print("Hello, World!")

Looks like you just copied and pasted your work from a python shell and as a result, you copied a bunch of stuff you don't need. Try using a text editor to put just this into a .py file and run it:```
#!/usr/bin/python
print("Hello, World!")
```

---

### Post by earthpigg on 2009-12-11
yeeeeeeeeah, i am not looking over your shoulder but i am increasingly suspecting there is more than two lines of text in your hello world program.

stop using idle.

use gedit or leafpad or nano.

just the two lines. nothing else. there should be no word "Python" in capital letters ***anywhere*** in the program.

```
#! /usr/bin/python
print("Hello World!!")
```

that is ***it***.

> ```
aaron@aaron-desktop:~$ python /home/aaron/pythonstuff/hello.py
File "/home/aaron/pythonstuff/hello.py", line 1
Python 2.6.4 (r264:75706, Nov 2 2009, 14:38:03)
^
SyntaxError: invalid syntax 
```

there is no reason for a line in your program to read "Python 2.6.4 (r264:75706, Nov 2 2009, 14:38:03)". none at all.

---

### Post by nothingspecial on 2009-12-11
> **earthpigg said:**
> doesn't there have to be a space after the crunchbang and before the /?

ie:

```
#! /usr/bin/python
```

and not

```
#! /usr/bin/python
```


It doesn`t matter if you have a space or not or even 3 spaces.

And if you are not comfortable putting your python scripts in /usr/bin because it`s easy to mistakenly delete or overwrite something vital, you can make a directory ~/bin and put it there.
Only you will be able to run it from the terminal then though.

---

### Post by aaron_the_dude on 2009-12-11
Oh, thank God, I finally got it!

1.  Copied Earthpig's Hello World into GEDIT TEXT EDITOR.
2.  Saved as Hello.py into /home/aaron/pythonstuff
3.  Used the terminal and wrote python /home/aaron/pythonstuff/hello.py

> aaron@aaron-desktop:~$ python /home/aaron/pythonstuff/hello.py
Hello World!!


I kinda feel stupid and sorry for making something that should be simple like python difficult.  I hope now I would be able to make a game eventually for ubuntu.

---

### Post by earthpigg on 2009-12-11
> **aaron_the_dude said:**
> I kinda feel stupid and sorry for making something that should be simple like python difficult.  I hope now I would be able to make a game eventually for ubuntu.

its the 'simple' stuff that authors leave out of guides, assuming that the reader will somehow 'know' it already that often proves the most problematic.

in the future, try to read the error message -- you will see a ***lot*** of them when coding, so you had best get used to understanding that mumbo jumbo now.

```
File "hello.py", line 1
Python 2.6.4 (r264:75706, Nov 2 2009, 14:38:03)
^
SyntaxError: invalid syntax
```

set up gedit (or whatever you use) to show line numbers... then you can jump right to the exact line and start figuring stuff out. in this example, it was line 1... but later, it will help you to be able to jump right to line 55 or 150 or whatever.

i am just starting python myself (first programming language for me, too)... the book i purchased told me that things like IDLE where great later on, but early on its best to just keep it simple.

my normal setup: 

terminal window so i can run my script as i code to make sure "ok, so far so good".

gedit, with multiple tabs open. the current program, and an older one or two... so i can re-use code and don't have to figure out the same things over and over again. it makes it easy to see how i did something last time, so i can just do it like that again.

[thread on my noobish python stuff,]("http://ubuntuforums.org/showthread.php?p=8472829") if you want to join.

---

### Post by durand on 2009-12-11
The print statement you were using is for Python **3.x** while ubuntu uses Python **2.x** by default. If you want, you can use python3.1 by installing it with synaptic. You then need to change your #!/usr/bin/python to #!/usr/bin/python3.1

EDIT: Oh and IDLE is pretty terrible really. You should try SPE (see my sig) or something else. There are much nicer python IDEs to use, and they really will help.

---

