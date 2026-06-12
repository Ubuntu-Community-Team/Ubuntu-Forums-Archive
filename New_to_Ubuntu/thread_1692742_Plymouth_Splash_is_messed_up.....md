---
title: "Plymouth Splash is messed up...."
date: 2011-02-21
forum: New to Ubuntu
---

### Post by zer010 on 2011-02-21
Sorry for the poor headline, but I don't quite know how to better describe it in short.  
I had been tweaking my boot up by adding a nice background to GRUB2 and I got that how I wanted it, but I wanted to change the drab purple loading splash[ default.jpg].  Instead, I ended up changing the login screen's background which is cool.  
 I had googled around for a way to specifically change the load splash and found a few things.  I tried the ones that looked promising, but to no avail.  Finally, I remembered about the Plymouth Manager program [ [http://sourceforge.net/projects/plymouthmanager/](http://sourceforge.net/projects/plymouthmanager/) ]. So I get it and try it out and using the program seemed pretty smooth. However, when I restarted the load splash was definitely NOT what I was expecting[current.jpg].
 I un-installed PM and set to work on trying to rectify this problem. I tried re-installing Plymouth and even tried to install a different theme via Synaptic, but to no avail. Google doesn't bring up much because, apparently, many people confuse the load splash with the login screen....don't know why....
On top of the load splash, when I shutdown, I get the dark purple background with light purple text[shutdown.jpg]. 
Other than the splash screens, everything works great.  Hell, I wouldn't mind having the CLI text instead of splash screens if they were in the standard black and white, but I'd like to get this under control. It's been about two weeks and it's starting to get on my nerves :-k.

---

### Post by Mariane on 2011-02-22
IMHO the easiest way to change that kind of thing is to
1) Find an image you like, with high enough resolution (in advanced google image search you can specify minimum size of picture)
2) Save it to your Desktop or somewhere you can find it easily
3) Convert it to .jpg if it is not already in jpeg format. You can do this by opening it with some paint program and choosing jpeg in the "save as" options. 
4) Move it to replace the image you don't like (shutdown.jpg in your case). You might need root access if the file is somewhere unwritable without root access, so the command is something like: 

```

sudo mv <full path to newfile.jpg>/newfile.jpg <full path to shutdown.jpg>/shutdown.jpg

```

Replacing <full path to file> by the exact paths to the corresponding file. 

Mariane

---

### Post by zer010 on 2011-02-22
Well, that's pretty much what I did to change the GRUB background, but it doesn't explain what happened to the splash images....

---

### Post by zer010 on 2011-02-22
I just found this [http://ubuntuforums.org/showpost.php?p=9292589&postcount=16](http://ubuntuforums.org/showpost.php?p=9292589&postcount=16) and I'm thinking of trying it out. The only part that I'm not exactly clear about is updating framebuffer, but I'm sure there's got to be some info on that somewhere. 
I've also read that Plymouth is almost impossible to remove completely, but the themes can be removed so that there is just the scrolling text with no splash. I've also read that Plymouth is supposed to actually speed up the boot process.... 
It's starting to sound like Plymouth has been a pain from the get-go.

---

