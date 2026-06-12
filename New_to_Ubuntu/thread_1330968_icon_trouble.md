---
title: "icon trouble"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by thomz92 on 2009-11-18
hi everyone. ok i downloaded the black-white icon theme from gnome-look and it seemed to install fine but in the "places" menu the icons for each different folder (music, documents, etc) isn't the right type. And the folder icon for the "ubuntu one" folder is a nasty looking gnome icon. When i tried to change it back to the humanity icons, the same thing happened! please help!

---

### Post by emigrant on 2009-11-18
can you please explain what happened if you try to apply humanity icons?
also can you please past what you have in the following directories?

/usr/share/icons

~/.icons

---

### Post by thomz92 on 2009-11-18
well you know how the pictures/videos/etc. folders have their own unique fold icons? when i installed the black-white icons, the only ones that worked were the "pictures" folder and the "documents" folder. The rest had regular folder icons, except for the "ubuntu one" folder which was a gnome icon i think? and it sticks out because its ugly :) when i tried to change back to the humanity icons, the same thing happened to them.

srry im on a different computer right now so its hard to transfer them...but in my ~/.icons folder i have "black-white_2-Style" folder and in my /usr/share/icons folder i have folders like "humanity" and "highcontrast" and "handhelds" and stuff like that, but no "black-white_2-Style" if that was what you were looking for. was there anything in particular u were looking for?

---

### Post by emigrant on 2009-11-18
no, im thinking why the humanity icon is not working eventhough it is still there where it should be.
as for the other icon, from what i have so far experienced you don't always get what you see from the screenshots.
i installed the new karmic humanity icon set into my jaunty. but still i don't get the special effect added to music/documents/video etc... folders.
only the color and the design have changed, if you know what i mean.

---

### Post by thomz92 on 2009-11-18
yeah. i thought maybe it had to do with the names of the icons and what folder they're placed in...but then why didn't humanity work like it should when i changed back?

---

### Post by emigrant on 2009-11-18
move humanity from /usr/share/icons to ~/.icons and see whether that works.

---

### Post by thomz92 on 2009-11-21
> move humanity from /usr/share/icons to ~/.icons and see whether that works.

i did and it didn't...

---

### Post by thomz92 on 2009-11-23
bump... this is really bugging me. i HATE being a perfectionist :)

---

### Post by emigrant on 2009-11-24
can you see how the other accounts work?

---

### Post by thomz92 on 2009-11-24
do you mean the root account? otherwise there is no other account except me.

---

### Post by Buuntu on 2009-11-24
Sometimes similar things happen to me when I change themes but they are fixed when I restart.  So I have to ask, have you restarted and seen what happens?

---

### Post by thomz92 on 2009-11-24
> Sometimes similar things happen to me when I change themes but they are fixed when I restart. So I have to ask, have you restarted and seen what happens?

ok i logged out and back in and it fixed the problem. however, i still have that problem with the black-white icon theme i downloaded...

---

### Post by Podex on 2009-12-04
I seem to have the same problem. The icons of the default folders in home (Downloads, Music, Videos etc.) are showing the normal folder icon instead of their special icons.
Copying the Humanity folder from /usr/share/icons to ~/.icons does not solve this. Neither does restarting. 
I also tried reinstalling humanity-icon-theme. Then I tried totally removing humanity-icon-theme and then reinstalling it. This all didn't work.
So, I don't think this has to do with Humanity, since Human doesn't show special icons either.
Any ideas?

---

### Post by thomz92 on 2009-12-05
the icons for firefox and a few other programs aren't working either. They use the default icons. Maybe this is because the icon theme wasn't made specifically for ubuntu?

---

### Post by Buuntu on 2009-12-05
System > Preferences > Appearance, from there you can mess with the icon themes.  Try one that works ;)

---

### Post by Podex on 2009-12-06
> **Buuntu said:**
> System > Preferences > Appearance, from there you can mess with the icon themes.  Try one that works ;)

Pretty useless reply. If I was satisfied with using another icon theme I wouldn't have asked here for a fix to my problem. Obviously I already know how to switch to another icon theme...

Edit: It's almost like saying: Your Ubuntu doesn't work? Try another OS that works.
I'll try searching for a bug report on this.

Edit2: Ok I fixed this myself following woli's reply in this thread: [http://ubuntuforums.org/showthread.php?t=1299520](http://ubuntuforums.org/showthread.php?t=1299520)
I don't know how my user-dirs.dirs file changed though.

---

### Post by CaptainMark on 2009-12-06
ive had this problem for ages because i liked the black and white style icon kit, run ```
gksu nautilus
``` and navigate to usr>share>icons>black-white_2-style>scalable>places>256  youll notice that there folders called photos which should be pictures, [probaly it the icon pack was made on an older version when you had a folder places>photos] there are few others but if you do it for videos and stuff too it restores most of the icons, im still working on the ubuntu one folder, i dont know how the icon engine deals with spaces,

---

### Post by Buuntu on 2009-12-06
> **Podex said:**
> Pretty useless reply. If I was satisfied with using another icon theme I wouldn't have asked here for a fix to my problem. Obviously I already know how to switch to another icon theme...

Edit: It's almost like saying: Your Ubuntu doesn't work? Try another OS that works.
I'll try searching for a bug report on this.

Edit2: Ok I fixed this myself following woli's reply in this thread: [http://ubuntuforums.org/showthread.php?t=1299520](http://ubuntuforums.org/showthread.php?t=1299520)
I don't know how my user-dirs.dirs file changed though.

Sorry to insult you but I had to make sure you guys were installing/changing themes in the correct spot.  If you already have been using that then I apologise, I don't know what's wrong with the specific theme and how to fix it.

---

