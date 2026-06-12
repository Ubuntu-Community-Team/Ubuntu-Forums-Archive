---
title: "9 button mouse, configuring buttons 6 &amp;7"
date: 2011-08-30
forum: New to Ubuntu
---

### Post by krytorii on 2011-08-30
I have a 9 buttoned mouse. Standard left, right, wheel, plus there's an extra two on the side and the wheel tilts left and right.

How do I configure the wheel tilting? The  two on the side (buttons 8 & 9) already go back and forth in firefox and nautilus.

I know there's a lot of threads out there, but they're all confusing and I haven't found one that explains or links me to somewhere where it says how to formulate your own. I know which button is which using xev, and I know you can use the xorg.conf or imwheelrc to change it but nowhere explains what words will produce what effect.

Ideally I'd like the mouse tilt to switch between tabs when in FF.

---

### Post by VCoolio on 2011-08-30
I have a similar issue and I use xbindkeys: install that and add to startup applications. Inside bind the buttons to a script. Use "xbindkeys -k" and hit the mouse button to check what the syntax is for xbindkeys. For example, add in ~/.xbindkeysrc ```
"$HOME/bin/mybuttons 6"
   m:0x0 + b:6
"$HOME/bin/mybuttons 7"
   m:0x0 + b:7
```

And use the script to define what to do when these buttons are clicked in what application. For example, if the active window is firefox, simulate ctrl+tab or shift+ctrl+tab to switch tabs forward and backward. Install xdotool and xvkbd and create ~/bin/mybuttons like this:[php]#!/bin/sh

# check if button 6 was clicked
if [[ $1 == 6 ]]; then
        # check if firefox is the active window
        if [[ $(xdotool getactivewindow getwindowname | awk '{ print $NF }') == "Firefox" ]]; then
                # define to simulate ctrl+tab
                xvkbd -text "\C\t" -window $(xdotool getactivewindow getwindowname)
        # if not firefox, simulate "PageUp"
        else
                xvkbd -text "\[Prior]" -window $(xdotool getactivewindow getwindowname)
        fi
# check if button 7 was clicked
elif [[ $1 == 7 ]]; then
        # check if firefox is the active window
        if [[ $(xdotool getactivewindow getwindowname | awk '{ print $NF }') == "Firefox" ]]; then
                # simulate shift+ctrl+tab to active window
                xvkbd -text "\S\C\t" -window $(xdotool getactivewindow getwindowname)
        # else simulate PageDown
        else
                xvkbd -text "\[Next]" -window $(xdotool getactivewindow getwindowname)
        fi
fi[/php]

Run this in a terminal and switch within 5 secs to firefox to check if "Firefox" is indeed the string to check for:```
sleep 5 && xdotool getactivewindow getwindowname | awk '{ print $NF }' 
```

Adjust to your needs. For example define different behavior for these buttons inside libre-office or inside a terminal or whatever app you use a lot. Don't forget to make ~/bin/mybuttons or whatever filename you use executable: chmod +x /path/to/script.

---

### Post by PaulEdwards on 2012-08-30
Having this in your ~/xbindkeysrc works fine to switch tabs in Firefox & Chromium/Chrome:
```
"/usr/bin/xvkbd -xsendevent -text "\[Control]\[Next]""
  m:0x0 + b:6
"/usr/bin/xvkbd -xsendevent -text "\[Control]\[Prior]""
  m:0x0 + b:7
```


However, this does not work to switch tabs in Nautilus or Gnome-Terminal which is frustrating because the same actual keyboard combinations of Control + PageUp/PageDown DO perform the tab switch actions in those programs...

---

### Post by PaulEdwards on 2012-08-30
> **PaulEdwards said:**
> Having this in your ~/xbindkeysrc works fine to switch tabs in Firefox & Chromium/Chrome:
```
"/usr/bin/xvkbd -xsendevent -text "\[Control]\[Next]""
  m:0x0 + b:6
"/usr/bin/xvkbd -xsendevent -text "\[Control]\[Prior]""
  m:0x0 + b:7
```


However, this does not work to switch tabs in Nautilus or Gnome-Terminal which is frustrating because the same actual keyboard combinations of Control + PageUp/PageDown DO perform the tab switch actions in those programs...

Solved my problem by installing xautomation and modifying my xbindkeysrc as follows:

```
"xte 'keydown Control_L' 'key Page_Down' 'keyup Control_L'"
  m:0x0 + b:6
"xte 'keydown Control_L' 'key Page_Up' 'keyup Control_L'"
  m:0x0 + b:7
```

---

