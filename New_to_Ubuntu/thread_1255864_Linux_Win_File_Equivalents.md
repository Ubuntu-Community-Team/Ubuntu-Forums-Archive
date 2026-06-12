---
title: "Linux Win File Equivalents"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by zer010 on 2009-09-02
I have been wondering what exactly are the closest file equivalents between Linux and Windows.  There seems to be a definite relation between lib vs. .dll.  Mostly whats the Linux equivalent of an .exe?  Any others?  I think this would help a lot of n00bs (such as myself).  I somewhat understand the filesystem layout, but being able to pin-point certain app file-types would be nice.  Thanks to anyone who can help.

---

### Post by Xenomorph05 on 2009-09-02
for Ubuntu .deb is as close to .exe as it gets. there are rpm and yum and others for different distros.

---

### Post by techstop on 2009-09-02
> **Xenomorph05 said:**
> for Ubuntu .deb is as close to .exe as it gets. there are rpm and yum and others for different distros.

I disagree. A .deb is more like an .msi file (ie an installer). An .exe in Windows could be a standalone program, so the *nix equivalent could be a a shell script (.sh, .run etc), or a binary file (.bin).

Anyway, it's largely a pointless exercise, as Linux is not Windows. Linux doesn't identify file types by extension in the way that Windows does.

This might help;

[http://www.debianhelp.co.uk/fileext.htm](http://www.debianhelp.co.uk/fileext.htm)

---

### Post by 3rdalbum on 2009-09-02
A Windows dynamically linked library is exactly equivilant to a Linux dynamically linked library (or "shared object"). And a Windows executable is exactly equivilant to a Linux executable.

Well, what did you want me to say? Both systems use dynamic linked libraries. Every operating system has an executable file format. I don't know what you mean by  "being able to pin-point certain app file-types"; I can't see why you would need to know this stuff. If you try to run a program and it complains that you're missing a shared object, then you need to install one of the "lib*" packages corresponding to what is missing.

Linux doesn't actually need filename extensions, so Linux programs don't tend to have filename extensions. A lot of binary installers have ".run" or ".bin" at the end, but this isn't necessary. A binary installer is a Linux program just like the rest of them.

---

### Post by earthpigg on 2009-09-02
in addition to what everyone else said,

a .jpg is a .jpg. 
an .html is an .html.

things like that are universal, with the caveat that a .JPG will not be read as a .jpg by certain linux programs.

digital camera makers that name files .JPG by default should be growled at agressively. (yes, i know they can be renamed *en-masse* with a script. besides the point.)

---

### Post by Xenomorph05 on 2009-09-02
I think he just wants to install things and isn't looking for something to skip installs. I would say a .py file is pretty close to an exe when it comes to running code with out install.

---

### Post by 3rdalbum on 2009-09-02
> **earthpigg said:**
> in addition to what everyone else said,

a .jpg is a .jpg. 
an .html is an .html.

things like that are universal, with the caveat that a .JPG will not be read as a .jpg by certain linux programs.

digital camera makers that name files .JPG by default should be growled at agressively. (yes, i know they can be renamed *en-masse* with a script. besides the point.)

Linux isn't Windows, so can we please stop calling things by what their Windows name? It's not a ".jpg file", it's a JPEG or a JPEG image. It's not a ".html file", it's an HTML file or an HTML web page.

It's not a ".py file", it's a Python script.

And it's not a ".deb file", it's a Debian package.

It's not a ".sh", it's a shell script.

---

### Post by Xenomorph05 on 2009-09-02
There is nothing wrong with using file extensions for talking about types of files. If you want to say RPM Package Manager instead of a .rpm thats up to you.

---

### Post by anewguy on 2009-09-02
As already mentioned, there are no true file types in Linux.  There really is no relationship between a .exe or .com file in Windows to any Linux file type - I compile a lot of my C programs with no extension at all -> it simply isn't needed.  An image file has a header within the file that identifies it, so no extension is needed on those either.

You may find some programs that default to file name suffixes that look like Windows file types, but they are meaningless in that regard.

I had the same complaint, as have countless others, of wanting to know what the Linux equivalent of Windows things were - commands, file types (in Linux, purely a file suffix), etc..  I hated the advice at the time, but the real answer has been given here already - learn Linux as the seperate animal it is and don't try to compare things to Windows, as you'll only get confused.

Best of luck!

Dave :)

