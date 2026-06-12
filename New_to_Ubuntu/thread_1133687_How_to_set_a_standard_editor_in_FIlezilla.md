---
title: "How to set a standard editor in FIlezilla?"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by kramer65 on 2009-04-23
Hello,

I want to edit a script on my (remote) server but filezilla says that I have to set a standard editor first. I wanted to set bluefish as my standard editor so I went to Edit > Settings > File edits (freely translated from Dutch) where I want to set the standard editor.

I clicked on Browse and I now have to select the program. But where is the executable file which I have to select to get bluefish working..?

---

### Post by kramer65 on 2009-04-23
Nevermind! Found it!

For other users who read this. Most programs' executable files are in "usr/bin".

Cheers!

---

### Post by voltav on 2009-05-01
> **kramer65 said:**
> Nevermind! Found it!

For other users who read this. Most programs' executable files are in "usr/bin".

Cheers!

Thanks!

I had the same problem, even download other FTP clients but none gave me what gives Filizilla. 

 Thanks again.

---

### Post by mkoehler on 2009-05-01
You're right.  Executable files are typically found in a variety of "bin" or "sbin" folders throughout your filesystem.  Additionally, many of these directories are located within the PATH environment variable (type echo $PATH) in the terminal -> if the directory where the bin file is located is one of the directories in the path variable, then you don't have to type the full location of the file in order to execute it (e.g. instead of typing /usr/bin/gedit, I can just type in gedit).

---

