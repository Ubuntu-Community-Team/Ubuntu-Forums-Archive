---
title: "How do I use a file in the terminal?"
date: 2009-12-17
forum: New to Ubuntu
---

### Post by psam3 on 2009-12-17
I used cd to move to a directory (gnomenu) on my desktop, and I want to use the setup.py file, but when I type in setep.py it just tells me command not found. The reason I want to try to run it from the command is because when I do it by clicking on it nothing happens. Can anyone help? 

Thanks

---

### Post by jamieleshaw on 2009-12-17
Have you tried 'sh setup.py'?

---

### Post by tjwilli on 2009-12-17
> **psam3 said:**
> I used cd to move to a directory (gnomenu) on my desktop, and I want to use the setup.py file, but when I type in setep.py it just tells me command not found. The reason I want to try to run it from the command is because when I do it by clicking on it nothing happens. Can anyone help? 

Thanks

I'm guessing you have a python package/module to install with setup.py. If you are in the directory with the setup.py file, you just run this script with python like this (Don't type the '%')
```

% python setup.py install
```

To see the options from setup.py, type:```


% python setup.py --help
```

HTH.

---

### Post by psam3 on 2009-12-17
I tried the "python setup.py install" but I don't think it's working right, this is what happens
[IMG]http://i49.tinypic.com/w9tmvo.png[/IMG]

Any idea what that means? 

Thanks

---

### Post by Barriehie on 2009-12-17
I've developed the habit, since not memorizing my $PATH variable to precede filenames with ./ when doing something in the terminal; i.e.
```

python ./setup.py

```
If you've a folder that you use frequently you can add it to your $PATH variable easy enough.  This can be set in your /home/*username*/.bashrc file.
```

PATH=$PATH:*PathToYourFolder*  #PATH=$PATH:/home/*myusername*/Desktop/gnomenu
export PATH

```

Barrie

---

### Post by Barriehie on 2009-12-17
> **psam3 said:**
> I tried the "python setup.py install" but I don't think it's working right, this is what happens
[IMG]http://i49.tinypic.com/w9tmvo.png[/IMG]

Any idea what that means? 

Thanks

Did you run 'sudo make install' prior to running setup.py???

Barrie

---

### Post by psam3 on 2009-12-17
> **Barriehie said:**
> Did you run 'sudo make install' prior to running setup.py???

Barrie

That worked thanks!

---

### Post by sylentdogg on 2009-12-17
Why not use the package from [getdeb.net]("http://www.getdeb.net/software/GnoMenu"), or use the ppa from [launchpad.net]("https://launchpad.net/~gnomenu-team/+archive/ppa")? Its easier then installing from source. But if you really want to install from source, the readme.txt file explains how to install and what dependencies you need in order for it to install.:)

---

### Post by psam3 on 2009-12-17
> **sylentdogg said:**
> Why not use the package from [getdeb.net]("http://www.getdeb.net/software/GnoMenu"), or use the ppa from [launchpad.net]("https://launchpad.net/~gnomenu-team/+archive/ppa")? Its easier then installing from source. But if you really want to install from source, the readme.txt file explains how to install and what dependencies you need in order for it to install.:)

I didn't realize this stuff was available:) Oh well, it was a learning experience.

---

