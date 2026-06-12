---
title: "Huh? Where'd my program go?!?"
date: 2009-12-06
forum: New to Ubuntu
---

### Post by jessmanboo22 on 2009-12-06
I just installed something using the Ubuntu Software Center in Karmic Koala 9.10. (Armagetron Advanced). Now that it's installed, how do I access it? It's not in the Games folder under Applications...

I'm a complete n00b at Ubuntu, just installed it this morning. Have gotten Wine to work, attempted Windows Movie Maker and MSN Messenger; both aren't working however. I click their icons but nothing happens.

Any help for anything I said/asked would be greatly appreciated! :D
~Jessmanboo

---

### Post by davec64 on 2009-12-06
Try typing the following in a termina;

```
armagetron
```

Assuming that's how the programmed is named, it will either start or provide details of any errors.

MSN Messenger - rather than using a windows programme try either Empathy or Pidgin, both support MSN.

Windows Movie Maker - have a hunt in the software centre for an alternative. 

It's always best to use a native linux programme than try to get a Windows programme to work under linux, just remember linux isn't windows!  :)

---

### Post by jessmanboo22 on 2009-12-06
@MSN: Yeah, I am using Empathy but it's really hard for me to get used to and I was just trying to get the old MSN back. S'ok though! :)

@WMM: Ok, I'll have a look! I never really think that much outside the box :P

@Armagetron: Alright. I haven't even touched the terminal yet (NO I'M NOT SCARED I JUST... um...) but I'll try that out!

Thanks soo much!
~Jessmanboo

---

### Post by jessmanboo22 on 2009-12-06
[s]I tried typing "armagetron" into the terminal; it told me I didn't have the program "armagetron" installed. I typed armagetron advanced, and I still got that I didn't have "armagetron" installed. I clue'd in and typed armagetron advanced with quotes, and it just said I don't have "armagetron advanced" installed.

Is software that you install in the Ubuntu Software Center normally supposed to show up in the Applications menu, or do you have to create a launcher (YAY i learned that a shortcut from windows is called "launcher" in ubuntu!) manually?[/s]

EDIT: Never mind...: The icon finally showed up in Games! :D

~Jessmanboo

---

### Post by davec64 on 2009-12-06
Sometimes a programme doesn't come with a launcher that's entered in the Applications menu, other times it may not get installed.
If it works from the terminal you can always create a launcher and place it in the correct menu.

> Alright. I haven't even touched the terminal yet (NO I'M NOT SCARED I JUST... um...) but I'll try that out!

LOL You'll find if you ask for help you'll quite often get the answer as a series of commands to run in a terminal. Normally it's not that that is the only way to do it, it's just that it's easier to explain!

---

### Post by mickie.kext on 2009-12-06
Fot MSN replacement, try [aMSN]("http://www.amsn-project.net/"). You have it in Software Center(aplications menu in top left corner). 

Window Movie Maker, there is truckload of options. LIVES, Avidemux, Cinelera...

---

### Post by oldos2er on 2009-12-06
Did you try armagetronad ? Or type armag followed by Tab, to let the shell find the program.

---

### Post by davec64 on 2009-12-06
Now we're in trouble! I don't know what the application name is for armagetron.

You've got 2 options (both are the same just different ways of doing it:

Option 1 - Terminal
> Sudo apt-get reinstall armagetron-advanced
That will probably tell you it's not installed or doesn't exist if the name is wrong.

Option 2

Open Synaptic Package Manager
(which is under system >> Advanved)

Click on Search and Enter "armagetron" - it will find anything related to armagetron.

If the square next to the application is green then it is installed. So right click on it and select reinstall.

If it's not green click on it and select install.

I'm sorry but I've got to go out now, post back and I'll reply tomorrow.

All the best

---

### Post by jessmanboo22 on 2009-12-06
Thanks for all your help! See the edit in my above post...

~Jessmanboo

---

### Post by D3M0L1$H3® on 2009-12-06
Unless there is a true need for the program, always try finding Open Source alternatives to your software. Most programs like MSn and Movie Maker that are a part of Windows (came installed automatically) will not work in WINE

---

### Post by corncob on 2009-12-06
> **jessmanboo22 said:**
> [s]I tried typing "armagetron" into the terminal; it told me I didn't have the program "armagetron" installed. I typed armagetron advanced, and I still got that I didn't have "armagetron" installed. I clue'd in and typed armagetron advanced with quotes, and it just said I don't have "armagetron advanced" installed.

Is software that you install in the Ubuntu Software Center normally supposed to show up in the Applications menu, or do you have to create a launcher (YAY i learned that a shortcut from windows is called "launcher" in ubuntu!) manually?[/s]

EDIT: Never mind...: The icon finally showed up in Games! :D

~Jessmanboo

Rebooting the computer often  does wonders in getting icons to show up.  I mean a really hard reboot as in turning the computer off for a while.

---

