---
title: "Kino wont capture,&quot;Warning:1394 kernel...&quot;"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by MisFitt on 2010-02-04
Trying to capture video from mini DV.
-WARNING:1394 kernel module not loaded or failure to read/write/dev/raw1394!-
is displayed at the bottom of the program.
My camera whilst connected/on via firewire doesn't appear to register anywhere that I can see,boot into windows and it's fine...but I don't want to.
Any advice/recommendations/hints on non-crashing,not overly complicated programs that work easily and well with Karmic would be ever-so gratefully received!

btw-I did go into synaptic package manager and reinstalled Kino,same error.......

---

### Post by audiomick on 2010-02-04
Hi.
I don't know much about firewire; don't use it on the Ubuntu machine.
You probably already know that IEEE 1394 = fire wire, so the "raw1394" that it is complaining about is something to do with dealing with fire wire.

Open the synaptic package manager in system> administration and search "libraw1398". That is installed on mine, and looks like it _might_ have some relevance.

Yes, I just had a look in the manual for the program "kino". That is a video editor that imports DV via firewire. According to that, raw1394 is a set of drivers for firewire. From your error message, I would say that what you are trying to use wants to use that driver.

Sorry I can't be more help.

---

### Post by MisFitt on 2010-02-04
No worries Michael,thanks VERY much,will try that,makes perfect sense seeing I reinstalled kino anyway....

Reinstalled the one previously marked,libraw1394-11
but there's 2 more,libraw1394-dev and -doc I see but haven't installed but wondering what they're for.
I must assume everything needed associated with firewire,kino would have been installed,
still coming up with the same error......grr!It's been a looong few hours

---

### Post by audiomick on 2010-02-04
Just to check: you searched libraw1394 in the synaptic package manager and it didn't show up

OOPS: I just noticed I made a typo, I wrote 1398, which is wrong...:redface:

I also checked the dependancies for "kino", and libraw1394 is there. That means, it must be installed, actually, and if it isn't, I would be inclined to de-install and re-install kino completely just to make sure it has everything it needs.

---

### Post by MisFitt on 2010-02-04
> **audiomick said:**
> Just to check: you searched libraw1394 in the synaptic package manager and it didn't show up

OOPS: I just noticed I made a typo, I wrote 1398, which is wrong...:redface:

I also checked the dependancies for "kino", and libraw1394 is there. That means, it must be installed, actually, and if it isn't, I would be inclined to de-install and re-install kino completely just to make sure it has everything it needs.
Oh dear,I've done that,even rebooted for good luck,same error message

---

### Post by audiomick on 2010-02-04
I see you were editing as I was posting...
a dev file is usually not necessary for a Joe Bloggs user. They contain stuff that developers need.
a doc file is documentation. Might be interesting to look at, but I have no idea how it is accessed. It doesn't appear to be a man page. I installed it, and it doesn't show up in "man" from the terminal or in the Ubuntu help.

You've probably already seen this:
[https://help.ubuntu.com/community/Firewire](https://help.ubuntu.com/community/Firewire)

---

### Post by MisFitt on 2010-02-04
No I hadn't,thanks for saving me the search.
I do know that kino worked in my first karmic install........
looks like reading and checking back here,I'll give it another hour MAX tonight

---

### Post by Mustache Villain on 2010-02-04
Follow [this guide]("http://ubuntuforums.org/showthread.php?p=7596299#post7596299"), it seems like Ubuntu disables access to raw1394 due to security reasons.

---

### Post by MisFitt on 2010-02-04
what does "run it again as root" mean when I am using the terminal?
-very late here,a lot to learn after a sleep methinks,ta

---

### Post by audiomick on 2010-02-04
"run it again as root" means you need root privileges for whatever it is you were trying to do.

If it is a command line thing, put "sudo" and a space in front of whatever the command was. You will be asked for your user password, which you will not see as you type it in. Type your password and hit enter, and it should go.

If the command starts something with a graphical interface, like gparted for instance or the nVidia settings application or nautilus, the file manager, you should use "gksu" instead of "sudo".

There is a (short) page about it here
[https://help.ubuntu.com/8.04/administrative/C/terminal.html](https://help.ubuntu.com/8.04/administrative/C/terminal.html)
and a wikipedia page here
[http://en.wikipedia.org/wiki/Sudo](http://en.wikipedia.org/wiki/Sudo)



and some info here
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

The whole psychocats site is interesting, actually.edit:

just had a look at what the Mustache Villain linked to.
You mean this bit
> Now plug in your camercorder and run Kino. You'll most likely get an error in the status bar at the bottom of the program window when you click on the Capture tab.

 	Code:
 	$ gksudo kino 
Now run it again as root. If it works this time then these instructions should work for you. If not... well then, it sucks to be you.

I think.
It is a bit poorly laid out. The command above the words "now run it again as root" will start Kino with root privileges. That also looks like it might be the problem. The error you had could easily be that you (i.e. user you) doesn't have the right to access the file that the driver wants to access. Setting up a udev rule should sort that out. I had a similar issue with USB whilst trying to get Evolution to talk to my phone (had it working for a while, then something changed and it stopped...). I had to make a new udev rule to get that going.

---

### Post by MisFitt on 2010-02-04
One very simple thing I need to know is when I'm given 2 commands to put into terminal do I copy/paste them consecutively or both together?:-k

---

### Post by MisFitt on 2010-02-05
YES!!!
Thanks very,very much!

---

### Post by MisFitt on 2010-02-05
YES,thanks AudioMick,once again you've helped me,along with MV's link.
Appreciated more than you know.
I'm baffled as to why such a matter as firewire/dv was not dealt with BEFORE release,let alone today,seems a lot of people have had to deal with it.6 months ago I'd've had Buckley's chance,zero and would have been forced to bin it and look elsewhere.

OH AND REBOOT!!!!!! It only worked AFTER rebooting.

It's 2 weeks later and I've come back to my own thread because I'm having the same problem with a fresh install of Jaunty,64 bit.(dual-boot with xp pro 32 bit)
I gave up on Karmic as programs kept crashing,freezing and am trying 64 bit(Jaunty)for the 1st time.

---

