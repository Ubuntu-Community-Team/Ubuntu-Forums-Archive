---
title: "Difference b/w shell and terminal for beginner"
date: 2010-01-27
forum: New to Ubuntu
---

### Post by unmole on 2010-01-27
[CENTER]This is for the [Ubuntu Manual Project]("https://wiki.ubuntu.com/ubuntu-manual").

[LEFT]While introducing the command line, we are trying to explain the concepts of a terminal and a shell. The current passage reads
> A terminal is the Ubuntu equivalent to a command prompt in windows. It is used to enter commands which then perform an action. One of the most popular of these and the one included by default in Ubuntu is BASH (Bourne Again SHell)But this suggests that a terminal and a shell are the same. Can anyone come up with a better way of writing this so that while it is factually correct, it does not dumbfound the beginner.

Thanks in advance.
[/LEFT]
[/CENTER]

---

### Post by jd65pl on 2010-01-27
Is it really necessary to differentiate the two? An attempt to do so may lead to more confusion than clarification.

For the majority of new comers there is no advantage to using an alternative shell, zsh or csh for example, bash is fairly user friendly and the majority of users will be using it. I think differentiating the two adds an unnecessary layer of complexity.

---

### Post by unmole on 2010-01-27
Maybe you are right. Will have to get back with the team on that.

---

### Post by Marvin666 on 2010-01-27
A terminal is opened in a window, while using a gui. A shell replaces the gui.

---

### Post by coral66 on 2010-01-27
Surely a terminal session invokes a default shell (environment) as defined in /etc/passwd. When the session opens, the user can then change shell by typing in ksh, csh or whatever.

---

### Post by jd65pl on 2010-01-27
By explaining the two i.e. what is said in this [bug]("https://bugs.launchpad.net/ubuntu-manual/+bug/506803") there is little value added to for the reader of the manual, that is the audience, write for this audience not to satisfy some pedantic technical reason. If the reader wants to learn more on the topic they will no doubt come across the difference.

---

### Post by jd65pl on 2010-01-27
> **Marvin666 said:**
> A terminal is opened in a window, while using a gui. A shell replaces the gui.

What of tty 1-6 these are terminals I haven't opened them in a window or using a desktop environment? The shell doesn't replace a gui for many users i.e. ask someone who has little experience of using any CLI to move a file from one directory to another using bash.

---

### Post by coral66 on 2010-01-27
Coming from the era of pre-gui computer usage, when the only option was command line and a dumb terminal session, and still available with utilities such as PuTTY from a Windows environment, I don't fully understand how you you have a terminal session without a shell or a shell without a terminal. The two are joined at the hip. There is really only a single option for a terminal session, a character based screen using the command line, using the shell assigned, in the case of Linux as defined in /etc/passwd for the user.

Yes I still use the command line, but in it's place. I for one would rather carry around an MP3 player, and not worry about how it works, than a portable record player, and an armful of LPs!

Do people really want to know definitions of Terminal/Shell? Probably not. Knowing how to use them is a different matter.

---

### Post by jd65pl on 2010-01-27
I agree with this

---

### Post by Madel on 2010-01-27
> **coral66 said:**
> 
Do people really want to know definitions of Terminal/Shell? Probably not. Knowing how to use them is a different matter.

Yeah. That's the very reason the thread starter started this thread.  ;)

---

### Post by coral66 on 2010-01-27
I will now try to define shell and terminal, from which the differences should be apparent.

Terminal - this used to be a screen at the end of a piece of cable with a nominal size of 20 lines and 80 columns. Why 80 columns? It's the same width as punched cards - remember those? Now a terminal is a program which runs command line instructions.

Shell - this is a program that allows the system to understand the commands input above at the terminal. The shell is invisible, that is it works behind the scenes, and that the only thing you need worry about is that the system does what you tell (command) it to.

---

### Post by jd65pl on 2010-01-27
> **coral66 said:**
> I will now try to define shell and terminal, from which the differences should be apparent.

Terminal - this used to be a screen at the end of a piece of cable with a nominal size of 20 lines and 80 columns. Why 80 columns? It's the same width as punched cards - remember those? Now a terminal is a program which runs command line instructions.

Shell - this is a program that allows the system to understand the commands input above at the terminal. The shell is invisible, that is it works behind the scenes, and that the only thing you need worry about is that the system does what you tell (command) it to.

I think this is fair but what is the value of this in a 'beginners manual'? The reaction is likely to either be 'nice thanks for that, something I really didn't need to know' or 'what the heck is this talking about'.

---

### Post by audiomick on 2010-01-27
> A terminal is the Ubuntu equivalent to a command prompt in windows. It is used to enter commands which then perform an action. One of the most popular of these and the one included by default in Ubuntu is BASH (Bourne Again SHell)

> **coral66 said:**
> I will now try to define shell and terminal, from which the differences should be apparent.

Terminal - this used to be a screen at the end of a piece of cable with a nominal size of 20 lines and 80 columns. Why 80 columns? It's the same width as punched cards - remember those? Now a terminal is a program which runs command line instructions.

Shell - this is a program that allows the system to understand the commands input above at the terminal. The shell is invisible, that is it works behind the scenes, and that the only thing you need worry about is that the system does what you tell (command) it to.

I think it is a good thing to try and let the beginner know a bit about what is happening.

What about this, or something along these lines?

> A terminal is the Ubuntu equivalent to a command prompt in windows.
The terminal is a user interface that gives the user access to a shell.

