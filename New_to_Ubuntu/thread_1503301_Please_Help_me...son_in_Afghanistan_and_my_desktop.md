---
title: "Please Help me...son in Afghanistan and my desktop is gone."
date: 2010-06-06
forum: New to Ubuntu
---

### Post by militarymom8183 on 2010-06-06
It just disappeared after i had downloaded apps and shut down and did a restart. I can login and that is it. I spent 12 hrs yeturday trying to fix it myself with no luck. I do have the LiiveCD and tried to do the fix in terminal. I am doing something wrong. It says it doesnt recognize it. And u just cant imagine how excited I was to find that...write it on paper and run to the other room...type sudo Grub...and nothing. Says it does not recognize/know it. EEEEEEERRRRRRRR!!!!!!!!! Please tell me word for word how to do it please. Thank you so much. I have ran this program a 1/2 hr and think I really like it. Have only had the computer for 2 days period. I am a true beginner in all ways. I did learn one thing tho...my decision to t
ake computer classes has been reinforced 100 x. This fall!!!!
 
 
Thank you all who read and those who help me too. I am ready and waiting. My son is at war and we talk on YAHOO and SKYPE IM......the computer i am on has to go back soon. Then I will have nothing if this problem cant be worked out.
I have 10.4 Unbuntu...
 
Thank you in advance for all ur help.:)

---

### Post by halitech on 2010-06-06
if you can log in but are stuck at a terminal screen, try typing 
```
startx
```
and see if you get the gui back

---

### Post by sgosnell on 2010-06-06
The first thing to do is calm down, and slow down.  I'm still not sure exactly what your problem is, but I'm sure it can be fixed.  The first thing to remember is that everything in Linux is case-sensitive.  That means that grub, Grub, and GRUB are different things.  You have to get everything in the correct case, almost always all-lower-case, but not always.  If you can explain precisely what you're doing and the exact result, we can get you working.

---

### Post by lkraemer on 2010-06-07
Can you describe with more detail what was installed and what you are
seeing when you boot your Desktop.  The only way folks can assist is to
know what your Desktop Display is showing.  A Picture might be 
worthwhile, just take a snapshot, then if you can convert it to a png
type file, and post so it doesn't exceed the upload limits.

So, describe what you are seeing, then don't be so quick to install or
update software on a new system that you depend on for communications.

If you installed the latest Nvidia drivers (Hardware Drivers), you might
be dumped out to a Terminal Window.  I've had that happen on 8.04.4
Look at the Top line text on the Display.  Does it look like this:
```

Ubuntu 10.04 LTS xxxxx-laptop tty1
xxxxx-laptop login:

```
Notice the tty1 on the first line.  You can get there from the GUI by using
CNTL ALT F1 (where you depress CNTL and while keeping it held down you also
depress ALT, and then also F1 ...... to access tty1. There are F1 thru F6 for
tty1 thru tty6, and CNTL ALT F7 will take you back to the GUI.....assuming
that startx is running.)

If you are at tty1, do as halitech suggests and try running:
```

startx

```
If that doesn't get you to the GUI, try CNTL ALT F7
If that doesn't work go back to tty1 with CNTL ALT F1

We may need to do the following ONLY after you describe what you did
and what you are seeing on the Display...............................
BUT STOP HERE ........UNTIL YOU POST MORE INFORMATION................

REF:
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

If you are NOT in the Graphical User Interface (GUI) or tty1 (maybe you
have a blank screen after boot-up).  Do CTRL ALT F1 to get to tty1, and
login with your username and password.

Then, depending on your desktop environment, and I assume it is GNOME, run
..........For Gnome (Ubuntu) = gdm  Kubuntu= kdm  XFCE=xdm
```

sudo /etc/init.d/gdm stop

```
Run the reconfiguration after making a backup.......
First start by making a manual backup (even though one will be auto-generated
in the form xorg.conf.YearMonthDayTime):
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

```
Now run the configuration:
```

sudo dpkg-reconfigure xserver-xorg -phigh

```
Restart the GUI

You are in a tty, so run:
```

sudo /etc/init.d/gdm start

```
Then restart X.
```

startx

```

lk

---

