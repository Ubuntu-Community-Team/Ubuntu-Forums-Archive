---
title: "Starting multiple programs at once"
date: 2009-08-02
forum: New to Ubuntu
---

### Post by sonone on 2009-08-02
Hello,

I am using Ubuntu Studio for some months now, but i still dont know how i can start multiple programs with one click. Can you please help me, it would make working with Ubuntu much easier.

Thank You.

---

### Post by ecmatter on 2009-08-02
1. Do you have a bin directory in your home folder?  If you do, skip forward to step 2.  Otherwise, do the following:

```

mkdir ~/bin
chmod 755 ~/bin

```

```

sudo gedit ~/.bashrc

```

Add the following to the end of .bashrc and save:
```

PATH="$HOME/bin:$PATH"

```

2. Cut and paste the following into a text editor:
```

#!/bin/bash

firefox
thunderbird

exit

```Replace Firefox and Thunderbird with whatever programs you want to open and save as ~/bin/open.sh

```

chmod 755 ~/bin/open.sh

```Create a ~/bin/open.sh launcher on your desktop by right clicking on the desktop > create launcher.

Type: application
Name: open
command: ~/bin/open.sh

click ok

---

### Post by sonone on 2009-08-02
Thanks for the tip,

but unfortenately i cant get it working like that. The starter tells my permission denied and if i try to open open.sh itself nothing happens (i used the prorgram names qjackctl and zynaddsubfx).
Maybe its because i didnt saved open.sh via terminal (the terminal didnt wanted to do chmod... it said no such file or directory), but saved it via GUI of gedit into the new created bin folder in my home directory.
I'm not quite familiar with the terminal. Still Windows influenced.

Can you give some more advice please?

---

### Post by ecmatter on 2009-08-02
I'm not exactly sure, from what you've written, what went wrong.

Go ahead and delete the open.sh file and bin directory you just made and I'll try to walk you through the entire process.

Post back here when you're ready.

---

### Post by sonone on 2009-08-03
Ok, deleted.

I'm ready for the next try.

---

