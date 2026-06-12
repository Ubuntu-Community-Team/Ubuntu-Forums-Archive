---
title: "Help for compiling and installing software"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by melissawong on 2009-07-07
Hi, I'm new to Ubuntu... I'm trying to compile a tgz file. Haven't done that before so I don't know what to expect. I have followed the instructions of a few websites but I didn't get it to work. Here's what I did:

Before that, I make sure that gcc is installed by typing "sudo apt-get install build-essential"
1. mkdir /home/melissawong/src/ #create the directory and put tgz file inside#
2. tar -zxvf v_0.7.tgz #extract#
3. cd v_0.7 #open the extracted files#
4. more INSTALL #no such file or directory#
5. ./configure  #no such file or directory#
6. make # a bunch of lines came out. I think it's working but then again, mayb not#
7. su #enter root password#
8. make install #*** No rule to make target `install'.  Stop.#

Hmmm... anyone know what went wrong? Is it because of missing file? The application should be installed to /usr/local/bin. This may sound like a stupid question...but how do I open that?

Thanks in advance.
Melissa

---

### Post by halitech on 2009-07-07
what exactly are you trying to install?

---

### Post by LewRockwell on 2009-07-07
it is highly advisable to stick with what is available via the repositories

.

---

### Post by melissawong on 2009-07-08
> **halitech said:**
> what exactly are you trying to install?

It's a data analysis tool.

---

### Post by oldos2er on 2009-07-08
Can you provide a download link to it?

---

### Post by lavinog on 2009-07-08
> **melissawong said:**
> 
4. more INSTALL #no such file or directory#
5. ./configure  #no such file or directory#

this looks like the problem area
type ls and see if these files exist


> 
6. make # a bunch of lines came out. I think it's working but then again, mayb not#

usually there will be a statement at the end about exiting due to errors if there was a problem, but since there was no configure it is likely something went wrong.
> 
7. su #enter root password#

I think su is dissabled on ubuntu, use sudo instead
also, you should not see your password when you type it. (type sudo make install [press enter] then it should ask for your password) If you typed su [your password] and it was visible in plain view, someone with temporary access can view your bash_history and find your password

> 
8. make install #*** No rule to make target `install'.  Stop.#

This is also an error, likely caused by no configure

---

### Post by melissawong on 2009-07-09
[URL="http://www.ebi.ac.uk/%7Ezerbino/velvet/velvet_0.7.43.tgz"]--- link removed ---
[/URL]

---

### Post by twright on 2009-07-09
Hi,
firstly can I just warn you that generally if an application is distributed as source files this is intended for developers or hard core users so you should not be supprised if the process is less than intuitive and varies from program to program, if it is an option you should use a standard package to install.

In this case you just need to type use the make command to compile it:
```

cd ***[path of files]***
make
```

---

### Post by lavinog on 2009-07-09
The file:  Manual.pdf explains how to compile this program. It doesn't say to use configure. It also doesn't say it will install into /usr/local/bin. You will have to put it there manually if you need it to be there.
It also says you need a 64bit environment with at least 12gb of memory.

---

### Post by melissawong on 2009-07-09
> **lavinog said:**
> The file:  Manual.pdf explains how to compile this program. It doesn't say to use configure. It also doesn't say it will install into /usr/local/bin. You will have to put it there manually if you need it to be there.
It also says you need a 64bit environment with at least 12gb of memory.

Thanks everyone for the overwhelming responses. 

You're right. Because the manual says very little, I turned to other websites for help when the command line >make is not working. Just following the instructions of those websites. I'm using 64-bit and 4Gb RAM. The memory requirement is to run huge datasets which I believe has nothing to do with compiling.

---

### Post by melissawong on 2009-07-09
Oops.. I have a confession to make. I think the >make function is working all along. Only I didn't realize it. 

I found two exucutable files on the folder. I think it's the programs I'm trying to install. Now I have to figure out how to use it. Like I said earlier, I really don't know what to expect. So, please spare me!

---

### Post by twright on 2009-07-09
OK, if any mods are reading then this thread needs splitting. To rant and insult others work because of one's own limited appreciation of the work that other have given up their time to produce for free is not a valid reason to butt in on others threads. Simply quoting facts out of context to serve one's own childish political agenda is not helpful and downright rude - if you would not behave like that in real life please try and show the strange restraint online.

---

### Post by aysiu on 2009-07-09
> **twright said:**
> OK, if any mods are reading then this thread needs splitting. To rant and insult others work because of one's own limited appreciation of the work that other have given up their time to produce for free is not a valid reason to butt in on others threads. Simply quoting facts out of context to serve one's own childish political agenda is not helpful and downright rude - if you would not behave like that in real life please try and show the strange restraint online. I did some more investigating and it was pretty clear that poster was a troll, so I just moved it all to the Jail.

---

### Post by melissawong on 2009-07-09
Dear administrator,

Has this thread convince you enough to put an option for thread starter to close thread?

sincerely,
Melissa:lolflag:

---

### Post by lavinog on 2009-07-09
@aysiu: Thank you, but you timed it right when I was going to post so I almost posted on the wrong thread. 


> **melissawong said:**
> Oops.. I have a confession to make. I think the >make function is working all along. Only I didn't realize it. 

I found two exucutable files on the folder. I think it's the programs I'm trying to install. Now I have to figure out how to use it. Like I said earlier, I really don't know what to expect. So, please spare me!

What brought you to this program? What is your goal? Maybe there is a more user friendly alternative.

---

### Post by lavinog on 2009-07-09
> **melissawong said:**
> Dear administrator,

Has this thread convince you enough to put an option for thread starter to close thread?

sincerely,
Melissa:lolflag:

For future issues like this, use the report post button (located below each user name on the left: [img]http://ubuntuforums.org/images/buttons/report.gif[/img])
Leave a short message why you are reporting it like "This person is starting a flame war and is irrelevant to my problem."

---

### Post by aysiu on 2009-07-09
> **melissawong said:**
> Dear administrator,

Has this thread convince you enough to put an option for thread starter to close thread?

sincerely,
Melissa:lolflag:
No. In a case like this, the thread shouldn't be closed. This troll came in and started up a flamebaiting discussion in the middle of your support thread.

The proper action is the one I took--leave the thread open, move somewhere else the offending post and the replies to it.

---

### Post by baltadt on 2009-07-16
everything worked up to the dmesg. instead of it labeling the manufacturer it says...ndiswrapper ....couldn't prepare driver 'rt2870'
and 
ndiswrapper .... couldn't load driver rt2870:

---

