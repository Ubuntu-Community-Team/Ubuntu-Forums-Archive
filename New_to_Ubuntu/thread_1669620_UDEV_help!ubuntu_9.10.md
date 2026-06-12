---
title: "UDEV help!ubuntu 9.10"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by phanie on 2011-01-18
hello people of ubuntu..this is my first post here and i really need help..i am a newbie in ubuntu and i am having problems with my udev..

[IMG]C:\Users\ej\Desktop\udevadminfo[/IMG]

as you can see in the image,it is the udevadm info of my external hard drive..

[IMG]C:\Users\ej\Desktop\query=all[/IMG]

and i think the next image doesnt really require my explanation of what it is..lol

well,guys you see im trying to make a udev rule which initiates a script that logs of my pc whenever my device is added to the PC..this is my code:

> #!/bin/bash


for udi in $(/usr/bin/hal-find-by-capability --capability storage)
do
    
if [[ $(hal-get-property --udi $udi --key storage.bus) = "usb" ]]
    
then
        
gnome-session-save --kill --silent
    
fi

done

and the fllowing is the rule i've created for the device:

> ACTION=="add", Kernel=="sdb1", SUBSYTEM=="block", ATTRS{vendor}=="WD      ", ATTRS{model}=="3200BEV External", ENV{DKD_MEDIA_AVAILABLE}=="1" RUN+="/home/babyjessie/draft.sh" 


well,i think i have done anything and everything to make it work but sadly it doesnt..please help me guys,i really need this..

---

