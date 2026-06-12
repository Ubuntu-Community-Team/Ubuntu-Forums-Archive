---
title: "Small note on cross platform using gcc"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by anewguy on 2009-02-19
I have an app which I set up for cross-platform use, using libusb, GTK and gcc.  It works great in Linux, and works great in Windows, but I had 1 small problem I found the solution to and wanted to pass along here in case there are other beginners like me who might run into the same thing.

In Windows, I installed the libusb-win32 package, as well as GTK for Windows, mingw and msys, the last 2 to provide a unix-like command line environment and access to gcc to compile and link.

In Windows, an application in C or C++ (probably other languages that I don't know as well) require winmain() in place of main() so that the Microsoft compilers know to create a windowed application - with main() it assumes a command line application.

Well, my cross-platform application would run as a GTK window, but there was always another window in the background.  It turns out that this winmain() versus main() thing holds true in another context when using gcc in place of a Microsoft compiler.  You need to add -mwindows to the gcc line for it to generate a windows-based application in place of a command line application in Windows.  This addition got rid of the extra window that I had with my application.

Maybe this will help someone else.....

Dave :)

---

