---
title: "Wacom Bamboo CTL 460 tablet acts strange after a 'tap'"
date: 2011-06-10
forum: New to Ubuntu
---

### Post by ravinderw on 2011-06-10
Hello All,
 
I'm running ubuntu and a user of the OS rather than someone that delves under the hood. 
 
About a year back I managed to get my Wacom bamboo 460 working and all was good. I haven't used it for a while and needed to a couple of days ago. 
 
Plugging it in it seemed to work, but it exhibits a strange behaviour in that once I've tapped the pad with the pen, it seems not recognise any movement of the pen, unless I tap and drag the pen.
 
The nib of the pen is not sticking as I've tried drawing a pressure sensitive line in gimp and that shows the nib responding to pressure.
 
I've also booted into windows and found that it works perfectly there. I tried following some of the tutorials that I had previously bookmarked and am not having any luck.
 
Any suggestions?
 
Thanks!

---

### Post by Favux on 2011-06-10
Hi ravinderw,

Let's find out if your Bamboo Pen is on the Wacom X driver.  Enter in a terminal the following commands:  *xinput list* and *xsetwacom list*.  And post the outputs.

---

### Post by ravinderw on 2011-06-10
Thanks Favux for the reply.

for xinput list I get

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 4x5 Pen                        id=9    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 4x5 Finger                     id=10    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=12    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=14    [slave  keyboard (3)]


For xsetwacom list nothing is returned.

Does that help with the diagnosis?

Thanks.

---

### Post by Favux on 2011-06-10
Yes.  We can tell it is not on the Wacom X driver.  It's probably on the evdev X driver.

Check in /usr/lib/X11/xorg.conf.d and see if you have a 10-wacom.conf.  If you do please post the contents.  By the way I'm guessing you are using Lucid.  If I'm wrong let me know.

---

### Post by ravinderw on 2011-06-10
in /usr/lib/X11/xorg.conf.d/ I have 

05-evdev.conf
10-synaptics.conf
10-vmmouse.conf

Nothing else.

For the version of ubuntu, I found on the web to check type lsb_release -a and I got 

Distributor ID:    Ubuntu
Description:    Ubuntu 10.04.2 LTS
Release:    10.04
Codename:    lucid

Many thanks for the time.

---

### Post by Favux on 2011-06-10
Alright.  I guessed correctly and it is Lucid.

You'll need to manually add the 10-wacom.conf.  Use the example wacom.conf in part III. of the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") with the Lucid gedit line.  Just copy and paste the contents of the example into the empty file that opens up, Save, Close, and reboot.

And please consider joining this Launchpad bug report:  [https://bugs.edge.launchpad.net/ubuntu/+bug/770082](https://bugs.edge.launchpad.net/ubuntu/+bug/770082)  The more people who post on it the more likely they are to fix the issue.

---

### Post by ravinderw on 2011-06-10
Thanks Favux worked exactly as you said. 

I used xinput --list, to sort out my .xsetwacom.sh file and all is good to go. Till next time anyway.

Thanks again!!

---

