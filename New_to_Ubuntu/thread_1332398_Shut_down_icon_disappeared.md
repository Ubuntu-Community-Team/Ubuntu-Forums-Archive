---
title: "Shut down icon disappeared"
date: 2009-11-20
forum: New to Ubuntu
---

### Post by cloyd on 2009-11-20
Hi.  I'm new.  I love Ubuntu Netbook Remix 9.10.  My Gateway netbook came with windows home basic, and it constantly crashed, locked up, etc.  Ubuntu does everything I want it to do but print with my lexmark printer . . . so I am keeping windows for that. 

I am learning and sometimes things happen I just don't understand.  I was looking at different themes one day, and my shutdown icon at the top right corner of the screen just was gone.  It was grey, and when clicked, had a drop down menu with "shutdown, restart, hibernate, etc.)   Needing some way to shut the machine off, I simply pressed the power button and got a grey dialogue box in the middle of the screen with all the same options.  

Ok. no real problem. Still seemed to have a proper shutdown method, but I really didn't like the whole idea of pressing the power button.  Eventually, I found a applet to put a new shutdown icon in the panel.  Now, it is not grey, it is red, and it does not set at the far right of the panel, but to the left end of the other icon in the right side of the panel (to the right of the battery, wireless, speaker and date)

Everything is ok, but   . . .  What did I do?  How did this happen?  I just want to understand my system better.

---

### Post by Ampi on 2009-11-20
Didn't you simply richt-click your panel and choose "Add to panel"? Then you can add a red shutdown button.. 
The new UNR simply didn't add the shutdown button as a default..

---

### Post by cloyd on 2009-11-20
Yes, that is how I got the applet.  However, it was difficult.  It seemed that placement of the arrow cursor had to be very precise or I did not get the "add applet" menu. And I was unable to move applets around to place it back where it had originally been. But that is no real problem.  I just want to know how I lost the thing it the first place? It was there when I first installed Remix.  I noticed it was gone while messing around with different desktop themes.

By the way, thanks for the reply.

---

### Post by macklenc on 2009-11-29
I installed the netbook remix 9.10 as well, however, I never got the shut-down menu, I have given up on getting one, (I don't have an add to panel option) but if you cant move the icons in the Linux task bar, you should be able to right click on them and deselect "lock to panel" then you should be able to move them. (or you could just use the middle mouse button and drag):mrgreen:

---

### Post by oldmankit on 2010-03-10
I can confirm the same problem.  I used to have a grey applet that looked like a power button, with all options from switch user, logout, to poweroff, suspend etc.  One day I logged in to another user (whilst still logged in as myself), it gave some error about fast-user-switching, and now the grey power button is gone.  I cannot find it in the add to panel menu.  The new red one does not give half of the old options, such as logout.

---

### Post by 416inversed on 2010-03-10
> **oldmankit said:**
> I can confirm the same problem.  I used to have a grey applet that looked like a power button, with all options from switch user, logout, to poweroff, suspend etc.  One day I logged in to another user (whilst still logged in as myself), it gave some error about fast-user-switching, and now the grey power button is gone.  I cannot find it in the add to panel menu.  The new red one does not give half of the old options, such as logout.

I did the same thing. I solved it in terminal:

```

sudo apt-get install indicator-applet-session

```

Then right-click the panel>Add to Panel... and then select 'Indicator applet session'

That should return the other applet.

---

### Post by presence1960 on 2010-03-10
> **416inversed said:**
> I did the same thing. I solved it in terminal:

```

sudo apt-get install indicator-applet-session

```

Then right-click the panel>Add to Panel... and then select 'Indicator applet session'

That should return the other applet.

+1

Right click the panel exactly where you want the applet to go.

---

### Post by oldmankit on 2010-03-11
> **416inversed said:**
> i did the same thing. I solved it in terminal:

```

sudo apt-get install indicator-applet-session

```then right-click the panel>add to panel... And then select 'indicator applet session'

that should return the other applet.

+2

---

### Post by cloyd on 2010-03-12
Now I know: Others have had the same problem, and they don't know exactly why it happened.  I'm glad to get the grey applet back, though the red one works for me. I am the only user on my netbook, so no need to log out.

I don't always get the answer I want when I want it, but ultimately, people chime in, and I manage go get things working, and I learn _something_. Ubuntu is great, and the community is great. Having more fun with this than a barrel of monkeys.

---

### Post by kyletstrand on 2010-03-12
> **416inversed said:**
> I did the same thing. I solved it in terminal:

```

sudo apt-get install indicator-applet-session

```Then right-click the panel>Add to Panel... and then select 'Indicator applet session'

That should return the other applet.


Amen.  I did the same thing as well.  I found a whole bunch of real cool packages that I did add to my panel after accidentally deleting the Indicator session.  I also agree that the red shutdown button is too clunky and not functional enough for its size.

---

### Post by cloyd on 2010-05-04
Just an update. One day, after an update, the original or one that looked just like it, miraculously reappeared. ???????? I guess it is solved. But I like the klunky red one bettr

---

### Post by Riffronan on 2010-07-24
It's just being picky about eye candy, I guess but I also didn't like the gnarly red button (that didn't 'do' as much) clashing with the standard dark theme.  I just 'right click' removed it and then 'right click', 'add to panel', 'indicator applet session' and voila, there's the theme-friendly, ultra functional button again.

---

### Post by cloyd on 2010-07-24
Since this original post, I have switched to Lucid (and not the netbook version). However, I still kind of like the red one . . . it isn't red in all themes. But the reason I like it is the difference in the drop down menu. It is big easy to click on the right box. It does not give the option to change users, but I am the only one on this machine anyway. I keep* two *shutdown buttons. I guess it's kinda silly, but I have them anyway.

---

