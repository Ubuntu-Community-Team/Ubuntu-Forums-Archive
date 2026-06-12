---
title: "python shebang/hasbang (whatever you want to call it)"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by Lone_Joker on 2008-12-31
Well I just installed and updated Intrepid Ibex last night. I'm new to linux, and I'm learning Python right now.

Anywho I have this simple code:
```
#!/usr/bin/python
# Filename : helloworld.py
print 'Hello World'
```

But when I open the terminal and try to run it I get an error:
```
xxx@xxx-desktop:~$ cd PythonPrograms
xxx@xxx-desktop:~/PythonPrograms$ chmod a+x helloworld.py
xxx@xxx-desktop:~/PythonPrograms$ ./helloworld.py
bash: ./helloworld.py: /usr/bin/python^M: bad interpreter: No such file or directory
xxx@xxx-desktop:~/PythonPrograms$ 

```

Was it something I said? :-(
I tried going through Nautilus (that's the Ubuntu equivalent to Windows, right?) and finding the folder, but it says that the directory doesn't exist. Can I just make the folder, or does it have to contain certain files?

---

### Post by Delever on 2008-12-31
Your python installation should point to python2.5 version. It probably does.

Make sure [python2.5-dev]("apt:python2.5-dev") is installed in Synaptic (or using command line).

Also, check if there is some character at the end of that line (probably Windows end-of-line symbol).

You can convert line endings to unix format using [dos2unix]("apt:tofrodos") program.

---

