---
title: "no SDL library"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by mrbiggbrain on 2009-05-20
SO iv been trying to compile an emulator (mupen64) on my PS3 (becuse both my 64s dont like me much lately. 

so i cd isnto the directory (mupen64...somthing or another)
```

./configure
```

and it tells me i need to get SDLlib, so i

```
sudo apt-get install sdllib1.2-dev
```

and install the library, then i once again run

```

./configure
```

and it blatantly says 

```
*** No SDL library could be found!
```

what do i need to do to get this library going, and please remember im running on a PPC processor

---

### Post by Mornedhel on 2009-05-20
You didn't get any errors after your apt-get command ?

The usual package naming convention says it ought to be libsdl1.2-dev, not sdllib1.2-dev.

---

### Post by mrbiggbrain on 2009-05-20
> **Mornedhel said:**
> You didn't get any errors after your apt-get command ?

The usual package naming convention says it ought to be libsdl1.2-dev, not sdllib1.2-dev.

i apologize, that was my bad, i didnt take the information right from the console, it was as you said, i also did build-essential... should it be installed, heres the full error

```
nick@ubuntu:~/mupen64_src-0.5$ sudo ./configure
Found a working c compiler (gcc).
Checking SDL...
./config.temp: 3: syntax error: "(" unexspected
*** Couldn't find a working SDL library
```

---

