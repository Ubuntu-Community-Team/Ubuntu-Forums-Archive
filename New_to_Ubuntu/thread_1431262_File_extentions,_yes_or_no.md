---
title: "File extentions, yes or no?"
date: 2010-03-16
forum: New to Ubuntu
---

### Post by sixthwheel on 2010-03-16
I've read in the Ubuntu book, and some other places, that Ubuntu doesn't use file extensions.

However looking around my files, I see lots of different extensions.
I'm confused.:confused:

---

### Post by J V on 2010-03-16
It doesn't need file extensions... an unextended file can easily be opened by whatever opens it, but the program that then opens it *might* want you to add an extension... plus it beats running a file command every time you want to find out what a file is for :)

---

### Post by sixthwheel on 2010-03-16
Thanks JV, I think I understand.
It doesn't need it, but it helps.

OK, so lets say I want to install a program, how does Ubuntu know, that it is an executable file, if there is no extension?

---

### Post by J V on 2010-03-16
Well standard executables have the "Executable" permission checked, but most linux apps are contained in files that are unpacked with executables already on the system (You can't run a deb rpm or tar.gz, but you can use dpkg, untar, etc to "Install" them)

---

### Post by sixthwheel on 2010-03-16
I appreciate your time answering my question.
Thank You.

---

### Post by lykwydchykyn on 2010-03-16
Actually this is a bit of a misconception.

Desktop environments like GNOME or KDE actually *do* use file extensions to identify what program to open a file with, what default icon to give it, etc.  If you take a .txt file and change its extension to png, you'll find that its icon will change and double-clicking it will open your image viewer.

If you want to execute a text file as a script by clicking on it from a file manager or on the desktop, you have to give it a file extension such as ".sh" which your DE will recognize as executable.

At the command line level it's a different story.  File extensions at that level are just part of the name and have no bearing on what happens when you try to execute them.

---

### Post by kaibob on 2010-03-16
Most files in Linux contain information identifying the file type. For example, the first line of a bash shell script contains #!/bin/bash. I don't know a lot about this topic but for more information see:

[http://en.wikipedia.org/wiki/File_format](http://en.wikipedia.org/wiki/File_format)

---

### Post by lykwydchykyn on 2010-03-16
> **kaibob said:**
> Most files in Linux contain information identifying the file type. For example, the first line of a bash shell script contains #!/bin/bash. I don't know a lot about this topic but for more information see:

[http://en.wikipedia.org/wiki/File_format#Magic_number](http://en.wikipedia.org/wiki/File_format#Magic_number)

Magic numbers can be used to identify files at the command-line level, but that's different from the #!/bin/bash thing.

Basically, if you execute a file with execute permissions at the command line, it will do one of two things:

 - if it's an ELF executable (standard binary executable format, analogous to .exe files on windows), it will execute it.
 - if it's anything else (including binary files like images), it will try to interpret it as a script.  By default it interprets it as a bash script, but if you include a "#!" line it will use the interpreter you specify in that line (e.g., "#!/usr/bin/python").

But like I said, this is at the command-line level.  At the desktop environment level it's quite similar to how Windows behaves, utilizing the file extension to figure out what to do with the file.

---

### Post by kaibob on 2010-03-16
> **lykwydchykyn said:**
> Magic numbers can be used to identify files at the command-line level, but that's different from the #!/bin/bash thing.

You clearly know more about this than I do, and I guess this is just a matter of semantics, but the Wikipedia article states:

> So-called shebang lines in script files are a special case of magic numbers. Here, the magic number is human-readable text that identifies a specific command interpreter and options to be passed to the command interpreter.

---

### Post by lykwydchykyn on 2010-03-16
> **kaibob said:**
> You clearly know more about this than I do, and I guess this is just a matter of semantics, but the Wikipedia article states:

I clearly didn't know that :)

---

