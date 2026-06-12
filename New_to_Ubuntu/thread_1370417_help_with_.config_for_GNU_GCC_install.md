---
title: "help with ./config for GNU GCC install"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by alexkaz on 2010-01-02
Dear Community, 
I am a newbie who just installed ubuntu 9.1 and like it. 
My objective is to have a c, c++ compilers on a Linux platform for school. 

Can anyone help troubleshoot my ./configure errors?



1. What directory should the files be extracted into? ( is usr/bin/src the right one?)

2. When trying to implement ./configure ,I receive the following error: 
'configure: error: cannot find sources (move-if-change) in . or .. '

How can that be corrected?

3. the actions preceding this error were the following. 
step A. Download GCC 4.4.2 from GNU mirror to download folder on Ubuntu Desktop
step B. extracted files into  home/myname/gcc/srcdir
step C. attempted . /cofigure and sh ./configure with same error (cannot find source).
step D. used Synaptic Package Manager  and implemented the sections filter to find development tools, and unpacked all gcc and g++ packages. I reviewed every section and selected all packages related (but no guarentee I got all of the files needed)
step E. entered sudo apt-get -s install gcc, entered my [sudo] password and received the following response: 
reading package lists... Done
Building Dependency tree
Reatind State information .. .Done
gcc is already the newest version. 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 

Step F: I double checked and affirmed the build-essential package was installed. 

Step G: observed those packages installed via Synaptic were located under /bin/usr/src, and the other root directories, i.e. /etc ; /dev

Step H: at the prompt, if I enter gcc, the response is no input files, if I enter g++, the response is g++: no input files. 

Any clarifications or suggestions. 
I know the manual installation instruction steps are ./configure, then make, then make install, 

Thanks for any suggestions and help anyone can offer.

---

### Post by The Cog on 2010-01-02
I think you're trying to install things the hard way. Whenever I install the GCC, I just use this command, which brings in the pre-packaged compiler and all needed support files:
> sudo apt-get install build-essential
after which cc, gcc, g++ etc all seem to work fine.

---

### Post by KIAaze on 2010-01-02
> **alexkaz said:**
> 
Step H: at the prompt, if I enter gcc, the response is no input files, if I enter g++, the response is g++: no input files. 


Your problem is not installing or configuring gcc and g++ (you already did by installing build-essential). Your problem is using them.

For a quick introduction to using gcc and g++, see here:
[http://pages.cs.wisc.edu/~beechung/ref/gcc-intro.html](http://pages.cs.wisc.edu/~beechung/ref/gcc-intro.html)

---

### Post by alexkaz on 2010-01-02
Cog, thanks for the suggestion to use the sudo apt-get install build-essential. 
The results of that cmmd sequence were: 
reading package list ... Done
Building Dependency tree
Reading state information... Done
build-essential is already the newest version.
build essential set o mannually installed. 
The following packages were automatically installed and are no longer reuqired: 
libalut0.......
0 upgraded, o newly installed, 0 to remove and 0 not upgraded. 

So it looks like I'll follow up with the suggestion from KIAkaze to look at the gcc intro. 

Thanks for your response (I have to admit, I am still confused whether the gcc and g++ builds were done automatically through the Synaptic, the command line entires of ./configure or the apt-get commands that were entered before posting to the forum when troubleshooting... is it possible to do the "build" via all three methods?)

Happy New Year, alexkaz

---

### Post by alexkaz on 2010-01-02
KIAaze and community, 

Having clarified the gcc and g++ were installed, I attempted to run the Hello.c code, exactly as written at [http://pages.cs.wisc.edu/~beechung/ref/gcc-intro.html](http://pages.cs.wisc.edu/~beechung/ref/gcc-intro.html).

The hello.c was created via gedit, put into the directory home/alexkaz/ProgramLang/CLang/hello.c
At the prompt: gcc hello.c -o output     then tried g++ hello.c -o outputcpp
the following errors suggest the libraries  are not found or I need to link the folders for my c and c++ code to an appropriate directory with the c and c++ compilers  or libraries?

the errors are: 

gcc: output: no such file or directory
hello.c.:1:22: error: isostream.h: No such file or directory
hello.c: In function 'main':
hello.c:4 error: 'cout' undeclared (first use in this function)
hello.c:4:error: (Each undeclared identifier is reported only once)
hello.c:4: error: for each function it appears in.)

when attempting to run with g++ hello.c -o outputcpp, 
the same error above occurs
g++: hello: no such file or directory. 

I recall the GNC GCC instructions said the path to the objdir must include gcc, but if the both of the command line installation methods ( asp-get -s install build-essential or the ./configure; make; makefile install) automate the configuration and the build, then when and how do we implement a mkdir gcc to create a path with gcc ?

Thanks again for any suggestions and corrections anyone can offer?

---

### Post by falconindy on 2010-01-02
Your problem is in your includes. the library is 'iostream.h' not 'isostream.h'.

---

### Post by alexkaz on 2010-01-02
oops, sorry, in my program it is typed as " #include "iostream.h"
the "isostream.h" was a typo in the posting. 

Any suggestions ?

---

### Post by KIAaze on 2010-01-02
> **alexkaz said:**
> 
Thanks for your response (I have to admit, I am still confused whether the gcc and g++ builds were done automatically through the Synaptic, the command line entires of ./configure or the apt-get commands that were entered before posting to the forum when troubleshooting... is it possible to do the "build" via all three methods?)

Happy New Year, alexkaz

Happy new year to you too! :)

