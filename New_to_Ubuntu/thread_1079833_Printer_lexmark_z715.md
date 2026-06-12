---
title: "Printer lexmark z715"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by chmbrs on 2009-02-24
hello forum.  

im running a version of linux mint and i need some help installing my printer. since mint is built from debian, as well as ubuntu, its almost the same thing which is why im in this forum. 

anyway i tried a couple drivers and guides with no success. my printer is detected but it doesnt print.

any suggestions???????? thanks

---

### Post by halitech on 2009-02-24
typically lexmark printers are paperweights in linux (there are a few exceptions but not many). you could try the drivers for the z600 as per these instructions

[http://ubuntuforums.org/showthread.php?t=49714](http://ubuntuforums.org/showthread.php?t=49714)

---

### Post by chmbrs on 2009-02-24
thanks for quick reply. unfortunatelly those are one the instructions i followed with no result. when i put 

tail -n +143 z600cups-1.0-1.gz.sh

in the terminal it went crazy and started showing some crazy symbols and numbers. it was very weird. i hit ctrl+c and it wouldnt stop. finally it finished doing crazy stuff and terminal was back to normal. 

i tried few other instructions and all commands worked untill the last one said: command not found 

the command was:    

cd /etc/init.d/cupsys restart

and it was the last command from about 8.

---

### Post by llamabr on 2009-02-24
The full code was:

```
tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz # the sh script is broken for newer systems
```

I'm not sure the driver for the 600 will work for you, but you could at least try doing the command correctly to find out.

---

### Post by chmbrs on 2009-02-24
oooops????????!!!!!!!!!!!!!!! thanks ill try that and post outcome

---

### Post by chmbrs on 2009-02-24
ok i did everything again. 

the following command:

/etc/rc2.d/S19cupsys restart

produces this outcome:

bash: /etc/rc2.d/S19cupsys: No such file or directory

---

### Post by halitech on 2009-02-24
try 
```
sudo /etc/init.d/cupsys restart
```

---

### Post by chmbrs on 2009-02-24
but everything else shows that printer is connected and printing but its not

---

### Post by chmbrs on 2009-02-24
same thing command not found

---

### Post by llamabr on 2009-02-24
You put:

```
sudo /etc/init.d/cupsys restart
```

actually, I think it's

```
sudo /etc/init.d/cups restart
```

Try that, and report back.

---

### Post by chmbrs on 2009-02-24
that worked. 

* Restarting Common Unix Printing System: cupsd                         [ OK ]

however my printer still doesnt work. i selected z600 driver. 
in printer properties it says:
 Idle- Communication was lost. Please check your printer and connections.

everything connected good. thanks for your help

---

### Post by chmbrs on 2009-02-24
if i use x700 driver it says same thing

---

### Post by chmbrs on 2009-02-24
for some reason a process gs suddenly started runnig my cpu to 100% i had to kill it. printer still doesnt work. any other suggestions. thanks for all the help fellas!!!

---

### Post by llamabr on 2009-02-24
I never thought it would work, since that's the driver for a different printer.

This is not an absolute beginner problem.  You might try taking it to the appropriate forum.  

But lexmarks are generally very poorly supported in linux.  Note that this is lexmark's (not ubuntu's) fault, as releasing the driver source would allow us to develop it for you.

---

### Post by chmbrs on 2009-02-24
no blame on linux... lamaxmark sucks. which forum should i place this in????????????????????????????????

---

### Post by llamabr on 2009-02-24
which forum should i place this in

I'm sure there's a printer forum up there.

I'm not hopeful, though.  Printers have always been a problem, and Lexmark is at the top.

---

### Post by chmbrs on 2009-02-24
thanks buddy. you've been a great help. i appreciate it. thanks llamabr & forum

---

### Post by boblizar on 2011-11-07
not to beat a dead horse, or drag up dead orphaned threads, but another forum suggests gimp print for a z715, after a little digging i find the projects dead, and renamed to gutenprint...  synaptic gimp-gutenprint and some things around it...  ijsgutenprint looks like foomatic-db is required for foomatic-db-gutenprint and that wants to purge ubuntudesktop....

i have seen solved threads of this issue on other forums so i do know the problem is solvable, just a matter of what hoops need to be jumped through

some notes on my dead horse beating.....

[http://downloads.lexmark.com/downloads/cpd/CJLZ600LE-CUPS-1.0-1.TAR.gz](http://downloads.lexmark.com/downloads/cpd/CJLZ600LE-CUPS-1.0-1.TAR.gz)

---

