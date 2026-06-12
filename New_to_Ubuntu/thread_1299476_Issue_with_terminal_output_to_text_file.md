---
title: "Issue with terminal output to text file"
date: 2009-10-23
forum: New to Ubuntu
---

### Post by boson007 on 2009-10-23
Ok I know what the command is to print the output from the terminal to a text file.
e.g. I'll do $ ls > a.txt
and the file a.txt appears with the desired information in it.
However,  sometimes I run a program and want to pipe its output  to a text file, the file is create but remains empty:
e.g. $ ./program > a.txt
But a.txt will be empty even though "$ ./program " will print some data in the terminal.
If I do  "$ ./program &>a.txt" for instance I'll find the console output in my text file, but the data is still missing.
Any ideas?
Thank you!

---

### Post by dj-toonz on 2009-10-24
I think you might be looking at something like this 

Most sys admins know the importance of keeping an action log where various tasks, configuration changes, etc. are kept. Simple logs indicating, "I did this" or "John did that" may be sufficient in some organizations, but for some, full transcripts of changes made are desired. Doing a copy-and-paste of terminal output can be tedious at best, so one answer is to use a little-known program called script, which is part of the util-linux package on most Linux distributions.

script records everything in a session: things you type and things you see. It even records color; so if your command prompt or program output contains color, script will record it.

To use script, simply execute:

$ script

By default, it writes to a file called typescript in the current directory. From then on, everything you type will be recorded to that file. To write to a different file, simply use script /path/to/file.

When you're done, type exit. This will close down the script session and save the file. You can now examine the file using cat or any other program.

The downside of using script is the fact that it records all special characters, so your output file will be full of control characters and ansi escape sequences. This can be avoided by using a very Spartan shell with script:

$ SHELL=/bin/sh PS1="$ " script

When using script, don't use interactive programs or programs that manipulate the screen, like vi or top. They will ruin the output of the session. Otherwise, any command line programs you use and the steps you take to accomplish a task will be recorded. If you do need to edit a file in the transcript, consider exiting the script session and restarting it after the file edit with script -a, which will append the new session to the old session. 

Hope that Helps

---

### Post by boson007 on 2009-10-25
so far I was copy-pasting the terminal output to a file, but your suggestion is much more convenient. Thank you dj-toonz!

---

### Post by MountainX on 2010-07-06
To clean up the script output (typescript file), see this helpful info:

[http://www.ibm.com/developerworks/aix/library/au-screenshots1/index.html?ca=drs-#script](http://www.ibm.com/developerworks/aix/library/au-screenshots1/index.html?ca=drs-#script)

---

