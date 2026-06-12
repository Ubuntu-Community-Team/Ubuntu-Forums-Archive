---
title: "Run Without Sudo"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by th3j3ster on 2009-11-25
Hi Quick question. Is there any way to create a launcher for a command that requires sudo to run? I run SABNzbd+ and it requires sudo to run, but I can't seem to figure out how to get it to do so outside of the terminal. 

If that isn't possible...how do you get a program to run and not shut down if you close the terminal? I did searches for both of these, but I was unable to find what I was looking for...it is entirely possible that I'm computer-impaired after a long day of dealing with windows problems...please help...feel free to smack me if the answer is obvious

---

### Post by rudy.b on 2009-11-25
Yes, you should be able to edit the launcher command (right-click the launcher icon and select "Properties") and put sudo (or gksudo for graphical apps) in front of the startup command.

---

### Post by th3j3ster on 2009-11-25
Hmm...tried that already but it didn't seem to work...just tried again and that worked fine...odd I must have typed it wrong...several times...

Anyways, thanks!

Any idea how I can run it from the terminal without having to keep the terminal open

or 

how to run a .py or .sh from launcher? I've tried what seemed like the obvious... 
sudo ./example.sh, but that seemed to have failed miserably. 

Thanks again for you help!

---

### Post by staf0048 on 2009-11-25
I could be wrong, but you might want to try:

```

sudo sh ./example.sh

```

---

### Post by byStanderone on 2009-11-25
...you can evoke alt+F2 for the 'run application' window

---

### Post by rudy.b on 2009-11-26
> **th3j3ster said:**
> 
...
Any idea how I can run it from the terminal without having to keep the terminal open
...


You can try running the command with an ampersand (&) at the end and then exiting the terminal.  Note that if you quit the terminal by closing the window instead of typing 'exit' the child process will be killed as well.

For example, if I wanted to run gedit as a background process:

```

$ gedit &
$ exit

```

---

