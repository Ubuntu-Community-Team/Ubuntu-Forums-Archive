---
title: "Compiling .py files"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by fslezak on 2009-05-30
Hello!

I need some help compiling a .py file I made. It's name ends with .py.

I understand the "chmod +x" command, WHEN DO I USE IT???

Thanx

---

### Post by LeSaint on 2009-05-30
if you have the following at the top of the file:

#!/usr/bin/python

Then you can chmod +x it.(This makes it executable).

Bash will then execute the script via python.  Python is an intrepreter and the most it will compile to is its own byte code.

If it does this, you may see a .pyc file(which you dont run, you always run the .py)

Make sense?

---

### Post by Tibuda on 2009-05-30
You don't compile it. You make it executable when you chmod +x it, but it is still a text/plain file.

---

### Post by crazy_fox on 2009-05-30
chmod +x is used once you have a script or binary and you wish it to be executable.

Both of the questions you asked have a lot of available information if you google them.

---

### Post by braete on 2009-05-30
you could try sudo nautilus, cd to the location of your file then right click it, select properties then permissions and check the execution box (this is the newbie version of what the others said ... )

---

### Post by pmigneous on 2009-05-30
Python is an interpreted language, you can't really "compile" it, and produce binaries. You can, however, optimize it and make it much easier on the interpreter. If you do indeed want to compile a python script to bytecode, and not just run the .py, you'll need to cd to the directory where the .py(s) are, run "python", and then type import py_compile. After that, type ```
py_compile.compile('script.py')
```

If you're just asking how to run a python script, "python script.py" and viola. If you're doing chmod +x script.py, you are marking the file as executable. Assuming you have a shebang as the first line of the script (#!/usr/bin/python), you should be able to just ./script.py, instead of having to do "python script.py".

Hope that helps.

---

### Post by Tibuda on 2009-05-30
> **braete said:**
> you could try sudo nautilus, cd to the location of your file then right click it, select properties then permissions and check the execution box (this is the newbie version of what the others said ... )

No need for sudo if you are the file owner.

---

