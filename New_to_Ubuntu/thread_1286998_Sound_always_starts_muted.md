---
title: "Sound always starts muted"
date: 2009-10-09
forum: New to Ubuntu
---

### Post by Cuco3 on 2009-10-09
If you're using a Sound Blaster card (might work with other sound cards) and your Volume is always on mute when you start your computer, try following:
> 
Run "alsamixer" at the terminal or use the GUI volume control and set all sliders as desired.  When done press Esc
to exit.

on a terminal screen, run ```
sudo alsactl store [COLOR=Red]0[/COLOR]
``` [or if this is your nth sound card [where n is the number of soundcards in your computer) replace 0 with n-1] [I][COLOR=Silver]then on the terminal, run:[code]gksudo gedit /etc/rc.local[/code.][/COLOR][COLOR=Silver]add the following line at the end: /usr/sbin/alsactl restore


Save the file and you're done. Restart your computer to see if it works.[/COLOR][/I]  Source: [https://help.ubuntu.com/community/SoundTroubleshooting ]("https://help.ubuntu.com/community/SoundTroubleshooting")
Source: [http://linux.derkeiler.com/Newsgroups/comp.os.linux.misc/2007-02/msg00170.html](http://linux.derkeiler.com/Newsgroups/comp.os.linux.misc/2007-02/msg00170.html) 

Thanks to person who provided this help!

---

### Post by mac9416 on 2009-10-09
Several problems:

> mac9416@mac9416-laptop:~$ sudo alsactl store
[sudo] password for mac9416: 
Home directory /home/mac9416 not ours.

That doesn't seem right.

Also, you instructed to add "/usr/sbin/alsactl restore" at the *end* of /etc/rc.local, when I believe it should be *before* "exit 0". 
And when I ran "/usr/sbin/alsactl restore" from the terminal, it said "No such file or directory", although just "alsactl restore" worked fine. Apparently, alsactl is in a different directory.

Despite this, thanks for the howto because this is one of the few glitches still in my Karmic install. Hopefully we can solve these couple of problems. :)

Thanks!

---

### Post by Cuco3 on 2009-10-10
I found that Ubuntu Wiki has the same thing posted (a bit different, too) so I switched it to their procedure, which is one step easier, and added the link for those who want to read more.

The difference is marked with red and the parts removed are greyed out.

---

### Post by mac9416 on 2009-10-10
> mac9416@mac9416-laptop:~$ sudo alsactl store 0
Home directory /home/mac9416 not ours.

Although that error apparently has no effect on the final result, when I rebooted the sound was still muted. And here's the problem:

> mac9416@mac9416-laptop:~$ /usr/sbin/alsactl restore
bash: /usr/sbin/alsactl: No such file or directory

This did the trick:

> mac9416@mac9416-laptop:~$ /sbin/alsactl restore

Although I doubt it's necessary, I added the command to ~/.fluxbox/startup to be sure.

Thanks again!

---

### Post by justanotherperson on 2010-02-18
>___> i cant get to ~/.fluxbox/startup file or directory not found and the top commands also gave me the weird not ours thing + the alternative did not work lol :confused:

---

### Post by mac9416 on 2010-02-18
Hey,

Someone found a better way to solve this problem. You can find their method here: [http://ubuntuforums.org/showthread.php?p=8342636#post8342636](http://ubuntuforums.org/showthread.php?p=8342636#post8342636)

Hope that works!

---

