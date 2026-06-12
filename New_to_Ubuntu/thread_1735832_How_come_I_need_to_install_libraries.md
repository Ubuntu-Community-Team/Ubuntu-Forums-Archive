---
title: "How come I need to install libraries?"
date: 2011-04-21
forum: New to Ubuntu
---

### Post by Awesome96 on 2011-04-21
I'm fairly new to Linux, and to installing software using packages, or compiling source code. Sometimes I need to download a library as a dependency for a package I wish to install, and if I use apt-get it does so automatically.

   Now to the question; are the software packages I install already compiled into binary, and if so, why do I need to download the libraries, shouldn't they just be needed for the compiling. If the packages are not binary, but source code that is downloaded and compiled when I run "apt-get install xxx" is it then safe to remove the libraries after installing the software?

Thanks.

---

### Post by mikewhatever on 2011-04-21
Yes, you install pre-compiled binaries with apt-get.

---

### Post by Awesome96 on 2011-04-21
> **mikewhatever said:**
> Yes, you install pre-compiled binaries with apt-get.

Then how come libraries are sometimes in the dependencies?

---

### Post by mathgeek2000 on 2011-04-21
> **Awesome96 said:**
> I'm fairly new to Linux, and to installing software using packages, or compiling source code. Sometimes I need to download a library as a dependency for a package I wish to install, and if I use apt-get it does so automatically.

Welcome to Linux. 'apt-get' along with 'Synaptic Package Manager' are two of my favorite aspects of Ubuntu. They come from the Debian heritage of the Ubuntu Distribution, if you are interested.

   > **Awesome96 said:**
> Now to the question; are the software packages I install already compiled into binary, and if so, why do I need to download the libraries, shouldn't they just be needed for the compiling. If the packages are not binary, but source code that is downloaded and compiled when I run "apt-get install xxx" is it then safe to remove the libraries after installing the software?

Short answer: the dependent libraries are exactly that, dependent. A slightly longer explanation - The applications are binaries (for example if I install 'vlc' a multimedia app, it is a binary file - already compiled) but the file makes several 'function calls' to open windows, read files, present dialog boxes and so on. 

As with Windows, MacOS, AmigaDOS and other Operating Systems these common functions are written in library files. (Windows uses the extension .DLL, AmigaDOS used .library etc.) By writing the common calls in libraries, several programs can use them, and a consistent look and feel is presented to the user, without each programmer 'reinventing the wheel.'

---

### Post by Awesome96 on 2011-04-21
> **mathgeek2000 said:**
> 
Short answer: the dependent libraries are exactly that, dependent. A slightly longer explanation - The applications are binaries (for example if I install 'vlc' a multimedia app, it is a binary file - already compiled) but the file makes several 'function calls' to open windows, read files, present dialog boxes and so on. 

As with Windows, MacOS, AmigaDOS and other Operating Systems these common functions are written in library files. (Windows uses the extension .DLL, AmigaDOS used .library etc.) By writing the common calls in libraries, several programs can use them, and a consistent look and feel is presented to the user, without each programmer 'reinventing the wheel.'

Ok. I don't fully understand. The file makes function calls, but aren't these calls just binary code when it's compiled? Or does the binary code call to execute another binary code somewhere else? Also, are the libraries binary code as well, or are they something else? I'm sorry this response isn't so collected, but I think I got my message through.

---

### Post by ClientAlive on 2011-04-21
> **mathgeek2000 said:**
> Welcome to Linux. 'apt-get' along with 'Synaptic Package Manager' are two of my favorite aspects of Ubuntu. They come from the Debian heritage of the Ubuntu Distribution, if you are interested.

   

Short answer: the dependent libraries are exactly that, dependent. A slightly longer explanation - The applications are binaries (for example if I install 'vlc' a multimedia app, it is a binary file - already compiled) but the file makes several 'function calls' to open windows, read files, present dialog boxes and so on. 

As with Windows, MacOS, AmigaDOS and other Operating Systems these common functions are written in library files. (Windows uses the extension .DLL, AmigaDOS used .library etc.) By writing the common calls in libraries, several programs can use them, and a consistent look and feel is presented to the user, without each programmer 'reinventing the wheel.'


I 'think' the library also has to do with specific programming languages - but don't quote me on that. I'm just barely learning this stuff. These other guys know much better than I do.

Here:  [http://en.wikipedia.org/wiki/Software_library](http://en.wikipedia.org/wiki/Software_library)  is an article on wikipedia about it. There is also a section in the article about "2.3.2.4 Unix-like systems" but the general stuff seems pretty educational too.
:)

---------------------

Here's another article on wikipedia that is pretty good:  [http://en.wikipedia.org/wiki/Computer_system](http://en.wikipedia.org/wiki/Computer_system)  It talks about a lot of basic stuff you may already understand but there are a couple sections near that bottom that seem to address what you're asking about. The sections titled: "Machine code" and "Higher-level languages and program design".

---

