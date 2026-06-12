---
title: "how to compile source c codes not made for linux"
date: 2010-02-22
forum: New to Ubuntu
---

### Post by anantaacharya on 2010-02-22
I have to use an old but still very popular software. But unfortunately, it only has installation instruction and installation file for following 3 OS.

PC Compatible Running DOS
Sun SPARCStation Running SunOS
Apple Macintosh Running A/UX


 I also have the source codes written in C. Can I make a peace of software using those C files in ubuntu?? if yes how to?? 

remember that I have looked into many forums and almost of them have instruction for compiling the source code written for linux and no binary files. But I am talking about making from scratch I have 5-6 .c file and 1 or 3 .h file. Thats all I have in source code.

Thank you,

Any help is appreciated

---

### Post by Bradtek on 2010-02-22
Do you really think "Absolute Beginner Talk" the right place for this question ? :confused:

---

### Post by nikhilbhardwaj on 2010-02-22
yes ubuntu has a c compiler
and you could write your own software from scratch
you might want to read about gcc(gnu compilers collection)
and yes
the programming talk would definitely be a better place to post related questions

---

### Post by ankspo71 on 2010-02-22
What's the name of the software? Maybe it will already work in linux with the help of wine or any of the emulators. (see dosbox or dosemu in synaptic package manager).

---

### Post by biswajitLinux on 2010-02-22
If you want to compile the c code in ubuntu before compile you have to check wheather gcc compiler is installed or not .
following below steps to check gcc installed or not:
Go to system->prefrences-> synaptic package-> type the gc in serach press enter
then u install :
 
[COLOR=darkorange]open terminal->type sudo apt-get install gcc presss eneter[/COLOR]
after that open the terminal [COLOR=orange]-> type gcc filename of c press Enter[/COLOR]
[COLOR=orange]-> type ./a.out (where a.out store the output of c code)[/COLOR]
 
[COLOR=orange]-> display the out put.[/COLOR]
:D:Dhappy ????????????????
for more information visit [www.linux.com]("http://www.linux.com") and email me [EMAIL="biswajit_nit22@yahoo.com"]biswajit_nit22@yahoo.com[/EMAIL]

---

### Post by biswajitLinux on 2010-02-22
i think this will be very helpfull

---

### Post by lavinog on 2010-02-22
> **anantaacharya said:**
> 
PC Compatible Running DOS
save yourself the trouble and use dosbox

---

### Post by ad_267 on 2010-02-22
This isn't really a question that can be answered simply without having someone sitting at your desk and trying to get it to work themselves. I assume this is a proprietary piece of software and you can't post the code here?

You'll probably have to just learn about using gcc on linux and try to compile the code yourself. If there are any problems you can come back here and ask them specifically but it's impossible to say what might be a problem. If it works on DOS, SunOS and A/UX then it should be fairly cross-platform and it should't be too hard to get running.

You may have issues if it requires certain libraries that aren't available for Linux or it could require old versions of those libraries. If it's only 5 or 6 .c files then it's hopefully not too complex and should be straightforward to compile.

---

### Post by anantaacharya on 2010-02-22
Thank you everyone for help, 

First of all, sorry for posting in wrong place, but I still got help:D, 

I got quick solution by using wine emulator ( as I got 32 bit version for that too), dosbox could not help me but I think thats error in the program itself. 

compiling myself to make it linux ready may be interesting thing and would do it later when I have time.

Thank you great ubuntu community I will be seeking help whenever I am in problem

---

### Post by lavinog on 2010-02-23
What is this software, maybe someone can compile it.

---

