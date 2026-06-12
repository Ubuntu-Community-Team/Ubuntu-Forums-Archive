---
title: "Terminal, Bash Shell, tty...Difference?"
date: 2011-06-08
forum: New to Ubuntu
---

### Post by zer010 on 2011-06-08
A quick question on the proper use of these terms.  Specifically for a CLI only install, no X, what is the environment that I'm in? When a full GUI is installed the CLI is a "terminal emulator", right?  

The reason I'm wondering is because I have a CLI only install and I'd like to customize the prompt and such.  When googling around for tips, it became apparent that the CLI and GUI versions are about the same and yet different.  There seems to be more info on customizing the terminal emulator than anything else.  

I'm just looking for some clarification on the terminology so I can be more specific in my searches and questions.

---

### Post by webofunni on 2011-06-08
Terminal emulator allows users to use tty within a GUI environment. terminal in GUI is almost same as tty, except that it is more compatible to GUI, such that you can execute commands that require GUI in a terminal emulator.

---

### Post by BrandonC19 on 2011-06-08
Terminal is a catch-all approach to describing the CLI (Command Line Interface) of a *Nix O/S.

TTY is short for TeleType, which is reminiscent of the '60's where computer usage consisted of hooking a TeleType to a mainframe and response to commands where transmitted back to the Teletype machine in printout format.

Bash (short for "Bourne Again Shell", the successor to the original Bourne Shell) is the default command line environment in Ubuntu, and many other distros. But it's not the only one. The other more common shells are the C Shell (csh) the Z shell (zsh) and the Korn Shell (ksh). There's way more than that, but those are the most popular.

The main difference in themeing the shell is that with the GUI based terminal you're usually presented with a GUI to change color/layout/etc... but with a CLI only install you need to edit your .bashrc file in your home directory. _[COLOR=Red][Here's]("http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html%22")[/COLOR]_ a good site to help you with Bash customization.

---

