---
title: "The path references in Linux source code file"
date: 2009-09-07
forum: New to Ubuntu
---

### Post by hoangcuong2011 on 2009-09-07
Hi every one, thanks for reading my topic. I hope all of us can change the future of linux, or even change the world!
I've installed a new kernel version 2.6.30.5
This is a directory visting:
[IMG]http://i442.photobucket.com/albums/qq145/ferrell2011/linux_directory.png[/IMG]
there are many files .h : module.h, list.h ....
And this is a source code of module.h
[IMG]http://i442.photobucket.com/albums/qq145/ferrell2011/Screenshot-5.png[/IMG]
I don't know why in module.h:
#include <linux/list.h>
or
#include <linux/...> ( so on...)
but why not just #include </....>
Because all of this file both child of the path: ( Like fist image :)
/usr/src/linux2..../include/linux, i think the code will be (for example)
#include </list.h>, not #include <linux/list.h>
I don't know how can i write a linux kernel module cause i can't build it 
The error usually : "/usr/src/linux-2.6.30.5/include/linux/module.h:9:24: error: linux/list.h: No such file or directory"

---

### Post by KIAaze on 2009-09-13
Ok, slow down a bit: You don't know how to include header files in programs and you already want to write your own kernel module?! :shock:
Are you sure it doesn't already exist and just isn't enabled by default?

I strongly recommend doing a few [C tutorials]("http://www.google.com/search?q=c+tutorial&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a") first!

1) Screenshots are nice, but if you just want to show text/code, you can copy/paste it direcly into your post.
Use the [ CODE][/CODE ] tags for code, like this:
```
printf("hello world!\n");
```

2) Ok, now about the headers (that's what .h files are called), here's the explanation:
[http://msdn.microsoft.com/en-us/library/36k2cdd4%28VS.80%29.aspx](http://msdn.microsoft.com/en-us/library/36k2cdd4%28VS.80%29.aspx)
Under GNU/Linux, with the gcc compiler, use "-I" instead of "/I" to add include directories.
ex:
```
g++ -c -I/foo/bar -o main.o main.cpp
```
And GNU/Linux is case-sensitive, so "stdio.h" is not the same as "STDIO.H".

Using "#include </list.h>" as you suggested, would search for list.h in the root ("/") directory. Using an absolute path means it will only look in one place for the file: its absolute path.

3) You want to recompile the kernel? Here you go:
[http://www.linuxplanet.com/linuxplanet/tutorials/202/1/](http://www.linuxplanet.com/linuxplanet/tutorials/202/1/)
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

Please ask any further programming related questions here: [http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

4) Once you think you are ready to become a kernel developer (I don't think you are yet):
[http://lwn.net/Articles/160191/](http://lwn.net/Articles/160191/)
[http://kernelnewbies.org/](http://kernelnewbies.org/)

---

### Post by stderr on 2009-09-13
Hi hoangcuong2011.

I have to agree with KIAaze. I'm not even sure what you're trying to build... and no, the include directives are perfectly correct as they are.

Perhaps if you tell us at a much higher level what you're actually trying to achieve, we could help point you in the right direction, and I don't think it will involve you writing a kernel module - at least, not yet.

Quite aside from whether you're ready yet or not, I've never had a *need* to write a kernel module myself, and I've installed Ubuntu countless times on countless pieces of hardware. To quote the words of infamous Unix coder Jon "Maddog" Hall,

> "The next time you are stuck with a problem, perhaps the first thing you should do is take the time to see whether the solution already exists: You might find a secret colleague who has travelled that path before you".

---

