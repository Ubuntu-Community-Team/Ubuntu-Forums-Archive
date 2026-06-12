---
title: "IPW2100 problems on Toshiba m35 s359"
date: 2005-08-02
forum: Networking &amp; Wireless
---

### Post by optikshell on 2005-08-02
Check my thread [HERE](http://ubuntuforums.org/showthread.php?t=53874) ... thanks for all the input

---

### Post by simonjardine on 2005-08-02
[QUOTE=optikshell]Check my thread [HERE](http://ubuntuforums.org/showthread.php?t=53874) ... thanks for all the input[/QUOTE]
 Ok Iam on the same laptop as you, and i can say, that I love Ubuntu, it is working amazing, first fix your keyboard. Easy, , Mine is working greeeeeet(joke). 

OK open terminal type nano /etc/X11/xorg.conf
and add the bit this bit (Option          "XkbDisable"    "on") like below!

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "keyboard"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"
        Option          "XkbDisable"    "on"
EndSection

Your done, that will work, although i have to say, you sometimes get a slight delay, does'nt seem to bother me though.
The Toshiba seems to run Ubunutu really well, i am using Xfce4 Desktop, which i love.  \\:D/

---

### Post by optikshell on 2005-08-02
awesome, I'll do that as soon as I get home.  Thanks for the quick reply.  

Just for personal knowledge, what exactly does that do?

Oh, and for anyone else who might want to take a stab... my wireless still isn't working.  :?

---

### Post by optikshell on 2005-08-04
just an update for anyone who's had the same problem...

i re-installed... but this time picked my wireless connection as the connection for Ubuntu to do its original update from... and it worked.  

now my wireless works fine... how... i don't know.  anyway, if you're having the same problem with a fresh install, re-install and select your wireless as the connection for apt to update with during the installation.

---

