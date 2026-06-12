---
title: "Tooltip notification Black in color. How to change it?"
date: 2010-12-21
forum: New to Ubuntu
---

### Post by babloo75 on 2010-12-21
I have installed rekonq web browser (after failures of other web browsers e.g. firefox, chrome, seamonkey, Konqueror in ubuntu). But even this browser has a problem. The [COLOR="Blue"]Tooltip notification[/COLOR] pop up is black in color. Is there any way to rectify this fault in rekonq browser.

[Some of you may ask me the failures of other browsers, so I am telling in advance:
[COLOR="Red"]Firefox[/COLOR] is very very slow........ (as if I have a dial up internet connection)
[COLOR="red"]Google chrome[/COLOR] fails to open few web pages.
[COLOR="red"]Seamonkey[/COLOR] cannot be updated to the latest version
[COLOR="red"]Konqueror[/COLOR] has the same problem of black colored tooltip notification]

Can anyone suggest me a remedy for this?
Thanks in advance.

---

### Post by gmargo on 2010-12-21
There's a workaround here:
[http://ubuntuforums.org/showthread.php?t=1580266](http://ubuntuforums.org/showthread.php?t=1580266)

---

### Post by mcduck on 2010-12-21
It's possible to set the tooltip color yourself, ignoring whatever the GTK theme you are using defines. And there's two ways you can do this:

1. Install gnome-color-chooser and use that to set the color.

2. Create a file called *.gtkrc-2.0* in your home directory, add the following lines of text there and log out & back again:
```
style "custom-tooltip"
{
  bg[NORMAL] = "#ffffff"
  fg[NORMAL] = "#000000"
}
widget "gtk-tooltips" style "custom-tooltip"

```
(*bg[NORMAL]* is the background color, *fg[NORMAL]* is the text color. You can of course use whatever colors you like, this code would give you black text on white background.)

I prefer the second method, as it doesn't require installing any extra programs, and there's a lot of cool tweaks that can be done with the *.gtkrc-2.0* -file. :)

Edit:
Sorry, seems I missed the part about you using Reconq. In this case this of course doesn't help, as it's not a GTK program... You should be able to install *qt3-qtconfig* or *qt4-qtconfig* (depending on which one Reconq uses) and then set the theme for Qt applications with it.

---

### Post by babloo75 on 2010-12-22
Thanks a lot..... Now its fine.

---

### Post by t.h.w. on 2013-02-23
> **mcduck said:**
> It's possible to set the tooltip color yourself, ignoring whatever the GTK theme you are using defines. And there's two ways you can do this:

1. Install gnome-color-chooser and use that to set the color.

2. Create a file called *.gtkrc-2.0* in your home directory, add the following lines of text there and log out & back again:
```
style "custom-tooltip"
{
  bg[NORMAL] = "#ffffff"
  fg[NORMAL] = "#000000"
}
widget "gtk-tooltips" style "custom-tooltip"

```
(*bg[NORMAL]* is the background color, *fg[NORMAL]* is the text color. You can of course use whatever colors you like, this code would give you black text on white background.)

I prefer the second method, as it doesn't require installing any extra programs, and there's a lot of cool tweaks that can be done with the *.gtkrc-2.0* -file. :)

Edit:
Sorry, seems I missed the part about you using Reconq. In this case this of course doesn't help, as it's not a GTK program... You should be able to install *qt3-qtconfig* or *qt4-qtconfig* (depending on which one Reconq uses) and then set the theme for Qt applications with it.

Solution '2' did it for me. Thanks! :p (I only had the problem in Firefox...)

---

