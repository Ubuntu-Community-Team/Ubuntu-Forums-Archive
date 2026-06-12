---
title: "Can i see what's actually going on?"
date: 2011-09-07
forum: New to Ubuntu
---

### Post by kidsonp on 2011-09-07
Can anyone tell me how I can view what actually happens when I click on an icon in the GUI - like seeing the commands the machine runs in the terminal view? This may a daft idea and not actually possible - or useful.  I ask because I have copied and pasted commands from all the helpful people out there to fix glitches, but would like to know if I can integrate these (better) commands into the (defective) automatic script that runs when I click an icon.  Am I trying to venture into places too dangerous for mere mortals - or is this all part of the fun of Linux/Ubuntu?

---

### Post by nomko on 2011-09-07
Like you said it yourself, best way to do that is running the comand in a terminal. Everything what's happening will be visible in the terminal. This way you also can see if there are any error's.

---

### Post by kidsonp on 2011-09-07
Okay - so if I open a Terminal Session and then click on an icon in, say my Bookmarks toolbar, I should be able to see what the machine does and backtrack through the commands it has run.  I have sort of tried this already and was disappointed not to see squillions of lines of commands flashing by.  Was i supposed to see these?

---

### Post by madjr on 2011-09-07
enter the Matrix!

---

### Post by nipunshakya on 2011-09-07
actually i was willing to see the same thing...and about to start a new thread...but since OP has similar thread topic, i would like to merge it here.....as OP said it, is there any way to see what really goes inside the machine when i perform certain tasks?....im also a noob tryin to get inside the terminal...

---

### Post by dcsoldschool53 on 2011-09-07
[B]Click on at the following attachment, is this what you meant? I had clicked on an icon. It had opened a terminal and ran the command. After the command finishes running, it close the terminal. The command that is being used, is "gconftool-2 --dump /apps/panel > ~/panel_setting", without the quotations marks. It saves a copy of my gnome panel to my user account.

If this is not what you meant, I would suggest that you follow what nomko said.

I hope this will help you. :)[/B]

---

### Post by MG&amp;TL on 2011-09-07
Try opening a terminal, and 

```
nautilus
``` 

which will open a file browser. Any messages printed to stdout should show up.

This is probably a bit advanced if you don't know your way around a terminal, but you can get pretty much any package's source code in the ubuntu repos, by:

```
apt-get source <package name>
```

Have fun. I think the file browser's *nautilus* but there's lots of other packages.

To see a processes' name, type 

```
ps -axu
``` in a terminal, and look for the ones with your username on.

---

### Post by dodo3773 on 2011-09-07
> **kidsonp said:**
> Okay - so if I open a Terminal Session and then click on an icon in, say my Bookmarks toolbar, I should be able to see what the machine does and backtrack through the commands it has run.  I have sort of tried this already and was disappointed not to see squillions of lines of commands flashing by.  Was i supposed to see these?

If you click on an icon while the terminal is open you will not see any terminal output. In order to see output you type the process name in the terminal. Also, the process name is not always going to be the same as the name on the icon. A lot of applications have a verbose option. Verbose means more output. In order to see if an application does type "man applicationname" or "applicationname --help". What is the application that you would like to see output on?

Some applications may give little or no output . Nautilus is a great example. If you want to view system calls / signals use strace 
"strace applicationname"

---

### Post by kidsonp on 2011-09-07
Thanks folks - lots of things to try.  But to answer your question directly Dodo 3773 - I'm trying to open Skype, but when I, do it won't open my webcam.  I looked online and found a line of code which opens Skype and the webcam as I expect it to.  So I want to see is what the difference is between what clicking on the icon does, and what running the command line in terminal does - and maybe I can fix it. And if I break it - FUBAR!- I expect I can just re-install it.  This is a luxury I seldom have as a mechanical engineer.  Once a mechanism thing has gone FUBAR - well that's usually the end of it.

---

### Post by dodo3773 on 2011-09-07
> **kidsonp said:**
> Thanks folks - lots of things to try.  But to answer your question directly Dodo 3773 - I'm trying to open Skype, but when I, do it won't open my webcam.  I looked online and found a line of code which opens Skype and the webcam as I expect it to.  So I want to see is what the difference is between what clicking on the icon does, and what running the command line in terminal does - and maybe I can fix it. And if I break it - FUBAR!- I expect I can just re-install it.  This is a luxury I seldom have as a mechanical engineer.  Once a mechanism thing has gone FUBAR - well that's usually the end of it.

Clicking on the icon probably just runs the binary "skype" as in opening a terminal and just typing skype. Have you tried editing the icon and replacing the command in it to the line of code you found that works correctly? That seems like it would be the easiest solution.

---

### Post by kidsonp on 2011-09-07
Thanks folks - lots of things to try.  But to answer your question directly Dodo 3773 - I'm trying to open Skype, but when I, do it won't open my webcam.  I looked online and found a line of code which opens Skype and the webcam as I expect it to.  So I want to see is what the difference is between what clicking on the icon does, and what running the command line in terminal does - and maybe I can fix it. And if I break it - FUBAR!- I expect I can just re-install it.  This is a luxury I seldom have as a mechanical engineer.  Once a mechanism thing has gone FUBAR - well that's usually the end of it.

---

### Post by kidsonp on 2011-09-07
Oooo... Editing an icon - now that's a new game to play.  I haven't a clue how to do that but, oh well, what else have I got to do tonight but learn.  Thanks

---

### Post by dodo3773 on 2011-09-07
> **kidsonp said:**
> Oooo... Editing an icon - now that's a new game to play.  I haven't a clue how to do that but, oh well, what else have I got to do tonight but learn.  Thanks

If you need more help let me know.

---

