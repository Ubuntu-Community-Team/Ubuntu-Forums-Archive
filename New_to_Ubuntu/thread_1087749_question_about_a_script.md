---
title: "question about a script"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by cosine352 on 2009-03-05
Hi!
I am trying to run this script from crontab

> ##!/bin/bash
aplay /usr/share/sounds/purple/alert.wav
(for a in `seq 1 100` ;
do
echo $a;
sleep 1 ;
done) |DISPLAY=:0.0 zenity --auto-close --progress \
--text="Shut down in 10 mins" \
--title="WARNING"
case "$?" in
          1  )  exit 1 ;;
          0  )  shutdown -h now ;;
      esac

I have added this to my root crontab. 
The problem is it only plays the sound and do not executes the other commands. I have no idea what is wrong. I also tried moving the script file to the root home directory. Still no luck.

Oh one thing .... If I click on the 'run task' from 'gnome-schedule' it runs happily. 

Any help will be greatly appreciated.

---

### Post by cosine352 on 2009-03-06
bump

---

