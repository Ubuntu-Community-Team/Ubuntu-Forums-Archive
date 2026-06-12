---
title: "at command."
date: 2009-11-19
forum: New to Ubuntu
---

### Post by duds2008 on 2009-11-19
Hello good people! I am trying to do something for my friends and my own amusement. I am probably going about this in the wrong way. Forgive me for my ignorance. I am trying to write a script that outputs hilarious messages to the current terminal I am working on (thereby creating a sequence of messages, supposedly from an insane terminal)However I would like to make these messages appear at set times. I thought about using "at" so that I can specify messages to be outputed to the current screen after running the script. I would like the output to be printed at different times consecutively (I'm talking seconds here) However, at does not seem to behave in the way I thought it does, and seems to send the output to some other tty(I can see results by playing audio files with at but echo and ls give no output) Any ideas are sincerely appreciated. PS: here is an example of what I am trying to do:
$at now +1 min
> echo "system initializing"
> <ctrl+d> <EOT>
job 1 at Thu Nov 19 19:43:00 2009
$at now +2 min
> echo "system loaded. Preparing face recognition software..."

I know this is all a bit childish and silly, but I am currently learning about shell scripting and think scripts like these are a good learning starter. Is there an easier way to achieve what I am trying to do? Hope this all makes sense to you! :)

---

### Post by skatinjj on 2009-11-19
According to the documentation at

```
/usr/share/doc/at/timespec
```

you should be using MINUTE instead of min.

---

### Post by duds2008 on 2009-11-20
Thank you. I will give this a try. According to the book I was following (Ubuntu Linux Toolbox by Christopher Negus & Francois Caen), they put the example as "min", but this could be a print error. I will try later! Thanks:)

---

### Post by drseuk on 2009-11-20
> **duds2008 said:**
> Hello good people! I am trying to do something for my friends and my own amusement. I am probably going about this in the wrong way. Forgive me for my ignorance. I am trying to write a script that outputs hilarious messages to the current terminal I am working on (thereby creating a sequence of messages, supposedly from an insane terminal)However I would like to make these messages appear at set times. I thought about using "at" so that I can specify messages to be outputed to the current screen after running the script. I would like the output to be printed at different times consecutively (I'm talking seconds here) However, at does not seem to behave in the way I thought it does, and seems to send the output to some other tty(I can see results by playing audio files with at but echo and ls give no output) Any ideas are sincerely appreciated. PS: here is an example of what I am trying to do:
$at now +1 min
> echo "system initializing"
> <ctrl+d> <EOT>
job 1 at Thu Nov 19 19:43:00 2009
$at now +2 min
> echo "system loaded. Preparing face recognition software..."

I know this is all a bit childish and silly, but I am currently learning about shell scripting and think scripts like these are a good learning starter. Is there an easier way to achieve what I am trying to do? Hope this all makes sense to you! :)

Write your script in whatever language you prefer and add it as a cronjob to /etc/crontab ... :-)

---

### Post by 3rdalbum on 2009-11-20
Commands put into "at" will run in an invisible terminal; so when you try to run the "print" statement it will print it merely to a terminal that you can't see.

In order to print something to the current terminal, you'd need to write a bash script or something similar, that waits a certain amount of time (using the sleep command) and then prints the statement. You would also need to start the script in the terminal that will accept the printed output, and run it with the & symbol at the end so it runs asynchronously.

Then issue the "clear" command, and the terminal will clear so the user can't see what you've done.

---

