---
title: "sudo get-install cheese&gt; command not found"
date: 2009-09-01
forum: New to Ubuntu
---

### Post by pirate paul on 2009-09-01
Erm just reinstalled ubuntu, last time I installed cheese I went to applications>accessories>terminal    sudo get-install cheese   it got cheese.
now it says ..... command not found. Why ....heeeeeeeeeeeeeeeeeeeeeeelp!

---

### Post by ks07 on 2009-09-01
The command is wrong. Type:
```
sudo apt-get install cheese
```

---

### Post by pirate paul on 2009-09-01
I tried that too. command not found

---

### Post by lisati on 2009-09-01
> **pirate paul said:**
> I tried that too. command not found

Copy and paste the following to your command line:
```
sudo aptitude install cheese
```
If that doesn't work, please copy and paste the error message(s).

---

### Post by earthpigg on 2009-09-01
> **pirate paul said:**
> I tried that too. command not found

hrm....

does this command work for you?

```
ls
```
or this one:
```
uname -a
```

you dont have caps lock on or something do you?

---

### Post by pirate paul on 2009-09-01
Dont know how to copy and paste, typing the other commands....what about spaces, please give whole command.

---

### Post by PunkLV on 2009-09-01
Paste: Ctrl+Shift+V
Copy: Ctrl+Shift+C

---

### Post by jonobr on 2009-09-01
Hello


Are you doing this in the terminal window?

IF you go to applications-> accessories -> terminal

When the terminal window opens, if you type ls (lowercase) and get a command not found error, you have big problems my friend ,

---

### Post by steveneddy on 2009-09-01
Highlight the phrase with the mouse.

Move mouse to terminal window and press the middle mouse button down.It will c&p automatically in all Linux that way.

---

### Post by SunnyRabbiera on 2009-09-01
> **pirate paul said:**
> Dont know how to copy and paste, typing the other commands....what about spaces, please give whole command.

Copy and paste is the same on linux as it is on windows.
Hold down left mouse button on the text you need, until it is highlighted (the text will change color to indicate you selected it)
right click and select "copy"
then in your terminal select "paste", also using the right mouse button.
Copy and paste is the most basic thing you can do.

---

### Post by Niko Johnson on 2009-09-01
sudo apt-get install cheees

that should do it for you... you can always copy and paste with right clicking and choosing copy and then paste into your terminal.

---

### Post by pedro3005 on 2009-09-01
Yeah, actually, CTRL C and CTRL V will not work on terminal, so right click away. But they will work elsewhere on Linux. And BTW, you don't need to mess with terminals. Go to Applications, Add Remove Applications and search for Cheese there. Nice, simple GUI for you.

---

### Post by ks07 on 2009-09-01
> **steveneddy said:**
> Highlight the phrase with the mouse.

Move mouse to terminal window and press the middle mouse button down.It will c&p automatically in all Linux that way.
Wow now that's a cool little hidden feature. Thanks for sharing that. :D

Don't worry, I'm not gonna give another set of instructions to copy + paste. :P

---

### Post by SunnyRabbiera on 2009-09-01
Here is a vid on copy and paste:
[http://www.youtube.com/watch?v=c66pvfilotA](http://www.youtube.com/watch?v=c66pvfilotA)

Yes mainly features vista with notepad but the principle is the same in linux

---

### Post by jonobr on 2009-09-01
Its also avaible in the repos I believe,
If you go to system-> admin-> synaptic.,

Type in cheese in the search it should find it,

Nice and gui-fied

---

### Post by pirate paul on 2009-09-01
I was able to copy from here and paste in terminal window but not from terminal window back to here,
Command not found, wit above commands.

---

### Post by SunnyRabbiera on 2009-09-01
> **pirate paul said:**
> I was able to copy from here and paste in terminal window but not from terminal window back to here,
Command not found, wit above commands.
just do it the windows way then, install from here:
[http://packages.ubuntu.com/search?keywords=cheese&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=cheese&searchon=names&suite=all&section=all)

Select the package for your version and your architecture.
And please for the love of pete learn package management:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by ks07 on 2009-09-01
If none of those commands work, then something is not alright in your system. If you open a file browser window, e.g. your documents folder, then navigate to /bin

Look in that folder for the files 'ls' and 'uname'. (DON'T do anything to the files in there, they're important!) If they're gone, you've managed to uninstall some of the essentials from your computer.

---

### Post by pirate paul on 2009-09-01
It says cheese is installed in system>admin>synaptic ?????????????????

---

### Post by SunnyRabbiera on 2009-09-01
> **pirate paul said:**
> It says cheese is installed in system>admin>synaptic ?????????????????

did you look in your menu's?
Cheese is normally listed under the "graphics" submenu.

---

### Post by derrick81787 on 2009-09-01
This is the second thread you've posted about the exact same topic.  Your other one is here: [http://ubuntuforums.org/showthread.php?t=1255219](http://ubuntuforums.org/showthread.php?t=1255219).  It seems to me like you are being very unhelpful to the people who are trying to help you, and you are spamming the forums.  You've gotten many correct answers, but you won't get a better answer than this post: [http://ubuntuforums.org/showpost.php?p=7880398&postcount=12](http://ubuntuforums.org/showpost.php?p=7880398&postcount=12)

If you're going to ask for help on the forums, then you should at least try to figure it out, instead of wasting everyone else's time.


*** Edit ***
Actually, I guess this is the first thread and the other is the second.  Either way, the point stands.

---