### Post by rosencrantz on 2011-04-21
Some elements are common to a number of apps and are stored in libraries.
Take for example the GTK GUI - window structures, widgets, menus, decorations etc. are common elements for a large number of apps like GIMP, nautilus... If you included all these elements in each app, your system would get incredibly bloated. So, just build on the GTK libraries.

---

### Post by 3rdalbum on 2011-04-22
> **Awesome96 said:**
> Ok. I don't fully understand. The file makes function calls, but aren't these calls just binary code when it's compiled? Or does the binary code call to execute another binary code somewhere else?

Yes, and that somewhere else is the library :-)

Exactly the same happens with Windows, but application developers distribute all the libraries with their programs. Result: A Windows system could end off with a dozen different copies of the same libraries, scattered everywhere, maybe all different versions of the same libraries. Some libraries might have security problems, and you'd have to depend on the program developer to issue a new version of their program in order to fix the security flaw.

On Linux however, you have the library in one place for use with all programs, and you only need your distribution to update the library if there's a security flaw.

---

### Post by Locke_99GS on 2011-04-22
The libraries are actually dynamically linked, rather than statically linked. The linking process happens AFTER the code has been compiled into binary objects. 

With statically linked libraries, the objects are linked together into a single binary - when function calls are made that need to be passed to the library, it passes it internally, since the objects have been linked together. There is a downside to this though, when a small bug is found in a library function, the programmer fixes this then has to recompile and re-link the program. If all the libraries are statically linked, then one small change requires you to replace the entire program.

For dynamically linked libraries, the linker leaves the library as a seperate file, and instead links a small bit of code that lets the finished binary object call on remote objects. There are two obvious upsides to this. If said bug was limited to functions in one library and you can fix it without changing the method's prototype or adding/removing functions, then you can simply recompile the library and distribute only the library to your end-users. They replace it, and the main binary object never knows the difference.

This also allows for API's to be put in place, so that many programs can use the same library - even programs written in entirely different languages. For instance, back in the day a Pascal coder may have wanted to use a C library. He could do that, even without a proper API, by referencing the nth method prototype, assuming he knew the function's order of declaration in the library.

Consider now Adobe Flash - all it is a dynamically linked object. The browser sees the HTML indicating a flash object is to be used, it uses the Flash API to use functions from that library. Because of this method, Flash does not have to be compiled INTO the browser, nor does it have to be a separate application. Many, many, many programs use this style of programming. 

```
locke@cerberus:~$ sudo find / -name *.so | wc -l
5550

```

5550 libraries on my system. That'd make for a lot of software bloat if every program that shared any of those had to compile in it's own copy.

---

### Post by Awesome96 on 2011-04-22
Ok. So these libraries, are they binary or source code?

---

### Post by frup on 2011-04-22
They are binary.

---

### Post by Awesome96 on 2011-04-22
OK. So lets see if I got this.

When I install packages, they include pre-compiled software. This software sometimes need to use functions, so, even though it's binary, it can call other software in binary form. When many programs use the same functions, these functions are put into a library?

---

### Post by frup on 2011-04-22
Pretty much.

---

### Post by ClientAlive on 2011-04-22
> **Awesome96 said:**
> OK. So lets see if I got this.

When I install packages, they include pre-compiled software. This software sometimes need to use functions, so, even though it's binary, it can call other software in binary form. When many programs use the same functions, these functions are put into a library?



I don't know a lot about Linux but the idea I've gotten about it is it's like they break things up into more than one piece of (software?). They figured out what things are common to multiple apps and let all those apps get what they need from the one source, the library. This way the apps themselves are lighter and things are not duplicated on the system. I think there is also an advantage to a system being designed like that when it comes to updating.

By the way - looking at the x window system and how it works is a great way to learn about this kind of design concept.

:D

---

### Post by Vaphell on 2011-04-22
if you run premade binary file, all you need are required libraries in a binary form, ready to run. But if you want to compile stuff yourself, you need header files which are like a menu in a restaurant - they describe precisely what functions from libraries you can 'order'. Compiler checks if your code uses library functions properly and incorporates calls to them in the binary file.
In package manager you can find plenty <library_name>-dev packages - they provide these header files required if you want to write your own programs or compile from source.

---

### Post by ClientAlive on 2011-04-22
> **Vaphell said:**
> if you run premade binary file, all you need are required libraries in a binary form, ready to run. But if you want to compile stuff yourself, you need header files which are like a menu in a restaurant - they describe precisely what functions from libraries you can 'order'. Compiler checks if your code uses library functions properly and incorporates calls to them in the binary file.
In package manager you can find plenty <library_name>-dev packages - they provide these header files required if you want to write your own programs or compile from source.


Wow! That is so cool to learn that! Thank you for sharing. Sorry Awesome96 but I'm also learning from this. 

Dude! Vaphell! I think what you just said gave me enough of an understanding that I could actually compile something myself if I wanted to. At least I understand the concept of what is needed and what you are trying to do when you compile something. Thanks Vaphell!

Jake

---