The build-essential package is a "meta package", i.e. it only depends on other packages like gcc and g++. So when you install it, you will automatically install the gcc and g++ packages.
When installing packages via synaptic, aptitude or apt-get you are not "building" anything. You are just installing a package which has already been built!
This has the advantage that it's a lot faster, and easier too. :)

Building programs from source is usually only necessary for software not available in the repositories or to get the latest version.

More info:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

======================

Now back to your compiling problem:
It seems the link I gave you is a little bit out of date.
Try this:
Create a file "hello.c" containing this:
```
#include <iostream>
using namespace std;

int main() 
{
    cout << "Hello\n";
} 

```
Compile:
```
$ g++ hello.c -o hello 
```
Run the program:
```
$ ./hello 
Hello
```

Links:
A C tutorial: [http://www.iu.hio.no/~mark/CTutorial/CTutorial.html](http://www.iu.hio.no/~mark/CTutorial/CTutorial.html)
Forum programming section: [http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

---

### Post by alexkaz on 2010-01-02
great. I did get rid of one error, 
the gcc: output: file or directory not found and the g++: output:  file or directory not found. 

Is this because before trying to run g++ hello.c -o hello, I had created a symbolic link between between the folder with the hello.c and the gcc-4.4 folder (sudo ln -s Clang /usr/src/gcc-4.4) ?

When I implement the newer code by inserting the "using namespace std; " the following errors (that suggest the C standard library files are not found or installed or something) occur:
hello.c:1:20: error: iostream: No such file or directory
hello.c:2: error: expected '=', ',', ':', 'asm' or '_attribute_' before 'namespace' 
(the hello.c.:2: error goes away if I comment out  // using namespace std; 
hello.c: in function 'main'
hello.c:4: error: 'cout' undeclared (first use of function)
hello.c:4: error: (Each undeclared identifier is reported only once
hello.c:4: error: for ech function it appears in. )

How did you install your gcc and g++? seems like you're using them fine. Did you download the gnu gcc and gnu g++ from the GNU-GCC website hosted by the FSF?

Should I have a folder in the path named gcc?
Was the symbolic link between my folder that stores the .c and .cpp code  to the gcc-4.4 a good thing?

I am surprised  this is taking so long, seems like others have said they just donloaded and installed. not mentioning a "build", yet the GNU GCC webiste instructs -download-configure-build - test...

Thanks, I'm going to cry soon, being a newbie is :(

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

### Post by KIAaze on 2010-01-03
> **alexkaz said:**
> 2. The gcc and g++ would not find the gcc or g++ file until a symbolic link was created between the folder with code and the gcc-4.4.2 folder. 

I'm happy you solved your problems, but what you said there is wrong.
The messages
```
gcc: no input files
g++: no input files

```
mean you did not provide any input file like "hello.c" or "hello.cpp" on the command line. The minimum command lines would be:
```
gcc hello.c
g++ hello.cpp

```
generating executables named "a.out" (instead of "hello" when adding "-o hello")

Messages like:
```
hello.c:1:20: error: iostream: No such file or directory
```
mean that the include file "iostream" was not found.

gcc and g++ look in "/usr/include" or "/usr/include/c++/<VERSION>/iostream" by default.

If the "stdio.h" and "iostream" were not there or gcc/g++ still couldn't find them, you must have messed up your installation.
Next time, just install through the Ubuntu Software Center or Synaptic package manager like you said and all should work well. ;)

---

### Post by alexkaz on 2010-01-03
thanks for following up. 
All I know is when I used different library files (i.e. changing iostream to stdio.h for the gcc run) the program worked as gcc hello.c -o output 
then with the different library for hello.cpp, it compiled for g++ hello.cpp -o outputcpp
I also changed cout for the hello.c to printf, and kept cout << for hello.cpp version.

---

