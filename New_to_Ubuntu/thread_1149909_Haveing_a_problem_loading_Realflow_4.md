---
title: "Haveing a problem loading Realflow 4"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by aas452 on 2009-05-05
I am having a problem with launching Realflow, I have been posting to the realflow forum where I found a HOW TO installer, but the issue is that it is for for Fedora, and seems like I am getting error hile following fedoras steps.

[HTML]http://www.realflowforum.com/view_topic.php?pid=25261#p25261[/HTML]



The error I encounter is where I try to launch realflow


```
astanco@VoXEL:~$ realflow
/usr/local/realflow/lib
/usr/local/realflow/bin/realflow.bin: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory
astanco@VoXEL:~$ 

```

I search for libpthread.so.0 and it is located in two directories /lib32 and /lib64 , but the error presides.

Can anyone lend a hand??

---

### Post by Didius Falco on 2009-05-05
From this FAQ at the RealFlow site:

[http://www.realflow.com/faqrf/faq.php?category=14](http://www.realflow.com/faqrf/faq.php?category=14)

> [COLOR=#ff6600]4. Why do I get a "... libpthread.so.0: cannot open shared object file..." message when I try to run RealFlow in Linux?[/COLOR]In some Linux distributions (when this message shows up every time you run RF in GUI mode) you have to hack the "realflow" launching script. The file is placed in the RF installation folder under the "bin" folder. Just edit the file with any ASCII editor and comment the line "setenv LD_ASSUME_KERNEL 2.4.1" located near the end of the file. To comment out the line just type a # (hash) character at the beginning of the line.


I hope it helps...

---

### Post by aas452 on 2009-05-05
Awesomenesss Dude, great post, that worked wonders!!

---

### Post by Didius Falco on 2009-05-05
Glad it helped. I don't know Diddley about RealFlow, but I'm a pretty good Bo with a Google.  :guitar:

---

### Post by aas452 on 2009-05-05
haha, awesome dude, thanks again.

---

