---
title: "Turned my screen off"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by Djalmahal on 2009-03-11
I'm trying to help my friend to set up a lenovo x200 up with ubuntu. His screen resolution in Ubuntu was 1024*700, I was stupied enough to follow some post on ubuntu forums that said go to preferences>screen resolution un check mirror screens and set resolution to off. Now the result is that his ubuntu after shortly (1 sec) showing the brown screen has a black monitor. I dropped into recovery mode but I'm not geek enough to figure it out from the command prompt. How do I get back to the old resolution or does anybody know the x200 model and knows how to get into the 1200*800 mode.

Thanks
Andreas

---

### Post by teamcoltra on 2009-03-11
Just edit the xorg file:
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by Djalmahal on 2009-03-11
Would the easiest way be to run

  sudo dpkg-reconfigure xserver-xorg

in the recovery mode ?

---

### Post by teamcoltra on 2009-03-11
> **Djalmahal said:**
> Would the easiest way be to run

  sudo dpkg-reconfigure xserver-xorg

in the recovery mode ?

just run "sudo gedit /etc/X11/xorg.conf" 

and add the file... xorg file is really easy to figure out...it keeps the same pattern for each option.

---

### Post by Djalmahal on 2009-03-12
Ok, the reconfigure command wasn't accepted it says "need and action option"
and the gedit xorg..conf says
GTK warning : cannot open display

as I'm in recovery mode

So, what's next??

Thanks for any help
Andreas

---

### Post by teamcoltra on 2009-03-12
> **Djalmahal said:**
> Ok, the reconfigure command wasn't accepted it says "need and action option"
and the gedit xorg..conf says
GTK warning : cannot open display

as I'm in recovery mode

So, what's next??

Thanks for any help
Andreas
then just change gedit to edit and that should fix it.

Otherwise if you can get as far as the login screen, you can always try logging in with a terminal, which will then also have GUI support. I onetime had to go a week without x >.< elinks and irssi became my friends.

---

### Post by Djalmahal on 2009-03-12
Alright, I actually mispelled the reconfigure command, I ran it but it didn't go through screen resolution, it just reconfigured the keyboard.

So, the screen is still black, I'm in recovery mode, the command line is all I have and I need to tell the system to go back to 1024*700 resolution

Thanks for all your input

Andreas

---

### Post by cariboo on 2009-03-12
> Would the easiest way be to run

sudo dpkg-reconfigure xserver-xorg

in the recovery mode ? 

This is more than likely what you need to repair your problem, running the above command wil create a default /etc/X11/xorg.conf and get you back to your desktop.

I just read your post try:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Jim

---

### Post by teamcoltra on 2009-03-12
> **cariboo907 said:**
> This is more than likely what you need to repair your problem, running the above command wil create a default /etc/X11/xorg.conf and get you back to your desktop.

Jim

He just stated that the above command did not work though :(

sudo edit /etc/X11/xorg.conf

Find where it shows your display and where it says "none" which is what you set it to... replace that with 800X600 or whatever you need to display at

---

### Post by Kareeser on 2009-03-12
Give this a try

```
xrandr --output VGA --auto
```

Replace VGA with the proper output... sometimes it's LVDS, or VGA-0... check what it is by running "xrandr" without any switches.

---

### Post by Djalmahal on 2009-03-12
Ok the command

sudo dpkg-reconfigure -phigh xserver-xorg

still leaves me with a black screen.

And because my screen is black I obvioulsy can't just go into preferneces>screen resolution and change it to whatever.
On the webpage of Ubuntu [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) I found the instruction

If you set a resolution inappropriate for your monitor in the Screen Resolution GUI tool, you can reset it by running rm ~/.config/monitors.xml from a terminal. 

No when I run this from the recovery session>drop into root shell prompt the output is

rm cannot remove /root/.config/monitors.xml No such file or directory

Is that because I'm in the root shell and the file is in the user directory?

---

### Post by Djalmahal on 2009-03-12
Ok, I actually did the rm command for the user directory and the screen is back.

Now, If anybody still knows how to adjust the screen resolution on a lenovo x200 to 1200*800 that would be great.

Thanks for all your input
Andreas

---

### Post by Kareeser on 2009-03-12
Did you try xrandr?

---

### Post by Djalmahal on 2009-03-12
Yeah, I did do xrandr, that worked, now I created an .xrandr file in the home directory so the change is permanent. Only thing is the gnome panel is shorter because it still thinks it's the old resolution.

Andreas

---

### Post by Kareeser on 2009-03-12
That's great that it worked, Djalmahal!

The only thing now is that we want a more permanent solution, since your xorg.conf is buggered.

Can you try to run the code to regenerate xorg.conf again?

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Djalmahal on 2009-03-12
I sure could but now the higher resolution is permanent because I generated a file in the home directory call .xprofile with the appropiate xrandr command, that works except for the gnome panel size.

So, what does the command exactly do, because xorg wasn't able to detect the higher resolution before.

---

### Post by Kareeser on 2009-03-12
xrandr?

```

xrandr        --output VGA       --auto
^ command     ^ which output     ^ automatically decide best resolution & refresh rate
```

---

### Post by thrice_loved on 2009-05-11
I did a similar thing (thinking it would be cute to see my screen all warped I chose a resolution that I knew was incorrect) - screen went black and I freaked out!

Still I was able to fix it with this command 
** rm ~/.config/monitors.xml**
Although, as I'm really bad with terminal stuff I thought I'd let any other newbies out there know how i did it GUI-style with a live CD. 

I booted up off a live CD and opened up a terminal then I typed:  **sudo nautilus**

This opens a nautilus file browser in which I can change my system files.
I navigated to **~/.config/monitors.xml   **
In my case this meant switching on show hidden files and going to claire/.config.
I then cut-and-pasted the **monitors.xml **file into my home directory (that's always a good idea because you can put it back later if it doesn't work).

Then I rebooted and my screen was back. Yay!

---

