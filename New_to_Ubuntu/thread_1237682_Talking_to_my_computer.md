---
title: "Talking to my computer"
date: 2009-08-11
forum: New to Ubuntu
---

### Post by jdshelby on 2009-08-11
Hi all,

I'm not exactly sure I know what I'm talking about; even the terms that I'm going to use might not make sense of jive with reality, but let me give it a go.

How would I use a script to give instructions to my computer?  For example, I managed to make a python script that gave me a madlib game in terminal (thank you online guidebooks) and that was cool.  But how could I run a script that would not just do something in terminal, but that would actually tell my computer to open a certain application, like firefox, and then go to a certain webpage, like ubuntu forums?  Would I just figure out some way to do that in a python script, or would I need a different language to actually "speak" to my OS?  Did that make sense?

Thanks 
Justin

---

### Post by credobyte on 2009-08-11
Depending on what you want to do, you can do that in almost any language, however, without knowing bash, you'll not get anywhere ..

C++
```
system("<command>");
```

Python
```
os.system("<command>")
```

---

### Post by lykwydchykyn on 2009-08-11
> **jdshelby said:**
> Hi all,

I'm not exactly sure I know what I'm talking about; even the terms that I'm going to use might not make sense of jive with reality, but let me give it a go.

How would I use a script to give instructions to my computer?  For example, I managed to make a python script that gave me a madlib game in terminal (thank you online guidebooks) and that was cool.  But how could I run a script that would not just do something in terminal, but that would actually tell my computer to open a certain application, like firefox, and then go to a certain webpage, like ubuntu forums?  Would I just figure out some way to do that in a python script, or would I need a different language to actually "speak" to my OS?  Did that make sense?

Thanks 
Justin

It depends on the application really and what commands you can feed to it from the console.  For instance, in your example, you could create a script that just says:
```

firefox http://ubuntuforums.org

```

And that would do what you said.  It gets more complicated if you want to do complex GUI actions like clicking buttons within programs.  If they can't be scripted from the command line, there are solutions like gnee which record mouse/keyboard movements and can replay them, but I couldn't tell you how well that would work.

---

### Post by WRDN on 2009-08-11
For the gnome-desktop, Firefox is installed as the default web browser, but you cannot guarantee that the user will have it installed. Instead of setting the browser manually, you can use commands to retrieve the default web browser, allowing your script/application to be program agnostic (providing a web browser is installed that is). The most useful commands are:

```
xdg-open http://ubuntuforums.org
```

xdg-open will open the default program for a particular file type or URL. So for example, on a new Ubuntu installation it would open Firefox with the URL, and it will open gedit with a plain text documents.

You can also use:

```
x-www-browser http://ubuntuforums.org
```

x-www-browser is a system link that resides in /usr/bin. This opens the default browser with the URL specified (if any).

---

### Post by Hospadar on 2009-08-11
Keep in mind, if you are scripting, you will rarely use the same tools as you do when you do things graphically.

For example, I need to open a zip file, I suppose it might be possible to write some super-nasty script that opens up file manager, moves the mouse around, does the clickey, etc, but it would sure be a lot easier to use the command line utility "unzip" because then I'd just have to "unzip thatfile.zip"

Especially in linux, there is almost nothing that cannot be done on the command line (including browsing the intertrons) so if you are writing scripts, using a GUI program in the script should be your last resort.  It's not windows where nothing has command line options and it's a complete pain to get things done automatically unless you really know what you are doing.

---

### Post by jdshelby on 2009-08-11
Do you have any suggestions for sites that give me all these nifty commands as well as the syntax to implement them in bash via a script?  I've been looking at [http://ss64.com/bash/](http://ss64.com/bash/) and while it looks good, it doesn't seem exhaustive and isn't really showing me how to write a script.

Thanks
J.

---

### Post by Terl on 2009-08-11
The Linux Documentation Project has great resources for you - and free at that!  Here is a BASH scripting guide: [BASH Scripting How-To]("http://tldp.org/HOWTO/pdf/Bash-Prog-Intro-HOWTO.pdf").  There are also great tutorials on the web, just google for bash scripting tutorial

Another great site for [Linux commands]("http://oreillynet.com/linux/cmd/")

---

