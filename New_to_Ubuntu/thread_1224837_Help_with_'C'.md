---
title: "Help with 'C'"
date: 2009-07-27
forum: New to Ubuntu
---

### Post by Danzyg on 2009-07-27
Hello 

I am trying to learn how to program using the C language and so i bought a book that came with a version of ubuntu. I ended up just getting the newest version anyways. I am absolute begginer with Ubuntu and programming. To my question ... i cant seem to get even the simplest program to work like the "hello world" program i have look around at other threads and have read directions but nothing seems to work. Can anyone Help me plz?

---

### Post by jbrown96 on 2009-07-27
You will need to get a c compiler first. ```
sudo apt-get install build-essential
``` Then you need to write up your program. A text editor will be the best method. I recommend gedit; it's simple and installed by default. Try this hello world program, and save it as hello-world.c

```
#include <stdio.h>
int main() {
printf("hello world\n");
}
```


To run it the first thing you need to do is compile it. Open a terminal and change to the directory where you saved the file. ```
cd Desktop
``` or Documents or wherever you saved it. Then compile it with ```
gcc ./hello-world.c -o hello-world
``` the -o hello-world is the name of the executable; if you don't give it a name, then it will be called a.out. Run it with ```
./hello-world
```

---

### Post by keplerspeed on 2009-07-27
Ok, Ill see if I can get you started:

1) write the code, and save it as hello.c to your home folder. A simple hello world:
```

 #include <stdio.h>

int main()
{
  printf( "Hello World\n" );
}

```

2) Now compile the code. So open a terminal from applications>accessories>terminal and enter this to compile the program:
```

gcc hello.c

```

3) Now run your program, by entering this to the terminal:
```

./a.out

```

Ha, thanks jbrown96, beat me to it. I didnt mention build essential either so cheers.

---

### Post by Danzyg on 2009-07-27
Thanks very much i think that worked ... to make sure and to help me get the hang of it  can you walk me through another simple program ... I would very much appreciate it. :D

---

### Post by keplerspeed on 2009-07-27
When you ran the program did the terminal say "hello world" back to you?

If so, it worked. All you need to do is look in your book for some sample code, and compile as above.

---

### Post by Danzyg on 2009-07-27
this is what happened ... so i think it worked ... this may not be the right format ,but sorry i am noob. 

danzyg@ubuntu:~$ cd Desktop
danzyg@ubuntu:~/Desktop$ gcc ./hello-world.c -o hello-world
danzyg@ubuntu:~/Desktop$ ./hello-world
hello world

---

### Post by Danzyg on 2009-07-27
Thanks a lot it does work i changed the text inside so that it didn't just look like the title repeating... Time to start reading my book =)

---

### Post by Danzyg on 2009-07-27
I tried an example from my book and this came up ... can any one help

danzyg@ubuntu:~/Desktop$ gcc ./hello10.c -o hello10
./hello10.c:1:20: error: studio.h: No such file or directory
```
#include <studio.h>

int main()
{
int i;
for(i=0; i < 10; i++)
{
puts("hello, world!\n");
}
return 0;
}
```

---

### Post by occams_beard on 2009-07-27
should be <stdio.h> not "studio"

Also, when creating posts here titles like "I need help" aren't really useful. You should use a descrptive title.

---

### Post by Danzyg on 2009-07-27
ok thx for the thread advice and it works now ... thx a lot :D

---

### Post by lisati on 2009-07-27
> **Danzyg said:**
> ok thx for the thread advice and it works now ... thx a lot :D

Good luck with learning "C", feel free to continue asking questions. I'm sure there will be plenty of people available to help if you get stuck.

---

### Post by QIII on 2009-07-28
You may get a lot of "You should learn this instead ..." comments.

Disregard them.

Learn one and get it down.

Learn another.

Learn another.

Each has its upsides and its downsides for different purposes.

The main thing is to understand what you are doing and why it works in whatever language you are learning.

---

### Post by Danzyg on 2009-07-28
Thx a lot for your advice and help. I will be sure to ask any questions i have. First question =) does anyone know any good beginner C programing books. I have one but it is a little to advance.

---

### Post by jbrown96 on 2009-07-30
Not sure about basics, but the absolute best is nicknamed the "White Bible" or K&R (after the authors). It's actual title is "The C Programming Language" by Brian Kernighan and Dennis Ritche. I once asked a professor for a recommendation on a C book, and he pulled out the exact same 2nd edition from 1988 that I have today. It's a fantastic reference manual.

C is a really easy language to learn; there just isn't that much in it. That's not to say that it isn't powerful -- it is, but it's a reasonably simple language. 

I worked through the book, and I didn't have any trouble with any C that I wanted to write afterwards. The great part is that it's not overly long, which a lot of programming books tend to be. It's concise.

---

### Post by QIII on 2009-07-30
The Kernighan/Ritchie text is a pretty common standard text for learning C in US Universities.

---

### Post by OutOfReach on 2009-07-30
When I was learning C, I first started off with [this]("http://www.amazon.com/Absolute-Beginners-Guide-Other-Sams/dp/0672305100") book, it is a very good book especially for absolute beginners (hence the title), but it does not cover ALL of the language, so I read [this]("http://www.amazon.com/Programming-C-3rd-Developers-Library/dp/0672326663/ref=sr_1_1?ie=UTF8&qid=1248935794&sr=8-1") book after that which goes a lot more in depth.

---

