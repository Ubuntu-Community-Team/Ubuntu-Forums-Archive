---
title: "Mouse stuck in a strange mode"
date: 2010-08-29
forum: New to Ubuntu
---

### Post by theepdinker on 2010-08-29
My mouse clicks are stuck in a strange mode.  I now have to hold down Ctrl and/or Shift to make it select like it used to (and I am getting tired of pressing those for every click).  If I don't press one of those keys, I just get a hand cursor that can re-position a window, but not select things.

This started when I installed the sugar-emulator-0.88 via the Synaptic Package Manager (Ubuntu 10.04).  The Sugar emulator runs in a Zephyr window, and one uses Ctrl-Shift mouse clicks to shift between emulator window and native window.  So, I suspect some bug got the mouse stuck in an odd-ball mode.

I tried un-installing the Sugar emulator, but that didn't help.  

Anyone know how to get the mouse back to a "normal" mode?

---

### Post by sandyd on 2010-08-29
> **theepdinker said:**
> My mouse clicks are stuck in a strange mode.  I now have to hold down Ctrl and/or Shift to make it select like it used to (and I am getting tired of pressing those for every click).  If I don't press one of those keys, I just get a hand cursor that can re-position a window, but not select things.

This started when I installed the sugar-emulator-0.88 via the Synaptic Package Manager (Ubuntu 10.04).  The Sugar emulator runs in a Zephyr window, and one uses Ctrl-Shift mouse clicks to shift between emulator window and native window.  So, I suspect some bug got the mouse stuck in an odd-ball mode.

I tried un-installing the Sugar emulator, but that didn't help.  

Anyone know how to get the mouse back to a "normal" mode?
I think it killed the mouse bindings...
try
```

sudo apt-get install sugar-emulator-0.88
sudo dpkg --purge sugar-emulator-0.88 
```

---

### Post by theepdinker on 2010-08-29
Thanks, I tried that, but it didn't fix it

---

### Post by jtarin on 2010-08-29
Try Systems>ControlCenter>Personal>KeyboardShortcuts. See if your shortcut is bound there.
Also look in /home/username/.configs to see if any sugar configs were left over. Maybe it has its own folder in the /home/username. And System>Preferences>StartupApplications and look for associations.

---

### Post by theepdinker on 2010-08-29
Thank you, I just tried your suggestions but the mouse is still in the strange mode.

The mouse appears to be in a Macintosh emulation mode.  Anyone know how to get it out of that mode?
Or is that not the cause of my problem?

don@ubuntu:~$ lshal | grep mouse
  info.capabilities = {'input', 'input.mouse'} (string list)
  info.product = 'Macintosh mouse button emulation'  (string)
  input.product = 'Macintosh mouse button emulation'  (string)
  info.product = 'IBM Enhanced (101/102-key, PS/2 mouse support)'  (string)
  pnp.description = 'IBM Enhanced (101/102-key, PS/2 mouse support)'  (string)
  info.linux.driver = 'psmouse'  (string)
  info.capabilities = {'input', 'input.mouse'} (string list)
don@ubuntu:~$

---

### Post by jtarin on 2010-08-29
Not a solution.....10.04 doesn't have HAL they use UDEV.

---

### Post by sandyd on 2010-08-29
> **theepdinker said:**
> Thank you, I just tried your suggestions but the mouse is still in the strange mode.

The mouse appears to be in a Macintosh emulation mode.  Anyone know how to get it out of that mode?
Or is that not the cause of my problem?

don@ubuntu:~$ lshal | grep mouse
  info.capabilities = {'input', 'input.mouse'} (string list)
  info.product = 'Macintosh mouse button emulation'  (string)
  input.product = 'Macintosh mouse button emulation'  (string)
  info.product = 'IBM Enhanced (101/102-key, PS/2 mouse support)'  (string)
  pnp.description = 'IBM Enhanced (101/102-key, PS/2 mouse support)'  (string)
  info.linux.driver = 'psmouse'  (string)
  info.capabilities = {'input', 'input.mouse'} (string list)
don@ubuntu:~$
can you post the output of
```

cat /etc/X11/xorg.conf
```

---

### Post by jtarin on 2010-08-29
> can you post the output of

cat /etc/X11/xorg.conf

Probably doesn't have one. He's running Ubuntu 10.04 Lucid Lynx.

Can you run this command:```
xinput list | grep 'id='
```

---

