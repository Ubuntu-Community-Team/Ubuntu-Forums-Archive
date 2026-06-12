---
title: "hotkeys"
date: 2009-08-03
forum: New to Ubuntu
---

### Post by BarefootSoul83 on 2009-08-03
I use the keystrokes "Windows+M" and "Windows+E" a lot..  just yesterday these stopped working.  All of my other keystroke shortcuts  work.  I think I narrowed it down to the "Windows" key not working.  Any suggestions?

---

### Post by Volt9000 on 2009-08-03
In a terminal type

```

xev

```

Then focus on the window that popped up, and press your Windows key will monitoring the output in the terminal window. If the key is physically working, you should get a KeyPress and a KeyRelease event.

Try not to move the mouse, as mouse events will generate a lot of text.

---

### Post by BarefootSoul83 on 2009-08-03
Thanks Volt ... this is what I got...


KeyPress event, serial 30, synthetic NO, window 0x3e00001,
    root 0xb3, subw 0x0, time 55345001, (291,314), root:(301,411),
    state 0x10, keycode 133 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

---

### Post by Volt9000 on 2009-08-03
Ok so it seems the keyboard is physically working, but the shortcuts aren't being recognize.
I assume you also got a KeyRelease event as well?

---

### Post by BarefootSoul83 on 2009-08-03
oops...forgot to paste that too =-)  

KeyRelease event, serial 33, synthetic NO, window 0x3e00001,
    root 0xb3, subw 0x0, time 55345086, (291,314), root:(301,411),
    state 0x50, keycode 133 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False


hmm...why would the shortcuts be recognized one day and not the next?  I really didnt make any changes to my computer when it happened.  I think the only thing I did was install Virtual Box...

---

### Post by jacklinux on 2009-08-03
> **BarefootSoul83 said:**
> oops...forgot to paste that too =-)  

KeyRelease event, serial 33, synthetic NO, window 0x3e00001,
    root 0xb3, subw 0x0, time 55345086, (291,314), root:(301,411),
    state 0x50, keycode 133 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False


hmm...why would the shortcuts be recognized one day and not the next?  I really didnt make any changes to my computer when it happened.  I think the only thing I did was install Virtual Box...
im not sure, but maybe virtua box uses them, try closing that and then seeing the keys work.

---

### Post by BarefootSoul83 on 2009-08-03
Dont have it open... I loaded it a few days ago to try out ArchLunix.  never opened it more than once....

---

### Post by jacklinux on 2009-08-03
Well i'v never heard of this.
I take it you've tryed rebooting..maybe uninstall virtual box might help

---

### Post by wojox on 2009-08-03
Poke around in System > Preferences > Keyboard Shortcuts
Windows button is Super L

---

### Post by BarefootSoul83 on 2009-08-03
yeah...mojox...thats the first place I looked...  I could find no "SuperL" "Windows" or "meta"  ...nor could I find any command that specified the color invert...or the view of both desktops @ the same time...=-(

---

### Post by wojox on 2009-08-03
Virtualbox owns the keyboard:

[http://www.virtualbox.org/manual/UserManual.html#id2501332](http://www.virtualbox.org/manual/UserManual.html#id2501332)

---

### Post by jacklinux on 2009-08-03
> **wojox said:**
> Virtualbox owns the keyboard:

[http://www.virtualbox.org/manual/UserManual.html#id2501332](http://www.virtualbox.org/manual/UserManual.html#id2501332)
So to more or less fix he should unistall right?

---

### Post by HavocXphere on 2009-08-03
> **wojox said:**
> Poke around in System > Preferences > Keyboard Shortcuts
Windows button is Super L
+1

That option definitely has an effect on this.

Also running w/ or w/o compiz also has an effect on shortcuts.

---

### Post by BarefootSoul83 on 2009-08-03
so let me get this straight.... Virtual Box owns the keyboard even when it is not in use?

---

### Post by BarefootSoul83 on 2009-08-03
just to see...I uninstalled VirtualBox... NO DICE!  any other suggestions?

---

### Post by wojox on 2009-08-03
i don't use virtualbox but that's what I gathered from their site. Look in home folder and list all hidden files. When you uninstall an app. it won't remove the conf files from home for some strange reason. Maybe a reboot to.

---

### Post by BarefootSoul83 on 2009-08-03
Thanks man....  hmmm.... I rebooted... (the uninstall command I used was as follows:)


sudo apt-get remove --purge virtualbox-3.0

purge wouldn't take care of the conf file?

how do I go about finding the files to delete?

(newbie)

---

