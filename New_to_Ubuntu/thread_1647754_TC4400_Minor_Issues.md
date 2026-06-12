---
title: "TC4400 Minor Issues"
date: 2010-12-17
forum: New to Ubuntu
---

### Post by DipreSantana on 2010-12-17
Good evening people.

I've got a TC4400 tablet which I've put 10.10 64bit on, most everything is working great, but there are a few issues.

First, I can't get the screen to rotate when I put it in tablet mode, so far, I've got a small script with a button on the top panel, but I'd prefer if it rotated automatically.

Second, sometimes the top panel gets scrambled, the tray icons will overlap each other, and it just doesn't look pretty.

And third, flash is always crashing on me in Chrome.

What can I do to fix these issues?

---

### Post by Favux on 2010-12-17
Hi DipreSantana,

Welcome to Ubuntu forums!

Is that a Compaq/HP TC4400 tablet pc?  Does it auto-rotate in windows?

---

### Post by DipreSantana on 2010-12-17
> **Favux said:**
> Hi DipreSantana,

Welcome to Ubuntu forums!

Is that a Compaq/HP TC4400 tablet pc?  Does it auto-rotate in windows?

It is a Compaq TC4400, and it does auto-rotate in Windows.

---

### Post by Favux on 2010-12-17
Good.  It looks like you have a swivel hinge switch.  Let's see if we can figure out how it sends a signal.  In a terminal enter:
```
lsmod | grep hp_wmi
```
and see if you have the hp_wmi kernel module.

---

### Post by DipreSantana on 2010-12-19
Here's what I get:

```
renzo@RDST:~$ lsmod | grep hp_wmi
hp_wmi                  6467  0
```

---

### Post by Favux on 2010-12-19
Good.  There's a chance that Magick Rotation will work for you.  See the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1") method 4 for the link.  We moved the applet to Launchpad, so the new version 1.2, isn't on the thread.

Magick is a Python applet that gives you automatic rotation through the hinge switch signal the hp_wmi recognizes.  It has some other nice features too.  I'm eager to see how it works for you because you'd be the first HP TC4400 to try it (that I'm aware of).

So good luck!  And ask if you have questions.

---

### Post by DipreSantana on 2010-12-19
Alright, the good news is, Magick Rotation works, the bad news is, it's backwards, when I go into tablet mode, the screen rotates to normal, when I go into laptop mode, the screen rotates 90 degrees.

---

### Post by Favux on 2010-12-19
Great news!  :)

You are using version 1.2, correct?  That sounds like the xrandr rotate command is reversed for you.  Have you tried rebooting?  Quitting Magick Rotation, right click on the tray icon and chose Quit, and restarting it, double clicking on magick-rotation?  What happens if you go into Setup and change the Rotation state to normal or one of the other modes?

---

### Post by DipreSantana on 2010-12-19
I am using 1.2, I've rebooted, and changed the settings, it's still inverted.

---

### Post by Favux on 2010-12-19
Alright.  Go into Advanced Setup and check the Debugging tool logging on checkbox.  Hit Save.  Then rotate to tablet and back to laptop and then post the log.  Uncheck the checkbox when you are done and hit save.  The log will appear in your /home/username directory labeled magick-log_date.

---

### Post by DipreSantana on 2010-12-19
I got this.

```
2010-12-19 17:31:48: cur_state: 2 
2010-12-19 17:31:48: old_state: 0 
2010-12-19 17:31:48: calling rotation b: 
2010-12-19 17:31:48: right
2010-12-19 17:31:48: Change to Tablet mode
2010-12-19 17:31:49: checking for rotation
2010-12-19 17:31:49: /home/renzo/magick-rotation/checkmagick64
```

---

### Post by Favux on 2010-12-19
Alright, thanks.  We're stalling somewhere around checkmagick.  That's a bit of C code that listens in on xrandr.  Xrandr tells us what the screen orientation is.  So we're making progress.

I need you to try evtest on the new device node (hp-wmi) Magick created for you.  The command in a terminal would be:
```
sudo evtest /dev/input/hp-wmi
```
I would like to see the entire output after you enter that and then rotate the screen to tablet and then back to laptop.  Press ctrl + z to exit evtest.

I forget if evtest is installed by default.  If not enter in a terminal:
```
sudo apt-get install evtest
```

Edit:  forgot sudo for evtest

---

