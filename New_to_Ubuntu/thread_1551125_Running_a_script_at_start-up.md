---
title: "Running a script at start-up"
date: 2010-08-11
forum: New to Ubuntu
---

### Post by joealanbrooks on 2010-08-11
Hi all,

I have a script (twofingerscrolling.sh) that I want to run at start-up. 

The script is executable and looks like this:

```
#
# Synaptics TouchPad 2 finger Scrolling
#

# Set multi-touch emulation parameters
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 32 8
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 32 8
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Two-Finger Scrolling" 8 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 8 1 1

# Disable edge scrolling
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Edge Scrolling" 8 0 0 0

# This will make cursor not to jump if you have two fingers on the touchpad and you list one
# (which you usually do after two-finger scrolling)
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Jumpy Cursor Threshold" 32 110
```

I've searched these forums and google and asked friends and tried the following solutions.

**1. Adding my script to Start-up Applications**

> Go to System > Preferences > Startup Applications

'Add' it using the following parameters:

Name: Whatever you want
Command: /home/myusername/.my_script.sh
Comment: Whatever you want

..should work just fine.

This has not worked.

> Yeah you need to put sh before it

sh /home/myusername/.my_script.sh

should work.

No success with this either.

**2. Editing /etc/rc.local**

> nano /etc/rc.local
use either

/bin/bash [commands]
or
/bin/sh -c [command]

Hasn't worked.

**3. "Sessions"**

> Off the main menu: System > Preferences > Sessions. Click Startup Programs, Add, type your line, and click OK.

There is no "Sessions" in the Preferences menu.

So how can a script be run at start-up in Ubuntu?

([Here's someone who asked the same question unsuccessfully.](http://ubuntuforums.org/showthread.php?t=1376938))

---

### Post by bodhi.zazen on 2010-08-11
Does the script run if you log in and then run it manually ?

It appears you are setting preferences for an X session , so you will almost certainly want to run it at login (Start up applications) and not rc.local

I advise you put your script in 

~/bin (you will need to make a ~/bin directory first).

Also add a she-bang at the top of the script. I is a sh script ?

Add #!/bin/sh

Is it a bash script

Add #!/bin/bash

make sure the script is executable

chomd a+x ~/bin/script_name

Last, when you add it to your startup use the full path

/home/your_user/bin/script_name

Sometimes these things run too soon, so you may need to add a sleep 10 at the top

If the sleep works, reduce the time as low a possible.

---

### Post by joealanbrooks on 2010-08-12
sleep 2

...did it.  Thank you so much.

---

### Post by bodhi.zazen on 2010-08-12
> **joealanbrooks said:**
> sleep 2

...did it.  Thank you so much.

w00t =)

---

### Post by Kovooo on 2010-08-19
Yes, I have Lenovo S12 ION with ubuntu 10.04 and similar script ... it works on boot but when I resume computer from suspend or hibernate, two-finger scrolling stop working and I need manually re-run the script.
my question is if there is some solution to run script automatically

I'e tried adding script to /usr/lib/pm-utils/sleep.d but nothing ...

---

### Post by Jose Catre-Vandis on 2010-08-19
> **joealanbrooks said:**
> sleep 2

...did it.  Thank you so much.


So was that in rc.local ?

---

