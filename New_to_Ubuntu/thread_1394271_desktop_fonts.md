---
title: "desktop fonts"
date: 2010-01-30
forum: New to Ubuntu
---

### Post by DarinB on 2010-01-30
i chose a dark wall paper, i decided that a white desktop font would help to see the desktop icon titles. i went to config editor apps> nautillus > preferences> and added #ffffff after font name. is this a good idea or will it bite me on the gnome behind later????

---

### Post by natex on 2010-01-30
Instead I would goto the System menu on the task bar and use the gui tools. So:

System>Preferences>Appearance>Theme tab>Customize button (bottom right)>Colors tab

Then pick a color for your text. Then you can save this as new theme in case you want to play around a bit more with the colors or other customizations. Just my 2 cents :)

nate

---

### Post by DarinB on 2010-01-30
my way did not work i will try that thanks.

---

### Post by DarinB on 2010-01-30
no choice for desktop fonts? hmmm why so difficult to change that color?

---

### Post by mcduck on 2010-01-30
You can change the desktop font color (and other options) by creating a file called ".gtkrc-2.0" in your home directory, and adding ths piece of code there:

```
style "desktop-icon"
{
  NautilusIconContainer::frame_text = 1
  text[NORMAL] = "#ffffff"
  NautilusIconContainer::normal_alpha = 0
  NautilusIconContainer::highlight_alpha = 255
  NautilusIconContainer::dark_info_color = "#444444"
  NautilusIconContainer::light_info_color = "#bbbbbb"
}
widget_class "DesktopIcon" style "desktop-icon"
```

text[NORMAL] sets the text color, dark and light info colors are used for additional info lines (if you have enabled any for your current icon size in Nautilus preferences).

Setting frame_text on enables icon containers, which makes the text shadows disappear. Then setting normal_alpha to 0 hides the container, leaving you with nice shadowless icon texts. If you don't like that then just leave these lines out, set frame_txt to 0 or adjust the container alphas to your taste.

...and you'll have to log out and back again after editing the file to see the changes. :)

---

### Post by DarinB on 2010-01-30
how about the panel clock. i am using jaunty?
i want to use a dark background and the clock has black font. 
one method of going into the .theme doesn't work since i use a custom theme and that custom does not have the .gtkrc... in that folder????

---

### Post by DarinB on 2010-01-30
oh yeah the above is because i use a transparent panel option.

---

### Post by mcduck on 2010-01-31
Just add a bit more code into the same ~/.gtkrc-2.0 -file:

```
style "panel-clock"
{
  fg[NORMAL] = "#ffffff"
}
widget "*.clock-applet-button.*" style "panel-clock"
```

---

### Post by DarinB on 2010-01-31
i am not sure above i created the file in my home folder but nothing changes
i log out and log back in it is the same should it be in the /home or in /home/darin ??? done by root or user?

---

### Post by mcduck on 2010-01-31
the file should be "/home/darin/.gtkrc-2.0" (it will be a hidden file)

..and owned by your normal user since it's the user's settings you are changing.

---

### Post by DarinB on 2010-01-31
it does not seem to work, it does not seem so hard either create a file open with text editor copy paste log out log in...hmmm what am i doing wrong

---

### Post by mcduck on 2010-02-01
> **DarinB said:**
> it does not seem to work, it does not seem so hard either create a file open with text editor copy paste log out log in...hmmm what am i doing wrong

hard to say... Did you remmember the dot in the beginning of the file's name?

---

### Post by DarinB on 2010-02-01
one thing i do use a custom theme called rgs i think that is the main theme i built it from. does that make a difference?
and when i make a file with a .gtkrc-2.0 it comes out like a text file and i have to use text editor to copy the text?

---

### Post by DarinB on 2010-02-01
here are two screen shots this seems so simple why would it not work. i must be doing something really dumb.[ATTACH][ATTACH]145697[/ATTACH][/ATTACH]

---

### Post by mcduck on 2010-02-02
Whaterver themes you use makes no difference, anything defined in that file should override any theme settings. And yes, it's a plain text file

Anyway, the last line should be lke this:```

widget_class "*DesktopIcon*" style "desktop-icon"
```
Sorry about that, it was my typo on the instructions... :-\"

Also, are those really zeroes you have on the text[NORMAL] and the following alpha line?

---

### Post by DarinB on 2010-02-02
HAHA I was really going nuts for a few days i couldn't figure out what i was doing wrong. I was doubting my own abilities to read. thanks it worked perfectly.
I appreciate the patients, i don't know why i thought of doing screen shots i am glad i did. 
can i now change it to any color? and add the clock as well to the same file? 
thank you again it is great!

---

### Post by mcduck on 2010-02-02
> **DarinB said:**
> HAHA I was really going nuts for a few days i couldn't figure out what i was doing wrong. I was doubting my own abilities to read. thanks it worked perfectly.
I appreciate the patients, i don't know why i thought of doing screen shots i am glad i did. 
can i now change it to any color? and add the clock as well to the same file? 
thank you again it is great!

Yeah, use any colors (and transparency levels ) you want to. And yes, you can add the clock stuff and anything else you might want to override in your themes into the same file.

---

### Post by DarinB on 2010-02-02
thank you

---

### Post by DarinB on 2010-02-03
works great with clock as well i tried this for the weather report applet. 
but it didn't work any ideas

style "panel-weather-report"
{
  fg[NORMAL] = "#344D34"
}
widget "*.weather-report-applet-button.*" style "panel-weather-report"

i also tried with out the dash between weather and report

---

### Post by mcduck on 2010-02-03
Try this:
```

style "panel-weather"
{
  fg[NORMAL] = "#344D34"
}
widget "*.gweather-applet-2.*" style "panel-weather"
```

Another option would be something like this (which should set the text color for all panel applets):

```
style "panel-applet"
{
  fg[NORMAL] = "#344D34"
}
widget "*PanelWidget*" style "panel-applet"
widget "*PanelApplet*" style "panel-applet"
```

---

### Post by DarinB on 2010-02-04
cool thanks now i can change them all in one shot...
if i am using the panel-applet

should i remove the clock one since it seems redundant?



this is great even the stuff in my windows list is the same.thanks again

---

### Post by mcduck on 2010-02-05
> **DarinB said:**
> cool thanks now i can change them all in one shot...
if i am using the panel-applet

should i remove the clock one since it seems redundant?



this is great even the stuff in my windows list is the same.thanks again

Well, you can remove it if it's rredundant, or just comment it out (by adding a # in the beginning of every lne), so that you can still enable it again if you need it some day.

(I have a bunch of things in my gtkrc and I just enable/disable them based on what fits my current desktop theme & wallpaper.)

---

### Post by DarinB on 2010-02-05
great idea just rem them out but leave them.
thanks maybe i will put it back in and add the #

---

