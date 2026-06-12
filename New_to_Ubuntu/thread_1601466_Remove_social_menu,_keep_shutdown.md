---
title: "Remove social menu, keep shutdown"
date: 2010-10-20
forum: New to Ubuntu
---

### Post by Anutesyn on 2010-10-20
I've tried to remove the social menu thing (top panel the chat box with the name) but when I did that I also removed the shutdown menu. 

Is there any way I could do this? 

Thanks in advance.

---

### Post by ivarn on 2010-10-20
Yes, remove it and just add the "shut down" button to the menu from "add to panel".
Or you can remove the whole thing and use CTRL+ALT+DEL which is the shortcut for the same menu.

---

### Post by Anutesyn on 2010-10-20
I tried this but the shut down I added had the appearance from the old Ubuntu system. The red with white, kind of looked out of character. I might've just misunderstood it. I'll try again with the button.

edit:
Added it to the panel, figured maybe if I switched themes back and forth it might get the right look. Changed to Clearlook and it did change the icon to that theme but when I switched back to Ambience it had that almost XPish look (white on red).

---

### Post by Bluenoser81 on 2010-10-20
I did the same thing, and just added the "Shutdown" and "Log Out" applets by right clicking any free space on the top bar and selecting "Add to Panel..." It is a workaround, but I wonder if there is another way to get back that one button with drop down selections, instead of having to add two or three buttons to replace it?

---

### Post by subsynth on 2010-10-20
sudo apt-get remove indicator-me 

removes socail/me while keeping shutdown

sudo apt-get remove indicator-messages

removes mail/evolution notifications while keeping audio control

---

### Post by Anutesyn on 2010-10-20
> **subsynth said:**
> sudo apt-get remove indicator-me 

removes socail/me while keeping shutdown

sudo apt-get remove indicator-messages

removes mail/evolution notifications while keeping audio control

The commands did something. Will see what when I restart my laptop. Not sure if there's some "reload" command that won't remove any settings.
:D 
Edit: Restarted and the commands worked perfectly! Thanks a lot!

---

### Post by NealCrosby on 2011-02-19
> **subsynth said:**
> sudo apt-get remove indicator-me 

removes socail/me while keeping shutdown


I actually have the opposite problem.  I would like to add the social/me button.  How would I go about doing that?

---

### Post by grahammechanical on 2011-02-19
Hi NealCrosby

Go to Add to Panel and in the list select Indicator Applet Session and click Add. This will put the shutdown icon and the social/me menu in the panel. First you will only see the shutdown icon until you reboot.

Do not get confuse with Indicator Applet. This puts the sound and email icons on the panel

Regards.

---

### Post by h4xx0r on 2011-05-01
> **subsynth said:**
> sudo apt-get remove indicator-me 

removes socail/me while keeping shutdown

sudo apt-get remove indicator-messages

removes mail/evolution notifications while keeping audio control

Ok, Now the only thing I see is the shutdown drop-down menu :)
Thanks a lot dude ;)

---

### Post by beew on 2011-05-01
> **h4xx0r said:**
> Ok, Now the only thing I see is the shutdown drop-down menu :)
Thanks a lot dude ;)

You do realize this is an old thread? "Add to panel" no longer exist in Unity. But then you probably cannot remove the social menu in Unity either.

---

