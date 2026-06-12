---
title: "karmic cpu and ram problem need help"
date: 2010-03-02
forum: New to Ubuntu
---

### Post by Trinity33 on 2010-03-02
hi i have msi gt 725 so inside q9000 quad core 2ghz, ddr2 4gb, sound card intel acl 1200 and ati hdmi, graphic ati hd4850 500mb.

and my question is. when i boot up everything is working fine i updated everything sound is working i got the newest drivers from alsa and ati everything is just perfect and im happy. the just one or two problems is that when i dont use it at all just boot up and leave it without touching. in the beggining there will be around 300mb ram usage. then after around 30 min it will be 500mb then 2 hours it will go to 1gb and like that it will grow and grow and thats not good i need help with it. what i found is that when i open system monitor there will be many applications. and almost everyone is sleeping. sleeping and eating my ram bad applications. how to tell them to stop eat my ram!!!!. in a nice way. anyone have a solution? i dont want to just kill it cos it will comeback again i would need to kill it every hour. i want better solution. other thing is my cpu. there is not much usage after i installed ati driver. but still. why does applications like gnome monitor use my cpu when im not even touching my lappy. i think that gnome monitor don't have anything to do with it cos its just monitor so there must be some application that use my cpu to much. the usage is normally around 10% without even touching keyboard so it shouldn't be like that for sure. need solution for it too. 
and last question let say i want to try new graphic driver so i will install it then reboot my pc and cant see my desktop any more cos probably this driver did something bad:( my options are i will be able just to use shell so is there a way to boot up and change my settings to those from before i installed my last driver? like sort of safe boot like in windows. i tired ones new driver and what happen after reboot i lost my desktop was not able to boot and the minimal graphic mode didn't work to i had just option to use shell but didn't know what to type startx dint work. tried fix-vesa didnt work too. tnx for your help.

---

### Post by Sir Jasper on 2010-03-02
Hi,

I hope this works for you as it does in Xubuntu:

If you right click on a blank area of one of your panels, and then click + Add New Items then click C P U Graph which should be near the top in alphabetical order.

With the Graph on your panel left click on it and CPU and RAM usage should bring up a window showing percentage use (sorted high to low) by package.

Just keep it running for an hour or two and note what is causing the increase if the graph rises. You can freeze the window by right clicking in the top section (and holding down while you read from it).

My regards

This uses far less resource than gnome-system-monitor which seems itself to be resource hungry.

---

### Post by shae on 2010-03-02
I believe the ram "issue" you describing is coming from your background in Windows XP and before.  Having ram free was once thought a good thing, but that is not really the case.  In Linux, the kernel makes more efficient use of your hardware by caching information in ram although it is no longer needed.  This cache allows access to that information nearly instantaneously if it is needed again, thus making the computer seem faster.  On the other hand, if more ram is needed for a different application, ram is quickly freed from the cache and used for those programs.

Only consider the ram use a problem if you see your swap partition being used a lot.

---

