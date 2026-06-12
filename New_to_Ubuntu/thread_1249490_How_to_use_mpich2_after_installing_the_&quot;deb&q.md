---
title: "How to use mpich2 after installing the &quot;deb&quot; ?"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by deadguysleeps on 2009-08-25
I'm using Ubuntu 9.04 desktop edition and i've got an assignment to install and run mpich2 on 2 computers. So, I've downloaded the .deb file from [http://www.mcs.anl.gov/research/projects/mpich2/downloads/index.php?s=downloads]("http://www.mcs.anl.gov/research/projects/mpich2/downloads/index.php?s=downloads"), double click on the .deb file and finished installing it.

The problem is, the user guide told me how to run mpich2 after compiling the source code and not the "double-click the .deb thing". So, I don't know how&where to run it. The official user guide says:

> 
Let us assume that the
directory where MPICH2 has been installed is /home/you/mpich2-installed, and that you have added that directory to your path, using

setenv PATH /home/you/mpich2-installed/bin:$PATH

Then to run an MPI program, albeit only on one machine, you can do:

mpd &
cd /home/you/mpich2-installed/examples
mpiexec -n 3 cpi
mpdallexit

So, the real problem here, I don't know where it's installed. I've double-click the deb file again to see where it's installed but the files are installed everywhere. I've also run the command:

> #mpd &

and it told me to create a file .mpd.conf... and some more stuff... i did it and mpich2 still don't work. Some help please? Anybody out there have tried installing it from .deb?

---

### Post by cariboo on 2009-08-25
You can check where prgrams are installed by going to System-->Admimnistration-->Synaptic Package Manager and search for the package, once thae package has been found, highlight it and click the properties button.

Most executeables are located in /usr/bin.

---

### Post by ajgreeny on 2009-08-25
You can also fine the executable file path in terminal for most things ```
which mpich2
```though this does assume that the executable is called mpich2

---

### Post by alexlafreniere on 2009-08-25
To find an executable I usually do one of these:

```
whereis <your_app>
```

Now, a little bit of clarification is needed. Is your program a command-line app or a graphical one? If it's command-line only, there won't be an icon for it anywhere, you need to call it from the terminal. Even if it is graphical, you can still run it from the terminal. Run the bit of code from above, then run the binary executable. Then you'll know for sure whether it installed correctly or not.

---

