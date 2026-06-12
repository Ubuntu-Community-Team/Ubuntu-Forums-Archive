---
title: "Linux programming how to?"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by kernelnewbie1 on 2010-02-14
[B]Dear friends :) ,
[/B]

                    i am a wannabe linux programmer, i'm using ubuntu and wish to add a functionality like this :
the system should indicate the successful detection of usb device by a sound signal , please tell me how do i get started
 i am a beginner in linux programming , please help me.

---

### Post by Muzer on 2010-02-14
The easiest way to do that would be to write a udev/HAL (is that still used?) rule that launches a command-line media player like mplayer - how you would go about doing this I don't know. You could probably do it quite easily for hardware in general though, not just USB devices. I haven't written a udev rule in years though so I've almost forgotten how to do it I'm afraid - you could google around or wait for someone to give a better answer.

Writing an actual program (or script) to do it would be possible but it would definitely be easier to figure out udev rules - you would need to parse output from the command dmesg for mentions of USB devices being inserted.

---

### Post by beren.olvar on 2010-02-14
Linux programming is a very, very wide subject! 
For example, there are a lot of different programming languages used in a linux system nowadays. 

The first thing to know is whether you already know some programming language or not.
If you do, then tell us which one and maybe someone can tell you where to start to do get your project done.
If not, then you should first choose a programming language, learn a bit about it, and start playing around.

Linux folklore dictates that C or C++ should be your first choice. It is a very wide language in its scope and you can learn a lot by only using it, but it may get very complicated at some point. So I would recommend to start with something easier like python. With it you can write short snippets as well as big programs with user interfaces and so on. Try looking for a tutorial, there are a lot of them. Follow the simpler examples and given some time, you will be able to code your project.

have fun!

---

### Post by sandyd on 2010-02-14
> **Muzer said:**
> The easiest way to do that would be to write a udev/**HA**L (is that still used?) rule that launches a command-line media player like mplayer - how you would go about doing this I don't know. You could probably do it quite easily for hardware in general though, not just USB devices. I haven't written a udev rule in years though so I've almost forgotten how to do it I'm afraid - you could google around or wait for someone to give a better answer.

Writing an actual program (or script) to do it would be possible but it would definitely be easier to figure out udev rules - you would need to parse output from the command dmesg for mentions of USB devices being inserted.

HAL is being removed in Lucid.
[http://ubuntuforums.org/showthread.php?t=1381844](http://ubuntuforums.org/showthread.php?t=1381844)

---

### Post by thecliff on 2010-02-15
> **beren.olvar said:**
> 
Linux folklore dictates that C or C++ should be your first choice. It is a very wide language in its scope and you can learn a lot by only using it, but it may get very complicated at some point. So I would recommend to start with something easier like python. With it you can write short snippets as well as big programs with user interfaces and so on. Try looking for a tutorial, there are a lot of them. Follow the simpler examples and given some time, you will be able to code your project.

have fun!

I have to agree with starting with Python.  I do some web scripting (php, asp, etc) but just moved into programming a few months ago.  I started learning Java and have since moved to Python.  Java can be useful if you want to program for smartphones, etc but not the best when just programming for Linux.

---

### Post by MelDJ on 2010-02-15
see [http://ubuntuforums.org/showthread.php?t=333867](http://ubuntuforums.org/showthread.php?t=333867)

---

### Post by niffcreature on 2010-02-15
i think the answer to this question would be valuable to all linux noob programmers, so sorry if im hijacking.
is GTK a programming language, in the way that if you understand its language you could potentially rewrite the GUI of many applications?
i have been curious about this for a while, as i work with live audio the interface control can be very powerful

---

### Post by saif_held on 2010-02-15
Also check:
[http://ubuntuforums.org/showthread.php?t=1006662](http://ubuntuforums.org/showthread.php?t=1006662)

---

### Post by kernelnewbie1 on 2010-02-15
well i have had a course on c and c++, so that's my domain , now please tell me where to start 
thanks for response till now, 
love you linux-people:KS

---

### Post by ja660k on 2010-02-15
> **thecliff said:**
> Java can be useful if you want to program for smartphones, etc but not the best when just programming for Linux.

Java has everything, from midi to net, i've been using/learning java for 2 years and until they work out how to speed up the jvm it will be in c++ shadow, 

i agree with the learn python first crowd because it's a strictly typed language also code conventions in other languages like indenting blocks, it has a strong library and it uses alot of the C functions also 

so when you do learn C it wont be as confusing. And C is good to learn because it gives you a basis for C++, C#, objective C.
(i realize objective-C and C# dont have much to do with linux )

---

### Post by kernelnewbie1 on 2010-02-15
> **beren.olvar said:**
> Linux programming is a very, very wide subject! 
For example, there are a lot of different programming languages used in a linux system nowadays. 

The first thing to know is whether you already know some programming language or not.
If you do, then tell us which one and maybe someone can tell you where to start to do get your project done.
If not, then you should first choose a programming language, learn a bit about it, and start playing around.

Linux folklore dictates that C or C++ should be your first choice. It is a very wide language in its scope and you can learn a lot by only using it, but it may get very complicated at some point. So I would recommend to start with something easier like python. With it you can write short snippets as well as big programs with user interfaces and so on. Try looking for a tutorial, there are a lot of them. Follow the simpler examples and given some time, you will be able to code your project.

have fun!

i hav had a course on c & c++ , so dats my domain, please tell me where to start and what all to learn

---

### Post by beren.olvar on 2010-02-16
Ok, if the only thing you want to do is what you explained in the OM, then you could use inotify-cxx.
It's a library that allows you to trigger an action when the filesystem is modified.
So you could just point it towards /var/log/dmesg.log, which is the logfile that stores the relevant information coming from the kernel. Maybe someone else can help you to interact more directly with the kernel, which seems to be your goal. (Meanwhile try reading this [http://www.linuxtopia.org/online_books/linux_kernel/linux_kernel_module_programming_2.6/index.html](http://www.linuxtopia.org/online_books/linux_kernel/linux_kernel_module_programming_2.6/index.html))

You could also try doing some HAL scripting (check this post [http://ubuntuforums.org/showthread.php?t=904706](http://ubuntuforums.org/showthread.php?t=904706)), but it seems it will be replaced by DeviceKit, so I would advise you to learn how to communicate with this last one, although documentation doesn't seem very abundant.

---

### Post by kernelnewbie1 on 2010-02-19
hey linuxites !
 thank you , for ur replies , now wiith all your tips i am going to start my venture , i dont know where i am going to end but i am never going to give up , thanx again

:D "Starting is half done"

---

