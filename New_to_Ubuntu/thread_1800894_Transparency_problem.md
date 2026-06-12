---
title: "Transparency problem"
date: 2011-07-09
forum: New to Ubuntu
---

### Post by matuskap on 2011-07-09
Hi,
just now i have upgraded from 10.04 to 10.10 and I have problems dealing with transparency... i was using compiz before and now it seems upgrade didnt do much good. When i switch to metacity most problems disappear but still i have one thats really annoying. My "system monitor" got partially transparent somehow just like my terminal window and i cant seem to bring them back to normal. 

System monitor screen: 
[IMG]http://img193.imageshack.us/img193/3028/screenshot3za.png[/IMG]
[IMG]http://img64.imageshack.us/img64/4439/screenshot4jq.png[/IMG]

Beside the fact that its freaking ugly i also cant see a **** on white background. Its super annoying and obviously related to compiz somehow. Rest of windows are just like before upgrade, no problems there. Does anyone know how to turn it off? Also how to set image background in terminal without it being transparent. Because if i set Edit->profile preferences->Background->shadeblablabla...  to maximum, image disappears and background gets system default color. If its set low u cant see anything. I just want image without any freaking shading... 

Can someone pls help me with these "beauty" problems? Thx in advice.

---

### Post by LowSky on 2011-07-09
Easiest way is to delete these folders:
```
~/.gconf/apps/compiz
~/.compiz
```

then compiz can be restarted with its original settings.

---

