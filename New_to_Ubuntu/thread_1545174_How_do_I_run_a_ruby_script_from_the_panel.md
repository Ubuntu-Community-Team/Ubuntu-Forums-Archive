---
title: "How do I run a ruby script from the panel?"
date: 2010-08-03
forum: New to Ubuntu
---

### Post by PreciousBodilyFluids on 2010-08-03
I have a small Ruby script that I can run successfully from the command line:

rvm ree ruby ~/scripts/backup.rb

The "rvm ree" is present because I'm using the Ruby Version Manager (RVM).

What I'd like to do is add a button to my top panel in Ubuntu that would run the script for me in a terminal window. When I try to put this in a panel launcher, though, I get an error stating "There was an error creating the child process for this terminal".

Also, since the script has a lot of output that I'd like to be able to inspect, I'd like the terminal window to start maximized. The script is already set up to require user input before it exits, so the terminal closing prematurely isn't a problem.

Any suggestions on how I should set this up? I'm running Lucid Lynx. Thank you!

---

### Post by NoBugs! on 2010-08-03
xterm -hold -e "command goes here"

---

