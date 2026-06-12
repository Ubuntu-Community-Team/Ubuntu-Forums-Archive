---
title: "Configure extra buttons on mouse"
date: 2010-10-19
forum: New to Ubuntu
---

### Post by migs73 on 2010-10-19
Right, I have a new mouse with 11 buttons. I have checked a few how-to's but can't find one that fits with what I have.
Eventually worked out how to get a new xorg.conf file,([http://ubuntuforums.org/showthread.php?t=1401835](http://ubuntuforums.org/showthread.php?t=1401835)) see below

```
Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection
```

and that is the section for my mouse. It doesn't look like any of the xorg.confs in the how-to's. 
Although I can only see buttons 4 5 6 7 mentioned (for scrolling I assume) and they do work as up, down, left, right, scrolling (butons 1,2,and 3 work fine also). I also have an extra 4 buttons, two of which are seen in 'xinput test'.
Now then, how do I configure the last two buttons to be seen by X, and how do I map buttons 8 and 9 (and 10,11 if I can get X too see them)to do something meaningful.

Many thanks

Mike


EDIT: Buttons 8 and 9 actually already do what I want them to do...sort of, just the wrong way round!! ie 8 back in FF 9 forward. I would like it the other way round.

---

### Post by outleradam on 2010-10-19
Is this a Logitech MX Revolution?  I am having the same issue with my logitech mx revolution under Ubuntu 10.10
 
[http://ubuntuforums.org/showthread.php?p=9995957#post9995957](http://ubuntuforums.org/showthread.php?p=9995957#post9995957)

---

### Post by martinr on 2010-10-19
The key to being able to program mouse buttons beyond the ones already discussed is to install imwheel (from the Universe repository). Imwheel will enable you to define application-specific actions to your additional mouse buttons. 

Download and install imwheel using Synaptic, Adept, or apt-get 
Modify your /etc/X11/imwheel/imwheelrc or ~/.imwheelrc file to tell imwheel what to do with a mouse click when it happens in a particular application. See the Wikis referenced below for details on what you can do with your imwheelrc or .imwheelrc file. NOTE: You can use modifications to the ~/.imwheelrc to limit imwheel behavior to specific users on your system. 

Finally, if desired, tell X11 to run imwheel whenever X11 is started (modifying /etc/X11/Xsession.d/60imwheel_start-imwheel and changing IMWHEEL_START=0 to =1 in /etc/X11/imwheel/startup.conf). Alternately, you can start imwheel manually. 

See: [https://help.ubuntu.com/community/ManyButtonsMouseHowto#Mapping%20More%20Buttons]("https://help.ubuntu.com/community/ManyButtonsMouseHowto#Mapping%20More%20Buttons")

---

### Post by utilitytrack on 2010-10-19
**migs73**

Read this: 
```
$ man xmodmap
```

---

### Post by migs73 on 2010-10-19
> **outleradam said:**
> Is this a Logitech MX Revolution?  I am having the same issue with my logitech mx revolution under Ubuntu 10.10
 
[http://ubuntuforums.org/showthread.php?p=9995957#post9995957](http://ubuntuforums.org/showthread.php?p=9995957#post9995957)

Checked my mouse (no not a Logitech it is a Silvercrest) using xev and there is no event registered :(

Utility track

I'll maybe try that to reassign my forward/back (8/9) buttons.

Or maybe imwheel?

Looks like buttons 10/11 are out of the picture either way.

Thanks Guys

---

### Post by outleradam on 2010-10-19
just reread the problem.    You can fix your problem by simply going into firefox and typing about:config, then finding the proper option to reverse the keys.  it's a 1, you need to change it to a -1

---

### Post by mastablasta on 2010-10-20
> **migs73 said:**
>  
Or maybe imwheel?

 
imwheel seems to be the way to go. i haven't tried it yet (similar issue here), but i read the documentation. terminal scares me as it is so easy to mess up the system with it. just during the weekend i managed to mess up my sound again using terminal to install something. took me almost 2 hours to get things back where they belong. 
 
 that's why i liked windows more than DOS. :) things are much easier there with the graphics and i can't realyl mess it up as it won't let me. occasionally i found a way nonetheless...

---

### Post by mgorovoy on 2011-06-18
The solution discussed in  [this post]("http://ubuntuforums.org/showpost.php?p=10222311&postcount=9") allows control over all the options that exist for all types of devices recognized by Xorg, as opposed to the imwheel that only supports a subset of options for the mouse pointer alone. It took me a couple of days to find it, and it works for both Ubuntu 10.10 and 11.04.

-Michael

---

