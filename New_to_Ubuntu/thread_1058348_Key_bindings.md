---
title: "Key bindings"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by scheibo on 2009-02-02
Not entirely sure if this is the right forum to place this query in, but seeing as I've only been on Linux for 2 weeks I figure I'm still a beginner.

I have two questions related to keyboard shortcuts and the like.

1) I've figured out how to use **gconf-editor**  (apps->metacity) to let me run emacs by pressing CTRL+ALT+e. However, I'd also like a way to use the CLI non-windowed version of emacs (emacs -nw) from a keyboard shortcut. Simply putting '/usr/bin/emacs -nw' as the value in the command_1 and making a shortcut to it doesn't work. I'm wondering if there is in fact a way to be able to launch emacs -nw from a keyboard shortcut. 

2) Secondly, and possibly more complicated... On my Sony Vaio CS190 laptop, there is a key labelled "alt" on the right side of my spacebar. One would assume that this is Alt_R, to match the Alt_L key on the left side of the spacebar, but no. I tried to determine the value of this key 2 ways: one - by hitting it in the System->Preferences->Keyboard Shortcuts box and I found out it was recognized as 'ISO Level3 Shift'. I then tried using **xbindkeys -mk**, and this is the information I got from using the keystroke:

```
"NoCommand"
    m:0x80 + c:108
    Mod5 + ISO_Level3_Shift
```

So the system recognizes the key, but what I would want it to do would be to consider it as another Alt key. Is there any way I can tell my computer to recognize the 'ISO Level3 Shift' key as the Alt_R key? Or maybe get it to map the 'ISO Level3 Shift' key to the normal Alt key? (Alt_L)? I hope this makes sense. 

If this is in the wrong forum category, my apologies. TIA.
-scheibo

---

### Post by SteveDee on 2009-02-03
Take a look at System > Preferences > Keyboard > Layouts > Other Options > Third Level Choosers.

And if you discover anything interesting along the way about <ctrl> separation, it could be useful to the guys at this thread: [http://ubuntuforums.org/showthread.php?t=1056668](http://ubuntuforums.org/showthread.php?t=1056668)

---

### Post by scheibo on 2009-02-03
I figured out the answer to the first of my questions. I've determined that gconf-editor must run things the same way the Run dialog box does (typically Alt-F2 will pop up the run dialog). However, unlike the Run dialog box, the gconf-editor does not have a 'Run in terminal' option. The way around this... merely launch an instance of gnome-terminal followed by the -e option, and then whatever the command you would execute at the command line is. Therefore, editing this:

```
gnome-terminal -e "emacs -nw"
```

works perfectly. Possibly kluge, but still - it's possible for gconf-editor to launch CLI programs this way!

As for the mapping of the keys, I found this: [http://www.faqs.org/docs/Linux-HOWTO/Keyboard-and-Console-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/Keyboard-and-Console-HOWTO.html) site which looks interesting, but it doesn't make it very clear to me how i should go about changing my ISO_Level3_Shift into a Alt_R. Or even an Alt_L for that matter! Worth looking at though, I'm still trying to figure it out.

---

### Post by Sickafant on 2009-10-09
Try binding it with xmodmap

```
xmodmap -e "keycode **108** = Alt_R"
```

Where **108** is the keycode of the key. You can find the keycode by using xev in the terminal and pressing the right Alt key.

Not sure if it will stay bound, but you can always add the command to the end of your xinit or autostart or whatever.

---

### Post by raequin on 2010-04-19
I had the same problem with the right Alt key, and followed the lead above.

System -> Preferences -> Keyboard -> Layouts -> Layout Options -> Key to choose 3rd level

then select "Right Alt key never chooses 3rd level."

---