### Post by DipreSantana on 2010-12-19
```
renzo@RDST:~$ sudo evtest /dev/input/hp-wmi
Input driver version is 1.0.1
Input device ID: bus 0x19 vendor 0x0 product 0x0 version 0x0
Input device name: "HP WMI hotkeys"
Supported events:
  Event type 0 (Sync)
  Event type 1 (Key)
    Event code 138 (Help)
    Event code 148 (Prog1)
    Event code 153 (Direction)
    Event code 224 (Brightness down)
    Event code 225 (Brightness up)
    Event code 226 (Media)
    Event code 358 (Info)
  Event type 5 (?)
    Event code 1 (?)
    Event code 5 (?)
Testing ... (interrupt to exit)
Event: time 1292798432.944929, type 5 (?), code 1 (?), value 0
Event: time 1292798432.944940, -------------- Report Sync ------------
Event: time 1292798435.970695, type 5 (?), code 1 (?), value 1
Event: time 1292798435.970704, -------------- Report Sync ------------

```

Here you go.

---

### Post by Favux on 2010-12-19
Thanks DipreSantana.  That's exactly what it should show.  We have a mystery!  It should be working.

To recap Maverick 10.10 with a HP ? TC4400 tablet pc using the default Wacom X driver xf86-input-wacom 0.10.8 and the default linuxwacom 0.8.4-4 usb kernel driver wacom.ko.  And of course the 2.6.35 kernel and X server 1.9.0.

When the screen rotates the wrong way do the Wacom devices (like the stylus) rotate with it?

One last bit of data gathering to try before trying to figure this out.  Enter in a terminal the following:
```
sudo xxd -g1 /dev/input/hp-wmi
```
Ctrl z to quit again.  Again rotate the screen to tablet and back.  It should produce 6 lines, 3 after turn to tablet and 3 after return to laptop.  Again please post everything in the output.

Another thought occurs.  What video chipset does that model have?  Enter in a terminal:
```
lspci | grep VGA
```

---

### Post by DipreSantana on 2010-12-19
The pen works just fine when the screen inverts, it works as it should.

```
renzo@RDST:~$ sudo xxd -g1 /dev/input/hp-wmi
[sudo] password for renzo: 
0000000: 46 94 0e 4d 00 00 00 00 dd d0 07 00 00 00 00 00  F..M............
0000010: 05 00 01 00 00 00 00 00 46 94 0e 4d 00 00 00 00  ........F..M....
0000020: e7 d0 07 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0000030: 49 94 0e 4d 00 00 00 00 ff d8 0e 00 00 00 00 00  I..M............
0000040: 05 00 01 00 01 00 00 00 49 94 0e 4d 00 00 00 00  ........I..M....
0000050: 09 d9 0e 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
^Z
[1]+  Stopped                 sudo xxd -g1 /dev/input/hp-wmi

```

```
renzo@RDST:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
```

---

### Post by Favux on 2010-12-19
Huh, that looks good too.  It again shows the right Type and Code and shows the key press and release.  I'm going to ask my partner to have a look and see if he has any ideas.

So when you boot screen starts out in landscape mode like normal.  You've picked your rotation direction and selected Right and Saved it, correct?  When you rotate to tablet nothing happens.  But when you go back to laptop the screen now rotates to the Right or clockwise correct?  And now when you go to tablet the screen rotates to normal or landscape instead of portrait, correct?

OK, that's an integrated Intel video chipset that shouldn't give problems.  Some need the Option:
```
	Option	"RandRRotation"	"on"
```
in the "Device" Section in the xorg.conf.  But yours is rotating so I'm not sure if you need it.  We could take a look at your video stuff in xorg.conf, if you have any or have an xorg.conf (not always there is Lucid and Maverick).  It's located in /etc/X11.  You could navigate there with Places/Nautilus.  Or get a look at it by entering:
```
gedit /etc/X11/xorg.conf
```
It will pop up if it is there.

---

### Post by DipreSantana on 2010-12-19
Right, and there is no xorg.conf, I have a folder called xorg.conf.d, I don't understand what the issue is.

---

### Post by Favux on 2010-12-19
Alright, about what I expected.  So I think your video is good as it is and we'll leave it alone.
> I don't understand what the issue is
Me either.  I'll try and digest the information you've provided and we'll wait for Ayuthia to join us.  Usually he's pretty fast at responding but what with this being the holidays and all...

I hope I'm missing the obvious.

But given what you've shown I don't see why we can't get Magick working for you and other HP Compaq TC4400's.

---

