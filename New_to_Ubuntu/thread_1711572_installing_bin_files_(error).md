---
title: "installing bin files (error)"
date: 2011-03-21
forum: New to Ubuntu
---

### Post by imight on 2011-03-21
Hello,
I've been trying to install a .bin file but it wont let me do it.
I do the chmod.... as sugested on another posts
and then run it, iam sure iam on the right directory but it gives me a error message


bash: ./fznv29.bin: no se puede ejecutar el fichero binario

in english(or close to): cant execute the binary file

Any sugestions?
btw it can be from the file but i dont think thats whats happening.
Iam running on lubuntu!

Thanks in advance,

---

### Post by oldos2er on 2011-03-21
That error could be caused by trying to run a 32-bit executable on a 64-bit system, in which case you would need to install ia32-libs to run it.

---

### Post by Info-Seeker on 2011-09-04
Hey OldOS2er, 

your answer to imight regarding executing 32bit executables on a 64bit system actually fixed an issue I was having on something else.  I spent a number of hours on the problem, and yours was the correct solution.  I tried sending you a thank you via privmsg, but it said you had them disabled, so I just wanted to say thanks here.

For anyone else reading this, before I tried to execute the binary by calling it with bash, or any other shell for that matter, typing 'bash ./binary', 64bit Ubuntu would return a 'No such file or directory' error.  When I tried to execute it by invoking the shell to call it, I received the 'cannot execute binary file' error which led me to this thread.  

as soon as I installed the ia32-libs, it worked like a champ.

so thanks again to everyone who helped solve this issue, and good luck to everyone else who encounters it.  I hope this post helps you!

Info-Seeker

---

### Post by oldos2er on 2011-09-04
Glad you got it worked out! Could you please mark the thread as 'Solved' (under Thread Tools)? Thanks!

---

### Post by Info-Seeker on 2011-09-04
it's not my thread, do u still want me to do it?  I just found this thread while trying to fix my own issue and your post made it possible...

I am new here, so not 100% sure how things work... but knowing all this if you still want me to click something, I will...

Also, there is no solved under my thread tools... so that may negate the whole thing...  though I could just be looking in the wrong place...?

---

### Post by oldos2er on 2011-09-04
Oops, my bad. Only the thread creator can mark it solved. Sorry!

---

