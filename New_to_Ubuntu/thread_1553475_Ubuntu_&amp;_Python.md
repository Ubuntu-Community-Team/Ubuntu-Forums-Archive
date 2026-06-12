---
title: "Ubuntu &amp; Python"
date: 2010-08-15
forum: New to Ubuntu
---

### Post by Segofam on 2010-08-15
I am dabbling with Python, managed to enter into python 'Hello, Wold!' but can't run the program. This is where I am up to...

**Running Python Programs in Unix**

 If you are using Unix (such as Linux, Mac OSX, or BSD), if you make the program executable with chmod, and have as the first line:
 [LEFT] [FONT=monospace] #!/usr/bin/env python2
[/FONT]
 [/LEFT]
 you can run the python program with ./hello.py like any other command.


...and I am uncertain of what to do. I have played with it all day. Can anyone give me some direction???


Sincerely,


Scott

---

### Post by Terl on 2010-08-15
Try: ```
python ./your_program.py
```  Doing this you will not need that first line.  That line looks odd to me (not an expert, I just started too) but I think it should just be #! /usr/bin/env python.

You don't really need it if you use the first method I mentioned and tell it to use python up front..

---

### Post by GregBrannon on 2010-08-15
Where are you stuck? Assuming you've named your "Hello, World" program hello.py, what happens when you go to terminal and run the command,

```
./hello.py
```

?

(Next time, ask your programming questions in the "Programming Talk" forum.)

---

### Post by Segofam on 2010-08-15
> **Terl said:**
> Try: ```
python ./your_program.py
```  Doing this you will not need that first line.  That line looks odd to me (not an expert, I just started too) but I think it should just be #! /usr/bin/env python.

You don't really need it if you use the first method I mentioned and tell it to use python up front..

I get ...
scott@scott-laptop:~$ ./hello.py
bash: ./hello.py: Permission denied
scott@scott-laptop:~$ 

and...
scott@scott-laptop:~$ python ./hello.py
  File "./hello.py", line 1
    Python 2.6.5 (r265:79063, Apr 16 2010, 13:09:56) 
             ^
SyntaxError: invalid syntax
scott@scott-laptop:~$ 
...when I put python first.

Yeah, I tried that too, with no luck.
Maybe my syntax is wrong!!!
I am gonna put this down for the night and have another crack at it tomorrow, we might get some more input here hopefully, by the time I get home from work :)

---

### Post by Vaphell on 2010-08-15
permission denied is because if you want to run the script without preceding 'python' you have to **chmod +x** your file first (set as 'standalone' executable).

case with 'python ...' - there is no permission denied because you tell python 'take this file and run it' - script doesn't need to be +x here. You got a syntax error in your script though

---

### Post by Paqman on 2010-08-15
Of course, the other alternative is to install an IDE like idle or geany, which allows you to create and test your code in the same place.

---

### Post by Segofam on 2010-08-16
> **Vaphell said:**
> permission denied is because if you want to run the script without preceding 'python' you have to **chmod +x** your file first (set as 'standalone' executable).

case with 'python ...' - there is no permission denied because you tell python 'take this file and run it' - script doesn't need to be +x here. You got a syntax error in your script though

Hi Vaphell,
I saw that in...
**Running Python Programs in Unix**

 If you are using Unix (such as Linux, Mac OSX, or BSD), if you make the program executable with chmod, and have as the first line:
 [LEFT] [FONT=monospace] #!/usr/bin/env python2
[/FONT]
 [/LEFT]
 you can run the python program with ./hello.py like any other command.


...but how do you do that exactly???

---

### Post by Segofam on 2010-08-16
> **Paqman said:**
> Of course, the other alternative is to install an IDE like idle or geany, which allows you to create and test your code in the same place.

Hi Paqman,
I have installed "IDLE (using Python-2.6)"
Is that what you are suggesting?

If it is, I have not been able to run a program through it. In Wiki - somewhere - it says I can do it through edit, but there are no options in my edit tab to perform that function.

Sincerely,

Scott

---

### Post by Paqman on 2010-08-16
> **Segofam said:**
> 
If it is, I have not been able to run a program through it. In Wiki - somewhere - it says I can do it through edit, but there are no options in my edit tab to perform that function.


Right click on any Python file and go to "Open With" and pick Idle. Then when you click on any Python file it'll launch two Idle windows. The first is the editor, the second is a scratchpad area where you can run things. Hit F5 in the editor to run.

---

### Post by Segofam on 2010-08-16
Thanks Paqman,
I had to edit the list when doing a right click on the file to open with IDLE, so that is working now as you said i.e. the two windows.
I will get back to the online study at [http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python_2.6/Intro](http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python_2.6/Intro)
and...[http://hkn.eecs.berkeley.edu/~dyoo/python/idle_intro/index.html](http://hkn.eecs.berkeley.edu/~dyoo/python/idle_intro/index.html)
Any other suggestions are most welcome!
Kind regards,
Scott

PS: How do you make your thread "Solved"?
I still haven't figured that out!!!

---

### Post by Vaphell on 2010-08-16
thread tools (just above the first post of the thread) -> mark as solved

---

### Post by ender4 on 2010-08-16
> **Segofam said:**
> Hi Vaphell,
I saw that in...
**Running Python Programs in Unix**

 If you are using Unix (such as Linux, Mac OSX, or BSD), if you make the program executable with chmod, and have as the first line:
 [LEFT] [FONT=monospace] #!/usr/bin/env python2
[/FONT]
 [/LEFT]
 you can run the python program with ./hello.py like any other command.


...but how do you do that exactly???


make the first line of the python file "#!/usr/bin/env python" then, assuming your file is called "hello.py" you need to type the following in the command line in the directory that "hello.py" is located:
```

chmod +x hello.py

```

this command gives the file "executable permission" that is it can be executed as a standalone script.

What happens is bash looks at the first line of the file and if it starts with "#!" then it executes the command that follows the "#!" with the scriplt file as an argument.  So while #!/usr/bin/env python works. so does #!/usr/bin/python.

---

### Post by Segofam on 2010-08-17
> **ender4 said:**
> make the first line of the python file "#!/usr/bin/env python" then, assuming your file is called "hello.py" you need to type the following in the command line in the directory that "hello.py" is located:
```

chmod +x hello.py

```

this command gives the file "executable permission" that is it can be executed as a standalone script.

What happens is bash looks at the first line of the file and if it starts with "#!" then it executes the command that follows the "#!" with the scriplt file as an argument.  So while #!/usr/bin/env python works. so does #!/usr/bin/python.

Oh wow...thanks so much for that! I tried typing that in a few places with no result :-/
And again, thanks for the explanation too, much appreciated.

---