### Post by Ayuthia on 2010-12-19
> **DipreSantana said:**
> ```
renzo@RDST:~$ sudo evtest /dev/input/hp-wmi
Input driver version is 1.0.1
Input device ID: bus 0x19 vendor 0x0 product 0x0 version 0x0
Input device name: "HP WMI hotkeys"
Supported events:
  Event type 0 (Sync)
  Event type 1 (Key)
    Event code 138 (Help)
    Event code 148 (Prog1)
    Event code 153 (Direction)
    Event code 224 (Brightness down)
    Event code 225 (Brightness up)
    Event code 226 (Media)
    Event code 358 (Info)
  Event type 5 (?)
    Event code 1 (?)
    Event code 5 (?)
Testing ... (interrupt to exit)
Event: time 1292798432.944929, type 5 (?), code 1 (?), value 0
Event: time 1292798432.944940, -------------- Report Sync ------------
Event: time 1292798435.970695, type 5 (?), code 1 (?), value 1
Event: time 1292798435.970704, -------------- Report Sync ------------

```

Here you go.

I have a question about this information.  Was the first value (type 5, code 1, and value 0) when you switched to tablet mode and the second value (type 5, code 1, and value 1) when you returned back to laptop mode?

I just tried it out on mine and my values are the opposite of yours.  Usually the value should be set to 1 when it is in tablet mode and 0 when it is in laptop mode.

By any chance do you know the version of your BIOS?

---

### Post by Favux on 2010-12-19
Hi DipreSantana,

As Ayuthia points out it looks like I did miss the obvious.  My value of 1 and 0 are reversed from yours:
```
~$ evtest /dev/input/hp-wmi
Input driver version is 1.0.0
Input device ID: bus 0x19 vendor 0x0 product 0x0 version 0x0
Input device name: "HP WMI hotkeys"
Supported events:
  Event type 0 (Sync)
  Event type 1 (Key)
    Event code 138 (Help)
    Event code 148 (Prog1)
    Event code 224 (Brightness down)
    Event code 225 (Brightness up)
    Event code 226 (Media)
    Event code 358 (Info)
  Event type 5 (?)
    Event code 1 (?)
    Event code 5 (?)
Testing ... (interrupt to exit)
Event: time 1292812954.535521, type 5 (?), code 1 (?), value 1 <- you have 0
Event: time 1292812954.535558, -------------- Report Sync ------------
Event: time 1292812959.791186, type 5 (?), code 1 (?), value 0 <- you have 1
Event: time 1292812959.791220, -------------- Report Sync ------------

```
So what we are hoping is you have an early bios and they flipped the values with a later bios for your model.  It would make sense if all HP bios returned the same value as the later models bios' seem to.

---

### Post by Ayuthia on 2010-12-19
The easiest way to see if the rotation will work is to go into the magick-rotation folder and edit hpwmi.py:
```

gedit hpwmi.py

```
Look for:
```

SW_TABLET_MODE = 1

```
and change it to:
```

SW_TABLET_MODE = 0

```
Save it and then try running magick-rotation again.

---

### Post by DipreSantana on 2010-12-19
> **Ayuthia said:**
> I have a question about this information.  Was the first value (type 5, code 1, and value 0) when you switched to tablet mode and the second value (type 5, code 1, and value 1) when you returned back to laptop mode?

I just tried it out on mine and my values are the opposite of yours.  Usually the value should be set to 1 when it is in tablet mode and 0 when it is in laptop mode.

By any chance do you know the version of your BIOS?

When I switch to tablet mode nothing happens, when I switch back, it changes which rotates the screen 90 degrees.

My BIOS is F.0C, I'll see if there's a newer version.

Edit:  F.0C is the newest BIOS for the TC4400.

---

### Post by DipreSantana on 2010-12-19
> **Ayuthia said:**
> The easiest way to see if the rotation will work is to go into the magick-rotation folder and edit hpwmi.py:
```

gedit hpwmi.py

```
Look for:
```

SW_TABLET_MODE = 1

```
and change it to:
```

SW_TABLET_MODE = 0

```
Save it and then try running magick-rotation again.

After doing this, now it doesn't work at all.

---

### Post by Ayuthia on 2010-12-19
Ok.  Instead of running magick-rotation, can you run:
```

python hpwmi.py

```
This will just run the program that checks the /dev/input/hp-wmi file and rotates the screen.  It should rotate to the right (and not inverted because it is being run from the Terminal instead of magick-rotation).

Press control-c to stop the program.

Please let us know if any messages appear.

---

