---
title: "Writing C++ with Vim"
date: 2011-09-01
forum: New to Ubuntu
---

### Post by Tinker Tantrum on 2011-09-01
Hello Ubuntuer's (if that's even a word).

I want to learn C++  using the Vim. Which compiler would be best ? Any built-in commands to compile automatically? Any general advice would be helpful.

---

### Post by ubudog on 2011-09-01
This looks like a good guide for getting started with C++, and has some information about compilers.

[http://www.cprogramming.com/tutorial/lesson1.html](http://www.cprogramming.com/tutorial/lesson1.html)

Check this out to tweak your Vim setup to more suit C++ programming:

[http://www.derekwyatt.org/vim/working-with-vim-and-cpp/](http://www.derekwyatt.org/vim/working-with-vim-and-cpp/)

Let us know if you need any help, and I also recommend checking out the Programming subforum of the Ubuntu Forums, located here:

[http://ubuntuforums.org/forumdisplay.php?f=310](http://ubuntuforums.org/forumdisplay.php?f=310)

Enjoy!

---

### Post by robgraves on 2011-09-01
I have done this before. You obviously need vim, but i use g++ to compile the program.  So to use a hello world example from my terminal I typed:

         $ vim helloworld.cpp

then in vim, i type "I" to enter text and wrote the program as follows:

```
#include <iostream>
using namespace std;

int main () {
        cout << "Hello World!" << endl;
        return 0;
}



```

then i hit ESC to enter command mode, then Shift + ZZ to save and quit and then to compile it i enter in the terminal:

          $ g++ helloworld.cpp -o helloworld

if there were no errors it will give you your prompt back then just run the program from terminal:

          $ ./helloworld

and it outputs:
Hello World!

Voila!

---

### Post by ubudog on 2011-09-01
Great example robgraves!

---

### Post by robgraves on 2011-09-01
Thank you, ubudog!

By the way, if you need either vim or g++ it's

     $ sudo apt-get install vim g++

8-)

---

### Post by MG&amp;TL on 2011-09-01
Vim isn't newbie-friendly. (my apologies if you're not a newbie :oops:). Try gEdit or nano as a text editor instead. You can still use g++, or any other command-line compiler of choice.

To use gEdit:

Make a source file. Double-click. Write code (as given above ;)  ). click "SAVE". close. Enter command line. "g++ -o Myprog Mysourcefile.cxx"

to use nano:

from command-line, type, "nano Mysourcefile.cxx" and edit with the arrow-keys. then hit Ctrl+X and type Y to save changes, then edit filename (if required) and hit return. Compile with g++ as above.

Both of these support syntax highlighting, indentation, etc, whereas to my knowledge, Vim/Emacs don't. I don't know if this is helpful in anyway, but I think it could be.

[SIZE="1"]Just a minor correction: it's 'the vim text editor, or 'vim' not 'the vim'-or at least in popular linux culture it is so.[/SIZE]

---

### Post by Tinker Tantrum on 2011-09-01
robgraves that was excellent! It works too! Yes I am a newb and Vim isn't friendly to me.. but then again, my girlfriend wasn't friendly to me in the beginning either. hehe.

---

### Post by ubudog on 2011-09-01
> **Tinker Tantrum said:**
> robgraves that was excellent! It works too! Yes I am a newb and Vim isn't friendly to me.. but then again, my girlfriend wasn't friendly to me in the beginning either. hehe.

Cool!

:lolflag:

---

### Post by anewguy on 2011-09-01
If I might suggest, vim isn't exactly a beginners editor.  Perhaps you should consider one of the IDE type environments for Linux - they usually have an editor either built in or linked in, and they have things like the build built in so you can see the errors in an error box and modify your source on the same screen, etc..  Similar to IDEs like you might see on Windows.

Dave ;)

---

### Post by robgraves on 2011-09-02
BTW, for C++ i use codeblocks as my IDE, when i use an IDE...lol

---

### Post by ubudog on 2011-09-02
> **robgraves said:**
> BTW, for C++ i use codeblocks as my IDE, when i use an IDE...lol

Me too.

---

### Post by MG&amp;TL on 2011-09-02
I never use an IDE. But I DID use Code:Blocks ;)

---

### Post by TeoBigusGeekus on 2011-09-02
Prefer gvim instead of vim - support for copy/cut and paste from/to other apps.
Print this cheat sheet and google is your friend.

---

### Post by ubudog on 2011-09-02
Yes, you can find pretty much anything you want to know about programming from Google.

---

### Post by robgraves on 2011-09-03
> **ubudog said:**
> Yes, you can find pretty much anything you want to know about programming from Google.

Or almost any other subject for that matter...lol


BTW...my 100th post...woot! woot!

---

### Post by jzjavez on 2011-09-03
Vim isn't newbie-friendly. (my apologies if you're not a newbie ). Try gEdit or nano as a text editor instead. You can still use g++, or any other command-line compiler of choice.

To use gEdit:

Make a source file. Double-click. Write code (as given above  ). click "SAVE". close. Enter command line. "g++ -o Myprog Mysourcefile.cxx"

to use nano:

from command-line, type, "nano Mysourcefile.cxx" and edit with the arrow-keys. then hit Ctrl+X and type Y to save changes, then edit filename (if required) and hit return. Compile with g++ as above.

Both of these support syntax highlighting, indentation, etc, whereas to my knowledge, Vim/Emacs don't. I don't know if this is helpful in anyway, but I think it could be.

---

### Post by ubudog on 2011-09-03
+1 for Code::Blocks, it's pretty newbie friendly, I'm using it right now to learn C++.

---

### Post by Tinker Tantrum on 2011-10-27
I use CodeBlocks as well, however, I would like to mimic the codeblocks environment in VIM i.e. auto spacing with brackets; one touch compile/linking etc. Its been a project in itself so far.

---

