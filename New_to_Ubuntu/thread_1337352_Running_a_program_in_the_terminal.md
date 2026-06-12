---
title: "Running a program in the terminal"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by amcavoy on 2009-11-25
I have MATLAB installed and when I type 'matlab' in the terminal, the GUI opens and I have the full version of MATLAB running in front of me (ie. not running in the terminal).  However, when I run something like PARI/GP, the program runs right inside the terminal.  Is there any way I can do this with MATLAB?

---

### Post by doas777 on 2009-11-25
unfortunately this is not a generic question. it depends entirely on whether the makers of matlab wrote a text interface. if so, there is probably a command option that invokes it in text only mode.

---

### Post by abcuser on 2009-11-25
I have never installed 'matlab' or 'PARI/GP', but I just guest that first is GUI program and the second is some text program, is it? If so this is normal and I don't know if it can be avoided.

---

### Post by RedSingularity on 2009-11-25
MATLAB probably comes with a GUI where as the other program does not come with one installed by default.  Thats why it runs in the terminal.

---

### Post by amcavoy on 2009-11-25
When I access MATLAB via SSH (on my school's server) it runs in the terminal, so I thought there would be a way to do it on my local machine as well.

In general, if a program has a text interface *and* a GUI, how do you choose which one to run?

---

### Post by doas777 on 2009-11-25
open a terminal, and enter:
```
<app-name> --help
OR
<app-name>  -h
```it should print a "usage" message for that application, describing the command options. 
try matlab --help and see what it prints out.

it looks like you want --nodesktop, or possibly --nodisplay
[http://www2.phys.canterbury.ac.nz/dept/localref/LocalHelp/matlab-CLI.html](http://www2.phys.canterbury.ac.nz/dept/localref/LocalHelp/matlab-CLI.html)

---

### Post by Paqman on 2009-11-25
> **amcavoy said:**
> 
In general, if a program has a text interface *and* a GUI, how do you choose which one to run?

Have a look in the man page, it should have information like this.

---

### Post by amcavoy on 2009-11-25
Great, thanks for all of the replies.  "matlab -nodesktop" did the trick :)

---

### Post by XCan on 2009-11-25
```
 matlab -nojvm 
``` works as well, and is a tad bit less resource hungry. Works nicely unless you want to generate figures.

---

### Post by pi.boy.travis on 2009-11-25
Just FYI, you can run a GUI program over SSH, depending on your client. . .

---

### Post by bodhi.zazen on 2009-11-25
> **pi.boy.travis said:**
> Just FYI, you can run a GUI program over SSH, depending on your client. . .

Every ssh client I have ever seen allows this.

On Windows you need an X server which can be installed via Xming (Xming is portable) or cygwin.

---

