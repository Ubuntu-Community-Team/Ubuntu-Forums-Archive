---
title: "Save frequently used terminal commands"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by sydbat on 2009-02-03
This may be a dumb question, but I am wondering if there is a way to save the terminal commands I use frequently?

To clarify, when I go into a terminal, I can scroll through all the commands I have used (as far as I can tell) to find the relevant one I need (ex. sudo blah-blah). Is there a way to save this list, possibly in a text file, as a backup? That way, if I ever really bork the box, I can simply bring up the text file and find the commands I need, instead of having to search on the forum for them.

Does that make any sense?

---

### Post by lykwydchykyn on 2009-02-03
Bash automatically keeps a history.  You can search through it with ctrl-r.
Apart from that, you can just put the big ones in a script.

---

### Post by bhadotia on 2009-02-03
The file already exists. It is the .bash_history file in your home folder. Also note that it is a hidden file so it wont show up by default in the file browser. You need to press ctrl+h when in you home directory to see the file. Just back-up the file. Also older commands get deleted depending on your history size setting. In the terminal read the man page  for bash (man bash) to lrarn how to change this setting. The man page is huge so I recommend scrolling to enviornment variable section to see the relevant setting options. I could have told you about it but unfortunately I forgot and am down with sickness, so I don't want to search it myself;)

---

### Post by Hospadar on 2009-02-03
you can make aliases to commonly used commands.  For example I have one on my office machine to quickly ssh into my home machine.

If you type "alias" in the terminal it will show you all your current aliases

To make them, you also use the alias command.
Let's say I want to make an alias for ```
ssh -Y luke@myhomemachineip.dyndns.org
``` because I only want to type in something short like```
ssh-home
``` I can do a ```
alias ssh-home='ssh -Y luke@myhomemachineip.dyndns.org'
``` and now typing in ssh-home will run the longer command.

If you want your aliases to persist past a single terminal session, add them to the bottom of your ~/.bashrc file.
do a ```
nano ~/.bashrc
``` to edit your file (ctrl-o to save, ctrl-x to quit), scroll all the way to the bottom, you'll probably see some other aliases, just add all the ones you want, one alias per line.  Then to make sure they work, just open a new terminal or ```
source ~/.bashrc
```

---

### Post by sydbat on 2009-02-04
Thank you. This is one of the many perks of being part of this community...all the speedy and well informed help.

Now if I could only mark this as Solved...

---

