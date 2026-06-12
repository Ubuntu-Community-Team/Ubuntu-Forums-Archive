---
title: "Creating a launcher?"
date: 2010-01-27
forum: New to Ubuntu
---

### Post by tsiliman on 2010-01-27
Hello. I'm trying to create a launcher, that will contain three different commands. The commands are the following:
xcalib -green 1.000 0.0 40 -alter
xcalib -blue 1.000 0.0 40 -alter
xcalib -red 1.000 0.0 40 -alter

I want them to be executed at the same time, in order to have the ability to control my laptop's screen brightness. The launcher works if the command is only one. How could I combine them?
Totally beginner. 9.10 version used.
Thanks!

---

### Post by lotharmat on 2010-01-27
Could you not put them in a script and then attach the script to a launcher?

Do a search for "simple bash script Ubuntu" in google - there are some fantastic tutorials out there!

Hope it goes well.

---

### Post by 311005901 on 2010-01-27
[I]In the command section of the launcher preferences, make them execute one after another by adding the "&&" connector. Try
```
xcalib -green 1.000 0.0 40 -alter && xcalib -blue 1.000 0.0 40 -alter && xcalib -red 1.000 0.0 40 -alter
```
[/I]
Scratch that. Didn't work... Sorry.

---

### Post by tsiliman on 2010-01-27
I guess I could. But, isn't it possible for the launcher to handle more than one commands at the same time, at the same line?

---

### Post by tsiliman on 2010-01-27
No. The && thing does not work.

---

### Post by sisco311 on 2010-01-27
Try:
```
sh -c "command1 && command2"
```

---

### Post by tsiliman on 2010-01-27
> **sisco311 said:**
> Try:
```
sh -c "command1 && command2"
```

Yeap! This one works just fine. Thank you guys!

---

### Post by sisco311 on 2010-01-27
> **tsiliman said:**
> Yeap! This one works just fine. Thank you guys!

Cool!!!

Please mark your thread as [SOLVED] by selecting **Mark this thread as solved** from the [color="Red"]Thread tools[/color].

---

