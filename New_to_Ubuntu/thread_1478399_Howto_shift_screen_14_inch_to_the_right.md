---
title: "Howto shift screen 1/4 inch to the right?"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by held7over on 2010-05-09
Ubuntu 10.04 Gnome

My Acer Flatscreen displayed desktop image needs to be shifted about a quarter of an inch to the right. How can I do that?

Thanks! :P

---

### Post by -humanaut- on 2010-05-09
Try hitting the bottom on your monitor "menu" and go to the part where you can move the screen around there should be an "Auto" try that first if that doesn't set it right then you can just manually move it over. It's really simple its all done through the menu button on your monitor.

---

### Post by lkraemer on 2010-05-09
I used to carry around a DOS Boot floppy that contained an R.bat
G.bat and B.bat for RED, GREEN, and BLUE testing screens.  That
assured that the Monitor was set such that the colors were evenly
spaced on the Screen, so they displayed properly.  Then I'd boot
to Windows and try the final AUTO Adjust on the Monitor that was
previously suggested.

Blue.bat contained:
prompt $e[1;37;44m$p$g

Red.bat contained:
prompt $e[1;37;41m$p$g

Green.bat contained:
prompt $e[1;37;42m$p$g

SPECIAL ATTRIBUTE COMMANDS
$e[0m  Normal, white on black
$e[1m  Bold, high intensity
$e[4m  Underline if available
$e[5m  Blink
$e[7m  Reverse video

These five commands are called attribute commands.
They let you control the brightness, blinking and reverse video.

THE COLOR CODES
$e[30m  black letters..........$e[40m  black background
$e[31m  red letters............$e[41m  red background
$e[32m  green letters..........$e[42m  green background
$e[33m  yellow letters.........$e[43m yellow background
$e[34m  blue letters...........$e[44m  blue background
$e[35m  magenta letters........$e[45m magenta background
$e[36m  cyan letters...........$e[46m  cyan background
$e[37m  white letters..........$e[47m  white background
                  
The group of Ansi codes list 8 colors for the letters
and 8 colors for the background. Simple math shows
that 8 x 8 =64. Therefore, we have 64 possible
color combinations.

Ref:
[http://www.uncreativelabs.net/textfiles/software/BATS.TXT](http://www.uncreativelabs.net/textfiles/software/BATS.TXT)

lk

---

### Post by held7over on 2010-05-10
Thanks guys. That worked great! For some reason, I had this memory of doing something with a gui or something years ago to make the adjustment. Pushing a button on the bottom of the monitor was far easier.

---

