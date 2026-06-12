---
title: "Ubuntu stuck in &quot;simple&quot; or &quot;Recovery&quot; mode?"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by tomreid on 2010-04-18
Hi

My father in law had become a happy Ubuntu convert after having many issues before with windows viruses. 

I'm not sure how this came to happen though, he was installing some kind of update and the system now won't boot into the graphical operating system. 

See screenshot below, it seems to always boot into some kind of large terminal window. I have got some commands that seem like terminal commands to run.

I'm  not sure how to restore the system to work as before. 

Any help gratefully received.

cheers

---

### Post by J V on 2010-04-18
What happens if you hit ctrl alt F7?

---

### Post by quadproc on 2010-04-18
> **tomreid said:**
> Hi
...
See screenshot below, it seems to always boot into some kind of large terminal window. I have got some commands that seem like terminal commands to run.
cheers
Yes, your system is running in terminal mode.  The real question is why - there could be lots of reasons why it doesn't start in graphics mode any more.

Try this to see if graphics mode will run:
```
sudo service gdm start
```
If you get any error messages then please let us know.  If that line starts up graphics mode then you need to figure out why the graphics display manager is no longer being started automatically.  There are a bunch of files in /etc/init.d that get run at startup time; perhaps one or more of these is damaged or missing?

quadproc

---

### Post by tomreid on 2010-04-19
Hi

We got the error message "Unknown Job gdm". 

You may be able to see the full message from the attached screenshot.

cheers

---

### Post by tomreid on 2010-04-19
Oh and nothing happened when we hit ctrl alt F7

cheers

---

### Post by halitech on 2010-04-19
I'd almost make a guess that one of those updates was for the video card and it borked during install and took out the drivers and gdm. What kind of Toshiba laptop is he running? Do you know what video card he has?

---

### Post by quadproc on 2010-04-19
> **tomreid said:**
> Hi

We got the error message "Unknown Job gdm". 

That message suggests that X windows is not running.  The question would be "why isn't it?"  You may get some clues or hints from a couple of logs.

The system log at /var/log/syslog may say something useful; if you do a tail on it then you can read the last 24 or so entries.

Also, the X windows log at /var/log/Xorg.0.log may have something of use.  Maybe even dmesg in the same directory.

It would be useful to know if X windows starts up and then dies for some reason, or that it can't start for some reason.

quadproc

---

### Post by tomreid on 2010-04-19
Hi Halitech - I'd need to get the hardware details from him, from memory, the laptop is around 4 years old and is some form of Toshiba Satellite. I'm pretty sure the update has messed up the video card drivers somehow too.

Hi Quadproc - He gets the round Ubuntu logo after grub on power up, then it goes straight to the terminal window type environment. 

Can you let me know know how I call up "The system log at /var/log/syslog", etc?

cheers

---

### Post by quadproc on 2010-04-19
> **tomreid said:**
> 

Can you let me know know how I call up "The system log at /var/log/syslog", etc?

cheers
Sure, you have several choices.  Probably the simplest is System > Administration > Log File Viewer.  This will show you the most recent entries in the selected log.  It may not go back far enough to show what you want to see; more on this below.

Another choice is to use the Places function.  Select Computer > Filesystem > var > log > syslog; double click on syslog and the editor will start up and show the system log.

Or you could use the editor and open the syslog file.

Or you could use a command line and cat the chosen log file to the terminal, probably piping it through tail.

Many of the logs are automatically archived when they get to be large enough or old enough.  So the current log may not go back far enough for you to see what you are interested in.  The older logs are kept in the same directory but they are compressed.  To read one of them just double click on its folder in the Places dispaly and then uncompress it.

Edit: As halitech has noted (and I had overlooked), your graphics isn't working so the GUIs listed above won't work.  But you can use the cli and pipe through tail.

quadproc

---

### Post by halitech on 2010-04-19
since you can't get into the GUI, use 
```
lspci
```
to get the video card info
use
```
sudo cat /var/log/syslog | tail -n 20
```
to check the end of the log files

---

