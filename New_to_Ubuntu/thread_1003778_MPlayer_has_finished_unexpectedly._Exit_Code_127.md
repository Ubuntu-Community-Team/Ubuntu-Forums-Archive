---
title: "MPlayer has finished unexpectedly. Exit Code 127"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by Awesome ASim on 2008-12-06
hello every one , 
i have downloaded SMplayer because it's the bedt player for subtitles  , 
today i tried to run an arabic subtitle but i cannot so i searched for that on google and founs someone who did that , i have installed a file and run it but when i ran it, it says its corrupted then i tried to open an file with SMplayer and that what i have as an output
> MPlayer has finished unexpectedly. Exit Code 127

and here is the log
> /usr/bin/mplayer -noquiet -nofs -sub-fuzziness 1 -identify -slave -vo x11 -ao pulse -zoom -nokeepaspect -framedrop -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 79691788 -monitorpixelaspect 1 -subfont-autoscale 1 -subfont-text-scale 5 -subcp CP1256 -subpos 100 -contrast 0 -brightness 0 -hue 0 -saturation 0 -nocache -osdlevel 0 -vf-add screenshot -channels 2 /home/asim/Desktop/docs/Downloads/Zidane's Top Ten Goals Ever.wmv

/usr/bin/mplayer: error while loading shared libraries: libfribidi.so.0: wrong ELF class: ELFCLASS32

:guitar:

---

### Post by Awesome ASim on 2008-12-06
any body knows !!

---

### Post by rvm4000 on 2008-12-06
Do you have the package libfribidi0 installed?

---

### Post by Awesome ASim on 2008-12-06
yes

---

### Post by rvm4000 on 2008-12-06
For some reason mplayer can't load that library.

Are you using the 64-bit version of Ubuntu? Searching in google for that error message, it seems it happens on 64-bit systems when trying to use a 32-bit library.

---

### Post by Awesome ASim on 2008-12-06
yes i am using that :) , 

how can i solve that ,  it was fine :)

---

### Post by rvm4000 on 2008-12-06
Actually I don't know. I'm using a 64-bit kubuntu and I didn't have that problem (although I think I didn't try to use an arabic subtitle).

Did you try to reinstall libfribidi0 or mplayer?

If that doesn't work maybe you can try my builds of mplayer:
[https://launchpad.net/~rvm/+archive](https://launchpad.net/~rvm/+archive)

---

