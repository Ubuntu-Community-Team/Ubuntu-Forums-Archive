---
title: "&gt;:O     auto starting things in BASH"
date: 2010-08-17
forum: New to Ubuntu
---

### Post by B34ST1Y on 2010-08-17
Excuse the grumpy face in the title, but I am pulling my HAIR OUT trying to get a few simple commands to automatically issue when my Ubuntu machine starts up. 

I have checked other threads, and tried several things, from editing /etc/rc.local to allowing sudo without a PW for a specific script - nothing is seeming to work.

I have several miscellaneous commands that need to issue when the computer boots, and they need to be run as different users - some as root, and some as a different user. 

Can someone help me out? Or at least point me to a tried and tested tutorial? I don't want to have to use the GUI at all. There is a way, I know there is.

---

### Post by Zorgoth on 2010-08-17
to run a command as another user, you can use sudo -u.

---

### Post by B34ST1Y on 2010-08-17
Zorgoth - How can I achieve this without user interaction? I need (for example) a VNC server to startup with the user "owner" automatically when the server starts up, with no user interaction.

---

### Post by B34ST1Y on 2010-08-18
Does anyone know?? It needs to be 100% unmanned and start up automatically with the system.

---

### Post by nebileix on 2010-08-18
Try under System->Preferences->Startup Applications

Click add and enter command in there.

---

### Post by B34ST1Y on 2010-08-18
Nebileix -- I need to do this all without a gui, please :)

---

### Post by nebileix on 2010-08-18
> **B34ST1Y said:**
> Nebileix -- I need to do this all without a gui, please :)

Then try upstart.

It is the default to run services during boot for lucid.

[http://upstart.ubuntu.com/getting-started.html]("http://upstart.ubuntu.com/getting-started.html")

or

[http://wiki.frugalware.org/index.php/Upstart_Job_HOWTO]("http://wiki.frugalware.org/index.php/Upstart_Job_HOWTO")

---

### Post by B34ST1Y on 2010-08-18
Will this also work for Red Hat? I'm looking for the generic Linux autostart-a-script 100% unmanned. There has to be one....

---

### Post by nebileix on 2010-08-18
> **B34ST1Y said:**
> Will this also work for Red Hat? I'm looking for the generic Linux autostart-a-script 100% unmanned. There has to be one....

If you're using ubuntu lucid, then it is upstart.

As for redhat, i think they are still using rc to run jobs at different runlevel.(Not very sure thou)

---

### Post by B34ST1Y on 2010-08-18
ok, and then how can I get a script to run as userX without asking for a password?

---

### Post by nebileix on 2010-08-18
> **B34ST1Y said:**
> ok, and then how can I get a script to run as userX without asking for a password?

Please refer to Zorgoth reply or read the man page by

```
$ man sudo
```

---

### Post by P1ta on 2010-08-18
> **B34ST1Y said:**
> Nebileix -- I need to do this all without a gui, please :)

add your script to /etc/rc.local

---

### Post by B34ST1Y on 2010-08-19
> **P1ta said:**
> add your script to /etc/rc.local


Do I just dump the path to it into the rc.local file anywhere? I see a lot of what looks like code.

---

### Post by B34ST1Y on 2010-08-19
Ok, I dug up more of a reason why it "wasnt running" ....I dumped the output of the startup commands to a log file, and now its showing something like this (Tightvncserver output):

```
tightvncserver: The HOME environment variable is not set.
```


Now, I know rc.local is already running commands as root, correct? So it's trying to run tightvncserver, but bombing out because it cant load a profile right? How do I load a profile in the script? :-D

---

### Post by B34ST1Y on 2010-08-20
Any help on this last issue would help my overall problem a lot :)

---

### Post by AlphaLexman on 2010-08-20
The HOME environment variable is the current users home directory.

If I have followed the thread correctly, the script is run without any user input, and each user will have a different value of the HOME variable.

If you just need the script to execute for a certain user, you could edit the script and change the HOME variable to [ /home/username/ ].

---

### Post by B34ST1Y on 2010-08-20
Can you explain more? My "script" is one line of code - "tightvncserver"  and that's it.

---

### Post by B34ST1Y on 2010-08-20
this is the contents of my script:

```

#!/bin/bash
#!/usr/bin/tightvncserver
HOME=/home/vncuser
tightvncserver

```



I appended the HOME line to it, but after rebooting and checking the log -- it is still showing the same error. This script is being called from  /etc/rc.local and it it the ONLY line in the script. /etc/rc.local looks like this:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
sh /etc/init.d/tightvnc.sh > /var/tightvnclog.log 2>&1

```

---

### Post by Spice Weasel on 2010-08-20
Why don't you simply add the commands to your bashrc?

It's either at "~/.bashrc" for one user or "/etc/bash.bashrc" for global.

---

### Post by B34ST1Y on 2010-08-20
> **Spice Weasel said:**
> Why don't you simply add the commands to your bashrc?

It's either at "~/.bashrc" for one user or "/etc/bash.bashrc" for global.


For the sake of my original need, there will most likely be things running as multiple users. Wouldn't this create a conflict when the home path is hard coded to another user's path?

---

### Post by Spice Weasel on 2010-08-20
> **B34ST1Y said:**
> For the sake of my original need, there will most likely be things running as multiple users. Wouldn't this create a conflict when the home path is hard coded to another user's path?

This is why I would recommend using different user's bashrc to launch the programs that you need to run on that user. I'm not so sure how it would work out since I haven't ever tried something like this before, so I'm not sure about conflicts.

I'd try doing this in a VM first if you're unsure.

---

### Post by B34ST1Y on 2010-08-20
The server isn't in a production environment yet, so it's still OK to test things out. I added the line

```
HOME=/home/vncuser
```

to /etc/bash.bashrc   (at the top), but it's still giving the same error in  /var/tightvncserver.log   :mad::mad::mad:

---

### Post by Spice Weasel on 2010-08-20
I'm not sure what you're trying to do, but what about "su vncuser" in replace of changing the home directory?

E: This is in the script, of course. Putting "su" in your bashrc is a bad idea. :P

---

### Post by B34ST1Y on 2010-08-20
well, adding that got rid of the 'no HOME path' error --- but now there's a whole new slew of things showing in the error log

```
keyctl_search: Required key not available
Perhaps try the interactive 'ecryptfs-mount-private'
/bin/sh: /bin/sh: cannot execute binary file
keyctl_search: Required key not available
Perhaps try the interactive 'ecryptfs-mount-private'

```

---

### Post by Spice Weasel on 2010-08-20
That looks something like a permissions error, but I've got no idea what for.

---

### Post by B34ST1Y on 2010-08-23
It's probably something specific to the TightVNC program, but it's the standard APT package that comes with the distro. :(

---

### Post by nebileix on 2010-08-24
Sorry been busy lately.

Why not use different tty for different user and run the command in their individual .bashrc.

Try [HERE]("http://www.linuxadda.com/2010/01/enable-automatic-login-in-ubuntu-server.html")

---