### Post by matuskap on 2011-07-10
Well theres a button in Compiz settings manager that does the same just by clicking it, but i was hoping it wont come to that... Ive set too many default shortcuts and animations to remeber them all. Well i guess ill have to reset :( after all.

---

### Post by matuskap on 2011-07-10
Settings were reseted but the problem remains the same. :( Transparency in terminal and system monitor didnt change a bit. Any suggestions anyone pls?

---

### Post by wep940 on 2011-07-10
Try this:

Open a terminal window.  In an empty space in that window, right-click your mouse.  Select "Profiles" and then "Profile Preferences".  On the window that opens are a few tabs - click on the background one.  Click the box that says "Use background settings from system theme". OR you may want to uncheck that button and click on the transparent background button and then slide the slider for "Shade transparent or image background" all the way to the right.

Now go to compiz settings manager and uncheck the  opacify button and uncheck the Opacify, Brightness and Saturation button.

---

### Post by wep940 on 2011-07-10
You might also just want to right-click on the desktop, click the background tab, click the visual effects tab and click the top-most button so that no effects are enabled.

---

### Post by mcduck on 2011-07-11
Actually no, that's not something that Compiz controls (although it is related to Compiz in te sense that it uses compositing to allow the transparency).

Anyway, hat kind of transparency comes from your GTK theme. It seems you are using a theme based on Murrine engine, and the theme has transparency option enabled.

...and the solution is fairly simple, either switch to some other GTK theme, or edit the theme you are now using, the option for transparency should be pretty easy to find in the theme's gtkrc file.

Gnome-terminal's background transparency can be controlled in the terminal's preferences.

(Compiz wouldn't be able to do that kind of effect, while it can make things transparent, it only works at the window level, and can't separate window background and contents. So if the transparency was caused by Compiz, everything would be transparent, not just the background)

---

### Post by matuskap on 2011-07-11
About the terminal, all i want is nontransparent picture. If i set theme settings, theres no picture. If i set shading to the right, picture gets lost(really dont know why...):

[IMG]http://img827.imageshack.us/img827/2158/screenshot8go.png[/IMG]

IF i set it to mid, pic is partially visible, but its impossible to read sometimes (blue text from ls output and so on...)

[IMG]http://img707.imageshack.us/img707/2784/screenshot6qw.png[/IMG]


And  the theme, well its really big file and theres no transparency or opacify or any similar word (my mighty search failed). But still i was using this theme for ages on various distributions and even various ubuntu releases and i never had this problem pre-upgrade to Ubuntu 10.10 from 10.04. Thats also why it bothers me so much :(.
But i found a new Warning message: ```
(gedit:13838): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",
```

Any suggestions pls?

---

### Post by mcduck on 2011-07-11
> **matuskap said:**
> About the terminal, all i want is nontransparent picture. If i set theme settings, theres no picture. If i set shading to the right, picture gets lost(really dont know why...):

[IMG]http://img827.imageshack.us/img827/2158/screenshot8go.png[/IMG]

IF i set it to mid, pic is partially visible, but its impossible to read sometimes (blue text from ls output and so on...)

[IMG]http://img707.imageshack.us/img707/2784/screenshot6qw.png[/IMG]


And  the theme, well its really big file and theres no transparency or opacify or any similar word (my mighty search failed). But still i was using this theme for ages on various distributions and even various ubuntu releases and i never had this problem pre-upgrade to Ubuntu 10.10 from 10.04. Thats also why it bothers me so much :(.
But i found a new Warning message: ```
(gedit:13838): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",
```

Any suggestions pls?
Make sure you've turned off the "Use colors from system theme"-option.

Also, if you have the background set to use background image, then the transparency slider actually adjust between the image and the defined background color, while any transparency is defined by the image itself (assuming you are using a .png or .svg image which does have alpha support).

If you don't want transparency in the terminal background pic, try with a picture you are absolutely sure has no transparency.

What comes to the theme not being transparent before, either you had a version of the Murrine GTK engine that didn't support the transparency option, or you weren't running any compositing manager.

The transparency is defined by the theme, but it still needs support from the GTK engine, and some compositing manager (like Compiz, xcompmgr, or the built-in compositing support of Metacity or XFWM) to actally work. The theme is still the one that controls this, which also makes it the place where you'd want to disable it.

(Like I said, Compiz *can't* be responsible from what you are seeing, it wouldn't be able to do that even if one wanted to, the only thing that can do that is the combination of application & GTK engine with transparency support, and instructed to do so by the GTK theme.)

---

### Post by wep940 on 2011-07-11
Also, as I mentioned in my post and you have been expounding on, the terminal prefences are under the profile when you right-click in a terminal window.  There are a couple of things to note, however.  Even with no picture defined, you'll still have the background coming through the image UNLESS you click on the slider button and then move the slide to the right.  The further right, the less opacity.

Also, while not technically compiz, if you right-click on a blank space on your desktop, go to change desktop background, then the visual effects tab, if you click the "none" the terminal will no longer be transparent.

However, if your theme is overriding all of this, you either need to adjust your theme, live with it the way it is, or go with a different theme.  

I don't think you can really do what you are thinking with the background image in your terminal window unless you make that image non-transparent itself, as Mcduck has mentioned.  I have never tried a background image but with visual effects turned off in the desktop properties.

---

### Post by matuskap on 2011-07-11
Slider is slided to the right... its on the image i added to my post. All that does is hide image and show theme color which is grey or white (depending on "Use colors from system theme" from "Color" tab.)Its clearly visible from the snapshots... thats why i added them. Terminal window changes immediately so what u see is a result of setup options u see in preferences window next to it... Its this image and its .jpg. If shader turns between trans and system color then there must be some basic transp. from theme in work even before terminal window itself adjusts the background. Mby its the same that keeps messing with "System monitor". I just cant find out what is is.

[IMG]http://img543.imageshack.us/img543/5716/terminalpic.jpg[/IMG]

I dont know what previous engine did i use but with slider on the side image was fully visible.

If i wanted to chage it in gtkrc. Any suggestions what it might be? Cause i cant seem to find keyword like "trans" or "opa".

P.S.: Changing into different theme is not a solution. Main reason how i persuaded half of my family to reroll from Win to Ubuntu was that u can do freaking anything exactly the way u want it. Sure it can be done the way it was i just dont know how yet.

---

### Post by mcduck on 2011-07-11
Send the theme, or link to where I can find it, and I'll take a look.

---

### Post by mcduck on 2011-07-11
Wait a second. In the first post you said this happens when you switch to Metacity, yet you still seem to have window shadows and compositing.

Check that you haven't got Metacity's compositing support enabled. Press Alt-F2 and run "gconf-editor", browse to apps/metacity/general and make sure "compositing-manager" is disabled.

---

### Post by wep940 on 2011-07-11
Hey mcduck - I hope everything you've been doing is helping the OP.  I wanted to thank you myself because I'm learning things here as well that I didn't have a clue on!
 
So....Thanks!
 
Dave ;)

---

### Post by matuskap on 2011-07-12
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/274461](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/274461) this seems to be a discussion about the same problem i have. Anyway people seem to have different opinions about it being a bug or a feature. 

"gconf-editor" is disabled. While on metacity, its not transparent. As i looked up my first post it seems i have started to write sentence, deleted half and started to write new one. So to clear it out, metacity = ok, compiz = transparent.

---

### Post by matuskap on 2011-07-14
Well its kind of fixed... I switched to another theme since the old one was just too old, im not skilled enough to start debugging its code and still i dont think system wide disabling of transparency is a solution anyway.

---

