---
title: "troubles installing GTK+ 2.14.7 toolkit"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by myromance123 on 2009-01-15
Okeh, I know the GTK+ has a guide on how to install it but Im stuck at a certain part and I cant find anyone else with the prob or any solutions in the guide.

 I have downloaded the gtk+-2.14.7 file and extracted it to documents. After which I run the ./configure command to install it(partially or something?) . After that Im required to run the 'make' and 'make install' commands.

 This is where I cant go any further.

```
yusuf@yusuf-desktop:~/Documents/gtk+-2.14.7$ make
make: *** No targets specified and no makefile found.  Stop.

```

Thats the error I get. What am I missing? is something supposed to come after the make command? I tried doing what the guide said but this is my first time using the make command. I tried doing it with sudo too and the same message comes up as above..

Im sorry if the solution is obvious but I really dont know what to do.
All help is appreciated, thanks :)

---

### Post by mc4man on 2009-01-15
Your probably missing any number of basic build tools and required -dev packages for the specific build.

I'd think if you ran the configure again you'll see it failed.

Are you !00% clear on why you want to install this higher version of gtk on your system? You do realize it's pretty central to the overall operation

---

### Post by myromance123 on 2009-01-15
I ran the configure again and it didnt fail, but make did.
Hmm??

  I thought that GTK+2.14.7 was a developing tool to make GUI programs, am I wrong??

 If I am then can you show me where to get the right GTK+?
Im sorry Im a bit oblivious but I want to get on the right track, thanks for your speedy reply :)

---

### Post by mcduck on 2009-01-15
No, it's not a developing tool, if you mean some kind of graphical app for building program interfaces. It _is_ a toolkit that is commonly used to create program GUIs, but for that, you'd install the gtk2-dev packages (available in Ubuntu's repositories).

GTK2 itself is already installed, most of the programs you use are using GTK2 to draw their interfaces on the screen.

(For almost every package available there's a specific developer package available, easily recognized from the package name that ends with "-dev". These are the ones needed when compiling programs etc, while the normal packages are the ones that are needed when using those programs)

If you want a graphical tool for creating GTK2 interfaces, Glade is what you are looking for.

---

### Post by myromance123 on 2009-01-15
Wow! Thanks mcduck!

 You're a life saver :)
I was gonna go off in the wrong direction, thank you :)

Off to Glade with me :D

Just a few final questions:
1. Can I program in C using Glade?
2. Is the package named Glade Interface Designer?

Thanks yet again for your answers ^.^

---

### Post by mcduck on 2009-01-15
Glade seems to have libraries at least for C++, Python and Java, probably many other languages as well.

"Glade Interface Designer" sounds correct if you install it with the "Add/Remove Programs". The package itself is likely to have some other name, "glade-gnome" looks like the right one..

I'm definitely not a programmer myself, but I've understood that you write your program separately, using which ever way you like, and only the actual GUI is created with Glade.

Probably you can get a lot better information about using Glade in the "Development & Programming"-subforum.

---

### Post by myromance123 on 2009-01-15
Thank you very much mcduck :D

 Cheers~  :P

:guitar:

---

