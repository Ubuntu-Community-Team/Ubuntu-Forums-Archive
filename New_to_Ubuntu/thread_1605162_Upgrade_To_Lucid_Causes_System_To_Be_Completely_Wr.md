---
title: "Upgrade To Lucid Causes System To Be Completely Wrecked"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by Roger Allott on 2010-10-24
I have just 'upgraded' from karmic to lucid. I wish I hadn't.

The result of this upgrade is that my keyboard is now completely non-functional. That's not only my laptop's own keyboard but also my USB wireless one.

Being without a keyboard means that it's just about impossible to do anything at all. Of course, I've had to boot up Windows in order to post this plea for help.

Could someone help me diagnose the fault and correct it?

Secondly, any window that I open (my mouse still works, fortunately!) has absolutely no decoration. This means that there are no borders around anything, which is unsightly, but more importantly it means that I cannot move, maximise, minimise or close a window.

I tried going into System > Window and all I got was an error message telling me that there is no window manager designated (or words to that effect). Well, there certainly WAS a window manager there before I 'upgraded'! What's happened to it?

I've also lost my Cube, the four desktop wallpapers, and god only knows what else.

Note: If you suggest a method of resolving these issues, please take into account the fact that entering commands into Terminal are going to be just about impossible without a functioning keyboard, and that it's likely to take a while to respond because I'll need to shut down Windows, boot Ubuntu, do whatever is recommended, shut down Ubuntu, and boot Windows.

---

### Post by akand074 on 2010-10-24
Have you reactivated your proprietary drivers (System > Administration > Hardware drivers)? Also right click on the desktop and click "change desktop background" then try switching your theme to something else (perhaps your system is still trying to use Karmic's theme which was removed in Lucid?). Also go to compizconfig settings manager (System > Preferences > Compizconfig Settings manager, if its not installed just install it using synaptic package manager). Those are the only things I could suggest. Though if I was in your position I would just do a clean install.

---

### Post by SuaSwe on 2010-10-25
I agree with akand074, provided you either have a separate root directory and/or have all your stuff backed up!

Meanwhile, keep in mind that if you do need to "type" something into Terminal, you can always use Applications > Accessories > Character Map as an emergency solution. ;)

---

### Post by Roger Allott on 2010-10-25
Thanks for your help, chaps.

As it happens, the cure was System > Preferences > Appearance > Visual Effects

Of the 4 options, the first one (None) was selected for some bizarre reason. When I clicked the fourth option button (Custom), the system had a bit a think about the price of cheese and then magically found all of my old settings, which I chose to keep. 

And what's more, it fired my keyboards back into life!

---

