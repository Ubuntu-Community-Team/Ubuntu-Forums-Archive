---
title: "changing desktop background in eeebuntu.."
date: 2009-04-22
forum: New to Ubuntu
---

### Post by maggiemonic on 2009-04-22
hello! this question has likely been asked seven thousand times, but i have not been able to find a useful solution online so here goes:

i just got my eee pc 1000 and installed eeebuntu yesterday. this is my first experience with linux and all i want to do is change from this corny wallpaper. i can do it temporarily by right clicking and all, but there are two problems:

1. this either mounts 'home' or the file to my desktop, and when i remove either the wallpaper setting goes with it.

2. accepting 1., it is gone when i reboot anyway. annoying!

i tried running 'sudo gconf-editor' and going to desktop>gnome>background and changing picure_filename directly, but i get that i dont have permission and since trying that i can't seem to rename that anymore anyway. i have also chosen set as default and mandatory several times for kicks, if that changes anything.

long story, sorry, but isn't there a simple solution? i just want to add a picture  file to my usr/shared/backgrounds folder yeah? 

thanxxx!

---

### Post by llamabr on 2009-04-22
> **maggiemonic said:**
> 
i tried running 'sudo gconf-editor' and going to desktop>gnome>background and changing picure_filename directly, but i get that i dont have permission and since trying that i can't seem to rename that anymore anyway. i have also chosen set as default and mandatory several times for kicks, if that changes anything.


This isn't right.  Where do you type sudo gconf-editor?  In the terminal?  Do you know the sudo password?  You need to put in the password in order to overcome the permissions issue.

---

### Post by hansdown on 2009-04-22
Hi maggiemonic.

This should help.

[http://forum.eeebuntu.org/viewtopic.php?f=28&t=1942&p=7564](http://forum.eeebuntu.org/viewtopic.php?f=28&t=1942&p=7564)

It's also an entertaining look at another forum.

---

### Post by maggiemonic on 2009-04-22
i typed it into the run application line. whatever pops up when you press alt+f2. so would that have accoomplished anything if i had typed it in the terminal?

---

### Post by llamabr on 2009-04-22
Yes, always type commands into the terminal.  alt-f2 brings up a little thing to run an application, but you want to run a command.

Try it in terminal, and let us know what happens.

---

### Post by maggiemonic on 2009-04-22
> **hansdown said:**
> Hi maggiemonic.

This should help.

[http://forum.eeebuntu.org/viewtopic.php?f=28&t=1942&p=7564](http://forum.eeebuntu.org/viewtopic.php?f=28&t=1942&p=7564)

It's also an entertaining look at another forum.


i saw this before and it made me a litte scared to post because i am so very clueless about this stuff. i dont know how to put files in to  the usr/share/backgrounds folder. when i copy images from my media/user/mydocuments/etc and go to usr/share/backgrounds pasting is not an option. how can i change this?

---

### Post by maggiemonic on 2009-04-22
same deal:

"The application "gconf-editor" attempted to change an aspect of your configuration that your system administrator or operating system vendor does not allow you to change. Some of the settings you have selected may not take effect, or may not be restored next time you use the application."

...with no change in wallpaper.

---

### Post by hansdown on 2009-04-22
Actually, this may be easier.

---

### Post by hansdown on 2009-04-22
The way I do it in ubuntu 8.04 is,

Right mouseclick desktop.

Select "change background."

Select "add".

Now you can choose any picture from pictures, desktop, etc.

Is it the same for you?

---

### Post by maggiemonic on 2009-04-22
that method did  work yesterday, though i ran into the problems 1. and 2. stated above. strangely, although i can go add pictures to my choices in 'change desktop background' still, but selecting one does not change it from the default.  

so i went back thru the terminal to desktop>gnome>background  and right clicked on picture_filename and chose 'unset key' to try and undo any nonsense i caused by chosing set default and set mandatory previously. this changed nothing. 

will the fabric of the universe fall apart if it i put images in usr/share/backgrounds? it seems like a harmless place a lot of people'd want to get into.

---

### Post by Bölvaður on 2009-04-22
> **maggiemonic said:**
> will the fabric of the universe fall apart if it i put images in usr/share/backgrounds? it seems like a harmless place a lot of people'd want to get into.

When you place images in there they will probably be persistent in your appearance application where you pick wallpapers you have picked... 

alt+f2```

gksu nautilus ~/Desktop
```

this will give nautilus (filemanager) super user rights (gksu) and initiate it on your desktop. Or use just ~/ to begin in your user's home directory.
Then just copy the wallpapers and put into /usr/share/backgrounds


But this kind of looks like you are running from live cd or something. Do you lose your personal data after restarting?
If not, do the wallpapers still exist in their place but the appearance program have gone back to how it was before you dragged them in? (appearance program reset, no other changes)

---

### Post by maggiemonic on 2009-04-22
im not running off live cd, its installed for real. my personal files are fine, but it is resetting the appearance program whenever i reboot. 

i got my images into usr/share/backgrounds, which is wonderful! thanks! but even when they are in there and i add them to my choices via right clicking on the desktop and all, i cant apply them as wallpaper. 

after rebooting once, i was only able to choose the plain colored background with gradient and any image i chose didnt change that.  after rebooting twice, when i chose either of the two blue swirly default images the desktop loses the gradient, but when i select my added images the gradient remains. 

stupid details but strange. maybe  i guess im just stuck with a gradient desktop. thats a sad sad fate.

---

### Post by maggiemonic on 2009-04-22
i fixed it!

press alt+f2 and enter 'sudo gconf-editor' (sudo may not be needed) and make sure to select 'run in terminal'. enter password if necessary. go to desktop>gnome>background and look at the directory which picture_filename is associated with. save the image you want to have as wallpaper in this directory as whatever .jpg it says. make sure to type 

gksu nautilus ~/Desktop 
into the terminal prior, though in my case it said it didnt know what desktop was. still made it possible to alter usr/share/pixmaps/backgrounds/gnome/background-default.jpg.  in my case the gnome folder here did not exist, so i made it and put the image i liked in there and named it background-default.jpg. yay!

may also be needed to right click on picture_filename and chose set as default and/or set as manditory. 

thanks all!

---

