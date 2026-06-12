---
title: "need help with running some commands for my wireless card"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by popcat on 2009-01-15
ok so im very close to getting my wireless card to work but im stuck with the one line of code

```
sudo ndiswrapper -i ~/.driver/wifi/DRIVER/bcmwl5.inf

```

i need to run that but the problem is that my copy of the bcmwl5.inf is in a folder in my home folder, not the directory they have in the line of code. could someone help me out

---

### Post by Sorivenul on 2009-01-15
> **popcat said:**
> 
```
sudo ndiswrapper -i ~/.driver/wifi/DRIVER/bcmwl5.inf

```

Try:
```
sudo ndiswrapper -i ~/path/to/your/bcmwl5.inf
```
Where '/path/to/your/' is the actual path. Say if the .inf file is in '/home/yourusername/broadcomfiles/driver' the command would be:
```
sudo ndiswrapper -i ~/broadcomfiles/driver/bcmwl5.inf
```

The "~/" is terminal "shorthand" for '/home/yourusername'.

Hope this helps! Good luck!

---

### Post by Michael.Godawski on 2009-01-15
hi,

you can also try to install your wlan drivers with the graphical ndis as described here:


[LIST]
[*][http://godawski.oxyhost.com/solvingwireless.html#ndiswrapper](http://godawski.oxyhost.com/solvingwireless.html#ndiswrapper)
[/LIST]

---

### Post by popcat on 2009-01-15
it said command not found :(

---

### Post by popcat on 2009-01-15
michael in your tutorial when i launch the gui ndiswrapper thing it closes right away

---

### Post by NullHead on 2009-01-15
Did you download bcmwl5.inf and BCMWL5.SYS yet? Where did they go to once you downloaded them?

---

### Post by talsemgeest on 2009-01-15
> **popcat said:**
> it said command not found :(
Can you post the exact location of the .inf file?

---

### Post by popcat on 2009-01-15
its in a folder called DRIVER in my home folder and my account name is blaise.

```
/home/blaise/DRIVER
```

---

### Post by Michael.Godawski on 2009-01-15
Try to open the graphical ndis tool with this terminal command:

```
gksudo ndisgtk
```

You have to provide your sudo/login password to launch it.

---

### Post by Sorivenul on 2009-01-15
> **popcat said:**
> its in a folder called DRIVER in my home folder and my account name is blaise.
```
sudo ndiswrapper -i ~/DRIVER/bcmwl5.inf
```

---

### Post by talsemgeest on 2009-01-15
> **popcat said:**
> its in a folder called DRIVER in my home folder and my account name is blaise.

```
/home/blaise/DRIVER
```
Ok then, try running this: ```
sudo ndiswrapper -i /home/blaise/DRIVER/bcmwl5.inf
```

---

### Post by popcat on 2009-01-15
@talsemgeest and Sorivenul when i ran your codes it 
```
sudo: ndiswrapper: command not found

```

@michael when i ran yours it said
```
blaise@blaise-ubuntu:~$ gksudo ndisgtk
Traceback (most recent call last):  File "/usr/sbin/ndisgtk", line 364, in <module>
    NdisGTK()
  File "/usr/sbin/ndisgtk", line 122, in __init__
    self.setup_driver_list()
  File "/usr/sbin/ndisgtk", line 150, in setup_driver_list
    self.get_driver_list()
  File "/usr/sbin/ndisgtk", line 162, in get_driver_list
    output,retcode = getoutput("ndiswrapper", "-l")
  File "/usr/sbin/ndisgtk", line 34, in getoutput
    myproc = subprocess.Popen(cmd, stdout=subprocess.PIPE, stderr=subprocess.STDOUT)
  File "/usr/lib/python2.5/subprocess.py", line 594, in __init__
    errread, errwrite)
  File "/usr/lib/python2.5/subprocess.py", line 1153, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory

```

---

### Post by handydan918 on 2009-01-15
> **popcat said:**
> @talsemgeest and Sorivenul when i ran your codes it 
```
sudo: ndiswrapper: command not found

```



Try ```
which ndiswrapper
``` just to see if the system can find it.

Also, IIRC, the .inf should be ommitted when installing drivers in ndiswrapper...IF IRC....

---

### Post by popcat on 2009-01-15
@handy dan nothing come up when i type that and sorry i dont know what iirc is

---

### Post by talsemgeest on 2009-01-15
> **handydan918 said:**
> Try ```
which ndiswrapper
``` just to see if the system can find it.

Also, IIRC, the .inf should be ommitted when installing drivers in ndiswrapper...IF IRC....
Well, that means that ndiswrapper is not installed, which also means that the guide you have been following is not very good. Can you please give us a link to the guide that you have been following?

---

