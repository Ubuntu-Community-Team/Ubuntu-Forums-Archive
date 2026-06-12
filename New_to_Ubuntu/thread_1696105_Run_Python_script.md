---
title: "Run Python script"
date: 2011-02-26
forum: New to Ubuntu
---

### Post by hdanap on 2011-02-26
Hi 

Im new to programming, im trying to run a python script from the python prompt from withing the shell terminal and i keep geting error that 

the script ia called test1.py, I have tried to import the script with import test1.py and i get

Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named test1.py

pls help

Thanks

---

### Post by NightwishFan on 2011-02-26
To run a python script just run:
```
python /path/to/script.py
```

Import in python is to enable functionality, such as gtk or webkit that can extend python.

(In Ubuntu you can even right click the script, go to properties, permissions, check "mark as executable", then hit ok. After that you are able to just double click the script and choose "run in terminal")

---

### Post by Cheesehead on 2011-02-26
You don't normally run a python script from the python prompt.
```

cheesehead@spambot:~$ python
Python 2.6.6 (r266:84292, Sep 15 2010, 15:52:39) 
[GCC 4.4.5] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import make-me-a-sandwich.py
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named make-me-a-sandwich.py
>>> 

```


You normally run a python script from the regular shell:
```

cheesehead@spambot:~$ python make-me-a-sandwich.py

Make it yourself.

cheesehead@spambot:~$

```

---

### Post by doas777 on 2011-02-26
usually when writing a script file (in most unixy langagues) you add a [Bang line]("http://en.wikipedia.org/wiki/Shebang_%28Unix%29")
to the very top of your script file. 
here is a good python bang for ubuntu:
```
#!/usr/bin/env python
```

after you have added a bang line you can just call your script by name.
when executing a script when your command prompt is in the same directory that contains the script, put './' in front of the file name

```

/home/user/script.py
OR
cd /home/user
./script.py

```

---

### Post by hdanap on 2011-02-26
I tried both methods and none worked.

I used chmod +x test1.py to make it executable 

i double clicked it and it bring up some options like run in terminal, open content of file and run, but all didnt work.

Im confused

---

### Post by tgm4883 on 2011-02-26
> **hdanap said:**
> I tried both methods and none worked.

I used chmod +x test1.py to make it executable 

i double clicked it and it bring up some options like run in terminal, open content of file and run, but all didnt work.

Im confused

You would be better off posting the contents of your script here, so we can see what is going on and better offer assistance

---

### Post by morzid on 2011-02-26
hdanap

If you want to run python in terminal, get rid of the '.py' after test1. It justs confuses python.

---

### Post by doas777 on 2011-02-26
if you want to execute your script with a double click, you need two things: a script with a bangline in it (filename should end in .py, but is optional), and a launcher.

to create a launcher, rclick your desktop, and select "Create Launcher".
pull down "Type", and select "Application in terminal"
add a name, comment, and a command to launch your script.
then click OK and test your button.

if the script flashes up and then immediatly closes the window,
add a line like this to the end of your scripts logic flow:
```
raw_input("Press any Key to Exit") 
```

---

### Post by doas777 on 2011-02-26
> **morzid said:**
> hdanap

If you want to run python in terminal, get rid of the '.py' after test1. It justs confuses python.
say what?

---

### Post by hdanap on 2011-02-26
Wow that solved the problem, that ./scritp stuff

Thanks guys

---

### Post by hdanap on 2011-02-26
I added the bang line on top of the script 

then cd to the directory of the script then used ./script

i noticed that without the bang line at the top of the script, nothing worked

thanks again, im so glad

---

### Post by VastOne on 2011-02-27
> **morzid said:**
> hdanap

If you want to run python in terminal, get rid of the '.py' after test1. It justs confuses python.

> **doas777 said:**
> say what?

:o :)

I was shaking my head at this one too..

---

