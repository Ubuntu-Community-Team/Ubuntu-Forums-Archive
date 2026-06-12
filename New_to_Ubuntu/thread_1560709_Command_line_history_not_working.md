---
title: "Command line history not working"
date: 2010-08-25
forum: New to Ubuntu
---

### Post by mar3cus on 2010-08-25
I've installed Ubuntu server 10.04 on a VMWare player on my laptop. I login OK. At the command prompt I can type commands ok but the command history thing doesn't work. Such as up-arrow to go to the previous command. How do I turn this on?
 
I've found the history command. It shows a list of the commands I've entered. Autocomplete (Tab) does work for commands. 
 
Is there an environmental variable I need to set?
 
If I type bash to start a new bash shell, the up-arrow for previous command still doesn't work.

---

### Post by opticyclic on 2010-08-31
Post the contents of your config files 
.bashrc
.bash_profile
.profile

These are hidden so you will have to press Ctrl-H to see them in Nautilus.
I'm wondering if you accidentally turned on vi mode or something in your settings, which might be affecting your history.

Just to clarify, do you have a .bash_history file in your home directory as well? (No need to post it)

---

### Post by mar3cus on 2010-09-01
Thanks for this. I've found that history works using control keys such as <ctrl>p for previous and <ctrl>a to go to the start of a line. The arrow keys on my keyboard number pad do work when going up and down the history stack. It's just the four arrow keys (the ones in the shape of an inverted T) that don't join in the fun.
So it's probably a keyboard configuration problem? My stty -a looks like this:
 
speed 38400 baud; rows 30; columns 80; line = 0;
intr = ^C; quit = ^\; erase = ^?; kill = ^U; eof = ^D; eol = <undef>;
eol2 = <undef>; swtch = <undef>; start = ^Q; stop = ^S; susp = ^Z; rprnt = ^R;
werase = ^W; lnext = ^V; flush = ^O; min = 1; time = 0;
-parenb -parodd cs8 hupcl -cstopb cread -clocal -crtscts
-ignbrk -brkint -ignpar -parmrk -inpck -istrip -inlcr -igncr icrnl ixon ixoff
-iuclc -ixany -imaxbel -iutf8
opost -olcuc -ocrnl onlcr -onocr -onlret -ofill -ofdel nl0 cr0 tab0 bs0 vt0 ff0
isig icanon -iexten echo echoe echok -echonl -noflsh -xcase -tostop -echoprt
echoctl echoke
 
Actually quite a few keys are wrong. Eg Uppercase 2 displays an @ sign instead of a single quote and the # key displays a \
 
So I'm definitely thinking this must be some keyboard mapping problem.
 
Is that easily fixed?

---

### Post by opticyclic on 2010-09-01
This sounds more like you have the wrong keyboard setup.
Typically an Ubuntu installation uses American English :roll: (if it isn't British it isn't English! :biggrin:)
The American Keyboard has the @ symbol above the 2.
You need to work out what type of keyboard you have, generally the country you bought it in is a good enough guess.
You then need to change the keyboard settings:
[http://www.ehow.co.uk/how_5775380_change-keyboard-layout-ubuntu.html](http://www.ehow.co.uk/how_5775380_change-keyboard-layout-ubuntu.html)

---

### Post by mar3cus on 2010-09-03
Thanks very much. Mine is a UK keyboard. I've looked at the link and found it uses GNOME. I'm only using the keyboard via a terminal window. So I'm following a path with loadkeys and keymaps etc. I'll get there in the end :p

---

