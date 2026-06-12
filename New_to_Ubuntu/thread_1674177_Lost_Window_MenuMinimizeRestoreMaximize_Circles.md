---
title: "Lost Window Menu/Minimize/Restore/Maximize Circles"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by jamiehendrich on 2011-01-23
Newbie:

I have two computers.  On the second computer I just lost the little buttons on the right-hand corner of my screen. The appearance preferences are set to "custom" with the line, the square and the X.  I want the buttons.  

I have no idea how they disappeared and were changed.  They are on my first computer, just not on the second computer.  I've tried to google it and there was something about maclin4 but I don't have that as one of the choices to select under "appearance preferences" on either computer.

Could anyone please, in a very simple, basic fashion, tell me how to get those back?  I much prefer the buttons over the underscore, the square and the x.

Thank you very much.

Jamie

---

### Post by jamiehendrich on 2011-01-23
PS  As a clarification, they are the white oval, the amber button, the green button and the red button on my title bar up at the top, in the right-hand corner.  Thanks!

---

### Post by [Snc] on 2011-01-23
> **jamiehendrich said:**
> PS  As a clarification, they are the white oval, the amber button, the green button and the red button on my title bar up at the top, in the right-hand corner.  Thanks!

If i understood you correctly, You now have circles (like MAC) and want the normal buttons back.

Then go to "System" -> "Preferences" -> "Appearance" and select another Theme from the "Theme" tab, or click "Customize..." and choose the "Window border" type, there is also a preview available.

---

### Post by jamiehendrich on 2011-01-23
No, I want the Mac ones back on the second computer.  I want the buttons/circles back.

---

### Post by jamiehendrich on 2011-01-23
I went under "window border" and there is not one that has the white oval, the amber button, the green button and the red.

Is there a way I can copy it off my computer that still has them and copy that over to the second computer that doesn't.  I don't know where/what to look for.

---

### Post by jamiehendrich on 2011-01-23
here is a screenshot of how I want it to look.  This is the old computer.

The new one has an underscore, a box and an x.  I don't like that one.
I want the colored buttons.....if at all possible.  Wish I knew what I did to remove them from this new computer because I copied everything from the old to the new and it used to be on there.

Jamie

---

### Post by [Snc] on 2011-01-23
> **jamiehendrich said:**
> I went under "window border" and there is not one that has the white oval, the amber button, the green button and the red.

Is there a way I can copy it off my computer that still has them and copy that over to the second computer that doesn't.  I don't know where/what to look for.

Okay :) I see now what you want to do.

You would like to use the same theme on both computers.

On the one, that looks like you want, go to "System" -> "Preferences" -> "Appearance" and find out which Theme it uses and copy it to the other computer (find the name and find it in /usr/share/themes )

Then on the other computer copy it into /usr/share/themes and enable it in "Appearance Preferences"

Or, simpler, find the theme package online and install it.

ps. Make sure you use sudo when you cp, the themes are owned by root.
ps2. :} Please tell me if i was not clear enough...

---

### Post by jamiehendrich on 2011-01-23
I don't think I can do it like that.  Why?  Because it originally said "customized" or something and I did a "save as" and I put my jamie and the word "background."  But it put it in emerald manager ....or maybe I did.  

So...and when I go into themes, there are 137 themes in /usr/share.....whatever file you said to look in.  So....looks like I'm going to have to live with it.

It was a custom theme I think that my linux teacher had, but I don't know where to find it.

Thanks, though.

Jamie

---

### Post by jamiehendrich on 2011-01-24
Resolved.

I finally got ahold of my teacher.  You know all it was?  I had to do emerald --replace.  That's it.  And it's back.

Thank you for your response.  If I could have figured it out your way, I'm certain that would have worked as well.  I'm too "new of a newbie."

Have a great week.

Jamie

---

