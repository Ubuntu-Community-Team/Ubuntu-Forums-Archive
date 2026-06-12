---
title: "I just added a panel to the right side and I can't remove it"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by Momotombo on 2010-06-13
I clicked on the top panel with the menus and such and then I added one and now there's an empty space on the right. When I maximize firefox, for example, there's a panel-width empty space on the right going all the way up and down the screen.

How do I remove it? It's obviously not letting me right-click on it. Is there a general panel management software somewhere?

Also, I removed the shutdown/restart icon in the top right and I can't find the exact one to get it back. Not that it's a big deal, but I want to have some control over that.

And finally, with the mail icon, I downloaded pidgin along with a gmail notifier so now I want to get rid of the default chat, mail, and broadcast selections. How do I do that?

Thanks

---

### Post by Paddy Landau on 2010-06-13
There's a bug with the panels. Reboot and you should see your new panel.

---

### Post by Momotombo on 2010-06-13
Right, I actually force closed a panel and it quickly restarted and showed me the new, messed-up looking panel. I managed to delete it.

I have a new question along with the rest: How can I move icons around in the top panel? Some of them are behind the clock now and I don't want the clock to eventually move too close to the middle of the top panel

thanks again

---

### Post by kerry_s on 2010-06-13
> **Momotombo said:**
> Right, I actually force closed a panel and it quickly restarted and showed me the new, messed-up looking panel. I managed to delete it.

I have a new question along with the rest: How can I move icons around in the top panel? Some of them are behind the clock now and I don't want the clock to eventually move too close to the middle of the top panel

thanks again

i use middle click drag to move things around on the panel.

next time that happens just press alt+f2 & type "gnome-panel --replace"
that will restart the panels.

---

### Post by Momotombo on 2010-06-13
Hey, thanks a lot, I didn't know I could middle-click drag in the panels

Now, how can I put the power icon back in the top panel? I tried adding it, but I can't find the exact one.

And also, how can I remove the now defunct selections in the mail icon? That is, the "Chat" and "Mail" selections, since I already added gmail and pidgin.

thanks again

---

### Post by Jakiejake on 2010-06-13
> **Momotombo said:**
> Hey, thanks a lot, I didn't know I could middle-click drag in the panels

Now, how can I put the power icon back in the top panel? I tried adding it, but I can't find the exact one.

And also, how can I remove the now defunct selections in the mail icon? That is, the "Chat" and "Mail" selections, since I already added gmail and pidgin.

thanks again

I think it is the indicator applet

---

### Post by Jakiejake on 2010-06-13
Also if you ever want to reset the panels to default
In terminal type > .gconf it should open up a window go into "apps" and then delete the "panel" folder and reboot!

---

### Post by Momotombo on 2010-06-13
> **Jakiejake said:**
> I think it is the indicator applet

Okay. And when I tried adding an indicator applet it just duplicates the mail icon along with a couple of other programs that are open at the time.

---

