---
title: "fonts installer, missing package?"
date: 2010-02-02
forum: New to Ubuntu
---

### Post by degarb on 2010-02-02
Looking through snaptic I don't see an installer.   Here is why the relevant old threads might not work.

One thing I will point out,  most females live for formatting documents.  This is passtime and obsession. They will spend hours on a paragraph making it look exactly right.   So, it is a BIG mistake to not include a true type font installer under system or when you right click a ttf file.  Running scripts and command lines with sudo to open nautilus to install a font is out!  Again, they live for this tweaking.

I couldn't extract a a file.  I figured out that when you make a folder, it creates as permission root, so the user cannot write to the folder.  This is backwards.  If I create a folder anyone should be able to use it.  If I restrict it, fine.  but don't break something to protect it.    

I am a big believer is installing a system open, then locking down, one lock at a time.  Why, because you do not have a system to breach, if you cannot get anything working.   


Another annoyance that is hitting me as a new user who hasn't yet learned to live with inconvenience, is I cannot open a terminal from nautilus with command line already set to currently open folder.

---

### Post by dearingj on 2010-02-02
> **degarb said:**
> Looking through snaptic I don't see an installer.   Here is why the relevant old threads might not work.

One thing I will point out,  most females live for formatting documents.  This is passtime and obsession. They will spend hours on a paragraph making it look exactly right.   So, it is a BIG mistake to not include a true type font installer under system or when you right click a ttf file.  Running scripts and command lines with sudo to open nautilus to install a font is out!  Again, they live for this tweaking.

It's fairly easy to install a font in Ubuntu. Just double-click the font file, and then click the "Install Font" button in the window that pops up.

> **degarb said:**
> I couldn't extract a a file.  I figured out that when you make a folder, it creates as permission root, so the user cannot write to the folder.  This is backwards.  If I create a folder anyone should be able to use it.  If I restrict it, fine.  but don't break something to protect it.

You must have been running as root or something when you figured that out. Normally when you create a folder, it creates it under your own name, not root. You can read and write to folders you create, and other users will by default have read-only access.

> **degarb said:**
> Another annoyance that is hitting me as a new user who hasn't yet learned to live with inconvenience, is I cannot open a terminal from nautilus with command line already set to currently open folder.

That's easy enough to fix; just install the "nautilus-open-terminal" package from within Synaptic.

---

### Post by oldos2er on 2010-02-02
If you want to install fonts available to your user, place them in ~/.fonts. If you want them available system-wide, put them in /usr/share/fonts/truetype/ (you'll need admin privileges to do so). Then update the font cache ```
sudo fc-cache -fv
```

Edit: Nevermind.

---

### Post by degarb on 2010-02-02
> **dearingj said:**
> It's fairly easy to install a font in Ubuntu. Just double-click the font file, and then click the "Install Font" button in the window that pops up.



You must have been running as root or something when you figured that out. Normally when you create a folder, it creates it under your own name, not root. You can read and write to folders you create, and other users will by default have read-only access.



That's easy enough to fix; just install the "nautilus-open-terminal" package from within Synaptic.


Will do, thanks.  The big problem was I didn't see a font installer in snaptic, system>admin, right clicking on ttf.  Then googling, it ran up on long lengthy commandlines and scripts that didn't work.     I recommend adding it to right click context menu for the ttf files.   This would have saved me 2 hours.  And others.  The point of pointing out brick walls is to make the OS dominant.  A dominant OS means more software available for it and more compatibility.   Thus a win for existing users. 

When you use software for long, you become blind to design flaws.  Telling users to just live with a flaw, doesn't help the proper introspection to discover if something needs repair, or not.  It is like living with a lock that needs a key jiggle every turn.  If the builder allows a ton of quirks like this, he will go bankrupt.

---

