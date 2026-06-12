---
title: "VLC player as Default"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by Alex82 on 2009-03-13
Hello firstly Im sorry if this has been answered elsewhere but I can not find an answer.

VlC player works well if I manually select it from applications but it will not play any newer original dvds such as American Gangster or 3:10 to Yuma.

It plays backups well and also older originals, however I have now managed to make vlc my default player and upon loading it just greys out and then crashes.

Is there anyway to fix this available or do I just have to close totem and manually select vlc

many thanks

also could someone point me in the right direction to get k9copy to work as I am having no joy there either very slow, saves no iso, crashes.

---

### Post by humphreybc on 2009-03-13
I generally just right click on files and go to properties then choose open with and select VLC. This should make it the default for that particular file type. There are only half a dozen or so main video types so it shouldn't take that long to cover all of them.

I'm not sure if there is some sort of "default file types/applications" GUI interface like what windows has.

As for VLC crashing and not playing newer DVDs, I'm not sure. Perhaps upgrade to 8.10? Have you got all the right codecs? The ubuntu "extended extra" pack? Newest version of VLC from the repositories?

---

### Post by Razmear on 2009-03-13
Howdy,
I'm a noob too, but give this a try. 
First enable the 'control center', it's a lot like Window's Control Panel and I really don't know why it's not enabled by default. I just found it last night by accident. 
To enable it, right click on the System Menu, Select Edit Menus, Scroll down to System and select it, then in the right pane check Control Center and hit close. 
Now when you hit the System menu you'll have a third option for Control Center, open it up and under Personal choose Preferred Applications. On the Multimedia tab you can select your preferred media player. 
I haven't found a global file associations applet yet that covers all file types, if anyone knows of one please add it to this thread. 

eb

---

### Post by humphreybc on 2009-03-13
> **Razmear said:**
> Howdy,
I'm a noob too, but give this a try. 
First enable the 'control center', it's a lot like Window's Control Panel and I really don't know why it's not enabled by default. I just found it last night by accident. 
To enable it, right click on the System Menu, Select Edit Menus, Scroll down to System and select it, then in the right pane check Control Center and hit close. 
Now when you hit the System menu you'll have a third option for Control Center, open it up and under Personal choose Preferred Applications. On the Multimedia tab you can select your preferred media player. 
I haven't found a global file associations applet yet that covers all file types, if anyone knows of one please add it to this thread. 

eb

Cool i've never seen that control center before. Seems silly not to have it enabled by default!

---

### Post by suitedaces on 2009-03-13
System > preferences > preferred applications does the same job on mine.

---

### Post by abybaddi on 2009-03-13
> **humphreybc said:**
> Cool i've never seen that control center before. Seems silly not to have it enabled by default!

You are right it's really cool.

---

### Post by Alex82 on 2009-03-13
> **Razmear said:**
> Howdy,
I'm a noob too, but give this a try. 
First enable the 'control center', it's a lot like Window's Control Panel and I really don't know why it's not enabled by default. I just found it last night by accident. 
To enable it, right click on the System Menu, Select Edit Menus, Scroll down to System and select it, then in the right pane check Control Center and hit close. 
Now when you hit the System menu you'll have a third option for Control Center, open it up and under Personal choose Preferred Applications. On the Multimedia tab you can select your preferred media player. 
I haven't found a global file associations applet yet that covers all file types, if anyone knows of one please add it to this thread. 

eb

Can't get that in my Hardy?  Its the dvds that make everything go grey and crash?

---

### Post by wildman4god on 2009-03-13
Download a program called Ubuntu tweak it allows you to set file type associations for every type of file. It also does a lot more, its like tweakui only for Ubuntu

