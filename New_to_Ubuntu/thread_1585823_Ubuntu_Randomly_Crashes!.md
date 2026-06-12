---
title: "Ubuntu Randomly Crashes!"
date: 2010-10-01
forum: New to Ubuntu
---

### Post by Avidanborisov on 2010-10-01
I don't know why this is happening!
Ubuntu sometimes just randomly crashes, my screen turns black and I can't do nothing except turning my power down!

---

### Post by migs73 on 2010-10-01
try looking here. there may be something that will work for you.

[http://ubuntuforums.org/showthread.php?t=1558917](http://ubuntuforums.org/showthread.php?t=1558917)

oh and welcome to the forums!

---

### Post by sikander3786 on 2010-10-01
Does it really happen randomly? Do you remember any running programs e.g, Firefox, Flash etc.

Did you try killing X by using Ctrl + Alt + Backspace when the screen goes blank?

If you don't have the Ctrl + Alt + Backspace combination enabled, you can enable it from System > Preferences > Keyboard > Layouts > Options > Key sequence to kill the X Server and tick the corresponding box.

---

### Post by davrosuk on 2010-10-01
"random" crashes are *normally* the result of an underlying hardware problem - there are other possibilities, but its far more likely to be a problem with a bad memory DIMM for example.

---

### Post by Avidanborisov on 2010-10-01
Well I don't know what is DIMM and Doing Ctrl+Alt+Backspace will kill all the processes which is kinda like shutting down the computer. I mean, what if I am at the middle of a downloading progress? Doing this won't be a great solution.

and other ideas?

---

### Post by QIII on 2010-10-01
Genuinely random crashes are often hardware related.  But we don't know if the shut downs are really random or if you are doing similar things at the time.

Hardware is generally the easiest to rule out, so let's start there.

The first thing I would do is to shut down on crash, restart the computer, enter the BIOS and check the CPU temp.  (I'd tell you how to use the sensors applet on your gnome panel, but that would take more time than actually shutting down and looking at the BIOS for right now.)


Second, at your next startup, run memtest from the GRUB menu.  Let it run  for a long time.  Several hours or even overnight if you can.

Open your case and blow out all the dust bunnies before you start the rest.

Third, make sure that your memory modules and all of your cards are still firmly seated in their sockets.  Even with the screws and clips that hold them down, they can still become slightly dislodged and cause problems.


Finally, get a bright flashlight and look over your motherboard for problems that are readily visible.  Burned components.  Leaky components.  Blistered components.  Scratches on the PCB that uncover the traces.

---

### Post by Avidanborisov on 2010-10-01
> **QIII said:**
> Genuinely random crashes are often hardware related.  But we don't know if the shut downs are really random or if you are doing similar things at the time.

Hardware is generally the easiest to rule out, so let's start there.

The first thing I would do is to shut down on crash, restart the computer, enter the BIOS and check the CPU temp.  (I'd tell you how to use the sensors applet on your gnome panel, but that would take more time than actually shutting down and looking at the BIOS for right now.)


Second, at your next startup, run memtest from the GRUB menu.  Let it run  for a long time.  Several hours or even overnight if you can.

Open your case and blow out all the dust bunnies before you start the rest.

Third, make sure that your memory modules and all of your cards are still firmly seated in their sockets.  Even with the screws and clips that hold them down, they can still become slightly dislodged and cause problems.


Finally, get a bright flashlight and look over your motherboard for problems that are readily visible.  Burned components.  Leaky components.  Blistered components.  Scratches on the PCB that uncover the traces.
OK... I will try to run the memtest when my computer boots. but can you explain me whats wrong? I didn't really understand what you said...
And I don't know if I explained myself wrong: **The crashes don't cause shutdowns**. I just have to shut down my system since it isn't responding.

And as long as I remember I don't have problems with my hardware. The crashes are only in Ubuntu and I have dual boot with XP, just saying...

---

### Post by QIII on 2010-10-01
I shouldn't have used "shut downs".  Let's say "crashes" or "freezes".  

No.  I can't magically tell you what is wrong.  We have to find out what is wrong.  There are a lot of reasons why this could be happening.

Different OSes behave differently in those "boundary" conditions preceding hardware failure.  For instance, Linux can be more sensitive to impending disk failure than Windows.

Remember, I said we are eliminating hardware failure.  If we decide that is not the problem, we put it aside and work on something else.

If you think your hardware is OK, then one quick thing to check might be /var/log/messages and /var/log/syslog and check the entries just prior to the freeze.  (You'd have to note the time of the freeze and restart to get at the log, of course.)  A quick way to look at them (but not the way I prefer) would be to open gedit, navigate to the files and look at them.  You can view the contents without elevated privileges.

---

### Post by Avidanborisov on 2010-10-01
> **QIII said:**
> I shouldn't have used "shut downs".  Let's say "crashes" or "freezes".  

No.  I can't magically tell you what is wrong.  We have to find out what is wrong.  There are a lot of reasons why this could be happening.

Different OSes behave differently in those "boundary" conditions preceding hardware failure.  For instance, Linux can be more sensitive to impending disk failure than Windows.

Remember, I said we are eliminating hardware failure.  If we decide that is not the problem, we put it aside and work on something else.

If you think your hardware is OK, then one quick thing to check might be /var/log/messages and /var/log/syslog and check the entries just prior to the freeze.  (You'd have to note the time of the freeze and restart to get at the log, of course.)  A quick way to look at them (but not the way I prefer) would be to open gedit, navigate to the files and look at them.  You can view the contents without elevated privileges.
Ok but before messing with my hardware I will try to follow a suggested sollution from another thread that was linked to here (changing drivers in xorg.conf file). If that won't work I guess I will go with the hard way.

---

