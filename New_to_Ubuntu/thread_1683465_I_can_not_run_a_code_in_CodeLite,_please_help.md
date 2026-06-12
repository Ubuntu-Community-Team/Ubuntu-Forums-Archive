---
title: "I can not run a code in CodeLite, please help"
date: 2011-02-07
forum: New to Ubuntu
---

### Post by harbimilan on 2011-02-07
Hi guys,
I'm new to Ubuntu, and to this forum as well.
I installed Ubuntu 10.10 3-4 days ago, and I've been playing with it since now.
And I'm an amateur program developer. So here is my question:

I installed CodeLite, and tried to write a very easy code in C, 
if required: here is my code :)

#include <stdio.h>

int main()
{
    printf("hello world\n");
    return 0;
}

(the file name is furkcdenemesi1)

when I press Run (Ctrl + F5) , I get this output in a terminal window:

[COLOR=Purple]/usr/lib/codelite/codelite_exec: 22: ./furkcdenemesi1: not found
Press ENTER to continue...[/COLOR]

what do I have to do to run my C code?

thanks in advance, and sorry for my bad english.

---

### Post by Jetso on 2011-02-07
I'm not sure if this will work in the IDE your using, but it worked in Code::Blocks. You need g++ to get this,  ```
sudo apt-get install g++
```

That might work. If not I might know something else, but I'll tell you if it comes to that.

---

### Post by AliciaTenB on 2011-08-01
Hello I am an absolute beginner to ubuntu and C++ programing. I am having the same trouble as harbimilan, I finally got a code that passed the build and I am ready to execute it. However when I go to run it a window pops up and says, 

[COLOR=Black]"[/COLOR][COLOR=Purple][COLOR=Black]/usr/bin/codelite_exec: 22: ./boxcar: not found
Press ENTER to continue...[/COLOR]

[/COLOR]
As I said, I am completely new to this, so I dont understand what Jetso said to do to fix this. Could you give me step by step instructions? Where do I but that line of code? In my program?

Thanks so much, 
Alicia

---

### Post by vincegata on 2011-08-01
Both CodeLite and Code Block have their own forums, you probably get better help over there.

Besides that I'd recommend using Qt Creator as your C++ IDE, despite its name you can use it for C++ development. The problem with CodeLite and Code Block these are "one-man-show" products created by a single or a handful of developers. First the support is limited with them, then sooner than later once you get better with C++ you will bump into some limitation in those products especially with debugging. Qt Creator on the other hand is backup up by Nokia and forums are very lively. 

A couple of months ago I was choosing a C++ IDE for Ubuntu and I ended up with Qt Creator and Eclipse, Eclipse though is too much complicated for a beginner.

Happy coding!

btw, there is a subforum for programming on Ubuntu.

---

