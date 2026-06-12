---
title: "Changing panel autohide direction"
date: 2010-05-30
forum: New to Ubuntu
---

### Post by trikster_x on 2010-05-30
I was wondering if anyone knows if it is possible to change the autohide feature on the gnome panel so that instead of the default behavior it behaves like pressing the hide buttons you can enable in properties; i.e. if the panel is on the top edge of the screen it should auto hide to the left or right and unhide on mouse over.

I am using a netbook and having any panels open eats up a lot of screen real estate.  At the same time it is fairly frustrating to have the panel pop up every time I try to minimize , close or otherwise manipulate the titlebar of a window.

Any help with this is greatly appreciated.

---

### Post by orlox on 2010-05-30
I haven't been able to obtain that kind of behavior, and I don't think there's a simple way to get it. The configuration options available by right clicking the panel are very scarce. You can get the full panel option by using gconf-editor (alt+f2 and type "gconf-editor" and run it). If you look into apps/panel/toplevels you will found entries for each of your panels (for instance, I have one named top_panel_screen0, and chances are you will see it also with that name). In there, all the options available can be modified, and they are well described. In there, I couldnt find a way to implement what you mention...

In any case, I found a nice way to keep the panel where it doesnt waste my space (I don't have a neetbok, but I like to optimize my screen space), and I attach a screenshot of it. If you like it, this is how I did it (with gconf-editor):

[LIST]
[*]check auto_hide
[*]uncheck expand
[*]move panel to position you want it in
[/LIST]

Since I use buttons on the left, I left the unexpanded panel on the top right. It uses unused space, and I don't need to hide it!

---

### Post by trikster_x on 2010-05-30
Thanks for the suggestion.  I didn't realize you could actually move an unexpanded panel.  I'll have to do this until I find a way to get exactly the behavior I want.  

If anyone knows how to get the panel to hide the way I am looking for, your knowledge would still be greatly appreciated.

---

### Post by trikster_x on 2010-05-30
Wanted to give this another run today and see if anyone has an idea :)

---

### Post by sdennie on 2010-05-30
The other option is to change the unhide delay of the panel.  It's in the same gconf-editor section that orlox mentioned.  A slightly longer (or much longer) delay in in the unhide_delay property would cause a lot fewer false positives when trying to click window decorations.

---

