---
title: "ssh + vnc, remote network admin help"
date: 2007-04-10
forum: Networking &amp; Wireless
---

### Post by tedrampart on 2007-04-10
please forgive me if I'm asking a silly question.  I'm sort of a network n00b.. I've searched, and came close, but no cigar...

I recently got a network up and running at work, where sadly I'm the administrator of the network (the other folk have no clue whats going on).  

I setup remote desktop, and SSH with a DDNS, so I could fix stuff off site.  both SSH and rdesktop work fine (well, aside from locking up mouse input on the remote systems).

what I can't seem to figure out, is how to load applications from the SSH bash, and have them appear on the remote desktop.

I've tried:
  export DISPLAY="localhost:0", but that didn't work, I've also tried replacing "localhost" with the hostname of the remote computer, and still keep getting errors stating it can't load gtk, or visual etc.. and the app doesn't appear on the screen.  

please bear in mind, I'm not trying to X forward, I guess its the opposite of that.  

I know, I could just open a terminal on the desktop through VNC, but alot of times, its just easier and faster to do it from SSH bash..

please give me some advice, or point me to a thread that will help. :confused: 

thanks

---

### Post by thelinuxguy on 2007-04-10
> **tedrampart said:**
> 
I've tried:
  export DISPLAY="localhost:0", but that didn't work, I've also tried replacing "localhost" with the hostname of the remote computer, and still keep getting errors stating it can't load gtk, or visual etc.. and the app doesn't appear on the screen.  


I had taken this down from a site long ago but haven't used it myself. It may work for you.

After SSHing to the remote machine, **gain root** and use the following commands:
```

$ XAUTHORITY=/home/<username>/.Xauthority
$ export XAUTHORITY
$ DISPLAY=:0
$ export DISPLAY

```

Let me know if it really works.

---

### Post by tedrampart on 2007-04-10
> **thelinuxguy said:**
> I had taken this down from a site long ago but haven't used it myself. It may work for you.

After SSHing to the remote machine, **gain root** and use the following commands:
```

$ XAUTHORITY=/home/<username>/.Xauthority
$ export XAUTHORITY
$ DISPLAY=:0
$ export DISPLAY

```

Let me know if it really works.

YES!!

it definately works.  now will I have to type that all in everytime I log in?  is it possible to make a script for this?

also where can I find info on what all this stuff means?

thanks a bundle..

---

### Post by twistedknight on 2007-04-10
if you can ssh into a remote machine you can do x11 forwarding with a trailing -X

a good lookup for you would be x11 forwarding with SSH

---

### Post by tedrampart on 2007-04-11
> **twistedknight said:**
> if you can ssh into a remote machine you can do x11 forwarding with a trailing -X

a good lookup for you would be x11 forwarding with SSH

isn't x11 forwarding meant to load the app onto my desktop, and not the remote desktop?  I need the app to load onto the remote desktop, and I'll view it on vnc...

the one above worked nicely the first time, but the second time I tried it I got the same errors.. I'll try again right now.

edit - its definately not working now.  I tried a few times tonight, and can't seem to get it to work.  Pops up with the original error.  strange that it worked once, and then no more.

---

### Post by twistedknight on 2007-04-12
yes the apps x output is forwarded to your local screen but it runs off the remote systems hardware ie filesystem cpm mem all that jive and any config changes or file edits effect the remote sys

---

### Post by tedrampart on 2007-04-14
> **twistedknight said:**
> yes the apps x output is forwarded to your local screen but it runs off the remote systems hardware ie filesystem cpm mem all that jive and any config changes or file edits effect the remote sys

but thats not what I need.. I need the apps x output to display on their screen, not mine.
  
this worked once, but then it never worked again:
$ XAUTHORITY=/home/<username>/.Xauthority
$ export XAUTHORITY
$ DISPLAY=:0
$ export DISPLAY

---

### Post by thelinuxguy on 2007-04-14
> **tedrampart said:**
> 
this worked once, but then it never worked again:
$ XAUTHORITY=/home/<username>/.Xauthority
$ export XAUTHORITY
$ DISPLAY=:0
$ export DISPLAY

Have the permissions for the .Xauthority file changed after u ran the above? Can u try setting the permissions and ownership back to the original user (if it has changed) and running it again?

---

### Post by thelinuxguy on 2007-04-14
If the above doesn't work, try setting XAUTHORITY with every command you issue. This is inconvenient but see if it works.

Example: $ XAUTHORITY=/home/<username>/.Xauthority gedit

More information about this can be found in the "How do I run an X client as root when the X session is run by a user?" section at [http://www.ambienteto.arti.beniculturali.it/cgi-bin/dwww?type=file&location=/usr/doc/xfree86-common/FAQ.gz](http://www.ambienteto.arti.beniculturali.it/cgi-bin/dwww?type=file&location=/usr/doc/xfree86-common/FAQ.gz)

---

### Post by tedrampart on 2007-04-14
I'll read this over tonight and see if I can figure something out..

as far as setting the xauthority back to the original permissions/ownership, how would I go about doing that?  

sorry I'm a bit of a noob with the console commands...

---

### Post by thelinuxguy on 2007-04-15
> **tedrampart said:**
> 
as far as setting the xauthority back to the original permissions/ownership, how would I go about doing that?  


gksudo nautilus
Navigate to <username>'s home folder
View >> Show hidden files
Right click on .Xauthority >> properties >> permissions
Set the owner and group back to <username> (if it has changed)

---

### Post by tedrampart on 2007-04-15
okay, the .Xauthority was at the original user, so I went and put in the orginal list of commands you gave me, and it worked fine.  I'm not sure what happened between the original time it worked and the time it stopped working.  

I guess I'll have to double check the ownership again if it stops working.  thanks alot for your help, its definately needed!

edit ... so I got "sudo chown <username> /home/<username>/.Xauthority .. and then typed in the:
$XAUTHORITY=/home/<username>/.Xauthority
$export XAUTHORITY
$DISPLAY=:0
$export DISPLAY
and it works just fine.. 

now I just need that to be put into a script.  I've put in the following into "xauthscript.sh":
#!/bin/bash
$XAUTHORITY=/home/staff/.Xauthority
$export XAUTHORITY
$DISPLAY=:0
$export DISPLAY &

I've set the permissions and made it executable and all that jazz....it keeps saying that command not found for every line... so I tried the same with no "$"'s and didn't get the command not found routine.. but it didn't work.  any suggestions?

---

