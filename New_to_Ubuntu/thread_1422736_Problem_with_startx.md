---
title: "Problem with startx"
date: 2010-03-05
forum: New to Ubuntu
---

### Post by Revo99 on 2010-03-05
Hello Again,

I am trying to start my x server using the following command:

startx

When I press enter the screen try's to refresh to go into Xserver (I assume) then I get the following:

reece@EVANS:~$ (with a little rectangular symbol after $ symbol. Sorry dont know how to find that symbol)

This shows in smaller text in the top lefthand corner of the screen. as a terminal message.

I think it could be to do with my screen settings or ATI 5770 graphics card.

Anyones help is appreciated.

Thank you again in advance.




I think its correct to start a new thread. Sorry If its not.

---

### Post by Bachstelze on 2010-03-05
Try to run a X program (for example [font=monospace]xclock[/font]) from the terminal you see. If you see a clock appearing, it means that your X server is running. Now you need to install a window manager. ;)

---

### Post by Revo99 on 2010-03-05
> **Bachstelze said:**
> Try to run a X program (for example [font=monospace]xclock[/font]) from the terminal you see. If you see a clock appearing, it means that your X server is running. Now you need to install a window manager. ;)

Thank you for your post. Bachstelze. 

[FONT="Arial Black"]So the steps I took:[/FONT] 

From normal terminal typed in xclock and got the following:

reece@EVANS~$ xclock

then got "Error: Can't open display:"

[FONT="Arial Black"]Then tried this[/FONT]

reece@EVANS~$ startx 

The screen flickers and displays the below as tiny text. I then cant type or do anything I have to turn off computer from with power button to restart.

eece@EVANS:~$ &#58748;
:cry::?

---

### Post by Bachstelze on 2010-03-05
How did you install your X server? You do not seem to have a standard installtion.

---

### Post by Revo99 on 2010-03-05
> **Bachstelze said:**
> How did you install your X server? You do not seem to have a standard installtion.

Used Code:
sudo aptitude install xorg

This is the thread I posted about installing an X server.

 [http://ubuntuforums.org/showthread.php?t=1422017](http://ubuntuforums.org/showthread.php?t=1422017)

Appreciate your help. Thank you!

---

### Post by patchwork on 2010-03-05
Did you install a window manager with it?

---

### Post by Revo99 on 2010-03-05
> **patchwork said:**
> Did you install a window manager with it?

Thanks for the post patchwork. No I didn't. All I have done is install xorg. How would I choose and install a window manager.

Cheers,

Reece

---

### Post by patchwork on 2010-03-05
There are a lot to choose from, and everybody has their own preferences.  I use icewm, fluxbox, and metacity on different systems for different purposes.  Check out [http://xwinman.org/](http://xwinman.org/) and find one you like, then install and try to restart the x server.  

icewm is lightweight and very customizable (but probably not good for those looking for a plug and play window manager, as it requires some manual setup in text files)

fluxbox is slightly more ready to use out-of-the-box, but isn't heavily loaded.

metacity is the default window manager on ubuntu desktop installs

All are in the repos:

sudo apt-get install <choice of window manager>

---

### Post by Revo99 on 2010-03-05
> **patchwork said:**
> There are a lot to choose from, and everybody has their own preferences.  I use icewm, fluxbox, and metacity on different systems for different purposes.  Check out [http://xwinman.org/](http://xwinman.org/) and find one you like, then install and try to restart the x server.  

icewm is lightweight and very customizable (but probably not good for those looking for a plug and play window manager, as it requires some manual setup in text files)

fluxbox is slightly more ready to use out-of-the-box, but isn't heavily loaded.

metacity is the default window manager on ubuntu desktop installs

All are in the repos:

sudo apt-get install <choice of window manager>

Looking into this I think FVWM would be good. Any thoughts. i will install and post how it go's.

In terms of window manager do I need to use any commands to open this before startx command.

Thank you

---

### Post by doorknob60 on 2010-03-06
No, but add your WM to the ~/.xinitrc file first. Example, for openbox:
```
exec openbox-session
```
or fluxbox:
```
exec fluxbox
```

Pretty straightforward IMO :) Better than using GDM and KDM, DMs are just a waste of resources :P Well I guess they're good if you have multiple users, but for me, not needed :D

---

### Post by Revo99 on 2010-03-06
Thanks you Bachstelze, patchwork & doorknob60 for your help through this. This has resolved the problem.

---