### Post by DipreSantana on 2010-12-20
```
renzo@RDST:~/magick-rotation$ python hpwmi.py
type e556  code 4d0e  value 0
type d817  code 0  value 0
type 5  code 1  value 0
type e556  code 4d0e  value 0
type d820  code 0  value 0
type 0  code 0  value 0
type e558  code 4d0e  value 0
type 3083  code f  value 0
type 5  code 1  value 1
type e558  code 4d0e  value 0
type 3090  code f  value 0
type 0  code 0  value 0
^CTraceback (most recent call last):
  File "hpwmi.py", line 52, in <module>
    h.run()
  File "hpwmi.py", line 21, in run
    input = fd.read(8)
KeyboardInterrupt

```

It still stayed the same when in tablet mode, and rotated when in laptop mode.

When I say inverted, I mean it rotates to the right while it's supposed to be in the normal orientation and vice versa.

---

### Post by Ayuthia on 2010-12-20
Sorry about that.  I found that I changed the code line instead of the value line.  Can you change SW_TABLET_MODE back to 1 and then go to line 42 where it shows:
```

                    if ev_val:
                        rotate = ROTATE_TABLET
                    else:
                        rotate = ROTATE_LAPTOP

```
and change line 42 to read:
```

                    if not ev_val:
                        rotate = ROTATE_TABLET
                    else:
                        rotate = ROTATE_LAPTOP

```

That should reverse the correct portion and hopefully things will swivel correctly.

Or if you are comfortable with unpacking a tar file and copying the file over, you can use the attached file which has the change.

---

### Post by DipreSantana on 2010-12-20
It worked, I can confirm now, that this will work on both the TC4400 and the TC4200.

I knew it had to be something simple, thanks for the help.

Now on to the soft buttons.

I tried to get them to work, to no avail.  There was a tutorial I followed, but it was for 10.04, and it didn't work for me.

---

### Post by Favux on 2010-12-20
Outstanding!

Now to figure out how to add the TC4200 & TC4400 to the code.  By the way did you investigate the BIOS issue?  Results?

---

### Post by DipreSantana on 2010-12-20
> **Favux said:**
> Outstanding!

Now to figure out how to add the TC4200 & TC4400 to the code.  By the way did you investigate the BIOS issue?  Results?

Well, both machines have the latest BIOS, and in the settings there are no options for the hinge.

And what do you mean add to the code, how do I do this?

---

### Post by Favux on 2010-12-20
You anticipated me, latest BIOS and no setting to change.  So the TC's are the reverse of the other models and nothing to be done about that.

No changing the code is on us.  I'm wondering how we identify the TC's.  Do you think you would have been able to find a check box in Advanced Setup (or maybe Setup) that said something like "Check box if screen orientation reverse of anticipated:"?

---

### Post by DipreSantana on 2010-12-20
> **Favux said:**
> You anticipated me, latest BIOS and no setting to change.  So the TC's are the reverse of the other models and nothing to be done about that.

No changing the code is on us.  I'm wondering how we identify the TC's.  Do you think you would have been able to find a check box in Advanced Setup (or maybe Setup) that said something like "Check box if screen orientation reversed:"?

That'd be a good idea, and yes I went through all the settings and even some of the scripts, unfortunately, I didn't know what I was looking for, but I'm sure anyone who could install the package could find the option to invert the orientation if it were clearly labeled.

---

### Post by Favux on 2010-12-22
Hi DipreSantana,

I added a check box to Setup for the two TC models and changed the hinge logic.  Looks like everything is working.  It will be available in the 1.3 release of Magick.

If your interested in testing the changes please let me know.

---

### Post by DipreSantana on 2010-12-25
I'm very interested.

---

### Post by Favux on 2010-12-26
Good!

The changes are in 3 files:  oem_wmi.py, config.py, and gui_gtk.py.  But there had been other changes before the TC ones so this should be the current version in the unstable/testing branch.  Hopefully I didn't break anything assembling it.

Let me know if it works for you.

---

### Post by DipreSantana on 2010-12-27
It works perfectly, though the name of the setting can be a bit confusing.

---

### Post by Favux on 2010-12-27
Great!

I know, but that's actually what's happening and what needs to be fixed.  And why I stuck it in Setup rather than Advanced Setup.  Everything else I tried seemed clumsier.  Suggestions?

---

### Post by DipreSantana on 2010-12-27
I have no idea how to word it, I guess it could say something along the lines of, actually, since we've only seen this behavior on the TCs, just name it that, "check this ox if you own a Compaq/HP TC model tablet."

---

### Post by Favux on 2010-12-27
Not bad.  I'll think about it.  I just got myself worried that the TC's might not be the only models with the values reversed.  And not just HP, I got to wonder about other Brands of pc's.  We've already added the Dells.

---

