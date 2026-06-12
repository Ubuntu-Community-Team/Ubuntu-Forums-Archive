---
title: "compiling with free pascal(I found it)"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by baha'a on 2009-11-23
Hi guys

I'm trying to compile with fpc for about a week.(I'm using ubuntu 9.10)

and finally it worked (and I have tested it for two programs)

I'll give you the conclusion 

open a text editor (I'm using gedit)

write the program (take care of the syntax) let's say you wrote a program that prints hello world on the screen and named it HelloWorld.pas

and then save it with the extension .pas on any directory (let's say on your user directory /home/user)

open the terminal and write: fpc (for free pascal compiler) then where the program is 

in our example you'll write (fpc /home/user/HelloWorld.pas -Aas) the (-Aas) is the output parameter i.e you use it because the program has output. and don't forget it.

now you will have a resulting executable program named Hello World

you just open the terminal and run the executable i.e you write: /home/user/HelloWorld

and bingo it works.

hope this is useful.

---

### Post by RedRat on 2009-11-23
Interesting! I learned Pascal way, way back in the 70s! It was a great learning program acutually. It was supposed to teach programming for Algol but became a neat program for PCs back when. Glad to see that it still hangs around.

That being said, why Pascal? Why not C or C++? The C-programming languages are very similar to Pascal, except that you can get yourself into deeper trouble with C. Pascal does have some nice safety features in it. 

BTW, where did you get the compiler?
Oops, I just checked Synaptic and there it is!! I might give this a try. Take me back to good old days before Windows.

---

### Post by anewguy on 2009-11-24
I find this interesting as well.  Learned Pascal eons ago (as already mentioned, as a tool to Algol), and I think the last time I even made any changes to an existing Pascal program was back in the 80's sometime.  Seeing this post brought back a lot of old memories and got me curious enough I'll probably install the thing and see if I can even remember vaguely how to write a program in it now.

Thanks for bringing up old times!

Dave :)

---

### Post by baha'a on 2009-11-24
Hello!

Thank you so much for replying to my post.

I really felt so happy that I helped you remember those good memories

and I hope you enjoy pascal.

Baha'a

---

