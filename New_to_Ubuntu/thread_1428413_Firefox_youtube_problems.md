---
title: "Firefox youtube problems"
date: 2010-03-12
forum: New to Ubuntu
---

### Post by bonez4ever on 2010-03-12
I have the latest build of Ubuntu, which is 9.10 Karmic Kola, and I also have Fire Fox 3.5.8 and youtube videos load fine but the controls are completely unresponsive. I don't know what's wrong, but hulu works fine with controls and I have flash plug-ins if someone can help me I would greatly appreciate it.

-Bonez4ever

---

### Post by lovinglinux on 2010-03-12
Do you have 32bit or 64bit?

Use the [automated installer created by carlee](http://ubuntuforums.org/showthread.php?t=1414595). This tool  will install the best flash version according to your CPU architecture and will also attempt to remove any left-overs from previous  installations, thus helping to avoid conflicts with manually installed plugins.

For additional tips and instructions see the [COLOR="Sienna"]**Flash Optimization**[/COLOR] section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by sandyd on 2010-03-12
> **lovinglinux said:**
> Do you have 32bit or 64bit?

Use the [automated installer created by carlee](http://ubuntuforums.org/showthread.php?t=1414595). This tool  will install the best flash version according to your CPU architecture and will also attempt to remove any left-overs from previous  installations, thus helping to avoid conflicts with manually installed plugins.

For additional tips and instructions see the [COLOR="Sienna"]**Flash Optimization**[/COLOR] section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).
in case you miss the warning that I added to the front page, please click the "remove button" first...
a lot of people have made the mistake of not clicking it...

---

### Post by lovinglinux on 2010-03-12
> **carlee said:**
> in case you miss the warning that I added to the front page, please click the "remove button" first...
a lot of people have made the mistake of not clicking it...

Thanks. I didn't miss it. But I guess the users will see it when they go to your thread. I hope so :)

Anyway, I'm adding a note to my quotes. Better be safe than sorry.

Is it possible to implement the removal within the install feature?

---

### Post by sandyd on 2010-03-12
> **lovinglinux said:**
> Thanks. I didn't miss it. But I guess the users will see it when they go to your thread. I hope so :)

Anyway, I'm adding a note to my quotes. Better be safe than sorry.

Is it possible to implement the removal within the install feature?

hmmm... lets see...
I can just copy the system call functions from the removal button up to the install button. 

ill get to that sometime tomorow.

---

### Post by bonez4ever on 2010-03-13
> **lovinglinux said:**
> Do you have 32bit or 64bit?

Use the [automated installer created by carlee]("http://ubuntuforums.org/showthread.php?t=1414595"). This tool  will install the best flash version according to your CPU architecture and will also attempt to remove any left-overs from previous  installations, thus helping to avoid conflicts with manually installed plugins.

For additional tips and instructions see the [COLOR=Sienna]**Flash Optimization**[/COLOR] section of [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567").
I have Ubuntu 64-bit. I made sure I clicked the remove, however I' ve been waiting for 20 mins and the box went gray, did it freeze? I haven' t ended the program yet, tell me what to do next. 

Thanks
-Bonez4ever

---

### Post by bonez4ever on 2010-03-15
Any help, I ended the program should I click the "remove button" again or install Carlee's flash.

---

### Post by sandyd on 2010-03-15
> **bonez4ever said:**
> I have Ubuntu 64-bit. I made sure I clicked the remove, however I' ve been waiting for 20 mins and the box went gray, did it freeze? I haven' t ended the program yet, tell me what to do next. 

Thanks
-Bonez4ever
hmm....
your aparently one of the few who are having problems...

1. Count you do me a favour, and extract the program to your desktop?
then run
```

~/Desktop/adobe_flash_installer
```
watch the output

if its downloading, you get to wait for a while.
If it gets past downloading and gets stuck, post the output.
2. Are you connected to the internet?

---

### Post by bonez4ever on 2010-03-16
> **carlee said:**
> hmm....
your aparently one of the few who are having problems...

1. Count you do me a favour, and extract the program to your desktop?
then run
```

~/Desktop/adobe_flash_installer
```watch the output

if its downloading, you get to wait for a while.
If it gets past downloading and gets stuck, post the output.
2. Are you connected to the internet?
All right I' ll try that now , and Carlee I' am always connected to the internet ;).

Updates:
Uhh some sort of error here's the screen shot I honestly don't know what I did wrong, the screen shot should inform you [http://img697.imageshack.us/img697/7253/screenshotfbk.png](http://img697.imageshack.us/img697/7253/screenshotfbk.png)

---

### Post by lidex on 2010-03-16
Looks like a syntax error. Try this in your terminal:
```
cd ~/Desktop
ls
```
In that output find the full filename to use in previous commands - it needs to be exact.

---

### Post by lidex on 2010-03-16
Wait a minute, you downloaded the sourcecode. You need the third option: "adobe_flash_installer-ubuntu.tar.gz" from here:
[http://ubuntuforums.org/showpost.php?p=8872675&postcount=1]("http://ubuntuforums.org/showpost.php?p=8872675&postcount=1")

---

### Post by sandyd on 2010-03-16
> **bonez4ever said:**
> All right I' ll try that now , and Carlee I' am always connected to the internet ;).

Updates:
Uhh some sort of error here's the screen shot I honestly don't know what I did wrong, the screen shot should inform you [http://img697.imageshack.us/img697/7253/screenshotfbk.png](http://img697.imageshack.us/img697/7253/screenshotfbk.png)
your downloading the wrong file.
you should be downloading the adobe_flash_installer-ubuntu.tar.gz

---

### Post by Geoff918 on 2010-03-16
> **lidex said:**
> Looks like a syntax error. Try this in your terminal:
```
cd ~/Desktop
ls
```In that output find the full filename to use in previous commands - it needs to be exact.

Looks like it's called adobe_flash_installer-ubuntu.c my friend. perhaps you might even need to input sh and then the command. I've never run a .c script before, though. So, I'm just guessing at that part.

Maybe it needs to be compiled, would be my actual guess. Do you have gcc?

---

