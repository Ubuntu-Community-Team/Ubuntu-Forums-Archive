---
title: "Lost menu and panel configuration"
date: 2010-06-04
forum: New to Ubuntu
---

### Post by paulera on 2010-06-04
Hi there. I use to do the system updates daily. Yesterday I did some, and also played with the CompizConfig configuration manager ](*,). Result: the top panel, where the title of maximized windows, opened windows buttons, date/time and etc remains is empty!!! And that menu placed in desktop is all unconfigured too: the apps buttons are larger, the category buttons' text (on left) are with a smaller font.

how can i restore them???

I am using the Ubuntu Netbook Remix 10 (upgrade from 9) in a Acer Aspire One ZG5 (7'' screen)

Tks guys!

There is an screenshot (i have added the "show desktop" and "notification area")

[IMG]http://img697.imageshack.us/img697/1372/capturadetela1sq.png[/IMG]

---

### Post by llawwehttam on 2010-06-04
you can use a great built in tool to fix that.

Please copy and paste :

```
[COLOR=#ff0000][COLOR=Black]gconftool --recursive-unset  /apps/panel[/COLOR][/COLOR]
```into a terminal.

Should work for you.

You may have to type 

```
killall gnome-panel
``` afterwards if t doesn't automatically reset, gnome-panel then respawns fixed.

---

### Post by efrens on 2010-09-30
I'd like to confirm this problem. It is my first time installed UNR and accustomed to installing regular desktop ubuntu I installed compiz.

But then at the same session I realized I shouldn't so I removed anything compiz. My problem was that when I rebooted, the top panel isn't showing at all. All I can see is the menu the same way as shown at the screen shot by the first poster at the top.

I did a ps aux | grep gnome-panel and I can see (only) the clock and the network applets are running, though I can't see them.

Disappearing panels happened to me in Ubuntu Desktop before so I tried what I did to solve them then, and that is to follow instructions found here: [http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html)

But although it did show the top panel, the windows aren't behaving as they originally did. They aren't maximizing by default and aren't stacking nicely.

I bet that's because doing rm -rf ~/.gconf/apps/panel as was advised in the tutorial I followed remove the settings that was especially set for UNR.

Now what shall I do to get this thing back to normal UNR behavior?

---

