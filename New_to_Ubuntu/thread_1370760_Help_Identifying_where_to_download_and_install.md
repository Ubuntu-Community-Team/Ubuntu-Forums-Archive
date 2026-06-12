---
title: "Help Identifying where to download and install"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by alexkaz on 2010-01-02
Hello Community, 
A newbie here, 
I have several programs to download, GCC, G++, and SVMLight to use on the Ubuntu Linux platform for school. (the university does not allow downloading to campus computers) and projects requires downloading freeware and programming in C or C++. 

When downloading, I keep the files in the Download folder. 
The question is WHERE DO YOU EXTRACT software to?
do you keep it at the username/home directory or subdirectories??
or should they be installed and built on the admin. directory? /bin/usr or /bin/usr/share or /etc or /dev.  
I suppose this is the same as asking where to you put your root directory for programming software?

Do symbolic links make the location an insignficant issue?
Yet, I'm of the understanding the software name, i.e. gcc needs to be in the path when it is called or the computer cannot find it?

Suggestions, advice, help... !!

Thanks, :confused:

---

### Post by Paqman on 2010-01-02
On Ubuntu, the first place you should go for software is to Applications > Ubuntu Software Centre. That will automatically download and install the software for you from a safe online repository.

For a more advanced software management tool, go to System > Admin > Synaptic Package Manager.

---

### Post by Cheesemill on 2010-01-02
Installing the build-essential package will get you gcc and g++
```
sudo apt-get install build-essential
```

Downloading software munually should always be the last resort for a Ubuntu system:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by alexkaz on 2010-01-02
ok, that makes things simple. 
I may need to remove, uninstall the gcc and g++ 4.4.2 from GNU and resinstall.
Is there a simple way to uninstall the program (it does not appear in any of my drop down menus and I can only find the gcc files by  cmmd prompt: locate gcc   which returns a whole list of files, yet, I can't get g++ or gcc to run a simple hello.c or hello.cpp, as the library headers like iostream.h cannot be found. 

Suggestions?

---

### Post by chuina on 2010-01-02
Giving this command will show the  installed software's cache:

```
 ls /var/cache/apt/archives/
```

thnx.

---

### Post by Methuselah on 2010-01-02
How did you install the GCC you downloaded?
If you extracted and did 'make install' there is usually a 'make uninstall' you can run to remove the program.

---

### Post by alexkaz on 2010-01-02
great, thanks... I just ran it (again) and I get positive results confirming the package: 
reading package lists... Done
Building Dependency Tree
Reading State information .. Done
build-essential is already the newest version.
0 upgraded ....

so why can't a simple hello.c or hello.cpp code be run using gcc hello.c -o output? or similiar for .cpp? 
thanks for your thoughts, any suggestions?

---

### Post by Paqman on 2010-01-02
> **alexkaz said:**
> 
Is there a simple way to uninstall the program

If they're just archives of source code (tar.gz?) that you downloaded but didn't compile then you can just delete them. 

Any pre-compiled binaries that you download through Software Centre/Synaptic/apt-get can be uninstalled using any of those same tools.

---

### Post by Cheesemill on 2010-01-02
> **alexkaz said:**
> Is there a simple way to uninstall the program

This why we use package management systems instead of downloading and installing :)

Without knowing how you installed them we can't tell you how to uninstall.

---

### Post by alexkaz on 2010-01-02
Wow.. I'm glad you're all here because it became a cluster...mess

apparently I tried three approaches to download, configure and install GNU GCC and G++. 

First: 
downloaded gcc-core.tar-4.4.2.tar.gz, then (gcc-4.4.2.tar.gz, then gcc-ada...gz, and then gcc-objc ...gz)
created a srcdir and objdir as follows: home/alex/gcc/srcdir and home/alex/gcc/objdir
extracted all packages in to srcdir
then at the terminal ran ./configure from within objdir.  (but nothing happened, except errors like, cannot find configure   or cannot find source)
so...

Second attempt: 
searched for through the extracted files, found the configure file and double clicked it. The options to run in the terminal or to run were presented so I first chose terminal, which appeared and disappeared quickly, then chose run (non-terminal). I assumed something happened, but all following attempts to implement ./configure at the cmmd prompt returned source not found or configure not found. , ...so.... 

