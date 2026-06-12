---
title: "Broke Ubuntu With A Mouse?"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by Azhtabak on 2009-03-24
My ubuntu-breaking escapades continue it seems, as I have now managed to break ubuntu yet again - this time apparently with a mouse.

I put in the mouse (USB mouse itno my laptop) this morning, causing the laptop to display random colours at me, then just not respond - a reboot gave me a command line, which I was able to log in by, but had no windows or desktop environment as far as I'm aware. A second reboot resulted in nothing - I get a message about the hard drive being mounted in read-only mode, and a few error messages. I think I have a command line, I'm not sure. (Not at my computer at the moment)

Other relevent information (possibly?)

I installed gnome (via synaptic -> ubuntu-desktop) a while back, which regular spits out a few error messages at me, but doesn't seem to have caused any significant problems previously that I'm aware of.

Also, I had just installed a large amount of updates before this, possibly including a kernel update I believe, that required a restart to install - they seem to have installed on the reboot I believe, as the loading bar was slightly different :P

Anyone got any idea what I've managed to break? :(

---

### Post by HavocXphere on 2009-03-24
I'd venture a guess and say the mouse thing is pure coincidence.

Sounds to me like something about your computer hardware is flakey.

I'd try:
Booting with a PS/2 mouse instead of the USB mouse.
Running a memtest from the ubuntu boot disk.
Checking the harddrive. (I use Spinrite, but it costs $$$)

Also, not all USB ports are equal (Some are more equal than others;)), so try another one.

---

### Post by KCG102282 on 2009-03-24
> **HavocXphere said:**
> I'd venture a guess and say the mouse thing is pure coincidence.

Sounds to me like something about your computer hardware is flakey.

I'd try:
Booting with a PS/2 mouse instead of the USB mouse.
Running a memtest from the ubuntu boot disk.
Checking the harddrive. (I use Spinrite, but it costs $$$)

Also, not all USB ports are equal (Some are more equal than others;)), so try another one.


Agreed

---

### Post by pluckypigeon on 2009-03-24
> **kcg102282 said:**
> agreed

:p

+2

---

### Post by Azhtabak on 2009-03-24
Yeah, I guessed it wouldn't be :P Anyway, I have a new (I think positive?) development

I can no log in, but inly to command line level (so I just have a konsole, basically). When ever I try to run any programs, I get the message 'cannot contact x server'

After trawling the forums, I came upon this command:

```
sudo dpkg-reconfigure xserver-xorg
```

But that just leads me to the start of a configuration process I believe, where it then freezes.

---

### Post by Bölvaður on 2009-03-24
I see you are alpha testing so I assume reinstalling wouldn't be any problem at all to see what makes your computer go banana. Just be more careful with installing packages and perhaps just install one at a time to know which one is faulty.

I have found 1½ bugs in jaunty so far ^^ (you may want to report yours when you know what is up)

---

### Post by LowSky on 2009-03-24
1.5 bugs, thats it? 

I keep getting a flash issue, movie player doens'y like to play any of the restricted codecsexaile crashes almost everytime I use it for more than 15 minutes, and some radom occurances in the GUI version of the sources list things appearing/disappearing, perfectly good repos failing, unchecking a repos and it deletes itself only to apear later, really confusing? And these are the things I can think of off the top of my head.

Otherwise Its pretty stable with graphics and the desktop apps like firefox just have to restart if flash fails, usually fails if the webpage has too many flash enabled widgets, pidgin works fine, so does nautilus, mounting my hardware works fine too.

---

