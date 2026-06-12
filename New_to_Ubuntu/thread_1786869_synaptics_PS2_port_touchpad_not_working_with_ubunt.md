---
title: "synaptics PS/2 port touchpad not working with ubuntu 10.04"
date: 2011-06-20
forum: New to Ubuntu
---

### Post by odrik on 2011-06-20
synaptics PS/2 port touchpad not working with ubuntu 10.04
USB mouse works well

---

### Post by _0R10N on 2011-06-20
Hi! I've you recently installed Ubuntu, then try upgrading your repositories information and then updating your system. Perhaps is a misconfiguration that gets solved updating the system.

---

### Post by wep940 on 2011-06-20
> **odrik said:**
> synaptics PS/2 port touchpad not working with ubuntu 10.04
USB mouse works well

Ok, I'm not quite sure what you mean so I'll ask - it connects via a PS/2 port - that I can understand, but is this more than just a touch pad - are there any buttons, etc., on it?  You'll probably need to take the manufacturer name and the model and do a search in one of the big search engines similar to this:

ubuntu manufacturer model driver

I'm just guessing it's probably going to need a driver to work.

---

### Post by Sergio.G on 2011-06-20
Hi, to have a better overview of your problem and determine the possible solutions, could you be so kind and answer a couple of questions?

1. Is it a fresh Ubuntu install?
2. What version of the kernel are you using?
3. Did the Touchpad worked and suddenly stopped working?


Also try this:

Open the gconf-editor by pressing the keyboard combination: alt+f2
then, type gconf-editor, click run
navigate to:

desktop > gnome >> peripherals >> touchpad 

touchpad-enabled should be clicked, if not clicked then click on it

If it's clicked and still not working then post back the answer to the questions above.

Cheers

---

### Post by odrik on 2011-06-20
hello,

It's a 2.6.32-32 version.
I guess it was from the start,the touchpad not worked.
I've installed it with the USB mouse connected....
My notebook is a SONY VAIO VPCYA1V9E

In windows 7 is there no problem.
searching in device manager give's me the information mentioned:synaptics PS/2 port touchpad.

thx

---

### Post by MarjaE on 2011-06-20
Whoops. Misread.

Still, if it is one of the Alps touchpads, a lot of us are having the same problem. I can't turn off tap-to-click, which makes typing and cursor movement extremely erratic.

---

### Post by odrik on 2011-06-20
> **Sergio.G said:**
> Hi, to have a better overview of your problem and determine the possible solutions, could you be so kind and answer a couple of questions?

1. Is it a fresh Ubuntu install?
2. What version of the kernel are you using?
3. Did the Touchpad worked and suddenly stopped working?


Also try this:

Open the gconf-editor by pressing the keyboard combination: alt+f2
then, type gconf-editor, click run
navigate to:

desktop > gnome >> peripherals >> touchpad 

touchpad-enabled should be clicked, if not clicked then click on it

If it's clicked and still not working then post back the answer to the questions above.

Cheers

It's clicked and still not working .

---

### Post by Sergio.G on 2011-06-20
This is a bug that apparently has been around for a while, found a thread [_here_]("http://ubuntuforums.org/showthread.php?t=1150077") 
a little outdated but it is worth to try it, 

The post #2 gives a solution, the models tested are some Vaio VPC...

If you have a doubt how to do it, post back so we can assist you.

Cheers

---

### Post by odrik on 2011-07-02
Hi,

THX for the help

here's the solution

run in terminal:sudo gedit/etc/default/grub

change:

GRUB_CMDLINE_LINUX="i8042.reset i8042.nomux i8042.nopnp i8042.noloop"

save

run:sudo update-grub

reboot

This works on my Sony VAIO VPCYA1V9E

---

### Post by jtarin on 2011-07-02
Mark this thread solved then, please.

---

### Post by MarjaE on 2011-07-04
> **odrik said:**
> Hi,

THX for the help

here's the solution

run in terminal:sudo gedit/etc/default/grub

change:

GRUB_CMDLINE_LINUX="i8042.reset i8042.nomux i8042.nopnp i8042.noloop"

save

run:sudo update-grub

reboot

This works on my Sony VAIO VPCYA1V9E

Which gets it kinda-sorta working but not really working. This is NOT solved.

---

### Post by jtarin on 2011-07-04
> **MarjaE said:**
> Which gets it kinda-sorta working but not really working. This is NOT solved."kinda-sorta working"....a better description will enable better help.:p

---

### Post by MarjaE on 2011-07-04
I have a Sony Vaio E-series with an Alps touchpad which Ubuntu treats as a PS/2 mouse. However:

1. It detects *everything* as button1 clicks, the same as left-button clicks. It detects mouse taps, as well as slight pressure variations while moving the cursor, typing with my hands an inch from the touchpad, and stray hair. Okay, it doesn't detect breathing as button1 clicks.

2. Because of this, it is very hard to type while the touchpad is enabled, or to move the cursor with the touchpad without accidentally clicking on objects in its way. Which leaves the touchpad worse than useless.

3. I use a keyboard shortcut to disable the touchpad, but the touchpad enables itself again after each time the computer suspends.

---

### Post by jtarin on 2011-07-05
Have you tried the suggestions in the [Ubuntu documentation]("https://help.ubuntu.com/community/SynapticsTouchpad")?

---

### Post by MarjaE on 2011-07-05
Tried everything short of kernel hacking. Hosed the system at one point, and reinstalled, but lost some emails.

"Disabling Touchpad while Typing

    Go to System > Preferences > Mouse > Touchpad and uncheck 'Disable touchpad while typing' and 'Enable mouse clicks with touchpad' "

System > Preferences > Mouse > Touchpad DOES NOT EXIST if the computer detects the touchpad as a PS/2 mouse.

---

### Post by jtarin on 2011-07-05
You should read the documentation a little further....there is more mentioned than just:
 "Go to System > Preferences > Mouse > Touchpad and uncheck 'Disable touchpad while typing' and 'Enable mouse clicks with touchpad".

---

### Post by MarjaE on 2011-07-05
I read a lot more than that. I tried a lot more than that. Some of which hosed my system so I had to reinstall.

The big issue - which affects Alps and Elantech - is that the Synaptiks driver does not cover them - and all the fixes which either involve installing Synaptiks or use synaptics-specific fixes do not work for them... that's the vast majority of the documentation right there.

I picked out one example of where the documentation is just plain wrong, at least for my touchpad.

It isn't the only frakking example. Don't assume that just because someone hasn't found a solution, that they haven't read the documentation. In some cases, the documentation is very scattered and disorganized. In some cases, parts of the documentation are false, or some of the fixes may wreck the operating system. It is an old bug, it is a serious bug, it is known, and to the best of my knowledge it is unsolved short of kernel hacking. (The code for alps.c includes a section on how to edit the kernel to disable tapping. But I am not going to try to do that.)

---

### Post by jtarin on 2011-07-05
Excuse me for not being as informed as you about your touch pad situation. I'll try to do better next time.:P

---

### Post by Weeman3396 on 2012-08-23
Just registered to say Thanks.  I've installed Ubuntu 3 or 4 times on my laptop and always given up, as I've never been able to get the touchpad working.

I gave it another shot today after a year and this thread has solved my touchpad issues!

Just to confirm this works on a Dell Studio 1745 and I am very greatful ):P

---

