---
title: "Right ALT key on keyboard(s) don't work"
date: 2010-06-10
forum: New to Ubuntu
---

### Post by itsols on 2010-06-10
Hi,

I'm a left-hander. Thus I need to often use the shift/Alt/Ctrl keys on the right.

Problem: All's fine but my right ALT key does not work.

BTW, this is my laptop - Dell Inspiron 1150. I use an A4Tech KBS-720 external keyboard for most of my long-hour work. Strangely, the problem persists on every keyboard, including the standard built-in one.

Note: This has been the case from the beginning of my early installations on this laptop. But if I boot into Windows (which I don't do even twice a month now), all's fine.

And there's something else... while typing in caps, sometimes I tend to hold down the SHIFT and hit the space bar. When I do this, the space bar does not work. It can be quite irritating to make sure I release the Shift and hit space.

Back in the early 90s, I recall we had this shift+space issue in DOS when working with Turbo C.

Any ideas please... :)

---

### Post by flanagan on 2010-06-11
Have you tried this? [http://ubuntuforums.org/showthread.php?t=1277966]("http://ubuntuforums.org/showthread.php?t=1277966")

---

### Post by itsols on 2010-06-11
Hey flanagan,

Thank you VERY MUCH! My right ALT key works! Actually, the link you gave me was related in a way. I took System > Preferences > keyboard > Layouts > Options > Key(s) to change Layout. Then I changed it from "both alt keys" to "left alt + left shift".

Now that is resolved. But I still have the issue with the space bar not working when I press it with the Shift. It kind of slows me down when I have to first release the shift and hit the space bar.

Thank you anyway! That was a great help :)

---

### Post by lyonya20011 on 2010-07-21
This doesn't work for me. My /etc/default/console-setup looks like this (bottom part of the file):
```
XKBMODEL="pc105"
XKBLAYOUT="us"
XKBVARIANT=""
XKBOPTIONS=""
```Please help, I have Ubuntu Lucid 32 bit.

---

### Post by simosx on 2010-07-21
These types of issues come up quite often.

Here is the gist.
1. It's important to try to fix these issues through the GUI and avoid adding/making changes to the 'xorg.conf' file. If you have to change xorg.conf, it's a quick and dirty workaround that does not help Ubuntu users. Things tend to change and in the next release the workaround will probably not work.
2. The right-Alt key is the default key for keyboard layouts for keyboard layouts that support extended characters. For example, in my keyboard layout (GB English), I press RightAlt + 1 and I get ¹.
3. If you want to use RightAlt as a typical Alt key to open menus, etc, you need to make a decision:
  a. Do you want switch keys so that RightAlt is a typical Alt key (open menus, etc) and LeftAlt is the key to type extended characters such as ¹²³?
  b. Do you want to have both Alt keys to open menus?

For [a]: Use the Keyboard Preferences to set the 'Third level key (to type ¹²³)' to LeftAlt. Then, RightAlt should be free and it should open menus. If RightAlt does not open menus, then we got a bug and we treat it like a bug (file bug report on launchpad.net etc).

For [b]: Two options, either select a keyboard layout does not support extended character typing (such as the default US English) and keep just one layout in the list. Or change the Third Level key to some obscure key such as Win or something you do not need.

4. You mention that Shift+Backspace does not work for you. For any such query, you need to show your layout settings, with

gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

In addition, check at Language Support that IBus is not selected in the Input Methods list. I think Shift+Backspace is the shortcut to switch layouts in IBus.

---

### Post by itsols on 2010-07-21
Since it came up, my ALT key now works, but I DO have a problem hitting the SPACE bar with SHIFT held down. When I do this, the cursor does not move.

At first, I thought this to be an issue with my laptop's keyboard but even the ones plugged in via PS/2 or USB also have the same issue. Strangely though, it works fine on WINE-based apps. Eg: notepad.

And if it means anything, here's the output of the command 
     gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

>  layouts = [us,ara	qwerty_digits]
 options = [eurosign	eurosign:5,grp	grp:lctrl_lshift_toggle]
 model = 


NOTE: I really appreciate having this command but what I really wonder is how to get at them? Is there a standard manual that outlines these commands?

Many thanks!

---

### Post by simosx on 2010-07-21
The gconftool command reads the configuration of the Keyboard Preferences. You can get the same information if you open 'gconf-editor' and navigate to the same location in the gconf settings, at /desktop/gnome/peripherals/keyboard/kbd

These values are the standard X.Org configuration values for keyboard layouts. If you google for 'XKB', you will get several resources. In pre-GNOME times, you would need to use the 'setxkbmap' tool to enable the layout settings. If you google on setxkbmap, you can find how to convert the above info into a setxkbmap. If you take the part 'layouts = [us, ...]' only, in setxkbmap it would look like

setxkbmap us,ara -variant ",qwerty_digits"

(the , in  ",qwerty_digits" means that qwerty_digits goes to 'ara' while 'us' has the default settings).

If Shift+Space works in Wine, then something is blocking for the rest of the system. Did you check this thing about IBus as mentioned above?

You can also google for 'xev' to find how to debug non-responding keys in Linux.

---

