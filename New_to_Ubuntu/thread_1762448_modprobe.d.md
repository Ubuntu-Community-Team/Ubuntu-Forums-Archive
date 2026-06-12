---
title: "modprobe.d"
date: 2011-05-19
forum: New to Ubuntu
---

### Post by Mariane on 2011-05-19
Who came up with such a strange name for a directory and why? 

(My question is not related to any specific problem, I'm just puzzled by a directory which name has a dot in it). 

Mariane

---

### Post by mcduck on 2011-05-19
Actually the directories with the ".d" in the name are a rather clever trick. They are used to replace a single configuration file with a directory full of smaller configuration files.

So in this case, you could either have a single, long config file called "modprobe", or you can split it into many smaller files and put them into directory called "modprobe.d", and the system will automatically read all those small files instead of the single modprobe file.

Anyway, dots in directory names aren't that much of an issue in Linux/Unix systems, it might seem strange if you are used to the Windows way with file name extensions separated by a dot, but Linux doesn't actually care about such things that much so you are free to use multiple extensions in file names, or no extension at all. Same goes for directories of course.

---

### Post by Mariane on 2011-05-24
Thank you. Yes I came across files called a.b.c.d... 
.d means it's a directory? 
And what about the rest of the name? I read it as two 
words, "mod probe". So it probes something that starts 
with "mod" but what? 

Mariane

---

### Post by mcduck on 2011-05-24
Modprobe is a program used for loading and unloading kernel modules. For example when you plug in  some USB device modprobe is used to load the appropriate driver for it.

[http://en.wikipedia.org/wiki/Modprobe]("http://en.wikipedia.org/wiki/Modprobe")

What comes to the ".d" in the end of a file/directory name, it doesn't necessarily mean anything at all. Like I said, Linux doesn't really care about file name extensions and instead detects file types by their actual contents. A file is a file, and a directory is a directory, regardless of what you name it. The use of ".d" at the end of the directory name is just a common scheme used when replacing a single config file with a directory of config files.

---

### Post by nothingspecial on 2011-05-24
mod is short for modules which are what you might think of as drivers. 

The kernel detects your hardware and loads the modules it needs to run (sound, networking, graphics etc etc)

The command modprobe loads (or unloads with the -r option) modules into the kernel while the system is running.

/etc/modprobe.d (and /etc/modules) are configs where you can specify which modules you do and do not want loaded at boot.


It's useful when the kernel modules (drivers) don't work very well and there is another one that works better.

---

### Post by Mariane on 2011-05-31
Now I've really learnt something! 
Thanks a lot to all of you :guitar: 

Mariane

---

