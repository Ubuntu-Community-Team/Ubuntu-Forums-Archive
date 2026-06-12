---
title: "While is booting, appears a message of missing file, What does it mean?"
date: 2011-01-30
forum: New to Ubuntu
---

### Post by saresu on 2011-01-30
**[COLOR=Red]mobprobe: FATAL'Couldn not load /lib/modules/2.6.35-25-generic/modules.dep: No such file or directory[/COLOR]**

**Is this a problem in my OS?**


My Ubuntu is 10.10 coverted to Dream Studio.

My laptop is a Toshiba Dynabook core 2 duo 2.00ghz 2Gb Ram

---

### Post by pi3.1415926535... on 2011-01-30
Hello,
It seems to be related to the kernel because of the "2.6.35-25-generic", 2.6.35-25 being the kernel version. Generally if the computer boots, and you do not notice any problems, there are not any major problems.

---

### Post by saresu on 2011-01-30
> **pi3.1415926535... said:**
> Hello,
It seems to be related to the kernel because of the "2.6.35-25-generic", 2.6.35-25 being the kernel version. Generally if the computer boots, and you do not notice any problems, there are not any major problems.
Hum.. not having problems with booting but, im having problems to run Ardour VST. are they separate things?

I dont know what exactly to ask but, Normally since Im absolute beginner, everything in Linux is a problem and confusing for me. Im going to use this laptop for "Professional Recording". Dont u think this "kernel stuff" will cause me problems on the future?

Is there a way for me to fix this? If this is supposed to be fixed?

---

### Post by pi3.1415926535... on 2011-01-31
Sorry for not being more clear, the kernel is the basis of Linux, that allows programs to run. Assuming that Ardour VST is audio software, then it is connected to the kernel to the extent all other programs are, so it could be causing a problem, though from the error, as far as I know, it seems unlikely.

---

### Post by saresu on 2011-01-31
> **pi3.1415926535... said:**
> Sorry for not being more clear, the kernel is the basis of Linux, that allows programs to run. Assuming that Ardour VST is audio software, then it is connected to the kernel to the extent all other programs are, so it could be causing a problem, though from the error, as far as I know, it seems unlikely.
Its okay...

but how can I fix it?

---

### Post by NightwishFan on 2011-01-31
It is probably a separate issue. I have had this message before and everything worked.

---

### Post by Elfy on 2011-01-31
Running vst's in ardour needs some fiddling.

I would suggest you start a thread in  [Multimedia]("http://ubuntuforums.org/forumdisplay.php?f=334") or [Studio]("http://ubuntuforums.org/forumdisplay.php?f=335") forums. Probably the Studio will be the best bet.

Keep this thread for your other issue.

---

### Post by saresu on 2011-01-31
> **NightwishFan said:**
> It is probably a separate issue. I have had this message before and everything worked.
[COLOR=DarkRed]*"It is probably a separate issue. I have had this message before and everything worked."*[/COLOR]

I have no idea what u r talking? U mean, somebody had this same problem and It worked??

Im not asking about Ardour, Im asking about this message that shows while im booting. Im asking if there is a way to fix it

---

### Post by Bluenoser81 on 2011-01-31
Check this thread out for more information: 

[http://ubuntuforums.org/showthread.php?t=1615091](http://ubuntuforums.org/showthread.php?t=1615091)

Basically, it is just a bug that has never been fixed (most likely having to do with hardware timing seems to be the consensus). After update my kernel a few times, the message disappeared, so it maybe be an issue for kernels within a specific range (e.g., 2.6.35-22 to 2.6.35-25 or something).

---

### Post by saresu on 2011-01-31
I made a mistake here... sorry for repost this
[COLOR=Black][/COLOR]

---

### Post by saresu on 2011-01-31
> **Bluenoser81 said:**
> Check this thread out for more information: 

[http://ubuntuforums.org/showthread.php?t=1615091](http://ubuntuforums.org/showthread.php?t=1615091)

Basically, it is just a bug that has never been fixed (most likely having to do with hardware timing seems to be the consensus). After update my kernel a few times, the message disappeared, so it maybe be an issue for kernels within a specific range (e.g., 2.6.35-22 to 2.6.35-25 or something).
[Bluenoser81]("http://ubuntuforums.org/member.php?u=1151740") Thank you. That's a real reply! I understand now...

I will read the thread you showed.

Thank you again

---

