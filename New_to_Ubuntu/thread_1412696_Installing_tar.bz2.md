---
title: "Installing tar.bz2"
date: 2010-02-21
forum: New to Ubuntu
---

### Post by aliasghar1451 on 2010-02-21
i m a beginner in ubuntu and i m having a problem when ever i try do install a tar.bz2 file after doing ./configure when i write make it shows "make: *** No targets specified and no makefile found" plz can anyone help

I m using Ubuntu 8.04

---

### Post by halitech on 2010-02-21
what are you trying to install? there might be an easier way then using a tar file. Also, when using tar files and mak you need to have build-essential installed first.

---

### Post by aliasghar1451 on 2010-02-22
> **halitech said:**
> what are you trying to install? there might be an easier way then using a tar file. Also, when using tar files and mak you need to have build-essential installed first.

thank for the help
i was downloading gparted and i found the easer way but i dont understand way wasnt i able to install it this way and how do i install buil-essential

---

### Post by NCLI on 2010-02-22
> **aliasghar1451 said:**
> thank for the help
i was downloading gparted and i found the easer way but i dont understand way wasnt i able to install it this way and how do i install buil-essential

[This]("http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html") should answer all of your questions.

---

### Post by d3v1150m471c on 2010-02-22
```

cd /path/to/folder/containingthetarball

tar -xf filename.tar.bz2

```After you extract the tar use this command and tell us what is inside it

```

ls

```Keep in mind, not every tar is going to install the same way or even "install". I've had some that run right from the folder.

---

### Post by halitech on 2010-02-22
> **aliasghar1451 said:**
> thank for the help
i was downloading gparted and i found the easer way but i dont understand way wasnt i able to install it this way and how do i install buil-essential

why not open Software Center or Synaptic and search for it and install it that way. Same with build-essential.

---

### Post by 3rdalbum on 2010-02-22
I haven't compiled any software for probably about a year. PPAs are popular because they save a lot of time.

You're getting that message because your terminal isn't in the correct directory, or possibly because you haven't run the ./configure command.

If you want to move your terminal to the correct directory, you need to type 'cd', hit the space bar, and then drag the folder to the terminal.

---

### Post by m4tic on 2010-02-22
i often use point and click to install .tar files. unpack that .tar file and open the folder extracted, double click file 'configure' and select open in terminal. easier for you that way. if it says you have insuficient rights. i open terminal and type: sudo nautilus . go to your home folder and do the first step again. after close nautilus and terminal befor you do anything else!

---

### Post by ssdt on 2010-02-22
Is there any way to convert the tar.bz or tar.bz2 into .deb?

---

### Post by atomizer on 2010-02-22
> **aliasghar1451 said:**
> thank for the help
i was downloading gparted and i found the easer way but i dont understand way wasnt i able to install it this way and how do i install buil-essential


Please search for software in Synaptic 
(system=>administration=>Synaptic Package Manager)

If the software is not there, you still can compile from source (if you have build-essentials) Compiled software will NOT be auto-updated, it will NOT show in synaptic and will NOT be uninstallable with one click

Gparted is installable with synaptic.

---

### Post by 3rdalbum on 2010-02-22
> **ssdt said:**
> Is there any way to convert the tar.bz or tar.bz2 into .deb?

tar.gz and tar.bz2 are merely compression formats, like Zip. A tar archive can contain pretty much anything; a theme, some pictures, source code for a program, or a compiled binary.

So, no. It's like asking if there's a way to convert an ISO to an EXE.

---

