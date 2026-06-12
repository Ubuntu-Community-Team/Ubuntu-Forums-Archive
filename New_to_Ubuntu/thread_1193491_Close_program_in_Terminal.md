---
title: "Close program in Terminal?"
date: 2009-06-21
forum: New to Ubuntu
---

### Post by Amadameus on 2009-06-21
Hello everyone. First of all, this forum is excellent and I've been happily lurking for quite some time - there are a lot of answers on here!

**Here's the problem:**
---I am running Linux KeyLogger in Terminal and the program runs correctly, without any error messages for either my keymap or the output file.
---Despite this, after several hours of using the computer, I still find nothing in the output file!
---My friend suggested that the program only dumps into the output file when the program is closed. 
------Killing the process (by closing Terminal) does not cause it to dump.
------I am unable to make further commands in the Terminal window because the standard [COLOR="Green"]**_username_@_computer_:~$**[/COLOR] is not present.
---Because of these two problems I am unable to confirm when LKL dumps its data into the output file.

In any case, I can get LKL to work, but I can't get it to actually DUMP anything!

Does anyone else use LKL, and if so have they had this problem? I would also be quite open to any other suggestions about other keylogging programs that may have a better interface.

Thanks in advance!

---

### Post by Azrael3000 on 2009-06-21
maybe it works if you do not use the default kill but rather the standard quit signal.
According to kill manpage you would do this by
```
sudo kill 123 #pid
```
where you obvioulsy replace #pid by the corresponding number.
hth

---

### Post by Metallion on 2009-06-21
This isn't a solution for your problem at hand but I thought I'd just mention how you can get your username@computer:~$ back.

First hit control+z to freeze the program and get your prompt back.
Now type bg to continue running the program in the background while retaining your prompt.

I hope it's helpful.

---

### Post by Amadameus on 2009-06-22
Azrael: I can't find the program's #pid because it hides at the kernel level... :(

Metallion: Tremendously helpful! Thanks so much!

This only raises another question, though:
1) If I run LKL in the background and am unable to find it's #pid to run a kill command, how do I kill it?

---

### Post by Bachstelze on 2009-06-22
You can find a list of all running processes with their PID's with the [font="monospace"]ps[/font] command.

---

### Post by Azrael3000 on 2009-06-22
you have to use the
```
ps -e
```
command. As far as I know that displays all processes.

---

### Post by Thingymebob on 2009-06-22
run the program with ```
lkl&
``` which will background the task allowing you to continue using your terminal and use option l to start logging and o to specify an output file e.g:```
lkl -lo keyboard.log &
```

---

### Post by billgoldberg on 2009-06-22
> **Amadameus said:**
> Hello everyone. First of all, this forum is excellent and I've been happily lurking for quite some time - there are a lot of answers on here!

**Here's the problem:**
---I am running Linux KeyLogger in Terminal and the program runs correctly, without any error messages for either my keymap or the output file.
---Despite this, after several hours of using the computer, I still find nothing in the output file!
---My friend suggested that the program only dumps into the output file when the program is closed. 
------Killing the process (by closing Terminal) does not cause it to dump.
------I am unable to make further commands in the Terminal window because the standard [COLOR="Green"]**_username_@_computer_:~$**[/COLOR] is not present.
---Because of these two problems I am unable to confirm when LKL dumps its data into the output file.

In any case, I can get LKL to work, but I can't get it to actually DUMP anything!

Does anyone else use LKL, and if so have they had this problem? I would also be quite open to any other suggestions about other keylogging programs that may have a better interface.

Thanks in advance!

If it's running in the terminal, press ctrl+c

---

### Post by t0p on 2009-06-22
Hitting **Ctrl-C** should end the program.

**EDIT:** Bah! Beaten to it!

---

### Post by Azrael3000 on 2009-06-22
sure will Ctrl+C quit the program, but will it also cause the program to dump? I doubt that.

---

### Post by Amadameus on 2009-06-25
Ctrl-C does end the program but does not cause it to dump.

I've tried everything I can to get this logger to work, I've simply given up. Tomorrow morning I'll try a new one. If I can get it to work, I'll post all relevant information here.

Thanks guys!

---

