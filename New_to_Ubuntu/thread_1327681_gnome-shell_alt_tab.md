---
title: "gnome-shell alt tab?"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by coldReactive on 2009-11-15
Where's my alt-tab?

According to the following screenshot: [http://twitpic.com/l43rh](http://twitpic.com/l43rh)

there should be one, but when I hit alt-tab, nothing comes up!

---

### Post by eagle416 on 2009-11-15
In Kubuntu, I can only do tricks like that when I've enabled Desktop Effects. I also have to choose how I switch: with the desktop cube, the slide cards, or present all side by side. Then I can configure the keyboard shortcuts. Try to enable desktop effects and configure the shortcuts for each transition type in GNOME.

---

### Post by uBeer on 2009-11-15
The picture is a preview of an upcoming release of gnome, so it is only available as a test environment.

If you really want to try it out you could install the package gnome-shell (if you run 9.10 it's in the repositories) and then run ```
gnome-shell --replace
``` to activate but be warned: it is not stable!

---

### Post by uBeer on 2009-11-15
I think I misunderstood and you're actually running gnome-shell. Weird that it doesn't work. I tried it out about a week ago and I saw that the alt-tab thing worked...

Sorry that I can't help you with it!

---

### Post by coldReactive on 2009-11-15
> **eagle416 said:**
> In Kubuntu, I can only do tricks like that when I've enabled Desktop Effects. I also have to choose how I switch: with the desktop cube, the slide cards, or present all side by side. Then I can configure the keyboard shortcuts. Try to enable desktop effects and configure the shortcuts for each transition type in GNOME.

compiz is incompatible with gnome-shell.

---

### Post by vange on 2009-11-16
I experience the exact same issue: running gnome-shell, but ALT+TAB doesn't work.

Maybe it has something to do with my customization of Visual Effects before starting gnome-shell - I have played around with different task switchers in compiz-config before starting gnome-shell, and were forced to reconfigure my ALT+TAB (as some task switchers used CTRL+ALT+TAB, which I didn't like).

If I create a new user on my laptop this issue doesn't appear, so I think it has something to do with my previous customization.

Do anyone have a clue where you can configure this behavior in gnome-shell? This prevents me from playing around with gnome-shell.

---

### Post by coldReactive on 2009-11-16
> **vange said:**
> I experience the exact same issue: running gnome-shell, but ALT+TAB doesn't work.

Maybe it has something to do with my customization of Visual Effects before starting gnome-shell - I have played around with different task switchers in compiz-config before starting gnome-shell, and were forced to reconfigure my ALT+TAB (as some task switchers used CTRL+ALT+TAB, which I didn't like).

If I create a new user on my laptop this issue doesn't appear, so I think it has something to do with my previous customization.

Do anyone have a clue where you can configure this behavior in gnome-shell? This prevents me from playing around with gnome-shell.

I've purged compiz (meaning, removing its config), so I don't think it's that.

---

### Post by Locke_99GS on 2009-11-16
I'm running gnome-shell right now as well, also with no Alt+Tab functionality.

---

### Post by vange on 2009-11-17
I got it working! Use gconf-editor and check your settings for the key apps->metacity->global_keybindings->switch_windows. For details, see this link: [https://bugzilla.gnome.org/show_bug.cgi?id=591671](https://bugzilla.gnome.org/show_bug.cgi?id=591671)

---

### Post by Locke_99GS on 2009-11-19
Yay vange! :) Works for me now.
edit: Ohh yes, BTW, I like it. Very clean, nice.

---

### Post by eagle416 on 2009-11-20
> **coldReactive said:**
> compiz is incompatible with gnome-shell.

KDE has its own effects. I don't have Compiz or Beryl installed at all.

---

### Post by mastmaulaa on 2011-10-15
thanks vange..
now i think i can give a shot to GS after this fix!

---

### Post by Balthazar_Droid on 2011-10-20
I am having a similar issue, except Alt-Shift-Tab works, but Alt-Shift doesn't. I have it set in gconf editor, and under system>keyboard settings>navigation. I can't get it to work at all. Has anyone ran into this?

---

### Post by vange on 2011-10-22
Hi Balthazar_Droid - I am currently not using Gnome Shell, so unfortunately I cannot help you. I recently did a clean install of Ubuntu Oneiric 11.10, and I haven't grown tired of Unity yet - but if I do, I will try Gnome Shell again.

---

### Post by Silent Warrior on 2011-10-22
I'm using Mint 11, so I only have Gnome Shell from PPA, but see if installing the Shell extension Window Navigator helps. You'll have to use gnome-tweak-tool to enable it, then restart the shell.

---

### Post by wate on 2011-10-23
reset the unity profile* with CCSM or via terminal:
unity --reset

and reset gnome-shell.

*Save your current unity profile before reset, if you want to save your changes.

Doesn't have much sense, but it solved my problem.
Hope it solves yours too.

---

### Post by topdownjimmy on 2011-11-06
I know this is an old thread, but I just came here from a Google search and thought I'd help out anyone else who did the same.

This has to be set in System Settings > Keyboard > Shortcuts > Navigation > Switch applications

Ubuntu disables this by default so that it doesn't conflict with Unity window switching, I assume.

---

