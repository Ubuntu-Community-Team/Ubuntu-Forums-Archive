---
title: "using screen in shell script"
date: 2011-08-12
forum: New to Ubuntu
---

### Post by hoxzyk on 2011-08-12
Hello,

I would just like to know how i would have a shell script execute in a different screen.

Its to run minecraft server so its like this..

```

#!/bin/sh
BINDIR="$(dirname "$(readlink -fn "$0")")"
cd "$BINDIR"
java -Xincgc -Xmx1G -jar Mineshafter-server.jar

```I thought i could just add screen -d -m like on the second line... any help would be Swell :]

---

### Post by hoxzyk on 2011-08-12
Any one???

---

### Post by ofnuts on 2011-08-12
> **hoxzyk said:**
> Hello,

I would just like to know how i would have a shell script execute in a different screen.

Its to run minecraft server so its like this..

```

#!/bin/sh
BINDIR="$(dirname "$(readlink -fn "$0")")"
cd "$BINDIR"
java -Xincgc -Xmx1G -jar Mineshafter-server.jar

```I thought i could just add screen -d -m like on the second line... any help would be Swell :]
Something like:
```

xterm -e java -Xincgc -Xmx1G -jar Mineshafter-server.jar

```

---

### Post by hoxzyk on 2011-08-12
Thats cool but ima be using CLI so wanna be able to use this kinda thing, 

[https://help.ubuntu.com/community/Screen](https://help.ubuntu.com/community/Screen)

#!/bin/sh
screen -d -m
BINDIR="$(dirname "$(readlink -fn "$0")")"
cd "$BINDIR"
java -Xincgc -Xmx1G -jar Mineshafter-server.jar


I dun get why this dont work... then again im not good at scripts...

---

### Post by hoxzyk on 2011-08-12
Its all good!!! i had it in wrong order....


```
 
#!/bin/sh
BINDIR="$(dirname "$(readlink -fn "$0")")"
cd "$BINDIR"
screen -S minecraft java -Xincgc -Xmx1G -jar Mineshafter-server.jar

```


Worked ok!

---

### Post by ofnuts on 2011-08-12
> **hoxzyk said:**
> Thats cool but ima be using CLI so wanna be able to use this kinda thing, 

[https://help.ubuntu.com/community/Screen](https://help.ubuntu.com/community/Screen)

#!/bin/sh
screen -d -m
BINDIR="$(dirname "$(readlink -fn "$0")")"
cd "$BINDIR"
java -Xincgc -Xmx1G -jar Mineshafter-server.jar


I dun get why this dont work... then again im not good at scripts...
You have to launch screen and tell it to run a command:
```

screen java -Xincgc -Xmx1G -jar Mineshafter-server.jar

```
Writing scripts isn't hard. Reading the docs carefully is :)

---