Third  attempt: 
using Synaptic, under section filter, development, I found gcc and g++ files to install. 
so I then reviewed every section, skimmed all description and selected all that seemed appropriate and even some that didn't. 
ran the sudo apt-get install build-essential  and got postive results, even suggestions for un-needed files, which I removed through the Computer Janitor

Then trying to run gcc and g++ were error plagued until I created a symbolic link between the folder containing the code files and the gcc-4.4.2 folder. 

However, now the hello.c  and hello.cpp files generate "iostream.h" not found and <iostream> not found, yet when I enter cmmd prompt: locate iostream, I see various versions for different software packages. 

What would be the "best" next step?  if the build-essential is affirmed, shouln't the  gcc and g++ function properly and find the header and STL files?

Should it be uninstalled and re-installed?

thanks for your thoughts to help clean up this mess and learn a lot. 

The objective is to have functional c and c++ compilers to write code and run with other freeware for class like SVM Light, and programming microprocessors and controllers via Linux C and C++ rather than WinXP and it' barriers for clean C implementation with peripherals and other code. 

:) Happy New Year, Day 2

---

### Post by alexkaz on 2010-01-02
thanks, just ran it,  and returned a list of files (most with .deb (for Debian Linux? but I'm running Ubuntu 9.1 Linux, so I thought) printed in red. 
I did find the iostream files and gcc and g++ files with the  >> locate [file]  so the iostream, gcc and g++ files are there in various directories. 
Should there be one folder entitled 'gcc' ? so when the gcc hello.c -o output is implemented the system goes to the gcc folder and then processes the request?

---

### Post by halitech on 2010-01-02
Ubuntu is based on Debian and uses the same package manager as Debian so don't be alarmed you are seeing .deb files

---

### Post by alexkaz on 2010-01-02
SOLUTIONS for GNU-GCC and GNU-G++ INSTALL: 
SOLUTIONS for GCC and G++ test script hello.c and hello.cpp. 

Thank you for everyone's assitance over some pretty naive errors (guess that's the only way to learn something new). 

A suggestion for Ubuntu is to add the simple instructions to a download and install common software posting, for specific software, i.e. GCC. 

Here are the solutions to be shared: 

1. My installation of GCC and G++ were chaotic because I coudn't get the ./configure command to work as provided by the GNU GCC Homepage that provides instructions. 
Fortunately, the Ubuntu Software Center makes downloading the software and installing it easier than the GNU Homepage Instructions. Also the Synaptic Package Manager simplifies finding  and verifying the correct package versions for the 'build'. 

Summary:  Just use the Ubuntu SW Ctr to download and install, then the Synaptic Mgr for finding the most current upgrades and explanations for the file functions. 


2. The gcc and g++ would not find the gcc or g++ file until a symbolic link was created between the folder with code and the gcc-4.4.2 folder. 

Also the failing to code the differences between hello.c and hello.cpp prevented their compilation. .c uses #include "stdio.h" and .cpp uses #include <iostream> for
printf("hello\n"); //.c version and using namespace std cout << 'hello\n'; //.cpp version.

---

### Post by alexkaz on 2010-01-02
SOLUTIONS for GNU-GCC and GNU-G++ INSTALL: 
SOLUTIONS for GCC and G++ test script hello.c and hello.cpp. 

Thank you for everyone's assitance over some pretty naive errors (guess that's the only way to learn something new). 

A suggestion for Ubuntu is to add the simple instructions to a download and install common software posting, for specific software, i.e. GCC. 

Here are the solutions to be shared: 

1. My installation of GCC and G++ were chaotic because I coudn't get the ./configure command to work as provided by the GNU GCC Homepage that provides instructions. 
Fortunately, the Ubuntu Software Center makes downloading the software and installing it easier than the GNU Homepage Instructions. Also the Synaptic Package Manager simplifies finding  and verifying the correct package versions for the 'build'. 

Summary:  Just use the Ubuntu SW Ctr to download and install, then the Synaptic Mgr for finding the most current upgrades and explanations for the file functions. 


2. The gcc and g++ would not find the gcc or g++ file until a symbolic link was created between the folder with code and the gcc-4.4.2 folder. 

Also the failing to code the differences between hello.c and hello.cpp prevented their compilation. .c uses #include "stdio.h" and .cpp uses #include <iostream> for
printf("hello\n"); //.c version and using namespace std cout << 'hello\n'; //.cpp version. 

:popcorn:

---

