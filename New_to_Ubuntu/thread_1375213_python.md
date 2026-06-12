---
title: "python"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by Moose32315 on 2010-01-07
I have several questions about using python with ubuntu.  I've just started using ubuntu and python so I don't know very much about either.  I'm running ubuntu off a flash drive for right now to evaluate it.  

So ubuntu came with python 2.6 and I wanted to use 3 so I installed it.  I guess I installed it manually with the make command.  I was able to access python 3.0 from the terminal just fine.  Although, I don't know how to run scripts in python so I wanted to download IDLE to run them like I did in windows.  However, when I went to the software center to download IDLE the thing said the package dependencies cannot be resolved.  I then looked at the list of installed programs and saw that 3.0 wasn't listed as an installed program.

Now I'm trying to uninstall 3.0 and then reinstall 3.1 and IDLE 3.1 with the software center since it doesn't recognize 3.0.  I tried navigating to the python directory to uninstall it with the command sudo make uninstall, but for some reason it doesn't recognize the ubuntu folder.  I typed cd /home/ubuntu/Python-3.0 in the terminal to find the folder in which python was installed, but it doesn't change the directory.  I can set the directory to home just not to the ubuntu folder.  So if anybody has any suggestions it would be greatly appreciated.

---

### Post by Buuntu on 2010-01-07
Are you sure the name of the user is ubuntu?  Just to make sure run this:
```
ls /home
```
That should display all the contents of the home folder.

Is it giving you an error message when you try to change directory to ubuntu or just saying that it can't be found?

---

### Post by Miljet on 2010-01-07
As I understand it, when you install from source (use make install) your package manager has no record of what you installed. So if you install a program from source and then try to install a support package through the package manager, you will almost always run into trouble.

In other words, either install both programs through the package manager or both from source code.

---

### Post by Captain_tux on 2010-01-07
Since it seems you're new to Ubuntu (and Linux), just a heads up that installing software in Linux is a billion times simpler than it is in Windows... no more hunting down applications and packages to install, just flip to your package manager and install away.

That is especially true in Ubuntu, with the use of Synaptic.

---

### Post by firefly2442 on 2010-01-08
To check what version of Python you have installed you can run this in the terminal (commandline):

```
python --version
```

---

