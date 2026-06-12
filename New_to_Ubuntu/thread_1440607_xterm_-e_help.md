---
title: "xterm -e help"
date: 2010-03-27
forum: New to Ubuntu
---

### Post by jba6511 on 2010-03-27
I am trying to write a bash script that uses xterm -e to ssh to a host and run a simple perl/C script. For example xterm -e 'ssh -p <snip>; perl script.pl'. The issue I am running into is that the output is not displayed or is displayed in the wrong order. For instance, one of the scripts prompts for input, then runs the command. However, there is no prompt displayed in xterm, but if you type some data and hit enter, the script executes as it should. The other executes, but the colored headings are all displayed at the end of the script. I do not have this problem when ssh to the host and running the scripts using bash. Any ideas? Is their an alternative to xterm -e to launch in the new window?

---

### Post by Brandon Williams on 2010-03-29
Depending upon the command I'm running via ssh, it is sometimes necessary to give ssh the '-t' flag to force pseudo-tty allocation in order to get the terminal to display the correct behavior. In other words: xterm -e 'ssh **-t** -p <snip> perl script.pl'

---

