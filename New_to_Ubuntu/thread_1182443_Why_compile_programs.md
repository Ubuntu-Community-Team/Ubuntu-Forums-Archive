---
title: "Why compile programs?"
date: 2009-06-09
forum: New to Ubuntu
---

### Post by LinuxFox on 2009-06-09
I got the hang of compiling programs on Ubuntu, specifically using the "prefix" line to install it to where I want, but I want to know a little more about compiling.

Is there any difference installing by compiling or using a package (deb, autopackage, etc)?  Also, is there a good site to read about compiling to learn more about it?

Please answer my questions I just want to learn more about compiling.  Thanks for any answers.

---

### Post by lazyart on 2009-06-09
If the application you want is not in .deb form, then you will have to compile.  Otherwise if given the choice between .deb and compiling (for the same version), take the .deb.  The .deb will uninstall easier than the straight compile (although you can compile to a .deb which would give you that benefit).

If you're running something like Gentoo, you won't find any packages as your OS is compiled for just your hardware.  This streamlines the OS as there are no extra parts for hardware you don't or won't own.  Takes a bit more work to maintain a Gentoo system.  But all applications much be compiled.  And Gentoo users like it that way.

---

### Post by lisati on 2009-06-09
One advantage of compiling over using a .deb file is a greater ability to customize the software to your needs. The down side is that to make use of this ability [s]usually[/s] can require some degree of programming knowledge, which might be a nuisance if the software designer chose to use a programming language that you're not familiar with.

On the other hand, using something like a .deb file is that the software comes "ready to go" - if the person who put the package together has done it well, all dependencies will be met, and it will work "out of the box" with a minimum of fuss.

---

### Post by amingv on 2009-06-09
Also take into account that if you didn't have the ability to compile, there wouldn't be much purpose to open sourcing.
If you modify a program you must be able to compile it to benefit from the modifications.

Some distributions make very minor modifications to some packages, too, so if you want to run a mint version of the package, compiling is often the only way to go (specially true with the kernel).

In general, compiling software in the computer were you'll be using it may turn a binary more suited for your processor and in more accordance with your current libraries and resources as well, which some people seem to find good.

---

### Post by kpkeerthi on 2009-06-09
[https://wiki.ubuntu.com/PackagingGuide]("https://wiki.ubuntu.com/PackagingGuide")

[https://help.ubuntu.com/community/CompilingSoftware]("https://help.ubuntu.com/community/CompilingSoftware")

---

### Post by LinuxFox on 2009-06-09
So it allows customizing the software for yourself and computer.  Now that's pretty cool, though I don't know programming to try it myself.  All I've done is compile to install and use it, not to mention just look at the source code.  For example, looking at an open source game's graphics files.

Thanks for the answers, it helps me understand compiling a bit better. :)

---

### Post by konqueror7 on 2009-06-09
also, compiling packages from their sources enable flexibility of installing of applications across different distros, instead of finding each distro's binary package like .deb or .rpm...

the downside which i hate the most so far is that when the source your compiling has many dependencies, which could become a pain in the a**...:D

---

### Post by jjbin on 2009-06-09
Mark!

---

### Post by jjbin on 2009-06-09
Mark!
   and firstly I was a little pazzled I just wondering the "compile" alwasys used in the program write tools is  the same meaning about the compile u dicussed here?
   and I found .rpm couldn't compile(I just guess I should use this verb:))
nomarlly in the ubuntu.
    I am a very newie,but it would pull out of the cloudy over my head

---

### Post by lisati on 2009-06-09
> **jjbin said:**
> Mark!
   and firstly I was a little pazzled I just wondering the "compile" alwasys used in the program write tools is  the same meaning about the compile u dicussed here?
   and I found .rpm couldn't compile(I just guess I should use this verb:))
nomarlly in the linux
    I am a very newie,but it would pull out of the cloudy over my head

Just a thought: The basic idea behind the compilation process is to take a program that's in a form that means something to programmers, and to translate it into a form that's meaningful to a computer. The idea behind the "package manager" used to create a ".deb" or ".rpm" file is to collect a bunch of files into a form that makes it easy to distribute them to other computers, with the intent of installing them.

---

### Post by konqueror7 on 2009-06-09
> **lisati said:**
> Just a thought: The basic idea behind the compilation process is to take a program that's in a form that means something to programmers, and to translate it into a form that's meaningful to a computer. The idea behind the "package manager" used to create a ".deb" or ".rpm" file is to collect a bunch of files into a form that makes it easy to distribute them to other computers, with the intent of installing them.

yup, which is very much subjective to the distro's package managers...

---

### Post by bruno9779 on 2009-06-09
> **jjbin said:**
> ...

   and I found .rpm couldn't compile(I just guess I should use this verb:))
nomarlly in the ubuntu.
    ...



You can install many .rpm in ubuntu by converting them to .deb using a package called "alien".

Although i wouldn't advise this as there are issues sometimes.
If you find an .rpm, and no .deb, look for source and compile instead.

---

### Post by decoherence on 2009-06-09
Sometimes you will find a package in the repository that wasn't compiled with the flags you want. One example is ffmpeg. The Ubuntu repository version of FFMPEG is missing support for certain audio/video formats due to licensing restrictions.

If you want to use ffmpeg to work with those formats, you must recompile it with the correct flags to enable support. For potential legal reasons, Ubuntu would not be able to distribute that version.

---

### Post by blackxored on 2009-06-09
The main advantage of compiling is optimization and customization. That's almost the important to it. 
In the other side, and I'm amazed it haven't been mentioned already, is that the use of a package manager for software management, provides the actual management of that software, regarding updates, clean removals including configuration and temp files, and the like. I'd prefer packaging against compiling-only, but that's a personal choice. Just remember that by packaging you're contributing to the [distro] community, and you gain support of it against your work.

---

### Post by andrew.46 on 2009-06-10
Hi decoherence,

> **decoherence said:**
> Sometimes you will find a package in the repository that wasn't compiled with the flags you want. One example is ffmpeg. The Ubuntu repository version of FFMPEG is missing support for certain audio/video formats due to licensing restrictions.

If you want to use ffmpeg to work with those formats, you must recompile it with the correct flags to enable support. For potential legal reasons, Ubuntu would not be able to distribute that version.

Well to give the Ubuntu devs their due they have often left the way open for much of the functionality to be restored with FFmpeg at least. Details of this particular case can be seen here:

 HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg 
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

And of course there is the ubuntu-restricted-extras package which restores a lot of functionality initially removed from many packages.

All the best,

Andrew

---

