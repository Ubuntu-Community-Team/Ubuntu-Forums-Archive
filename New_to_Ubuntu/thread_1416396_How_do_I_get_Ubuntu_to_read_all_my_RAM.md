---
title: "How do I get Ubuntu to read all my RAM?"
date: 2010-02-26
forum: New to Ubuntu
---

### Post by seventhsamurai on 2010-02-26
Hi Guys

Been noticing that although I have 3 GB of RAM in my Acer Extensa 4420, Ubuntu only reads 2 GB. The same thing is happening on an assembled Desktop where I have installed Ubuntu. The desktop PC has 4 GB of RAM installed but Ubuntu only reads 2 GB.

Is there some limitation like Windows XP where it cannot read above a certain amount or is there some hotshot fix to make it read the entire thing?

Thanks.

---

### Post by ndefontenay on 2010-02-26
Hi.

You need to install ubuntu for x64 architecture. You probably have the ubuntu x86 version at the moment.

---

### Post by seventhsamurai on 2010-02-26
both are running the x64 version

---

### Post by PaulReaver on 2010-02-26
maybe the graphics card is sharing (stealing) some of your ram.
my ati hd4250 steals 960mb

---

### Post by Peter09 on 2010-02-26
How are you checking the amount of RAM? Also - how much is seen during the BIOS boot.

---

### Post by codemaniac on 2010-02-26
To avoid wasting RAM and speed up applications, Linux uses as much otherwise
unused RAM as possible for the disc cache. For that reason, the first line of output
from "free" command that often shows little free RAM can be misleading.
Pay closer attention to the second line of output, which shows the amount of RAM
actually available for applications.

---

### Post by skymera on 2010-02-26
If you have integrated graphics, it is probably reserving system memory to use as graphic memory.

What graphic card do you have?

Post the output of 

```
 lspci 
```

---

### Post by switch10 on 2010-02-26
Where are you looking to see how much ram you have?

put this in a terminal:

```
 cat /proc/meminfo 
```

scroll to the top and it should say "MemTotal"

---

### Post by gallifrey on 2010-02-26
I have always been confused by the RAM issue myself. I have a 4GB system, and used x64 Karmic, and free -m reported 3891 MB. I am now using x86 Karmic, and free -m is reporting 3951 MB Ram!! There has to be a glitch somewhere, and I don't use PAE from the server kernel.

EDIT: Sorry. I know my comment wasn't a productive and helpful one. My apologies if it looked like I was trying to Hijack the thread!

---

