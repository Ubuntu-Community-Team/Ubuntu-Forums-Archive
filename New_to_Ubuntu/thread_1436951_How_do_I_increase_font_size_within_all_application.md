---
title: "How do I increase font size within all applications?"
date: 2010-03-23
forum: New to Ubuntu
---

### Post by Chuck_N on 2010-03-23
[SIZE=4]  I found System/Preferences/Appearance/Fonts and increased the size there. That works well, but only on desktop and system menus.
  Now I would like to increase fontsize like in Yahoo mail, where I spend much time. I don't seem to find it in the application itself and would prefer a system override to control all applications
  Thanks.[/SIZE]

---

### Post by mikewhatever on 2010-03-23
[SIZE="4"]In Firefox, Edit->Preferences->Content.

Also set the minimum size under Advanced.[/SIZE]

---

### Post by Mykk on 2010-03-23
You could also try holding down ctrl and using the middle mouse scroll button (assuming it has one) to change the size of certain things. Works in the web browser i know that much ;)

---

### Post by philinux on 2010-03-23
> **Chuck_N said:**
> [SIZE=4]  I found System/Preferences/Appearance/Fonts and increased the size there. That works well, but only on desktop and system menus.
  Now I would like to increase fontsize like in Yahoo mail, where I spend much time. I don't seem to find it in the application itself and would prefer a system override to control all applications
  Thanks.[/SIZE]

In firefox.

View>Zoom>zoom in

or ctrl +

---

### Post by Chuck_N on 2010-03-23
oh thanks, that helps my eyes muchly.   :D

---

### Post by ENigma885 on 2010-03-23
Firefox keeps ur zoom preferences for each site u visit. So that u don't have to change the font size every time u visit the same web page. Which is pretty useful indeed and time saving.

*[COLOR="Red"]**To keep that behaviour unaltered[/COLOR] after cleaning the cache:*
- Make sure that *Site Preferences* in *Clear Recent History * is [COLOR="Red"]un[/COLOR]checked. (*Tools>Clear Recent History*) as in the attached image.
[[IMG]http://img440.imageshack.us/img440/8955/recenthistory.png[/IMG]](http://img440.imageshack.us/i/recenthistory.png/)

---

### Post by Chuck_N on 2010-03-23
hmmmm.....   ctrl-mousewheel  generates a few concentric circles, but I can't see that it does anything else.

---

### Post by Chuck_N on 2010-03-23
[QUOTE=ENigma885;9014741]Firefox keeps ur zoom preferences for each site u visit. So that u don't have to change the font size every time u visit the same web page. Which is pretty useful indeed and time saving.

thanks. I will keep that in mind.

---

### Post by Chuck_N on 2010-03-23
ah, love that  view/zoom/zoom in.   I can now read without straining my eyes.  I just got a new 20" LCD and loved all that was on the screen, but everything was too small to read.  Now I'm fixed up. Thanks.

---

### Post by ENigma885 on 2010-03-23
> **Chuck_N said:**
> hmmmm.....   ctrl-mousewheel  generates a few concentric circles, but I can't see that it does anything else.

mm..weird those circles. No worries though.
__________________

[SIZE="3"]***To sum up the whole thing[/SIZE]
to control the page zoom u have many options and all do the same thing (as mentioned in previous posts):-
**1-** U can go to (*View>> Zoom>> Zoom in*) [or out if u changed ur mind :D]
**2-** Press Ctrl + ( + ) (that's ctrl and the plus sign in ur keyboard)
**3-** Press Ctrl and move ur mouse wheel (but make sure that Firefox window is active ie in front)

- Also, If u want to restore the original zoom settings, press Ctrl + (zero) or from the *zoom menu* choose reset.
_________________________

***Just an additional note,*** try pressing *Super button* (that's the keyboard button with Windows Logo) and move ur mouse wheel back and forth. It will zoom all the displayed screen in/out.

---

### Post by dullard on 2010-03-23
> **Chuck_N said:**
> hmmmm.....   ctrl-mousewheel  generates a few concentric circles, 

You can disable that if you wish. System>Preferences>Mouse
In the "General" tab, uncheck the Locate Pointer checkbox.

---

### Post by sinkyboy2000 on 2010-03-24
I have the same problem.  The menus in programs like ktorrent and VLC are tiny.  I can hardly read them.  Is there any way to make this text bigger (I'm using XFCE).

---

### Post by sinkyboy2000 on 2010-03-24
Nobody?
 
This is a really annoying problem and I've got nowhere serching the forums or google.

---

### Post by The Cog on 2010-03-24
I found that the best way was to go into the font setup, go advanced, and change the dpi (dots per inch) setting that gnome thinks you have. If you increase the dpi by say 10%, the desktop makes every font larger (use 10% more pixels high and wide) to try and keep the font the same size. This seems to affect even programs where you don't seem to have any other way of changing the font size, such as the menus in firefox. Firefox needs restarting before it starts using the new dpi which makes testing a little slow, but it's worth the effort.

While I'm at it, I like to set the antialias hinting to "slight", which has the effect of thickening the characters up a bit. Otherwise I think they tend to look rather spindly.

---

