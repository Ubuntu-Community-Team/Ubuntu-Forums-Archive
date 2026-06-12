---
title: "Terminal pane is empty"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by gv29847 on 2009-01-20
I ran the Ubuntu 8.10 Live CD on the hardware below, and it boots. I can run all the apps that are part of the installed set, but if I run terminal it just comes up as a completely blank white pane. Any ideas on a fix?

The CD checks out OK from the CD check menu, and the hash checked out OK to. If I run the same CD on another system, terminal comes up fine.


PC is a Dell Optiplex GX110, 800 MHz Pentium III, with 512 Meg RAM, and C = 10G, D = 120 G, E = 120 G (All IDE), F = CD burner 52x read, G = 500 Gig USB hard drive. No RAID.

---

### Post by NTolerance on 2009-01-20
Are desktop effects turned on?  Can you post a screenshot?

---

### Post by gv29847 on 2009-01-20
How do I know if "desktop effects" are on? Will post screenshot but problem is the pc is in regular use under XP and it takes around 40 mins to boot under the live cd, and then I have to return it to XP - so I cannot casually do stuff under ubuntu with it. Under what exact conditions is a screen shot useful?

---

### Post by Terl on 2009-01-20
> **gv29847 said:**
> How do I know if "desktop effects" are on? Will post screenshot but problem is the pc is in regular use under XP and it takes around 40 mins to boot under the live cd, and then I have to return it to XP - so I cannot casually do stuff under ubuntu with it. Under what exact conditions is a screen shot useful?

No, the screenshot is not necessary.  I think he may have missed the fact you are running the live cd.  I can say if it really takes that length of time to boot the live cd there is something not quite right.  What kind of graphics card does the pc have?  

You mentioned that the other programs run; do they run well?

---

### Post by NTolerance on 2009-01-20
> **gv29847 said:**
> How do I know if "desktop effects" are on? Will post screenshot but problem is the pc is in regular use under XP and it takes around 40 mins to boot under the live cd, and then I have to return it to XP - so I cannot casually do stuff under ubuntu with it. Under what exact conditions is a screen shot useful?

Go to the Desktop Effects tab in System -> Preferences -> Appearance to check the status of Desktop Effects.  Try changing the setting to "off" and see what happens.  On some graphics cards Desktop Effects can cause strange artifacts potentially like what you're describing.  A screenshot could show whether this is a graphical error or possibly a software or configuration problem.

---

### Post by NTolerance on 2009-01-20
> **Terl said:**
> No, the screenshot is not necessary.  I think he may have missed the fact you are running the live cd.  I can say if it really takes that length of time to boot the live cd there is something not quite right.  What kind of graphics card does the pc have?  I see you said it is a P3, do you know the processor?

Live CD or not, a screenshot would give us more information.  Is there some "white terminal" problem going around that's common knowledge?  I want to see what it looks like.

---

### Post by Terl on 2009-01-20
> **NTolerance said:**
> Live CD or not, a screenshot would give us more information.  Is there some "white terminal" problem going around that's common knowledge?  I want to see what it looks like.

I agree but when he was describing 40 minute boot time, I figured there was more wrong...

---

### Post by gv29847 on 2009-01-20
Processor - only that it is an Intell P3 at 866 MHz
Graphics - no seperate card - whatever Dell put on their Optiplex GX110 mainboard. One source says this is "Intel Direct AGP embedded in the Intel 810e chipset" with 4 M RAM.
Applications - I have seen no other problems in my limited exploring.
will check and post re desktop effect in about 20 minutes when boot completed. Will also post screenshot with just the basic descktop after running terminal - OK. (But all it will show is a basic desktop with a white rectengle in one corner.) Whoops just realised I don't know how to do a screenshot under ubuntu!!??

---

### Post by NTolerance on 2009-01-20
> **gv29847 said:**
> Processor - only that it is an Intell P3 at 866 MHz
Graphics - no seperate card - whatever Dell put on their Optiplex GX110 mainboard. One source says this is "Intel Direct AGP embedded in the Intel 810e chipset" with 4 M RAM.
Applications - I have seen no other problems in my limited exploring.
will check and post re desktop effect in about 20 minutes when boot completed. Will also post screenshot with just the basic descktop after running terminal - OK. (But all it will show is a basic desktop with a white rectengle in one corner.) Whoops just realised I don't know how to do a screenshot under ubuntu!!??

Applications -> Accessories -> Take Screenshot

I'm suspecting that Desktop Effects is possibly turned on due to your Intel 810 grapihcs chip.  Intel chips are the only ones where Desktop Effects are turned on by default even when booting from a Live CD.

Another thing you could try would be to change the terminal background color.  By default it's white, so go to Edit -> Profile Preferences -> Colors tab and try something like the "Grey on Black" scheme and see what happens.

---

### Post by gv29847 on 2009-01-20
OK - yes you guys are good - selecting Visual Effects to none fixed the problem. I took a screen shot with VE in normal mode - is it still worth moving and posting it?

---

### Post by NTolerance on 2009-01-20
> **gv29847 said:**
> OK - yes you guys are good - selecting Visual Effects to none fixed the problem. I took a screen shot with VE in normal mode - is it still worth moving and posting it?

:cool:

No need to get a screenshot now that your problem is solved.

---

