---
title: "Mail Notification at boot-up?"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by bug67 on 2009-08-18
I've got the application "Mail Notification" set up to start when I start my computer.  I did this by adding it to "Startup Programs" in System Preferences.  Problem is, it *never* starts up when I start my computer.  I always have to launch it myself.  It works fine after I do launch it.  How can I remedy it not starting up at boot?

---

### Post by colsandurz on 2009-08-19
try 

```

sudo rc-update /path/to/script default

```

not sure if this will work entirely, I've never done this using an absolute path.  If that doesn't work you can try putting a symbolic link to the script in /etc/init.d and removing the path in the rc-update.

---

### Post by SoftwareExplorer on 2009-08-19
I had problems with starting things with startup programs because you can't make them go in a specific order. Maybe that's the problem? I don't really know anything about mail notification but that might be the problem. You can solve it by writing a script like this
```
#!/bin/bash
sleep 10
<command to run>
```Save it.
Right click on it, go to properties, permissions, and set it as executable. 
Have the startup programs run the script.

Hope that helps. If you need clarification or it doesn't make sense just ask, I'm just tired right now.

---

### Post by jrox717 on 2009-08-19
In Startup Applications, look at what command is actually supposed to run (under Edit). Maybe it has some options attached to it which make it not work properly? Try launching the program from the command line and then use that command in the Startup Applications form.

---

### Post by bug67 on 2009-08-20
> **jrox717 said:**
> In Startup Applications, look at what command is actually supposed to run (under Edit). Maybe it has some options attached to it which make it not work properly? Try launching the program from the command line and then use that command in the Startup Applications form.

I've actually got the path to the location of the app itself (/usr/share/applications/mail-notification.desktop) set up as the launch point.  I guess that's not how it works?  How do I launch from terminal and use that command as the start at boot command?  Thanks.

---

### Post by jrox717 on 2009-08-20
Try typing in "mail-notification.desktop" into the terminal. The command should actually be the name of a program in /usr/bin, so you can look around there to find the correct file if the first one doesn't work. Once you find the command, you can put that in the "command" box in Startup Applications.

---

### Post by bug67 on 2009-08-20
> **jrox717 said:**
> "...The command should actually be the name of a program in **/usr/bin**..."

That was it.  It starts up now @ boot but now I have another issue.  I have it "checking" an IMAP account (MobileMe) as default and for some reason, it's not automatically connecting to it.  After I right click on the little flashing "error" icon and choose "refresh," everything works as it should.  However, I'd rather everything just happen.  Thanks for the pointers to where the actual program was located.  At least I got that sorted!  :D

**_EDIT_**:

I think what may be happening is this application is launching before my Internet connection is established.  Anyway to tell it to wait until after a connection is established?

---

### Post by pedro3005 on 2009-08-21
As said before, try putting this on the command.
'sleep 10 && command'

---

### Post by bug67 on 2009-08-27
Mr. SoftwareExplorer walked me through it and I got it working.  Thanks!

Now, how do I mark this thread as "Solved?"

---

### Post by SoftwareExplorer on 2009-08-28
You can go to the first post and edit it. Add [Solved] to the start of the title. You can also scroll down to the bottom of the page and add a solved tag. (Well, actually, I'm even allowed to do that, so I think I will)

---

