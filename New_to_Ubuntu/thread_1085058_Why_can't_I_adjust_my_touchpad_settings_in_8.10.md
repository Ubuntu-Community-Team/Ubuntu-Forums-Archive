---
title: "Why can't I adjust my touchpad settings in 8.10?"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by jonobe on 2009-03-02
Having upgraded to 8.10 (K)ubuntu, I can't seem to find a way of turning off the touchpad.  This is driving me crazy - I type a lot, and suddenly my hand touches the pad, and the cursor has jumped across the page and I'm typing lines in the wrong place.  
But I managed to turn off the pad previously, in ubuntu 8.04.  Is it possible in 8.10?  I noticed xorg.conf is now controlled by upgrades automatically and what i do won't affect things.  Really?

I'm foxed.  I can't believe I can't turn off the touchpad any more.

If any one knows any solutions, I would much appreciate.

elp

H

---

### Post by dtom2444 on 2009-03-02
Two options:

1. You can add a small delay (like in Windows) so that only a few seconds after you strike a key will the touchpad be enabled. 

[http://ubuntuforums.org/showthread.php?t=271052&highlight=disable+touchpad+while+typing](http://ubuntuforums.org/showthread.php?t=271052&highlight=disable+touchpad+while+typing)

OR

Applications -> Add/Remove and install TouchFreeze (which serves the same purpose)

2. You can disable the touchpad altogether (which is what i did)
Applications -> Add/Remove and install Touchpad. Then, 
System -> Preferences -> Touchpad 
and configure the touchpad to your liking.

NOTE: sorry, didn't read carefully enough. This is for Ubuntu. Not sure if this would also work on Kubuntu. 

Best of luck.

---

### Post by Donkeykwon on 2009-03-02
I had a hell of a time configuring my touchpad for Xubuntu.  Here's a link that applies to all versions [https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig]("https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig").  Also, because the instructions are a bit confusing, here's the step by step of how I turned off that damn button tap:

1) Go to you terminal and type gksudo gedit /etc/hal/fdi/policy/shmconfig.fdi  (**Note**: If you don't have "_gedit_", replace it with whatever simple text editor you have like "_mousepad_")

2) Next paste in this:
```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="input.x11_driver" string="synaptics">
      <merge key="input.x11_options.SHMConfig" type="string">True</merge>
    </match>
  </device>
</deviceinfo>
```

3) Save and close your text editor and reboot.  Now you can access synclient.

4) Go back to your client and type in "synclient -l" this will list all the functions of your touchpad.  TapButton1 is the variable that controls the function you want to turn off. So type in:
```
synclient TapButton1=0
``` and your good to go.  

This setting will be reset when you turn off your computer, so to make it permanent...

5) Go to "autostart applications" in your settings manager, add an app, name and describe it properly, and type in "synclient TapButton1=0" in the command box.

Hope this helps.

---

### Post by jonobe on 2009-03-04
Thanks for this - I used your wonderfully clear instructions:KS to get shm working - i couldn't find a way (no useful xorg in 8.10) until I read this.  I now use touchfreeze program (to get a timed delay on touchpad activation while typing) and it works great whereas before it didn't at all.

---

### Post by flirtingmtbear on 2009-03-12
I just went into Applications: Add/Remove: Accessories: TouchFreeze
and it isn't working, so that isn't a good fix, unless I didn't install and apply it right.
I am having the same problems with typing and it's driving me batty!!!
Other than that, so far I love Ubuntu.  I switched from being a Windows user less than 1 month ago and love the "Duh" factor here!!!
Help with the touchpad would be lovely!!!

---

