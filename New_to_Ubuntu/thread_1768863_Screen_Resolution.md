---
title: "Screen Resolution"
date: 2011-05-27
forum: New to Ubuntu
---

### Post by duke66 on 2011-05-27
I'm running Ubuntu 32bit in a virtaulbox.  It's working great but I want to manually change the screen resolution because the options listed don't have 1200x900.  I've been using xrandr -s 1200x900 and it tells me that is not an option.  What am I doing wrong here?

---

### Post by MichaelSammels on 2011-05-27
OK. First of all, if you are using the graphical version of Ubuntu you can go to System -> Preferences -> Monitor.

Secondly, have you installed the VirtualBox Tools and are you sure that your computer supports the resolution that you are trying to switch to?

---

### Post by duke66 on 2011-05-27
Sorry the computer resolution is 1600x900 and that is not listed in the monitor options.  So my question is can you change the resolution manually in bash?

And yes I installed the tools because that was how I was able to get out of the 800x600 little window I was stuck in before.

---

### Post by Hansholz on 2011-05-27
Good post. I've seen this same message when I was trying to add new resolutions.
     
     ```
xrandr --addmode VGA1 1024x600
xrandr --output VGA1 --mode 1024x600 
```

It worked the first time I did it, and I added 1440x900, then adding new resolutions after that using xrandr --addmode didn't work and I got the same message as you.

I wondered if there was a maximum number of resolutions I could have ('cos I had about 12 of them) but the --delmode function didn't work. I'm subscribing to this thread as I'm interested to know why I can't add customised resolutions above what's already in my xrandr output.

---

### Post by avtolle on 2011-05-27
Venturing into an area where I have little knowledge or experience is dangerous, but a question: what resolutions are supported by the host system drivers? IIRC, this is a potential limiting factor.

---

### Post by duke66 on 2011-05-27
what was the actual code you used to add a different resolution?

---

### Post by duke66 on 2011-05-27
> **avtolle said:**
> Venturing into an area where I have little knowledge or experience is dangerous, but a question: what resolutions are supported by the host system drivers? IIRC, this is a potential limiting factor.

System -> Monitor-> 
1600x1200 (4:3)
1440x1050 (4:3)
1280x960 (4:3)
1024x768 (4:3)
800x600 (4:3)
640x480 (4:3)

---

### Post by avtolle on 2011-05-27
Take a look at [http://www.linuxformat.com/forums/viewtopic.php?t=6438](http://www.linuxformat.com/forums/viewtopic.php?t=6438) 

@duke66, thanks for the information. There is a suggestion in the above link that increasing your virtual screen size gives additional resolution options. Disclaimer: I have little experience w/this , but a quick read of the link seemed to indicate an idea or two. Good luck.

---

### Post by duke66 on 2011-05-27
Thanks for the help guys but still no dice.  I read through the tutorial and I could not access the CD.  Nothing seems to work. If I figure it out I'll post the what I did.

---

### Post by wildmanne39 on 2011-05-27
> **duke66 said:**
> Thanks for the help guys but still no dice.  I read through the tutorial and I could not access the CD.  Nothing seems to work. If I figure it out I'll post the what I did.
Hi, have you installed guest additions for virtualbox then it will let you change the resolution. Also install the expansion pack for virtualbox.):P

---

