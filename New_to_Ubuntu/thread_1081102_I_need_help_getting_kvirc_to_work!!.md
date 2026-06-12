---
title: "I need help getting kvirc to work!!"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by heidirose12345 on 2009-02-26
Okay,I realise that there are other irc clients that are more suited to ubuntu, but this is the one that I have been using for quite awhile and like a lot.

I downloaded kvirc from here
[http://www.kvirc.net/?id=releases&platform=unix&version=3.4.2&group=debian&lang=en](http://www.kvirc.net/?id=releases&platform=unix&version=3.4.2&group=debian&lang=en)

I installed it, and I assumed that it would work. I searched through my programs and couldn't find it. I think I searched everywhere.

I then typed kvirc into a terminal window and I got the output

kvirc: error while loading shared libraries: libkparts.so.2: cannot open shared object file: No such file or directory

What does this mean? And how do I fix it? I googled the error message, and got no hits :(

I'm completly new to ubuntu, though have used something similar a little at university, but it was all nicely set up and ready to go

Edit: Errrr I hope this is the right forum for this, I just kinda guessed it might be because it's probably something really silly causing the problem :P

---

### Post by Sirron on 2009-02-26
It looks like you're missing that library, you could find it and install it manually, or you could install kvirc from the repositories.

Open the Synaptic Package Manager, and search for kvirc. Set it to install, and the package manager will identify that it requires other software to be installed in order to work, and so, set that to install also.

---

### Post by heidirose12345 on 2009-02-26
nvm I got it working :P

---