---

### Post by zer010 on 2009-09-02
I fully understand that file extensions are not needed in Linux.  I also fully understand that Linux is NOT Win.  I'm no programmer (yet), so I'm unsure of how to find pieces of programs, such as the launching file (in win, usually an .exe).  Is the only way to launch an app is through the menus or terminal?  Where do I find most of an app that has been installed?  It seems pretty scattered about in the filesystem, admittedly not as bad as the scattering of some files in Win.  I've heard that it's the not the name of a file that is tell-tale, but more-so the location. Is this true?  I know that it's like comparing oranges to cars, but I'm just trying to understand what's running on my machine. :confused:

---

### Post by DGortze380 on 2009-09-02
> **zer010 said:**
> I fully understand that file extensions are not needed in Linux.  I also fully understand that Linux is NOT Win.  I'm no programmer (yet), so I'm unsure of how to find pieces of programs, such as the launching file (in win, usually an .exe).  Is the only way to launch an app is through the menus or terminal?  Where do I find most of an app that has been installed?  It seems pretty scattered about in the filesystem, admittedly not as bad as the scattering of some files in Win.  I've heard that it's the not the name of a file that is tell-tale, but more-so the location. Is this true?  I know that it's like comparing oranges to cars, but I'm just trying to understand what's running on my machine. :confused:

The whereis command might help you a bit .. here's an example.

```

me@ubuntu-desktop:~$ whereis firefox
firefox: /usr/bin/firefox /usr/lib/firefox /usr/lib64/firefox /usr/share/firefox


```

The binary, the compiled program itself is at: /usr/bin/firefox
/usr/bin is in your path, so to run firefox, just type firefox

The libraries used by the program are at: /usr/lib/firefox and /usr/lib64/firefox

Various items are typically kept in the share directory, firefox holds some files there as well: /usr/share/firefox

A number of personal config and preferences files are at: ~/.mozilla


Yes, names are pretty much arbitrary, as are extensions.
The location can be arbitrary as well, but there are conventions for certain directories.

---

### Post by Viva on 2009-09-02
Executables in linux are files with excute permissions. It could be just a text file or a binary, it is an executable as long as it has permission to execute.

---

### Post by oldos2er on 2009-09-02
> **zer010 said:**
>   Is the only way to launch an app is through the menus or terminal?  Where do I find most of an app that has been installed?  :confused:

 What other way do you want to launch an app?

 You can see where each file in a package is installed by using either Synaptic (Status, Installed, right-click on a package, Properties, Installed Files) or in a terminal **dpkg -L <package name>**.

---

### Post by zer010 on 2009-09-02
> **oldos2er said:**
> What other way do you want to launch an app?

 You can see where each file in a package is installed by using either Synaptic (Status, Installed, right-click on a package, Properties, Installed Files) or in a terminal **dpkg -L <package name>**.

Can I get to an executable of say... Terminal Emulator, and run it from the file?  Once I was messing around in another DE and somehow I had no menus and couldn't get to the terminal.  I had access to all my folders, but couldn't figure out how to launch an app from them.  I tried the Ctrl+Alt+F1, but I couldn't log in (I guess that's another thread).  So can I launch an app from the GUI file navigator?

---

### Post by sourav123 on 2009-09-02
This might not be the exact answer to the question, but it may help determine the file type. Since linux does not follow any file type extension, if you are in doubt what type of file you have (such as music/video/document), execute the command below and it will tell you the file type.
```
file <filename>
```

---

### Post by oldos2er on 2009-09-02
> **zer010 said:**
>   So can I launch an app from the GUI file navigator?

 Yes.

---

