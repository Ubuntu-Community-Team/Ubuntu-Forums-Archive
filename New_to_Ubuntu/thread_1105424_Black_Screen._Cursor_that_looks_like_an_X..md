---
title: "Black Screen.?? Cursor that looks like an X.??"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by Edgar09 on 2009-03-24
Hello.....
Iam new at Ubuntu 8.10 & i have problem.......
Like 5 days ago i changed something on the login window appearence... it will go through the normal boot stuff (all that white text, "Starting System" or whatever, and even the black loading screen with the orange progress bar and "Ubuntu") then it gos to a black screen.!! And the cursor has a shape of an X..

In other words i cant get to my desktop....
I removed compiz,gnome & i think even grub..... but i still cant get to my desktop.... Ubuntu Pros:o.!! i need help.....:(

---

### Post by mgmiller on 2009-03-24
This is annoying.  Short of rebooting my computer and taking notes, I can't give you the exact steps to fix this.

There are 2 things you can try.

when you have the black screen with the "X" try hitting ctrtl/Alt/F1 simultaneously.

This should give you a text based login.  Just give it your regular user name and password when prompted.

Once you are logged in, enter the command:
```

sudo xfix
```

Once it's done, go back to ctrl/alt/F7 and hit the ctrl/alt/backspace keys to restart x.

Hopefully, that will get you back to a graphical desktop.

If that does not work, reboot and right after it posts and it says starting linux, there is an "F key" to hit get it to display the verious kernels and stuff you have available.  (This is the part I get fuzzy on, so bear with me).

I believe the last choice is to fix the graphical subsystem.  Let it do that and then when it restarts, you should be back in X with the open source driver running.  You will then need to run the  System > Administration > Hardware drivers utility to get the accelerated drivers working again if you so desire.


Hope this helps..

---

### Post by Edgar09 on 2009-03-24
Thanks 4 the reply iam gonna check out right know...

---

### Post by Edgar09 on 2009-03-25
The command
sudo xfix 
doesnt work..???
Its says xfix isnt a command

And i dont rally understand the last part.???!!
Do i go to the command & do a 
Sudo rebbot then just press f ????  or how.??
:confused:

---

### Post by mgmiller on 2009-03-25
OK, sorry about that.  I rebooted one of my machines and took some notes.

Right after it posts, it will briefly say "press esc to enter boot menu".  This is only displayed for a short time, so keep you eyes open for it.  

Next, you will see a list of the Ubuntu kernels that are installed.  The newest are at the top, older ones are below.  Every other line will say (recovery mode) after it.

what you want to do is use the up/down arrow keys to select the top most (recovery mode) kernel.  Hit enter to continue.

Lots of text and scary looking stuff will scroll by.  Finally you will get a blue screen with a grey "Recovery Menu" displaying.

The bottom choice is "xfix  Try to fix the X server".

Just use the up/down arrow keys to high light that choice and then hit the tab key to high light the "ok" in red.  Then hit enter and wait for it to finish.  Follow any prompts, they should be pretty obvious.  

Eventually, you should end up back on your desktop with the open source driver loaded.

---

### Post by Edgar09 on 2009-03-26
Mmmmmm... I already did that...
Do you think by installing Kubuntu on the disc of Ubuntu i would get all back.???:lolflag:

---

### Post by anewguy on 2009-03-26
If you really removed gnome (either via synaptic or via apt-get) then you have no desktop to boot into.

Go to the terminal at boot (cntrl/alt/F1), login using your normal userid and password, and do this:

sudo apt-get install gnome-desktop-environment


Removing compiz I'm not worried about - it's just eye candy.  Just be sure you removed the 2 key components:

sudo apt-get remove compiz
sudo apt-get remove compiz-core

then reboot and see if you can get to your desktop.

There are a LOT of things I have with gnome in the name in synaptic, so you may have to go through and add others after you are up.

I'm not sure what your mean by removed Grub - if you used synaptic package manager or apt-get you can reinstall Grug via:

sudo apt-get install grub

However, I'm a little curious how you can be booting to Ubuntu without grub or another bootloader already in place.

Dave :)

EDIT:  Be aware you still might not be able to get to the desktop - it's possible your video driver got lost and will need to be reinstalled.

---

### Post by Edgar09 on 2009-03-26
Did that but its says package not found "sudo apt-get install gnome-desktop-environment"

& the compiz has been all removed...
What shound i do.???:(:confused:

---

### Post by mgmiller on 2009-03-26
The package "gnome-desktop-environment" is not part of a standard ubuntu install.  It is in the universe repository.

Perhaps he romoved parts of ubuntu-desktop?

In which case he should:
```
sudo apt-get install ubuntu-desktop
```Going back to your original post, you said you changed something in the login window.  This is before you get to your desktop and where you enter your user name and password.  Can you still get to this window, or does the screen go black before it displays?

Or did you make a change in:  System > Administration > Login Window   ?
And after rebooting or logging off and on, that's when the trouble started?

I did a little digging around and I wonder if you didn't change the default session type to "Secure Remote Connection".

By default it should be set to "Run Xclient script"

---

### Post by yeats on 2009-03-26
> I removed compiz,gnome & i think even grub..... but i still cant get to my desktop.... Ubuntu Pros.!! i need help.....

I don't normally advise reinstalls (on principle), but if you're new to this, you might just consider starting over and reinstalling...

---

### Post by Edgar09 on 2009-03-27
Hello ubuntu Pros.. i got myself in a big problem
I removed Grub & cant get to windows.??!! Man.!! I just did a big mistake.!  THe Bootloader says it cant find grub & the error is number 17
How can i get into windows again.?!
Shound i reinstall ubuntu.??
Today i downloaded kubuntu but on my usb & i dont know how shound i burn to a CD or a DVD.!? 
What shound i do Ubuntu:KS pros.???

---

### Post by cheapie on 2009-03-27
Try downloading the Ubuntu server edition CD and booting from it. There should be an option there that says "Rescue" or "Repair" or something like that.

---

