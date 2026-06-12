---
title: "im confused with the shell(s)"
date: 2009-08-16
forum: New to Ubuntu
---

### Post by flyingsliverfin on 2009-08-16
riiiight.... can someone tell me the different shells available, which one ubuntu uses, and the differences between the available ones and the one ubuntu uses?

---

### Post by Miljet on 2009-08-16
[http://penguin.dcs.bbk.ac.uk/academic/unix/linux/shells/index.php](http://penguin.dcs.bbk.ac.uk/academic/unix/linux/shells/index.php)

---

### Post by earthpigg on 2009-08-16
gnome-terminal is the one ubuntu uses by default.

to to applications -> add/remove and search for 'terminal'.

install 20 of them, see which one you like the best.

---

### Post by prvteprts on 2009-08-17
Technically, you are referring to the "Terminal Emulator" applications. In the past, a single UNIX computer may have several "dumb" terminals connected to it, which users use to login to and use that same machine at the same time. These applications (konsole, terminal) are virtual terminals which run under a graphical interface.

The term "shell" refers to the program which interprets commands, which is why it could also be called command (line) interpreter. There are different kinds of shells, Bourne shell (sh), Bourne-again shell (bash), C-shell (csh), etc. These shell programs have different capabilities and different syntax. 

Any terminal emulator application can run any shell program you want. The default shell in Ubuntu is bash. If it seems confusing, try messing around with ctrl+alt+f1 to f4. These are virtual terminals which emulate the terminals in the old days. Ctrl+alt+f7 is the terminal for running the graphical interface.

---

### Post by mcduck on 2009-08-17
Actually the default shell (/bin/sh) in Ubuntu is Dash. 

Bash is the default user shell.

And the difference between the two? Dash is lighter and faster, but with less features. Bash has more features but since the policy is that scripts using /bin/sh should only have standard POSIX features anyway it makes sense to use simpler shell to run all the system stuff. Moving to Dash was one of the main reasons for faster startup times in Ubuntu 6.10 and later.

---

### Post by trilobite on 2009-08-17
> **flyingsliverfin said:**
> riiiight.... can someone tell me the different shells available, which one ubuntu uses, and the differences between the available ones and the one ubuntu uses? 
Hi - 
 Bash is the default user shell on Ubuntu (and in my experience, the vast majority of other distros too). There's a very detailed comparison page on Wikipedia here - 
[http://en.wikipedia.org/wiki/Comparison_of_command_shells](http://en.wikipedia.org/wiki/Comparison_of_command_shells)

There are even more than are shown on that page, by the way. 

There can be some differences in the syntax of commands between shells. Also, some shells support things like custom prompts, functions, default arguments and so on, whereas other shells don't. The above page gives a useful overview. 

I've tried a couple of other shells, but have very much stuck with bash. It's very widespread and quite user-friendly, in my opinion. By the way, there is a shell called "fish" (for Friendly Interactive Shell) that you might want to try too. Here's the URL for that - 
[http://fishshell.org/index.php](http://fishshell.org/index.php) 
- Hope this helps! 
- trilobite

---

### Post by scorp123 on 2009-08-17
> **earthpigg said:**
> gnome-terminal is the one ubuntu uses by default. "gnome-terminal" is only the graphical front-end, it's not the shell itself. The real shell that is used per default is "bash"
[http://en.wikipedia.org/wiki/Bash](http://en.wikipedia.org/wiki/Bash)

Slight correction --- another poster further up is right, the new default is "dash" ... But for the average user "bash" and "dash" look and feel the same with the exception that "dash" supposedly is a slight bit faster and lighter:
[http://en.wikipedia.org/wiki/Debian_Almquist_shell](http://en.wikipedia.org/wiki/Debian_Almquist_shell)

---

### Post by flyingsliverfin on 2009-08-17
so right now (with no new terminals installed yet) when i go to applications -> acessories -> terminal that is BASH (emulator?) right? And this terminal could also be called   Gnome - Terminal   correct?



i looked at dash and csh, compared them to what i liked about bash and decided to stick with bash; bash also seemed a bit more user friendly as trilobite said. My dad said that the most used terminal is bash, and if i want to learn a terminal then i should start with bash.

ill have to take a look at fish..

---

### Post by mcduck on 2009-08-17
When you go to Applications/Accessories/Terminal you open a program called Gnome-temrinal. It's a terminal emulator, which means that it's a software that's purpose is to act as if it was a [computer terminal]("http://en.wikipedia.org/wiki/Computer_terminal").

Most typically terminal emulators emulate the DEC VT100 or some of it's successors: [http://en.wikipedia.org/wiki/VT100]("http://en.wikipedia.org/wiki/VT100"). For example Gnome-terminal defaults to VT102 emulation.

What runs inside the terminal is completely different thing, and not really tied into the terminal emulator itself. So the terminal doesn't emulate Bash, or any other shell. It emulates hardware terminal, and runs Bash.

***

What comes to which shell to use, you'd better stick to Bash for now, but if you start writing shell scripts and such then it's a good idea to avoid bash-specific features to keep your scripts compatible with other shells.

---

### Post by oldos2er on 2009-08-17
zsh is a great shell program.

---

### Post by Kinetic1001101 on 2009-09-13
> **Miljet said:**
> [http://penguin.dcs.bbk.ac.uk/academic/unix/linux/shells/index.php](http://penguin.dcs.bbk.ac.uk/academic/unix/linux/shells/index.php)


People who never make mistakes seldom make anything! 

Great quote...who wrote it?

:D

---

