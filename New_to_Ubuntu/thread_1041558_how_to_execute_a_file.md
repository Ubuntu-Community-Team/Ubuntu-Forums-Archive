---
title: "how to execute a file"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by akshayubhat on 2009-01-16
sorry for being silly.
I have downloaded a program for Linux called affinity propagation.
In windows i can execute it by calling the apcluster.exe followed by arguments through dos prompt.
But in case of Linux package there is no exe file.
There are two files in the package one is .so file and another one called as apcluster but it hasn't got any extension. 
So can you please tell me how to execute the file and which one.
After futile efforts i kept on getting error saying file opened due to unspecified type.:confused:
Many thanks

---

### Post by Daveth on 2009-01-16
it may not have an extension but it has a file type- I guess apcluster is a script which needs to be run....

---

### Post by HotShotDJ on 2009-01-16
Right-click on the file.  Select "Properties."  Under the "Permissions" tab, check off "Allow executing file as program" then click close.  ONLY do this if you absolutely trust the program -- especially if you will be running it with superuser privileges (not recommended!)

---

### Post by akshayubhat on 2009-01-16
ya but what should i type on shell prompt.
and generally in windows i make following call
apcluster.exe sim.txt pref.txt ttmp

what should i similarly type of bash?
this is the linux package
[http://www.psi.toronto.edu/affinitypropagation/software/apcluster_linux32.zip](http://www.psi.toronto.edu/affinitypropagation/software/apcluster_linux32.zip)
(40kb only)

---

### Post by akshayubhat on 2009-01-16
tired giving permission to execute but bash still says
that command not found.:confused:

---

### Post by HotShotDJ on 2009-01-16
After you have set the executable bit, you can run it in a terminal by navigating to to correct directory and typing ./filename (obviously, replace "filename" with the correct name of your file)

The ./ tells the terminal to look in the current directory.  For security reasons, Linux normally will only execute files that are located somewhere in PATH... the ./ overrides this security feature.  Use it with care.

---

### Post by akshayubhat on 2009-01-16
Thanks i think the problem is solve.
Though now the apcluster is asking me
libstdcc++.so.5

any chance you know anything about it.
seems to be general c++ library

---

### Post by HotShotDJ on 2009-01-16
> **akshayubhat said:**
> Though now the apcluster is asking me
libstdcc++.so.5Either use Synaptic Package manager to install libstdc++5 or type the following in a terminal:```
sudo apt-get install libstdc++5
```(Since the program you are running is not provided and installed via the package management system, you'll have to resolve dependencies manually.)

---

### Post by akshayubhat on 2009-01-16
Thanks its done.

---

