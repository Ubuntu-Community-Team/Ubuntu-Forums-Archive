---
title: "Ubuntu crashes when trying to burn a video dvd"
date: 2009-06-22
forum: New to Ubuntu
---

### Post by Seanzee on 2009-06-22
Ubuntu crashes whenever I try to burn a dvd.
I've uses Devede, DVD Styler, and others.
Devede and DVD Styler crashed Ubuntu.
Brasero gives me the error that it can't burn with the plugins
it currently has.
I've tried converting the .avi file to a DVD compatible format with WinFF, but that also crashed Ubuntu.

I suppose its the conversion process that crashes Ubuntu, but I don't know how to fix this. Any help is appreciated.

I am new to Ubuntu so if there is missing information to help find a solution let me know what it is or how to get it and I'll try to find it.

---

### Post by SunnyRabbiera on 2009-06-22
Hmm, what version of Ubuntu are you trying to use?

---

### Post by Seanzee on 2009-06-23
Ubuntu Jaunty 9.04

---

### Post by zvacet on 2009-06-23
Maybe try k3b.

---

### Post by Seanzee on 2009-06-23
K3B, from what I can tell, doesn't support video dvds.
Which I need because I'm trying to make a dvd to be
played in a dvd player.

---

### Post by halitech on 2009-06-23
at what point does Devede crash? I've used it successfully for ages and never had it crash. I use Devede to create a iso and then use k3b to burn it.

---

### Post by aeiah on 2009-06-23
if they're all crashing when converting from avi then they're all probably using ffmpeg. i know winff does, anyway.

launch one of them from the terminal and see what is reported when the error occurs. id do it with winff since that is probably the simplest one in terms of the tasks it's trying to complete for you.

---

### Post by Seanzee on 2009-06-23
It's not exactly DeVeDe that crashes. It's Ubuntu, but as for exactly when it crashes it depends. Sometimes it gets up to 50%, other times 15% and so on.

Ok, will do as soon as I figure out how to run a program from a terminal.

---

### Post by halitech on 2009-06-23
have you checked your cpu temps and ram? almost sounds like it could be a hardware issue

to run a program in the terminal you open the terminal and then type the name of the program

---

### Post by aeiah on 2009-06-23
> **Seanzee said:**
> 
Ok, will do as soon as I figure out how to run a program from a terminal.


applications > accessories > terminal

type the name of the program. its usually fairly intuitive. you can hit tab half way through and it will auto-complete the name. it'll just launch the program as normal, but any errors or anything will get reported in the terminal. if your whole ubuntu crashes though then that isnt much use unless you've got a keen eye and can see what it says before everything breaks. perhaps a better solution is to check the logfiles. i think you can do this easily from within the administration menu in ubuntu now

---

### Post by sadaruwan12 on 2009-06-23
Theres a very simple solution just reinstall your system that will solve most of your problems ;-)

---

### Post by Seanzee on 2009-06-23
I don't think its a hardware issue as I can leave my laptop on for as long as I like without it crashing the way it does. It'll only crash when I try to convert the .avi file to anything.

I figured out how to run from terminal, but it still crashed Ubuntu. I found the log, but what am I looking for in it?

I would like to avoid a full reinstall for a number of reasons.

---

### Post by halitech on 2009-06-23
unless something is heating up too much or using more ram then when at an idle then it might be fine. If you have the live cd, boot from it and run the memtest86+ to test the ram

---

### Post by aeiah on 2009-06-23
> **Seanzee said:**
> 
I figured out how to run from terminal, but it still crashed Ubuntu. I found the log, but what am I looking for in it?


anything that says 'error' 'segfault' or 'halt' would be a good start. you might want to open it in a text editor and do a wordsearch to make things easier. when linux shuts down, it tends to report it like: "going down for halt!". anything around that area might give you a clue as to why. of course, it could die before it has chance to manually turn its self off.

---

### Post by Seanzee on 2009-06-23
Ok, when I ran the memory test my computer had crashed again.

Maybe it is a hardware issue?

---

### Post by halitech on 2009-06-24
> **Seanzee said:**
> Ok, when I ran the memory test my computer had crashed again.

Maybe it is a hardware issue?

sounds like probably a ram issue. what kind of board and cpu do you have? When it crashes the next time, reboot immediately and go into the BIOS and check the health monitor to see your temps.

---

### Post by Seanzee on 2009-06-24
I've an HP Pavilion DV6000.
I swapped out Vista for XP,
then XP for Ubuntu.
From what I've found, this model
has an issue with overheating.

I've setup GNOME sensor applet.
GPU: 127 Degrees Farenheit/53 Celsius
ACPI: 82 Degrees Farenheit/28 Celsius

With only Opera web browser running.

I'll post with how hot it gets while
converting or burning DVDs.

---

