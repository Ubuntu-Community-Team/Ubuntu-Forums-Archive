---
title: "Extract .exe"
date: 2011-04-26
forum: New to Ubuntu
---

### Post by Vistz on 2011-04-26
I have an executable .exe file and I would like to be able to look at it's contents. I've already tried using 7z but I got ```
Error: Can not open file as archive

```Is there another way to look at files inside?

---

### Post by tgm4883 on 2011-04-26
> **Vistz said:**
> I have an executable .exe file and I would like to be able to look at it's contents. I've already tried using 7z but I got ```
Error: Can not open file as archive

```Is there another way to look at files inside?

Are you sure it is an archive?

---

### Post by Vistz on 2011-04-26
> **tgm4883 said:**
> Are you sure it is an archive?

When I look at the properties, it says the type is:

```
DOS/Windows executable (application/x-ms-dos-executable)
```

So I'm guessing that this isn't an archive file...

---

### Post by tgm4883 on 2011-04-26
> **Vistz said:**
> When I look at the properties, it says the type is:

```
DOS/Windows executable (application/x-ms-dos-executable)
```

So I'm guessing that this isn't an archive file...

Well that doesn't tell a whole lot, but in my experience if you can't open it with archive manager then it probably isn't an archive (probably a binary file)

---

### Post by lisati on 2011-04-26
Short answer: Some .exe files contain archives, many (most?) don't. A file type of "exe" usually indicates that it's an MS-DOS or Windows program file, something that you'd EXEcute (i.e. run as a program) rather than use as a data file.

---

### Post by calavier62 on 2011-04-26
Even if you were able to extract the .EXE (MS-Win Executable) file, the individual libraries and/or .DLL files wouldn't be of any use. 
I would instead install WINE via apt-get: ```
sudo apt-get install wine
```
synaptic, or the software center; and see what the .exe file runs or installs.

---

### Post by Anuovis on 2011-04-26
It might not be the best idea to run it if you don't know what it actually is though. 

This can lead to some minor inconveniences in Ubuntu with Wine (just don't ever run Wine as a root) and possibly to the total destruction of the OS in Windows. Some .exe files contain harmful code.

Another thing to consider is that Wine might not run the file properly. You'll likely need Windows. Or you may run it via Windows with VirtualBox inside of Ubuntu, safer that way for sure. 

If you are certain the thing is an archive, installing a Windows version of 7-zip on your Wine might help as well.

---

### Post by Vistz on 2011-04-26
> **calavier62 said:**
> Even if you were able to extract the .EXE (MS-Win Executable) file, the individual libraries and/or .DLL files wouldn't be of any use. 
I would instead install WINE via apt-get: ```
sudo apt-get install wine
```synaptic, or the software center; and see what the .exe file runs or installs.
I already have Wine. But I wanted to see what the files looked like before I ran it.

---

### Post by gandaran on 2011-04-26
> **Vistz said:**
> I already have Wine. But I wanted to see what the files looked like before I ran it.
try [peazip]("http://www.peazip.org/peazip-linux.html"), peazip can sometimes open and extract simple .exe and .msi files.

---

### Post by HermanAB on 2011-04-26
Hexedit

Here is the file format: 
[http://www.skyfree.org/linux/references/coff.pdf](http://www.skyfree.org/linux/references/coff.pdf)

---

### Post by wep940 on 2011-04-26
I know there are a "zillion" of extract programs out there, but this also sounds like a DOS program that is used to extract things from the old data and cab files. I doubt this is a compressed file, but rather a program that is used TO extract things from some sort of compressed file.
 
So, where did you get this program and why?
 
EDIT: Just noticed that you never said the program itself was called extract.exe - I guess I ran it together looking at the thread title.  So......what is the actual full name of the exe file, where did you get it, and why do you need it?

---

### Post by Mark Phelps on 2011-04-28
The file extension .exe is used in Windows for self-extracting archives.  So, it COULD be an archive, but it's embedded inside an executable.

---

### Post by wep940 on 2011-04-28
Yeah, I kind of ran the words in the title together to make a file name - didn't see the space at first.  Sure hope the OP posts back the answers to the questions so we can help more.
 
Thanks Mark Phelps.

---

### Post by Scot_Bernard on 2012-06-28
I solved the extract with an .exe with nVidia nForce drivers.

This one where opened ok with archive manager for list folders and files inside, but fail when trying to extract.

So with 7z x [filename.exe] it works. I've the package p7zip installed.

Maybe it work for you too.

---

