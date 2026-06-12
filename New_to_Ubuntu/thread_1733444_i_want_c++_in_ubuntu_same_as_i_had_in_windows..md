---
title: "i want c++ in ubuntu same as i had in windows."
date: 2011-04-19
forum: New to Ubuntu
---

### Post by abhishek39 on 2011-04-19
i am learning c++ i my school.
i want to use c++ in ubuntu same as i used in windows.
plz explain me step wise as i am totally new to ubuntu.
thanks for help.

---

### Post by sanderd17 on 2011-04-19
what do you mean by "same"? The same editor will probably not be possible. So you'll have to search an editor that you like.

It is also possible that they use windows specific liraries or code in your school. In that case, you should ask your teacher to teach iso C++.

---

### Post by vivek.pandey on 2011-04-19
so may be you used dev c++ or turbo c++ in windows .. right ?
see if this link helps [http://ubuntuforums.org/showthread.php?t=1711697](http://ubuntuforums.org/showthread.php?t=1711697)

---

### Post by abhishek39 on 2011-04-19
> **vivek.pandey said:**
> so may be you used dev c++ or turbo c++ in windows .. right ?
see if this link helps [http://ubuntuforums.org/showthread.php?t=1711697](http://ubuntuforums.org/showthread.php?t=1711697)

ok
let me try this..

---

### Post by Locke_99GS on 2011-04-19
If you use MS Visual Studio at school and are looking for a similar IDE, I suggest taking a look at MonoDevelop.

---

### Post by josephmills on 2011-04-19
code light or bluefish or frama-c or coqlde you can find all of these in the ubuntu software center

---

### Post by pascal_cuoq on 2011-04-19
> **josephmills said:**
> code light or bluefish or frama-c or coqlde you can find all of these in the ubuntu software center

Neither frama-c nor coqIde will do you any good to write C++. I am not familiar with code light but I guess bluefish is an acceptable programming editor (although probably nowhere near what the OP means when he says "same ... as in Windows").

---

### Post by Locke_99GS on 2011-04-19
You can write C++ programs in any editor - the IDE is only important when you want features like code completion, group/comment hiding, class presentation, whatever...

---

### Post by josephmills on 2011-04-19
> **pascal_cuoq said:**
> Neither frama-c nor coqIde will do you any good to write C++. I am not familiar with code light but I guess bluefish is an acceptable programming editor (although probably nowhere near what the OP means when he says "same ... as in Windows").

you are right sorry try code lite

---

### Post by abhishek39 on 2011-04-20
> **josephmills said:**
> you are right sorry try code lite

i hav tried codelite
but what i write these commands
as i used to write in windows
i shows some errors
while in windows it shows no errors and runs perfectly.
**_CODES_**
> #include<iostream.h>
 #include<conio.h>
 void main()
 {
 cout<<"hello";
 getch();
 }

**_ERRORS_**
> I HAVE ATTACHED A SCREENSHOT TO THIS

NOW WHAT!!!

---

### Post by Locke_99GS on 2011-04-20
Change:
```
#include<iostream.h>

```

To:
```
#include<iostream>

```

I think you also have to have main() return an int. I used to have it return void, and started returning int - I don't remember if it was a requirement or not.

---

### Post by josephmills on 2011-04-20
please take a look at this [http://codelite.org/LiteEditor/CppCheck](http://codelite.org/LiteEditor/CppCheck) hope that this helps

---

### Post by stchman on 2011-04-20
> **abhishek39 said:**
> i am learning c++ i my school.
i want to use c++ in ubuntu same as i used in windows.
plz explain me step wise as i am totally new to ubuntu.
thanks for help.

Explain the same?
You can use the same type of IDEs (Netbeans, Eclipse), and as long as you don't need C++ for Windows specific libraries you can do what you want.

---

### Post by ashickur.noor on 2011-04-20
Use codeblocks. It is a crossplatform.

---

### Post by josephmills on 2011-04-20
> **ashickur.noor said:**
> Use codeblocks. It is a crossplatform.

**EDIT**rm vmluniz

---

### Post by josephmills on 2011-04-20
could I please remove this message thank you so much

---

### Post by stchman on 2011-04-20
> **abhishek39 said:**
> i hav tried codelite
but what i write these commands
as i used to write in windows
i shows some errors
while in windows it shows no errors and runs perfectly.
**_CODES_**


**_ERRORS_**


NOW WHAT!!!

Use this:

[PHP]
#include <iostream>

using namespace std;

int main( void )
{
    char c;
    
    cout << "hello ";
    cin >> c;
    cout << "Character typed = " << c << endl;
    
    return 0;
}
[/PHP]This will do somewhat the same thing.

---

### Post by Raan03 on 2011-04-20
First we'll need to know what program you're using at school for C++? I assume Borland Turbo C (due conio)? For this, there are some equivalents for Ubuntu.

Second of all, depending on your compiler, you'll need to configure it so it 'll compile a Windows .exe file (especially for when you need to hand in some homework!) mingw can cross compile -- search documentation on google.

Looking at your code, to be able to run it in Ubuntu, I'd recommend this one:

```


#include <iostream>
#include <conio>
using namespace std;
// *.h are obsolete and can be left out.
// make sure you have that conio placed file somewhere in his include path
// this program will run fine without the conio file, as it's not used. Comment it out if you can't figure out how to put the conio.h in one of the include paths yet.
// tell him you're using the std namespace


int main()
// void main() is C-code, main should return an integer in C++
{
    cout << "hello";
    cin.get();
    // getch() is pretty sloppy C coding -- try replacing it with cin.get();
    return 0;
} 

```

** EDIT **
also make sure you've got the build-essential installed (sudo apt-get install build-essential) -- try compiling it then with "g++ -Wall <path of .cpp file> -o test"
-Wall will give you all Warnings that he will come across
-o will specify the output file

After this, try running it in a terminal (./test).

---

### Post by abhishek39 on 2011-04-21
thanks friends for your reply.
now i have understood, after reading your comments, that it is quite difficult to have same type of turbo c++ as i did in windows.
no problem, i have done my homework in my friends computer.
and I'll install windows xp. 
and use turbo c++.
thanks again.

---

### Post by wep940 on 2011-04-21
If you'd really like to use Ubuntu as well, try either setting up a dual-boot system (you'll have a choice when your computer boots to use Windows or use Ubuntu), or perhaps install Ubuntu and then install XP in a virtual machine inside of Ubuntu.  You can then run your Turbo C++ in the Windows virtual machine, and if curious, copy the code over to an Ubuntu file and try compiling it there to see what would be different.

---

### Post by deconstrained on 2011-04-21
> **abhishek39 said:**
> ...that it is quite difficult to have same type of turbo c++ as i did in windows.
That's because different API's and compilers are available on Windows, and different compilers will treat code differently when they compile, especially because not all compilers adhere well to ISO/ANSI standards. Apart from that, the language (C++) is exactly the same on both platforms.

---

### Post by wep940 on 2011-04-21
Also, you may want to look at geany as an IDE in Ubuntu.  It's seems to work pretty good, but then again most of these do.  As mentioned by another user, Code-Blocks is actually cross-platform, but that doesn't mean you can code just any old thing in it and transfer it to another OS with Code-Blocks and make it work.  Everything is library dependant, and if you are learning in a Windows C++ environment you probably going to use Windows-only libraries, especially if you are trying to do GUI'd apps.  Things like Code-Blocks work best when you use something like GTK to do the GUI'd apps as there is a Windows version of GTK as well.  I have written apps using GTK in Linux and was able to port them to Windows by adding a couple of #ifdef's to put OS-specific differences in place.

---

### Post by Raan03 on 2011-04-22
Anyway -- [here](http://en.wikipedia.org/wiki/Comparison_of_integrated_development_environments#C.2FC.2B.2B) 's a list of comparisation of different IDE's used in Linux and Windows.

If you're interested in the C++ language, may I suggest you to start out on an IDE / program that hasn't autocomplete? I know it's harder and more work to get the act together than using autocomplete, but it'll certainly benefit you on the long run.

e.g. When I started learning C++ in school, I'd make a linux-variant at home (using gEdit & g++) before making a Windows-variant in VSE. C++ programs in Windows have it slightly easier because of the libraries available. It was easier to recreate it Windows because I knew more or less how the code is typed which benefited me a lot in tests (speed advantage -- I'd type the program at least twice as fast as the Windows-only script kiddies (including error-handling) -- no matter how hard they studied for it) at school.

---

