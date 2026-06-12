---
title: "Assistive Technology Support and  mouse, touchpad..."
date: 2010-08-12
forum: New to Ubuntu
---

### Post by Mike Krall on 2010-08-12
Have an ASUS UL50Ag with ELAN Smart-Pad that has no controls in 10.04 as configured. 

Got the attached screen-shot when in Sys. > Pref. > Mouse and clicking on "Accessibility" tab check boxes. 

I've got no idea what "enable and logout" means or does... whether clicking it might have positive effect on solving lack of touchpad control... or not. 

Would someone help with this, please?

Mike

---

### Post by Paul820 on 2010-08-12
It means it will enable it when you log out. It needs to log out and back in again and it should be activated.

---

### Post by Mike Krall on 2010-08-13
Thanks, Paul...

Do you know what effects enabling it will have on mouse and maybe touchpad?

Mike

---

### Post by QLee on 2010-08-13
Mike,
Unless you are setting this system up for someone who has a physical challenge, you probably don't want to enable Assistive Technology Support.

Are you trying to get something to work on your touchpad? I seem to remember several threads in the forum about touchpads and settings. If you do a forum search with your computer model and/or the touchpad type there might be something to help.

Here is one I have a link for, don't know if it applies to yours.
[http://ubuntuforums.org/showthread.php?t=1552064](http://ubuntuforums.org/showthread.php?t=1552064)

---

### Post by Mike Krall on 2010-08-13
Well, I learned a little about Assistive Technology Support and I understand your feeling it is not a thing to enable unless specifically needing it. I do wonder if enabling would cause 10.04 to "find" it has a touchpad, though... =]

Yes, having touchpad problems... ELAN Smart-Pad in ASUS UL50Ag. I've come across other ASUS and ELAN touchpad problems with 10.04 (and other Ubuntus). The discussions of solution-process are over my head. Really, I'm just looking for a way to turn the touchpad off (like Win7's Fn + F9 toggles this touchpad off/on), but I'm afraid it doesn't exist. 

I'll look at the link... thank you for your effort, QLee.

Mike

---

### Post by QLee on 2010-08-14
[QUOTE=Mike Krall]
Yes, having touchpad problems... ELAN Smart-Pad in ASUS UL50Ag. I've come across other ASUS and ELAN touchpad problems with 10.04 (and other Ubuntus). The discussions of solution-process are over my head. Really, I'm just looking for a way to turn the touchpad off (like Win7's Fn + F9 toggles this touchpad off/on), but I'm afraid it doesn't exist. [/QUOTE]

Okay Mike, I see some of those recent posts I vaguely remembered are yours. However, some of the recent ones from others seem to suggest newer kernels may work better, what kernel are you running. Several of the suggested fixes appear to make additions to udev rules or to an xorg.cfg (does your system use an xorg.cfg).

If you're really just looking for a way to turn the touchpad off, you can issue the command, synclient TouchpadOff=1 in a terminal, toggle back with synclient TouchpadOff=0. (For an explanation, use the command man synaptics in a terminal to read the manual page.)

You could come back to the forum to ask for explanations for anything you don't understand in those other posts.
Edit: By the way Mike, you really shouldn't ask the same question in different posts all over the forum, it makes it hard to track answers and sometimes people become irritated when they see the same post from the same person in several threads, having to answer the same question multiple times to make sure the poster sees it. However, I can understand your frustration with this issue.

---

### Post by Mike Krall on 2010-08-14
It was a choice between bumping the original thread, which had generated no discussion and moving myself to a similar thread where there was discussion. 

Following the link you posted, I read enough last night to understand there has been a kernel solution for Elantech touchpad/ELAN Smart-Pad (Running 2.6.32-24-generic-pae).

My touch pad works. I don't know that it works completely (as it would in Win7) because I don't use it and the only time I would use it is if my mouse quits. The reality is, "touchpad" is not anywhere in GUI "System" >... of my computer. 

If it is possible, turning the touchpad on/off from the keyboard would be ideal... that is... mouse quits... toggle touch pad on... fix mouse... toggle touchpad off.

Would you suggest a link where I can teach myself how to run these things you posted, please... *"If you're really just looking for a way to turn the touchpad off, you can issue the command, synclient TouchpadOff=1 in a terminal, toggle back with synclient TouchpadOff=0. (For an explanation, use the command man synaptics in a terminal to read the manual page.)"*

Mike

---

### Post by QLee on 2010-08-14
[QUOTE=Mike Krall
If it is possible, turning the touchpad on/off from the keyboard would be ideal... that is... mouse quits... toggle touch pad on... fix mouse... toggle touchpad off.

Would you suggest a link where I can teach myself how to run these things you posted, please... *"If you're really just looking for a way to turn the touchpad off, you can issue the command, synclient TouchpadOff=1 in a terminal, toggle back with synclient TouchpadOff=0. (For an explanation, use the command man synaptics in a terminal to read the manual page.)"*

Mike[/QUOTE]

Mike, that was the manual page I stated in my previous post.

You need to open a terminal window to enter the command, man synaptics. That will show you the manual page.

The other commands I stated for toggling the touchpad would also be entered into a terminal window.

You should find terminal on your menu and click to open it. Or, hold the alt key and push F2, which should open a dialogue box where you can type in gnome-terminal and push the run button.

After you understand what is going on, you will be able to figure out how to enter the commands directly at the Alt + F2 dialogue.

---

### Post by Mike Krall on 2010-08-15
"man synaptics" starts with:  "synaptics  is  an  Xorg  input  driver for the touchpads from Synaptics Incorporated.

The reading I mentioned from your link and through others there seem to imply solutions for non-function are manufacturer specific. At the point in the reading I found "Elantech touchpad" was solved for kernel prior to the one I'm running, there was still discussion and evolving solution for Synaptics and Alp touchpads. 

*"If you're really just looking for a way to turn the touchpad off, you can issue the command, synclient TouchpadOff=1 in a terminal, toggle back with synclient TouchpadOff=0. (For an explanation, use the command man synaptics in a terminal to read the manual page)."*

I'm wondering two things about the above, QLee... Isn't it specific to Synaptics touchpads... and... would you point me to a place I can learn how to take the two commands out of the machine? (I don't want to always be in one or the other, given a key stroke on/off is the best solution).

Mike

---

### Post by Mike Krall on 2010-08-17
I've read a little about key strokes and customizing them but I'm pretty well clueless about doing it. 

I'm wondering if there is any simple way of setting a keystroke to turn the touchpad off/on. 

I still haven't figured out why there is no "Touchpad" in Preferences, either under "Mouse" or as a stand alone. I don't know that it absolutely needs to exist, given the touchpad works, but it is curious.

I really do need to be able to turn it off/on, even if it has to be done through terminal. I don't know how to go about that, either.

Mike

---

