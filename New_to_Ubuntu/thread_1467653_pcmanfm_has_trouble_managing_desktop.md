---
title: "pcmanfm has trouble managing desktop"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by mathfreak123 on 2010-04-30
It'll be easier to explain what trouble with pcmanfm I'm having with pictures instead of words:

(ignore the red circles please)
What's actually going on is shown in "Screenshot.png" as an attachment.

What I really want to happen is shown as "Screenshot-1.png" as an attachment.

(I don't want another background on top of the background.) However, having this background on top is also the only area where I can add desktop icons. I can't do this anywhere else.

So, I want to know if this is a bug and I should use a different desktop manager for now, or if I could do something to pcmanfm to get it to work as intended. :S

(Extra, but not point of this thread really: the red circles circle Firefox with the icon I can't change.)

EDIT: Also, sorry about making the pictures a little too large. I thought I cut them down plenty, but it looks like I need to cut a bit more for slightly faster download speeds.)

---

### Post by kerry_s on 2010-04-30
as far as i know they all do that, i'm using nautilus in lubuntu an even it does it that way, when i tried rox it was like that to, even xfdesktop4 did that. 
perhaps a limitation of the root window an icons?

---

### Post by mathfreak123 on 2010-05-01
I tried nautilus in Lubuntu a while ago, and it seemed to work as expected, but I have the feeling I'd have to start nautilus (or set a start-up script) every time I log in for the desktop to work as intended. :S

---

### Post by kerry_s on 2010-05-01
> **mathfreak123 said:**
> I tried nautilus in Lubuntu a while ago, and it seemed to work as expected, but I have the feeling I'd have to start nautilus (or set a start-up script) every time I log in for the desktop to work as intended. :S

not sure i understand, nautilus does the same thing as pcmanfm.

ps: the autostart file is in /etc/xdg/lxsession/Lubuntu
it's just a matter of commenting out lines & putting yours.

---

### Post by mathfreak123 on 2010-05-01
I think I forgot to add in a few things. I apologize.

I have an external monitor attached to my laptop. Everytime I log in, I have /etc/xdg/lxsession/Lubuntu/autostart run and shut off my laptop's monitor and use the external. However, with pcmanfm, it ends up looking like the case in the pictures on my first post. :S

---

### Post by kerry_s on 2010-05-01
i'm sorry your confusing me.
are you trying to say it's not adjusting to the size of the external screen?

---

### Post by mathfreak123 on 2010-05-01
The size of the external screen is sized correctly.

What pcmanfm does is that it places the actual desktop with the icons on top of the background with the wrong size, so the desktop only covers a portion of the entire screen.

So, in the first picture, the actual desktop is the rectangular portion you can see. I can left-click and everything normal inside this rectangle. However, once I try left-clicking outside the rectangle, I either get no response, or the menu pops up inside the rectangle away from my cursor.

---

### Post by kerry_s on 2010-05-01
i think i understand, i would say it's a bug.
does restarting pcmanfm on the external monitor do anything?

---

### Post by phillw on 2010-05-01
Hi, 

a couple of things

ensure you have the up to date lubuntu [https://wiki.ubuntu.com/Lubuntu/DocumentationHelp](https://wiki.ubuntu.com/Lubuntu/DocumentationHelp)

lubuntu does not support dual screen as yet, it is on the "Wish List". I've written a quick 'how-to' for using RandR with lubuntu, but I stress it is **not** a core component of lubuntu [http://forum.phillw.net/viewtopic.php?f=18&t=84](http://forum.phillw.net/viewtopic.php?f=18&t=84) and it may, or may not work on your hardware.


Regards,

Phill.

---

### Post by mathfreak123 on 2010-05-02
> **kerry_s said:**
> i think i understand, i would say it's a bug.
does restarting pcmanfm on the external monitor do anything?

Stopping pcmanfm from managing the desktop, using nautilus, and switching back to pcmanfm seems to work all right... I think (it's been 2 days since I played around).

I notice that the external monitor works as intended if I log into GNOME, log out, and log into LXDE.

> **phillw said:**
> Hi, 

a couple of things

ensure you have the up to date lubuntu [https://wiki.ubuntu.com/Lubuntu/DocumentationHelp](https://wiki.ubuntu.com/Lubuntu/DocumentationHelp)

lubuntu does not support dual screen as yet, it is on the "Wish List". I've written a quick 'how-to' for using RandR with lubuntu, but I stress it is **not** a core component of lubuntu [http://forum.phillw.net/viewtopic.php?f=18&t=84](http://forum.phillw.net/viewtopic.php?f=18&t=84) and it may, or may not work on your hardware.


Regards,

Phill.

If that's the case, then I suppose I might have to live with it for a while. I've already looked a bit into xrandr, which is what I used to configure my two monitors whenever I log in with Lubuntu.

---

