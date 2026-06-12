---
title: "Oh Snap - My Resolution Choice Won't Log Me In!"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by coldReactive on 2009-11-06
So, yesterday, before I shut down, I decided to set my resolution to 1024x768 on my ThinkPad T41, because having it at 1400x1050 makes everything a bit small for my tastes.

But, when I started up my ThinkPad today, it wouldn't let me login to my xfce session (there's two of them listed, both do not let me login.)

So, I decided to login to KDE (since I have KDE installed by chance.) Well, to be honest, I couldn't do anything in it, my graphics apparently doesn't like KDE's kickoff menu, so I had to crtl+alt+del into logging out.

Then, I decided, hey, what about xterm? I logged into xterm. Now, nothing was on screen but xterm and the wallpaper. So, I decided I'd rebuild my desktop from terminals and keep all the terminals open so I could type all this.

(Now, if you run into this problem, skip over to step 3 while on xterm, you'll be much happier.)

1. I started xfce4-panel (Since xfce4-terminal is on there as a launcher)
2. launched xfce4-terminal from the panel launcher I had
2b. launched xfwm4 --replace so I could move windows around.
3. launched xfdesktop so I could  access my pretty right-click menu with all the applications (since I removed the applications menu from panel.
4. in a new xfce4-terminal tab, I launched nm-applet, because it was not running, so I had no wifi until I started it.

Now I'm typing here, in midori, hoping SOMEONE will help me restore my xfce session so I can login to it!

---

### Post by coldReactive on 2009-11-06
And here's a bug report for it:

[http://bugzilla.xfce.org/show_bug.cgi?id=5954](http://bugzilla.xfce.org/show_bug.cgi?id=5954)

---

### Post by coldReactive on 2009-11-06
Sorry but, I'm not going to wait 24 hours for a reply.

bump.

---

### Post by coldReactive on 2009-11-06
Yes, I went to ubuntu irc on freenode, no replies.

Guess I'll just reinstall the damn thing.

---

### Post by coldReactive on 2009-11-07
Came up again after I blanked my xinitrc or whatever after trying to install gnome-globalmenu2.

So it's not just a resolution issue.

---

