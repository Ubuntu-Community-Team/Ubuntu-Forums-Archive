---
title: "Bash scripting help!"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by soumo on 2009-07-25
I'm not sure this is the right forum let alone the right site, but perhaps someone can shed some light or point me to the right place?

I have set up a script to run on login or double-clicking the executable script file that would pair my ubuntu laptop to the external bluetooth mouse if a few conditions are met.

Here's the pseudo-code:
-output to screen a message to tell user to hit space/right arrow/whatever if they wish to begin
-read keyboard input within a timeout limit
-if input matches, alert user to turn on mouse, pair the mouse
-alert user pairing has occurred
-end

The actual code of the executable scroll.sh:
```
#!/bin/bash
echo "Connect BT mouse?\nhit <space>" | osd_cat -p top -A centre -s 2 -f '-b&h-lucida-medium-r-normal-*-74-*-*-*-p-*-iso10646-1' -c pink 
read -t 2 -n 2 keypressed
if [ "$keypressed" = 'bt' ]; then
    echo "Connect mouse\npairing..." | osd_cat -p middle -A centre -s 4 -f '-b&h-lucida-medium-r-normal-*-74-*-*-*-p-*-iso10646-1' -c pink &
    gksudo hciconfig hci0 reset
    sudo hidd --search
    echo "Successfully\npaired..." | osd_cat -p bottom -A centre -s 4 -f '-b&h-lucida-medium-r-normal-*-74-*-*-*-p-*-iso10646-1' -c cyan
else
    echo "Aborted..." | osd_cat -p middle -A centre -s 2 -f '-b&h-lucida-medium-r-normal-*-74-*-*-*-p-*-iso10646-1' -c black 
    exit    
fi
exit
```Some issues:

-Running from a terminal works okay[del], but the on-screen output writes the \n instead of skipping a line[/del].   I'd rather not use the terminal anyhow. [COLOR=Red]*SOLVED thx to TPL on linuxforums: use echo -e*[/COLOR]

[COLOR=Red]*Potentially unsolvable see: [http://www.linuxforums.org/forum/linux-programming-scripting/150535-absolute-begginer-needs-help-some-scripting-issues.html#post716361*](http://www.linuxforums.org/forum/linux-programming-scripting/150535-absolute-begginer-needs-help-some-scripting-issues.html#post716361*)[/COLOR]
-Double clicking on the scroll.sh gives me a few options, cancel, run in terminal, display, or run, from whence if I choose RUN, the first message pops up, but upon typing my input prompt to trigger the if condition, NOTHING happens.  I'm not sure if it's because the scroll.sh is still highlighted, but I've tried with all other windows closed to no avail.  If I run from terminal after clicking the scroll.sh, it works fine.

-If I set spacebar as the trigger input, it does not work in the above scenarios, but if I use letters such as 'bt' then it works fine in the terminal.  Optionally it would be good to be able to use an F-key or arrow key...

-I'd like to be able to extend the conditions to run the program if the mouse is on but not already paired.  Ie. if it's off, remind to turn on the mouse or if it's already paired, explain that it's paired.  I tried using some grep commands to look for the mac address of the mouse using hcitool dev command, but it seems that it's always present whether the mouse is off or on!  Is there a command that gives distinguished output for mouse on or off? 

Any help is appreciated!

---

### Post by soumo on 2009-08-12
Solved using zenity, see comments in:
[http://www.linuxjournal.com/content/use-bash-trap-statement-cleanup-temporary-files#comment-341228](http://www.linuxjournal.com/content/use-bash-trap-statement-cleanup-temporary-files#comment-341228)

---

