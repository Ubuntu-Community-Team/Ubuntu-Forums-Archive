---
title: "etext coursesmart"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by olayak on 2010-10-24
has anyone been able to use coursesmart's bookshelf through wine on any linux distro?
[http://www.coursesmart.com/](http://www.coursesmart.com/)
 
i have to read my etext through their bookshelf program, but i don't want to load into win just to do that!
 
thanks!

---

### Post by carl.davis on 2010-10-24
Have you tried to launch the program with wine?

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

---

### Post by daveincanada on 2010-11-08
> **carl.davis said:**
> Have you tried to launch the program with wine?

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

When you try to launch with wine, the following error message appears:

The file '/home/dave/Downloads/setup.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

Is there any way around this?

---

### Post by daveincanada on 2010-11-08
> **olayak said:**
> has anyone been able to use coursesmart's bookshelf through wine on any linux distro?
[http://www.coursesmart.com/](http://www.coursesmart.com/)
 
i have to read my etext through their bookshelf program, but i don't want to load into win just to do that!
 
thanks!

Hey just found this after looking around a bit:

How to install untrusted software
Sometimes you will have a good reason for installing software which is not part of the trusted Ubuntu repository system. If you need to do this then right click on the file and under the file permissions select the box marked 'Allow executing the file as a program'. You will now be allowed to (try and) install the file as a program.
If the file you want to run is on read-only media, like a cd, then you will have to copy it to your desktop before following the instructions noted above.

TLDR: Right click-->Properties-->Permissions-->Allow executing file as program

---

### Post by cboxhero on 2010-11-08
To run Windows programs
Just go into a terminal and type
```

wine (Your Program).exe

```without the parenthesise.

---

### Post by daveincanada on 2010-11-10
> **cboxhero said:**
> To run Windows programs
Just go into a terminal and type
```

wine (Your Program).exe

```without the parenthesise.

It won't run it, the cursor does its "working" thing and nothing happens. Any suggestions?

---

### Post by casper911ca on 2011-01-25
I was having issues with Coursesmart Bookshelf as well. I found that installing Mono through wine did not solve the issue, wine still tells me to install Mono
```
fixme:actctx:parse_manifest_buffer root element is L"asmv1:assembly", not <assembly>
wine: Install the Windows version of Mono to run .NET executables

```. 

A Gentoo forum reply offered some possible insight. 
[http://wine.1045685.n5.nabble.com/coursesmart-bookshelf-on-gentoo-td1713381.html](http://wine.1045685.n5.nabble.com/coursesmart-bookshelf-on-gentoo-td1713381.html)

> The program is using Windows Presentation Foundation, which is not 
implemented in mono. You may have better luck installing dotnet30 with 
winetricks. 

I have yet to attempt this. Winetricks was not available in the synaptic repos that I currently use [Main, Universe, Multiverse, Restricted].

---

