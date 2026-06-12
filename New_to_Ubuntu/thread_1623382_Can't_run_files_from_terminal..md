---
title: "Can't run files from terminal."
date: 2010-11-16
forum: New to Ubuntu
---

### Post by Jet8225 on 2010-11-16
I just compiled a small c++ script and now I want to run it. Thing is I've been trying to run if from the terminal and it's not working. 

Example: 
user@user~: Program.exe
Program.exe: command not found

Same thing without the .exe extension. Oh, and I am in the directory where the file is located. 
Anyone has any idea what's going on?

---

### Post by coffeecat on 2010-11-16
```
user@user:~$ ./filename_of_executable
```

You need ./ prefacing the filename to run an executable.

---

### Post by Verbeck on 2010-11-16
isn't .exe's windows executables :confused:

---

### Post by Jet8225 on 2010-11-16
It's not a windows executable. I just tried that just in case. It was the ./ that was missing. I had tried it but not in the right directory. Thanks.

---

### Post by coffeecat on 2010-11-16
> **coffeecat said:**
> ```
user@user:~$ ./filename_of_executable
```You need ./ prefacing the filename to run an executable.

> **Jet8225 said:**
> It was the ./ that was missing. I had tried it but not in the right directory. Thanks.

Sorry - just to clarify. I wasn't completely clear in my first post. When running an executable from the terminal you have to provide the path to the executable. In the case where you're already "in" the directory, you need to use ./ as the path. You could of course use '/home/username/filename' when you are in home in the terminal, but './filename' is quicker.

---

### Post by Jet8225 on 2010-11-16
Oh, I understand. I tried the ./filename on the home directory but it obviously didn't work. Just out of curiosity, would you mind explaining (if you can) why don't I have to do the same thing with emacs, gimp, or other similar applications?

---

### Post by HarrisonNapper on 2010-11-16
Because emacs and gimp are executable files located in a folder that is in the system path. Most folders for executables contain bin such as /bin, /sbin, /usr/bin, /usr/local/bin, etc (but not /etc :) (scheme)). If you add your program to the system path and type the name of the program, nix will search the system path for a file of that name and, if it finds it, it will execute it.

---

### Post by Jet8225 on 2010-11-16
I see... Thank you.

---

### Post by championboxes on 2010-11-16
Have you made the program executable?

```
chmod +x /path/to/file
```

---

### Post by Jet8225 on 2010-11-16
Yes.

---

