---
title: "C++ code and the ability to run the result"
date: 2011-04-12
forum: New to Ubuntu
---

### Post by machdohvah on 2011-04-12
OK... So I get excited to read that I would be able to see the source code of all the programs that I use... hmmm... then I try to read some the code... I actually thought to download various C++ compilers to dabble in coding in general... Then I find out that unless I download certain libraries from off the wall locations, I would never see the code run at all... Then I find that computer completely shuts down because of viruses from the libraries that I downloaded... Having to re-install Ubuntu several times only to start from scratch each time... The viruses stopped as soon as I decided to drop any thought of programming at all... Looking at my passion for programming going out the window, I gave up... I own Borland Turbo C++ for DOS and am used to its extensive help files... I feel I am locked away from ever using my skills at programming... It does not really matter as I am retired and all, but still I would like to be productive in this area... Any suggestions other than setting up my old DOS computer and sulking in a corner somewhere?

---

### Post by Locke_99GS on 2011-04-12
C++ hasn't changed much since the Borland days, except mainly things like the standard header names changing.

Examples: ctype.h is now cctype, stdlib.h is now cstdlib, math.h is now cmath, string.h is now cstring, etc...

Most nonstandard libraries in linux are easily installable via the apt system. Look for lib<libname> for binary libraries and <libname>-dev for library headers. Avoid, as much as you can at least, getting things elsewhere on the internet.


If you give us some specific examples of code you are having difficulty compiling, we may be able to see what the problem is and help.

---

### Post by seawolf167 on 2011-04-12
Just to throw in an editor thats good (besides all available text editors like Gedit, Notepad++, vi, nano, etc.) I really like Geany

```
sudo apt-get install geany
```

---

### Post by Locke_99GS on 2011-04-12
I like the MonoDevelop IDE... but don't tell anybody.

---

### Post by machdohvah on 2011-04-12
> **seawolf167 said:**
> Just to throw in an editor thats good (besides all available text editors like Gedit, Notepad++, vi, nano, etc.) I really like Geany

```
sudo apt-get install geany
```

I downloaded geany as instructed above.

> **Locke_99GS said:**
> I like the MonoDevelop IDE... but don't tell anybody.

I will try that one next. OK... so, I started with the proverbial HELLO program to see if I could even compile the thing. It promptly notified me that g++ needs to be installed. So, I installed g++4.5 and re-compiled. The attached screen shot resulted. I think what went wrong is that I needed to download g++ first and then g++4.5 over it. :)

---

### Post by machdohvah on 2011-04-12
OK... I did just what I said in the last post and it worked... One needs to first download g++ and then g++4.5 for it to work. But, I would still complain that there are no Borland like help files that clearly reveal help on each function in full detail. I noticed that there is a great deal of documentation included in the download. How do I access, for example, the proper help with examples included about the "printf" function?

---

### Post by RobikShrestha on 2011-04-12
I haven't seen any IDE providing such good help files. The only way to get help is the internet. [http://www.cplusplus.com](http://www.cplusplus.com) and so on.

---

### Post by seawolf167 on 2011-04-12
You'll probably want to get the following package as well to ensure you have everything needed for compiling source (if you intend to go that far)

```
sudo apt-get install build-essential
```

checkinstall also helps so you can easily remove installed source packages

```
sudo apt-get install checkinstall
```

As for help files, you can start [here]("http://en.wikibooks.org/wiki/C_Sharp_Programming") and [here]("http://en.wikipedia.org/wiki/C_Sharp_syntax") to look up C# commands/syntax/structure, etc.

---

### Post by wep940 on 2011-04-12
+1 on build-essential.  It includes everything for gcc as well as other things you need to really compile much.

---

### Post by machdohvah on 2011-04-13
SOLVED -- Using Geany, I am able to test for the code argument line using the terminal and accessing the same directory and issue a command like "./dump dump.cxx /p" for the program "dump" to access the command line argument to open the file "dump.cxx" with the request to paginate the result and proceed to spew results in the terminal correctly,

```
//      dump.cxx
//      
//      Copyright 2011 Michael Flower <machdohvah@gmail.com>
//      
//      This program is free software; you can redistribute it and/or modify
//      it under the terms of the GNU General Public License as published by
//      the Free Software Foundation; either version 2 of the License, or
//      (at your option) any later version.
//      
//      This program is distributed in the hope that it will be useful,
//      but WITHOUT ANY WARRANTY; without even the implied warranty of
//      MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
//      GNU General Public License for more details.
//      
//      You should have received a copy of the GNU General Public License
//      along with this program; if not, write to the Free Software
//      Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston,
//      MA 02110-1301, USA.

// DUMP.CPP

// This program displays a file in non-hex dump format by page.

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main(int argc, char* argv[]) { // access command-line arguments

  FILE *infile;
  long bytecount = 0;
  int linecount = 0, i;
  unsigned char ch;
  char yn;
  char filename[80] = "";
  bool Paging = false;

  if (argc >= 2)
    for (i=1;i<argc;i++) {
      if (argv[i][0] == '|') break;
      if ((argv[i][0] == '/') || (argv[i][0] == '-')) {
        if ((argv[i][1] == 'P') || (argv[i][1] == 'p'))
          Paging = true;
      }
      else strcpy(filename,argv[i]);
    }
  if (filename[0] == 0x00) {
    fprintf(stderr, "Input file name blank");
    exit(1);
  }
  if ((infile = fopen(filename, "rb")) == NULL) {
    fprintf(stderr, "Cannot open input file: %s.\n", filename);
    exit(2);
  }
  ch = getc(infile);
  while (!feof(infile)) {
    if ((bytecount % 64) == 0) {
      puts("");
      if (Paging)
        if ((++linecount % 24) == 0) {
          linecount = 0;
          printf("Non-Hex Dump of %s, continue?",filename);
          yn = getchar();
          if ((yn == 'n') || (yn == 'N')) break;
          puts("");
        }
      printf("%06lX   ",bytecount);
    }
    bytecount++;
    if (ch >= 16) putchar(ch);
    else putchar('.');

    ch = getc(infile);
  }
  printf("\n");
  fclose(infile);

  return(0);
}
```

---

