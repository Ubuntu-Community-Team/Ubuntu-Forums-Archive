---
title: "command line to see if CPU supports 64-bit?"
date: 2011-03-02
forum: New to Ubuntu
---

### Post by Arikaree105 on 2011-03-02
Hi all,

there exists a command line that one can use to determine if a PC supports 64-bit or not, based on one of the CPU flags, "lm"

I've used it, neglected to write it down, and can't find it on the forum again. Argghhhh.  So, please accept my apologies, but if anyone recollects I can use your help.

thanks!

ps: Am running on an older [Dell] PowerEdge 800. My later model PE800 3.2mhz supports it, but am having issues on this older model (Meerkatt says "No Thank You").

---

### Post by ajmc on 2011-03-02
lshw

---

### Post by jerome1232 on 2011-03-02
one way would be to

```
cat /proc/cpuinfo | grep lm
```

---

### Post by Arikaree105 on 2011-03-02
Fantastic,

Thanks all!

---

### Post by sisco311 on 2011-03-02
> **jerome1232 said:**
> one way would be to

```
cat /proc/cpuinfo | grep lm
```

There is no need to use a pipe with cat | grep (or any other command):

Wrong   : cat file | grep PATTERN
Correct: grep PATTERN file

Wrong   : cat file | tr ' ' '_'
Correct: tr ' ' '_' < file

---

### Post by jerome1232 on 2011-03-02
Thanks for pointing that out, I am a bit rusty with my stuff!

---

### Post by sisco311 on 2011-03-02
> **jerome1232 said:**
> Thanks for pointing that out, I am a bit rusty with my stuff!

You are welcome!

Running cat | grep in an interactive shell is a `venial sin'. :) 

But you shouldn't use it in scripts. For example, check out: [packer]("https://bbs.archlinux.org/viewtopic.php?pid=684142").


From the thread by **bruenig** (the developer of packer):

[i]The proper way to do this is grep $file. I have seen some very new bash coders use cat file | grep, but I have never seen someone use something as astonishingly redundant and slow as echo $(cat $file) | grep.

There are dozens of other examples like this. But the real issue is the performance such shoddy coding creates.

The command yaourt -Ss python takes 56.280 seconds to execute.

The command packer -Ss python takes 4.146 seconds to execute.

Yaourt is 13.5 times slower than packer. That is pretty serious.

Other examples abound, but that gives you a sense. Yaourt is just sloooooow.
[/i]

---

