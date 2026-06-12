---
title: "what is tar"
date: 2010-12-11
forum: New to Ubuntu
---

### Post by degarb on 2010-12-11
I am choking on some install packages because I don't understand tar.  Also, they give code to type, but never tell us what directory to run this code in.

Isn't taring  another way of saying click with a built in archive manager?   Wouldn't this nullify most posted instructions, since there is a simplier graphical way? I don't perform voodoo to open a zip file on windows.  Wouldn't you untar, anyway?  I wouldn't zip a zip file.

Why wouldn't a community move to declare this command level of instruction to be defunct.  It certainly alienates a major part of Windows users, even system engineers who have spent thousands of hours learning windows, but are less dedicated to spend similar time mastering something that seems less dedicated to commonsense, intuitive installation and use.


Now, I did read the 150 page manual (in 2009), the 1000 page ret hat manual (2000).  I just don't remember much after 3 to 12 months, so must start anew with each system jump.

---

### Post by CharlesA on 2010-12-11
You'd untar a tar.gz file by running this:

```
tar -xf somefile.tar.gz
```

All tar does is pack/unpack tarballs. You can use archive manager to unpack them via the GUI.

Is there a specific problem you are running into?

---

### Post by Hippytaff on 2010-12-11
A bit like zip in windows

---

### Post by Tricity on 2010-12-11
If you want to use a tar archive in a pointy-and-clicky way like you'd do in Windoze, try ark. 

(sudo apt-get install ark)

Ark opens archives, including tar files and allows you to drag-and-drop the files.

---

### Post by karthick87 on 2010-12-11
Checkout this [https://help.ubuntu.com/community/FileCompression](https://help.ubuntu.com/community/FileCompression)

---

### Post by degarb on 2010-12-11
> **CharlesA said:**
> You'd untar a tar.gz file by running this:

```
tar -xf somefile.tar.gz
```

All tar does is pack/unpack tarballs. You can use archive manager to unpack them via the GUI.

Is there a specific problem you are running into?

Well, trying to run abyss web server.  I just unzipped and run.   But typing internal ip on other machine won't bring up the sample index html.  So, I am not sure what needs to be done next.  Just reverse trying to read their install.  They give you a bunch of voodoo commands, but don't tell us what each command does or from what directory to run these commands.

I am guessing I need to open some UBU ports, or am missing something on the install (perhaps not compatible with UBU--I forget, are we debian...anyway... need to up my dosage on my long technical term memory medicine.)

---

### Post by StephenDavison on 2010-12-11
The name says it all: tar stands for tape archive.  However, these days it is most commonly used to package files and directories into an archive file on disk storage.  When used in combination with a compression utility like gzip, it is analogous to zip in Windows.  Always remember this with respect to UNIX-like (e.g. Linux) operating systems:  man is your friend; and by "man" I mean the manual pages command.  

> 
Why wouldn't a community move to declare this command level of instruction to be defunct. It certainly alienates a major part of Windows users, even system engineers who have spent thousands of hours learning windows, but are less dedicated to spend similar time mastering something that seems less dedicated to commonsense, intuitive installation and use.


So much could be written in response to the above quote.  I'll leave it with this:  perhaps you should stick with Windows then.

---

### Post by CharlesA on 2010-12-11
> **degarb said:**
> Well, trying to run abyss web server.  I just unzipped and run.   But typing internal ip on other machine won't bring up the sample index html.  So, I am not sure what needs to be done next.  Just reverse trying to read their install.  They give you a bunch of voodoo commands, but don't tell us what each command does or from what directory to run these commands.

I looked at the instructions and all it's telling you to do is to untar the file and then run a shell script from the directory you unpacked the tar to.

[http://www.aprelium.com/data/doc/2/abyssws-linux-doc-html/install.html](http://www.aprelium.com/data/doc/2/abyssws-linux-doc-html/install.html)

Why not just use Apache? It's in the repos and has a boatload of documentation.

---

### Post by lumore22 on 2010-12-11
Hi - 
tar stands for "tape archive" . The command options that I use to untar a file or pkg is:

tar xvfz filename.tar.gz .  

Putting a dash in front of the options is optional.  I usually follow this with the path to location where I want to install the pkg/file/.  For example:

tar xvfz  filename.tar.gz  -C /opt/lampp/.....


When you download a pkg, check the install instructions, usually found in a README file or an INSTALL file. THe info contained in these files will tell you where to extract the pkg files. 

Access the man page for tar. This doc will tell you what options are available for the tar cmd and what they mean and/or do.

Hope this helps!

Regards-

---

