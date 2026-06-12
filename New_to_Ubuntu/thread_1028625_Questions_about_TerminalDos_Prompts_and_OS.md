---
title: "Questions about Terminal/Dos Prompts and OS"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by Liliitha on 2009-01-02
Well I am guessing Terminal is just a command line program that allows you to talk to the operating system with out GUI?  DOS/MS-DOS is just like this and Windows used the DOS platforms just like Ubuntu uses the gnome platforms.  Am I correct with this? 

Also, if I would like to learn more Terminal lingo where can I go?

Was Gnome programmed in Assembly Language?


Also with the DOS/Gnome platforms what is being kept for OS programs such as Windows 95/98/2000 and Ubuntu?  I had just figured everything was kept the same only things were added to those programs, like better GUI other user intferfaces, so other programs are added to make the DOS and Gnomes platforms easier to use.  Is this the case or is there more to it?

---

### Post by bump_ on 2009-01-02
You are close.

The Terminal is just a shell just like the command prompt in Windows, but it is much more powerful. And yes, it is a way to talk to the OS without a gui.

MSDOS and Windows relationship is not the same as Ubuntu's with gnome. Gnome is just the Desktop Environment that displays the windows and themes. I'm not too clear on how MSDOS and modern Windows are related but I suppose that would be analogous to the Linux Kernel and Ubuntu in that the kernel is the heart of Ubuntu.

The shell used by default in Ubuntu is called the bash shell. To learn more about the shell and its commands, take a look at the bash reference manual. It has a wealth of information.

[http://www.gnu.org/software/bash/manual/bashref.html](http://www.gnu.org/software/bash/manual/bashref.html)

I am not sure what gnome was written in, but I highly doubt it was assembly. Not much is written in pure assembly anymore, maybe some embedded systems here and there.

I'm not sure I understand the last part of your question, but I hope this all helps.

---

### Post by handydan918 on 2009-01-02
No windows O/S has run on top of DOS since windows ME. After NT , the architecture totally changed. 
Not sure what your interest is in DOS.

With Linux, the terminal is usually a BASH shell. If you know the BASH shell, there is nearly nothing you can't do faster from a terminal than in a GUI.

---

### Post by OutOfReach on 2009-01-02
> **Liliitha said:**
> 
Was Gnome programmed in Assembly Language?


Also with the DOS/Gnome platforms what is being kept for OS programs such as Windows 95/98/2000 and Ubuntu?  I had just figured everything was kept the same only things were added to those programs, like better GUI other user intferfaces, so other programs are added to make the DOS and Gnomes platforms easier to use.  Is this the case or is there more to it?

No, GNOME was not programmed in the Assembly language, that would be extreme overkill. GNOME is in C (or at least most of it).

I don't quite understand your final question, mind clarifying?

---

### Post by 2hot6ft2 on 2009-01-02
If you know DOS and want to compare the DOS commands to Linux commands you'll like this.
[http://tille.garrels.be/training/tldp/apb.html](http://tille.garrels.be/training/tldp/apb.html)

---

### Post by Liliitha on 2009-01-02
Thanks so much for the info.  My last question was, what file is being kept?  Like for windows I think Fat32 was passed on from MSDOS to Windows 2000.  And for Ubuntu there must be a file that is used with a lot of different Linux system.  A file that these OS's have in common.  I think some one above said it was the heart of the Ubuntu system.  From OS to OS are these files that are shared changed or edited or do they remain the same and just have files added around them?

Is Ubuntu good for working with assembly and does anyone know any place I can find tutorials/open source for it?  I am a bit interested in Assembly since it allows the person to get really intimate with the computer.  I tried higher level languages and never understood them... then I picked up an old Assembly Language book and it just made sense.  Programming the IBM PC, the old Intel 8088 processor.  I don't really understand things until I know the question of why, higher level languages do that but not as much as Assembly.  Plus Assembly lets me use any previous knowledge of circuitry I have and use it to it's potential.  So assembly is one of the things I wish to learn while using Ubuntu.  Sadly, I have found assembly open source and tutorials are somewhat of a scarcity online... :(  It does seem as if you are correct and people are moving further and further away from assembly language.  Even sourceforge.net does not carry as many open source of assembly language.

---

### Post by bump_ on 2009-01-02
I think you might a bit confused by some things. FAT32 was a filesystem, not a file and modern Windows uses NTFS. A file system dictates the way to store files on a disk. I believe Ubuntu uses ext3.

The kernel is at the heart of any Linux distro, be it Ubuntu, Arch Linux, Fedora...etc. Having this kernel enables an OS to be called "Linux". What differs between these distos is the stuff around the kernel, the package manager, the desktop environment...etc. 

The kernel is not so much one file as a collection of files.

As for assembly, there is a reason that no one really writes projects in it. For one thing, writing a project over a certain size is painful. For another, C compilers these days are more effective at turning C code into machine code than most assembly writers. And if there is that one spot where you need every ounce of optimization and you are sure you can handle it better than the compiler; then you just write that small section inside of your C source.

---