[http://ubuntu-tweak.com/downloads](http://ubuntu-tweak.com/downloads)

enjoy :D

---

### Post by Alex82 on 2009-03-14
is it safe?

---

### Post by mc4man on 2009-03-14
Very quick and easy way to enable vlc as 'default' (autoplay) dvd player in hardy. Shouldn't take but a min. or so
(plus link out to enable other players,ect.

[http://ubuntuforums.org/showthread.php?p=4986640#post4986640](http://ubuntuforums.org/showthread.php?p=4986640#post4986640)

---

### Post by Alex82 on 2009-03-14
Big Thanks mc4man,
that works perfectly, I had already done the first part but its the vlc%f that makes all the difference I had vlc%u and I think before that I had vlc%w not sure what this actually means perhaps you could explain?
Also do you know if it is possible to get a working onscreen control panel? (pause, play etc)

---

### Post by mc4man on 2009-03-14
I think I'm about 12 hrs. different from you so gotta get some sleep (4am
I'm assumming your using vlc 0.8.6 ,the fullscreen controls are in the 0.9.x versions.

If you want to try a 0.9.x vlc you could either build it or there is a half decent build for hardy in the korn ppa.

It's pretty straightfoward to install/upgrade, if you decide to revert back to 0.8.6 you'll need to remove a few packages in synaptic first. 
It's probably best to search vlc first in synaptic and remove it, vlc-nox, libvlc0 and the vlc pulse plugin before installing the 0.9.8a version

you can get it here, change the sources list dropdown to *hardy* and copy and paste the source lines 1 at a time into System -> admin -> software sources -> third party -> add.
After that click close and then reload.

[https://launchpad.net/~c-korn/+archive/ppa](https://launchpad.net/~c-korn/+archive/ppa)

Then if you go back into synaptic and mark vlc for install or sudo apt-get install vlc you'll get the 0.9.8a version (and depends) which is the best 0.9.x ver.

Do note that ALL 0.9.x versions are broken in various little ways, it won't be till the 1.0 release that most are fixed.

I build a 1.0 every couple of wks., some things are fixed, progress is slow.

You may or may not be affected depending on your usage.

If vlc 0.9.8a stops responding or otherwise screws up the 2 best things to do are.

Start vlc from terminal with
```
vlc --reset-config
```

Or open up system -> admin. -> system monitor -> processes and see if vlc is 'sleeping', if so r.click -> kill...

---

### Post by wildman4god on 2009-03-14
> **Alex82 said:**
> is it safe?

yes it is safe, i use it all the time and have no problems.

---

### Post by Alex82 on 2009-03-14
> **mc4man said:**
> I think I'm about 12 hrs. different from you so gotta get some sleep (4am
I'm assumming your using vlc 0.8.6 ,the fullscreen controls are in the 0.9.x versions.

If you want to try a 0.9.x vlc you could either build it or there is a half decent build for hardy in the korn ppa.

It's pretty straightfoward to install/upgrade, if you decide to revert back to 0.8.6 you'll need to remove a few packages in synaptic first. 
It's probably best to search vlc first in synaptic and remove it, vlc-nox, libvlc0 and the vlc pulse plugin before installing the 0.9.8a version

you can get it here, change the sources list dropdown to *hardy* and copy and paste the source lines 1 at a time into System -> admin -> software sources -> third party -> add.
After that click close and then reload.

[https://launchpad.net/~c-korn/+archive/ppa](https://launchpad.net/~c-korn/+archive/ppa)

Then if you go back into synaptic and mark vlc for install or sudo apt-get install vlc you'll get the 0.9.8a version (and depends) which is the best 0.9.x ver.

Do note that ALL 0.9.x versions are broken in various little ways, it won't be till the 1.0 release that most are fixed.

I build a 1.0 every couple of wks., some things are fixed, progress is slow.

You may or may not be affected depending on your usage.

If vlc 0.9.8a stops responding or otherwise screws up the 2 best things to do are.

Start vlc from terminal with
```
vlc --reset-config
```

Or open up system -> admin. -> system monitor -> processes and see if vlc is 'sleeping', if so r.click -> kill...

Thanks very much for all of your help, Im currently running VLC media player 0.8.6e Janus, I think I will stick with this for now as it seems to be running perfectly at the moment and I can learn to live without onscreen controls for now.

---