A shell communicates the user's commands to the operating system.

The dafault shell in Ubuntu is BASH.... and so on

---

### Post by Hospadar on 2010-01-27
From my understanding:

A shell is like bash, but any GUI, such as gnome could be considered a shell, in that the shell allows the user to run commands and in general "do stuff".  Any program which allows the user to interact with the hardware, run commands, receive output, etc.

The terminal itself (as I would describe it) is the mechanism by which a text-only shell prints out text and recieves input from the hardware.  Most machines have a terminal (the ttys) built in, this is what you see on bootup.  A terminal which runs in gnome is more properly referred to as a "terminal emulator" since it emulates this lower level hardware terminal.

It would probably we wise to include the fact the both of these terms are used to describe a wide variety of things, and to emphasize that one should assume almost any use of "terminal" or "shell" to mean any text-based command line type situation.

---

### Post by J V on 2010-01-27
knowing it doesn't really matter... how about this:

A terminal is a window or screen which contains a shell, which is a format for command-line applications to use.

Edit: my post -1 is better :P

---

### Post by Diametric on 2010-01-27
> **coral66 said:**
> Coming from the era of pre-gui computer usage, when the only option was command line and a dumb terminal session, and still available with utilities such as PuTTY from a Windows environment, I don't fully understand how you you have a terminal session without a shell or a shell without a terminal. The two are joined at the hip. There is really only a single option for a terminal session, a character based screen using the command line, using the shell assigned, in the case of Linux as defined in /etc/passwd for the user.

Yes I still use the command line, but in it's place. I for one would rather carry around an MP3 player, and not worry about how it works, than a portable record player, and an armful of LPs!

Do people really want to know definitions of Terminal/Shell? Probably not. Knowing how to use them is a different matter.

Fair point and well made.  However, I, as a new Linux user and coming from a more technical background, appreciate it when i get the full story as opposed to what someone thinks I "need to know".  The intended audience must be taken into account into how the information is written.

---

### Post by jage on 2010-01-27
As a beginner I would suggest starting with something they understand.  This is coming from not understanding the difference between Alt+F2 run application, doing xterm & in said window, and using Ctrl+Alt+F2 to access a command prompt.

I've been using all three and couldn't tell you which is a shell and which counts as a terminal, or what anyone means when they say "Just type in sudo apt-get install whatever".  Type it in *where*? :D

So, having given you an idea of where I am, my suggestion would be to start with what they know (incidentially I doubt they will care that there are 80 columns and that matches a punch card- I imagine you're trying to reach the other direction, people who don't know what a Walkman is much less a TTY console).

That said, start with the GUI... > "A GUI is a graphical interface that allows the user to perform actions on a computer by using graphical representations an mouse and keyboard inputs, such as dragging and dropping a file to move or copy.

So what the GUI is doing is allowing you to enter commands using easy to understand graphical representations.  The trade off is that not every command or option is represented in the GUI.  To access these commands, or use commands that exist in the GUI you need a command prompt.

A command prompt can be accessed using the virtual terminals (???) through Ctrl+Alt+F2.  When you type a command such as ls -l, the shell (???) is what executes the command providing you a list of files and details- much like you would get a graphical version of in the GUI by using File Browser and details (details being the -l)...."OK, so I don't know what I'm talking about, or the terminology, and it's a little verbose- but my point is to relate it back to the GUI instead of green screen CRT terminals... that (IMHO) will make more sense to new users and be more in line with their perspective of how a computer works.

---

### Post by doas777 on 2010-01-27
a shell is a user interface into the system, be it text or graphical. the original dev's thought of shells as a wrapper around the system programming interfaces. so, a terminal is a shell, as is gnome/kde/xfce.

---

### Post by jd65pl on 2010-01-27
This is the level of confusion and mess that is likely to occur from distinguishing the terms in what is meant to be a 'beginners guide'.

Quite simply the operating system should work for the user, to make their hardware usable. The user should not have to work to use the system.

---

### Post by mcduck on 2010-01-27
Simple thing. Terminal is the device or program itself. Originally a hardware device witha screen and a keyboard, these days what we actually use is a *terminal emulator*, a program that behaves as if it was a terminal.

[http://en.wikipedia.org/wiki/Data_terminal]("http://en.wikipedia.org/wiki/Data_terminal")
(Most termianl emulators you'll see are programs that emulate old DEC VT100 devices: [http://en.wikipedia.org/wiki/VT100]("http://en.wikipedia.org/wiki/VT100"), just like you might emulate  some old gaming console to play it's games on your PC.)

Shell is what runs inside it (be it a text- or a graphical shell). All the text you see and the commands you write are related to the shell. All the old Windows versions (up to Win98) were just graphical shells.

The difference between the two is much the same as the difference between a web browser (terminal emulator) and web pages (shell, whatever is running inside the terminal).

(and yes, I do consider at least having heard of the difference between the two as usefull stuff, even for absolute beginners.)

---

### Post by Ji Ruo on 2010-01-27
I also have to question whether explaining a shell is extraneous. Are your intended audience people who want things to 'just work'? If so, don't bother. All you need to explain is that the terminal is a window you can bring up where you can type in commands instead of using the desktop. Also the basic keyboard shortcuts (especially how to copy and paste into it). And the malicious commands to be wary of (see the sticky here on the forums).

I think education is important but you will sacrifice the usability of the manual if you try to explain everything for the casual user. Pick your battles. I don't think you should expect the casual user to know about operating system concepts like the shell.

---