### Post by wojox on 2010-08-29
> **jtarin said:**
> Probably doesn't have one. He's running Ubuntu 10.04 Lucid Lynx.

Can you run this command:```
xinput list | grep 'id='
```

If he's running a nvidia card/chip he has one. ;)

---

### Post by pastalavista on 2010-08-29
It sounds to me like one of your Alt keys is stuck.

---

### Post by jmfal on 2010-08-29
or try this ::::::::put new batteries in your mouse

---

### Post by jtarin on 2010-08-30
> **wojox said:**
> If he's running a nvidia card/chip he has one. ;)
No matter one way or the other....it's still UDEV and there's no need to edit anything....just run the command I gave you and let's see the output. I only need one number.

---

### Post by salinmooch on 2010-08-30
I ran into this exact issue tonight, also after installing the sugar-emulator (0.87-2) package on lucid.  I uninstalled sugar and xephyr = no luck.  I can operate normal clicks if I push the alt button down, if not it defaults to alt-click behavior.  :(

Output of above commands:
```

lshal | grep mouse
  info.capabilities = {'input', 'input.mouse'} (string list)
  info.product = 'Macintosh mouse button emulation'  (string)
  input.product = 'Macintosh mouse button emulation'  (string)
  info.product = 'IBM Enhanced (101/102-key, PS/2 mouse support)'  (string)
  pnp.description = 'IBM Enhanced (101/102-key, PS/2 mouse support)'  (string)
  info.linux.driver = 'psmouse'  (string)
  info.capabilities = {'input', 'input.mouse', 'input.touchpad'} (string list)
  info.capabilities = {'input', 'input.mouse'} (string list)

:~$ xinput list | grep 'id='
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                                  id=11    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                    id=12    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Chicony USB 2.0 Camera                      id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]


```

---

### Post by jtarin on 2010-08-30
See below

---

### Post by jtarin on 2010-08-30
Enter this command and check your mouse. ```
xinput set-button-map 11 1 2 3 4 5 9 8 6 7
```then reboot and check again.

---

### Post by salinmooch on 2010-08-30
No joy.  I tried:

```
xinput set-button-map 11 1 2 3 4 5 9 8 6 7
```

followed by reboot and no luck.   If it helps I started a guest session and did not have the stuck in "alt-click" problem, so I'm happy to copy over or delete whatever config file is causing this.   Also, I do not understand the xinput output I posted above but I am only using the ALPS touchpad on this computer, I do not have any other mouse plugged in.

---

### Post by jtarin on 2010-08-30
> **salinmooch said:**
> No joy.  I tried:

```
xinput set-button-map 11 1 2 3 4 5 9 8 6 7
```

followed by reboot and no luck.   If it helps I started a guest session and did not have the stuck in "alt-click" problem, so I'm happy to copy over or delete whatever config file is causing this.   Also, I do not understand the xinput output I posted above but I am only using the ALPS touchpad on this computer, I do not have any other mouse plugged in.
Then 
```
xinput set-button-map 12 1 2 3 4 5 9 8 6 7
```If it works reboot and try again. If it stays...good if not we will try one other thing.

---

### Post by salinmooch on 2010-08-30
Followed your suggest and tried id 12 via:

```
xinput set-button-map 12 1 2 3 4 5 9 8 6 7
```

No luck there.  I did notice in gconf-editor there is still an entry for /desktop/sugar there are keys in /desktop/sugar/peripherals/keyboard/  but the keys within have no value.

Let me know what else to try.  And thanks for the help!

---

### Post by jtarin on 2010-08-30
Post the output of  ```
xinput list-props 12
```or
 ```
xinput list-props AlpsPS/2 ALPS GlidePoint
```

---

### Post by salinmooch on 2010-08-30
Out of curiosity I tried a brute force fix - I backed up my ~/.gconf directory, created a new user and copied the newuser's ~/.gconf over to my own directory and that fixed the 'alt-click' issue, :D of course reseting many of my settings. :( 

I tried running gconf-cleaner on my original .gconf setup which removed a bunch of old keys - but it did not fix the mouse button issue.  

So, it wouldn't take to long to redo my settings, but I'd rather just fix the faulty setting if I knew where it was!

---

### Post by salinmooch on 2010-08-30
Ok out put of the command (note, this is with the faulty .gconf):


```
xinput list-props 12
Device 'AlpsPS/2 ALPS GlidePoint':
    Device Enabled (154):    1
    Device Accel Profile (271):    0
    Device Accel Constant Deceleration (272):    1.000000
    Device Accel Adaptive Deceleration (274):    1.000000
    Device Accel Velocity Scaling (275):    10.000000
    Synaptics Edges (289):    153, 870, 115, 652
    Synaptics Finger (290):    12, 14, 127
    Synaptics Tap Time (291):    180
    Synaptics Tap Move (292):    56
    Synaptics Tap Durations (293):    180, 180, 100
    Synaptics Tap FastTap (294):    0
    Synaptics Middle Button Timeout (295):    75
    Synaptics Two-Finger Pressure (296):    139
    Synaptics Two-Finger Width (297):    7
    Synaptics Scrolling Distance (298):    25, 25
    Synaptics Edge Scrolling (299):    1, 0, 0
    Synaptics Two-Finger Scrolling (300):    0, 0
    Synaptics Move Speed (301):    0.400000, 0.700000, 0.039124, 40.000000
    Synaptics Edge Motion Pressure (302):    14, 79
    Synaptics Edge Motion Speed (303):    1, 102
    Synaptics Edge Motion Always (304):    0
    Synaptics Button Scrolling (305):    1, 1
    Synaptics Button Scrolling Repeat (306):    1, 1
    Synaptics Button Scrolling Time (307):    100
    Synaptics Off (308):    0
    Synaptics Guestmouse Off (309):    0
    Synaptics Locked Drags (310):    0
    Synaptics Locked Drags Timeout (311):    5000
    Synaptics Tap Action (312):    2, 3, 0, 0, 1, 3, 2
    Synaptics Click Action (313):    1, 1, 1
    Synaptics Circular Scrolling (314):    0
    Synaptics Circular Scrolling Distance (315):    0.100000
    Synaptics Circular Scrolling Trigger (316):    0
    Synaptics Circular Pad (317):    0
    Synaptics Palm Detection (318):    0
    Synaptics Palm Dimensions (319):    10, 99
    Synaptics Coasting Speed (320):    0.000000
    Synaptics Pressure Motion (321):    14, 79
    Synaptics Pressure Motion Factor (322):    1.000000, 1.000000
    Synaptics Grab Event Device (323):    1
    Synaptics Gestures (324):    1
    Synaptics Capabilities (325):    1, 1, 1, 0, 0
    Synaptics Pad Resolution (326):    1, 1
    Synaptics Area (327):    0, 0, 0, 0
    Synaptics Jumpy Cursor Threshold (328):    0
```

---

### Post by jtarin on 2010-08-30
A comparison between the two files, ~/xmodmap, ~/xinput in the /home/**username** directory and the /home/**new-username** directory would probably show something.Your old conf shows the touchpad enabled "1"="on".....Does anything work in your touchpad, at all?

---

### Post by jtarin on 2010-08-30
I would like to hear from the original thread starter before this thread got off topic from mouse to touchpad!

---

### Post by salinmooch on 2010-08-30
I diff'ed the directories and there are to many things different between the two for me to start on.  I do not have a ~xmodmap or ~xinput in either directory. . . hmmm...  I should add the touchpad works fine, and the keyboard work fine . . . . just when I right or left click its does the equivalent of a alt+left click or alt+right click.  Thus instead of clicking on a link in fire fox - it instead allows me to grab the window and move it (as you would if you alt+click).  It happens for all windows.


since I kind of hijacked this thread - I'll give a quick summary of my issue to this point:

I found I had a problem where my left clicks on my laptop where performing the equivalent of a alt+lef click.  I searched about and came across this thread - the originator stating they had install sugar-emulator and afterwards came across this problem.

I realized that I just installed the same package.  So I did an uninstall with purge and deleted the ~/.sugar directory.  With a reboot, no luck.  With jtarin's xinput suggestions and reboot - still no luck.  I noticed a sugar entry in gconf (under /desktop/sugar).  To my untrained eye nothing seemed amiss in this directory.  I tried gconf-cleaner which removed a bunch of keys, but the problem remained (and the sugar keys remained).  However, when I replaced my .gconf folder with that from a freshly added new user it fixed the alt- click issue for me however, with the issue that I have to reconfigure settings on my desktop and some gnome apps.

This brute force fix doesn't really tell me what the problem was though . . .  but its a livable solution.




> **jtarin said:**
> A comparison between the two files, ~/xmodmap, ~/xinput in the /home/**username** directory and the /home/**new-username** directory would probably show something.Your old conf shows the touchpad enabled "1"="on".....Does anything work in your touchpad, at all?

---

### Post by jtarin on 2010-08-30
I have to go out for a few hours but will be back to investigate this further unless someone comes up with a solution by then.

---

### Post by jtarin on 2010-08-30
Ok try to do a diff between the good and the bad of the command ```
xinput list-props 12
```

---

### Post by theepdinker on 2010-08-30
here:

don@ubuntu:~$ cat /etc/X11/xorg.conf
cat: /etc/X11/xorg.conf: No such file or directory

don@ubuntu:~$ xinput list | grep 'id='
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=10    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=11    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=13    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=15    [slave  keyboard (3)]
don@ubuntu:~$

---

### Post by theepdinker on 2010-08-30
And I checked some other user accounts that I had set up.  The other accounts still have "normal" mouse behavior, only "don@ubuntu" has the other mouse behavior.

---

### Post by jtarin on 2010-08-30
Enter this command and check your mouse.
```
xinput set-button-map 10 1 2 3 4 5 9 8 6 7
```
Doesn't work correctly try:
```
xinput set-button-map 11 1 2 3 4 5 9 8 6 7
```
if either work make note of which one, then reboot and check again.

---

### Post by salinmooch on 2010-08-30
> **jtarin said:**
> Ok try to do a diff between the good and the bad of the command ```
xinput list-props 12
```

Thanks again for all your help.

Done.  The diff reveals that in the working button case:

Synaptics Off (308): 1

and the nonworking (alt-click mode) case:

Synaptics Off (308): 0


This of course, makes no sense to me. . . as in both cases I'm using the touchpad.  I would ask xinput to change this setting just out of curiosity but I do not know how.  It seems like the bad setting may be somewhere else.

Now I am working with a new ~/.gconf imported from another user on the system, and I spent about 10 minutes reconfiging my system - so its a dirty but workable solution for me.  Now I'm just curious to what go changed.

---

### Post by jtarin on 2010-08-30
> **salinmooch said:**
> Thanks again for all your help.

Done.  The diff reveals that in the working button case:

Synaptics Off (308): 1

and the nonworking (alt-click mode) case:

Synaptics Off (308): 0


This of course, makes no sense to me. . . as in both cases I'm using the touchpad.  I would ask xinput to change this setting just out of curiosity but I do not know how.  It seems like the bad setting may be somewhere else.

Now I am working with a new ~/.gconf imported from another user on the system, and I spent about 10 minutes reconfiging my system - so its a dirty but workable solution for me.  Now I'm just curious to what go changed.Run the command ```
synclient -l
```

---

### Post by jtarin on 2010-08-30
Ok I found a guide to [test and configure touchpad ]("http://ubuntuforums.org/showthread.php?t=1401645")in Ubuntu. Mouse configuration is somewhat different, but neither are difficult.

---

### Post by vilcans on 2010-10-05
I'm the second one hijacking this thread saying "me too"!

The OP's problem is exactly the same as mine:

> **theepdinker said:**
> My mouse clicks are stuck in a strange mode.   I now have to hold down Ctrl and/or Shift to make it select like it  used to (and I am getting tired of pressing those for every click).  If I  don't press one of those keys, I just get a hand cursor that can  re-position a window, but not select things.

This started when I installed the sugar-emulator-0.88 via the Synaptic  Package Manager (Ubuntu 10.04).  The Sugar emulator runs in a Zephyr  window, and one uses Ctrl-Shift mouse clicks to shift between emulator  window and native window.  So, I suspect some bug got the mouse stuck in  an odd-ball mode.

I tried un-installing the Sugar emulator, but that didn't help.  

Anyone know how to get the mouse back to a "normal" mode?

I'll try to describe my problem in detail.

To be clear: There is nothing physically wrong with the mouse. I have  tested the "stick" on the keyboard (don't know what's it called, you  know the little thing between the g, h and b keys that IBM used to love)  and a USB mouse. Both have the same problem.

The problem only appears when I use the mouse. A mouse click is  interpreted as alt+mouse click. Middle-mouse click resizes the window  (just like alt+middle-mouse would normally). There is nothing wrong with  the keyboard. The alt key is not stuck when I'm using only the  keyboard. For example alt+f opens the File menu in the terminal. (If it  was stuck, pressing just F would open the File menu.)

Logging in as a different user removes the problem. xinput list-props  with all device numbers gives the exact same output on both users.

Help would be appreciated! I'm not very fond of the idea of creating a new login.

---

### Post by jtarin on 2010-10-05
You should read the entire thread then if it does not help post under your own thread as it will get answered specifically for your problem. Hijacking a thread is of no value to you if you are looking for an answer and you cannot find it in this thread..

---

### Post by vilcans on 2010-10-06
> **jtarin said:**
> You should read the entire thread then if it does not help post under your own thread as it will get answered specifically for your problem. Hijacking a thread is of no value to you if you are looking for an answer and you cannot find it in this thread..

Well, because I have the *exact* same problem as the OP, including getting it after installing Sugar, I thought it was a better idea to post in the same thread (which I have of course read). Silly me.

---

### Post by vilcans on 2010-10-08
OK, here's the solution:

Just remove .gconf/apps/metacity/general/%gconf.xml and the problem should go away. It did for me. :-)

I found this by using git bisect with a repo with one commit per file.

---

### Post by JohnR51 on 2010-10-22
Did you ever resolve this problem?  I just had the same thing happen when installing the Sugar emulator in Linux Mint.   Thanks /John

---

### Post by vilcans on 2010-10-25
Yes, read my last post. It fixed the problem for me.

---

### Post by bluetomgold on 2010-10-25
I have the same issue, following Sugar install and uninstall, with either the mouse or the touchpad. I wonder if anyone has actually installed Sugar with 10.04 and NOT had this problem...

I haven't managed to find the file below. None of the other fixes suggested have been reported to work so I'm inclined not to try them. 

> **vilcans said:**
> OK, here's the solution:

Just remove .gconf/apps/metacity/general/%gconf.xml and the problem should go away. It did for me. :-)

I found this by using git bisect with a repo with one commit per file.

I'd be glad to hear from anyone who has found a fix for this!

---

### Post by vilcans on 2010-10-25
Does it work if you log in as a different user?

I don't know why removing that file helped, but it seemed to contains some settings related to the mouse or keyboard.

---

### Post by bluetomgold on 2010-10-29
Creating a new user and logging in as that user has cleared it, yes. Thanks, that's better if not a total fix.

---

### Post by budderfly on 2010-11-05
> **vilcans said:**
> OK, here's the solution:

Just remove .gconf/apps/metacity/general/%gconf.xml and the problem should go away. It did for me. :-)

I found this by using git bisect with a repo with one commit per file.


I don't know exactly how to do this.

---

### Post by budderfly on 2010-11-05
Actually, I read another thread and the problem is very simple, I think we were all over thinking it. 

user:** ifland**  found the simple solution, i'm not going to take credit

> **ifland said:**
> I had the same problem and I managed to fix it by  going to System -> Preferences -> Windows and selecting "Alt" as  the movement key. (To actually click on the window without moving it, I  held the Ctrl key and clicked.)

- Orion

---

### Post by bluetomgold on 2010-11-14
> **budderfly said:**
> Actually, I read another thread and the problem is very simple, I think we were all over thinking it. 

user:** ifland**  found the simple solution, i'm not going to take credit

That's it! Thanks!

---

### Post by hopeididgood on 2010-11-24
Just adding another "thanks" here for everyone working through the problem...  I also installed Sugar and had exactly the same issue. (I'm so grateful I found this thread!)

---

### Post by bobprobst on 2011-02-05
> **vilcans said:**
> OK, here's the solution:

Just remove .gconf/apps/metacity/general/%gconf.xml and the problem should go away. It did for me. :-)

I found this by using git bisect with a repo with one commit per file.

This worked for me.  Thanks!

Edit:  I had also installed Sugar and had this problem.  I could click my Ubuntu menus fine but once I was in an application like FF or terminal, I had to ctrl-shift-click to do anything,

---

### Post by Buurmas on 2011-05-01
> **budderfly said:**
> Actually, I read another thread and the problem is very simple, I think we were all over thinking it.
Thank you! I was sure there had to be a straightforward solution to this strange problem.

---

### Post by kennedyjch on 2011-05-02
Had the same problem. Happened after installing the additional nVidia drivers (recommended) and hence starting up Unity interface. 

So following the advice "System -> Preferences -> Windows and selecting "Alt" as the movement key" had fixed it for me too....

But this should have never happened in the first place...

Thanks for the extremely helpful posting and solution.

---

