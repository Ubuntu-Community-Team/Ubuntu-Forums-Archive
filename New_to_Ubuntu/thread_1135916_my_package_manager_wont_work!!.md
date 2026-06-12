---
title: "my package manager wont work!!"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by natman on 2009-04-24
I have just installed Kubuntu 904 and my wireless wont work under the default network manager. So i plu in ethernet and load up kpackagekit to get wicd ( a new network manger that should work ) anyway i click apply chnages and all i see is " querying" this just stays there and wont change! I have tried sudo apt-get and adept neither does anything!

---

### Post by LinuxGuy1234 on 2009-04-24
What do you get when you press Alt+F2 and type this:
```
konsole -e 'bash -c "sudo apt-get install wicd; read"'
```
and press Enter?

---

### Post by natman on 2009-04-24
a blank terminal just pops up , there is no output just an empty prompt

---

### Post by natman on 2009-04-24
Okay i just tried Kpackagekit again and now it actually gives an error after i ask it to install a package. "we have encountered and error blah blah.." then the details are
> Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/packagekit/daemonBackend.py", line 109, in run
    threading.Thread.run(self)
  File "/usr/lib/python2.6/threading.py", line 477, in run
    self.__target(*self.__args, **self.__kwargs)
  File "/usr/lib/packagekit/aptDBUSBackend.py", line 1418, in doGetDepends
    "Dependecies for &#36001; cannot be satisfied: " -1.695610e+00)
TypeError: not enough arguments for format string


---

### Post by bumanie on 2009-04-24
Try > sudo apt-get update && sudo apt-get upgrade

---

