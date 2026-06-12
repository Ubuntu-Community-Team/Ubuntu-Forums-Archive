---
title: "[REQUEST] Modified Radiance Theme for Ubuntu"
date: 2010-09-22
forum: New to Ubuntu
---

### Post by dkjMusic on 2010-09-22
I find it difficult to hit the edges of the Ubuntu 10 Radiance-theme windows to resize them.

Is someone willing modify the Metacity theme to put thicker borders on the sides and bottom?

---

### Post by lkjoel on 2010-09-23
You can also try different themes.
Many have thicker borders.

---

### Post by bradleypariah on 2010-09-23
> **dkjMusic said:**
> I find it difficult to hit the edges of the Ubuntu 10 Radiance-theme windows to resize them.

[SIZE="5"]Right??!![/SIZE]

Sorry, I know my comment doesn't help.  Sorry.  I'm just enthusiastically agreeing. :P

---

### Post by lkjoel on 2010-09-23
> **bradleypariah said:**
> [SIZE="5"]Right??!![/SIZE]

Sorry, I know my comment doesn't help.  Sorry.  I'm just enthusiastically agreeing. :P
:lolflag:

---

### Post by dkjMusic on 2010-09-24
> **lkjoel said:**
> You can also try different themes.
Many have thicker borders.

Good point...but I really like the Radiance theme.

Maybe I can look at some of the thicker-border themes' innards and get some clues how to modify the Radiance theme.

Thanks.

---

### Post by dkjMusic on 2010-09-24
> **bradleypariah said:**
> [SIZE="5"]Right??!![/SIZE]

Sorry, I know my comment doesn't help.  Sorry.  I'm just enthusiastically agreeing. :P

Now that's where you're wrong. :)

To know that someone else has the same viewpoint encourages me to find a solution.

---

### Post by coffeecat on 2010-09-24
> **dkjMusic said:**
> I find it difficult to hit the edges of the Ubuntu 10 Radiance-theme windows to resize them.

Is someone willing modify the Metacity theme to put thicker borders on the sides and bottom?

There's a subforum for 10.10 until it goes final, and a relevant thread in there already. You might find it useful and/or interesting:

[http://ubuntuforums.org/showthread.php?t=1580260](http://ubuntuforums.org/showthread.php?t=1580260)

---

### Post by Vaphell on 2010-09-24
agreed, razor thin borders on the sides are a pain and this is a serious usability issue. I never bother with side borders and hit straight to the corner - thanks to a thicker bottom and a rather big active corner area you can resize horizontally with much less hassle than if you try to pinpoint non-existing side borders.

---

### Post by dkjMusic on 2010-09-25
> **coffeecat said:**
> There's a subforum for 10.10 until it goes final, and a relevant thread in there already. You might find it useful and/or interesting:

[http://ubuntuforums.org/showthread.php?t=1580260](http://ubuntuforums.org/showthread.php?t=1580260)

Thanks coffecat. I'll start following that thread.

---

### Post by ddonohu2 on 2010-09-25
To edit the border thickness of themes I do the following; open the terminal, go to the theme's directory (in this case I typed "cd /usr/share/themes/Radiance/metacity-1"), open the themes metacity file (sudo gedit metacity-theme-1.xml), edit left and right width values in the "General window layout" section from this:[INDENT]<!-- General window layout -->
<frame_geometry name="frame_geometry_normal" title_scale="medium" rounded_top_left="true" rounded_top_right="true"  rounded_bottom_left="true" rounded_bottom_right="true">
     <distance name="left_width" value="**1**"/>
    <distance name="right_width" value="**1**"/>

[/INDENT]to this:
[INDENT]<!-- General window layout -->
<frame_geometry name="frame_geometry_normal" title_scale="medium" rounded_top_left="true" rounded_top_right="true"  rounded_bottom_left="true" rounded_bottom_right="true">
     <distance name="left_width" value="**5**"/>
    <distance name="right_width" value="**5**"/>

[/INDENT]and save and exit gedit.

Hope this helps.

---

### Post by dkjMusic on 2010-09-26
> **ddonohu2 said:**
> To edit the border thickness of themes I do the following; open the terminal, go to the theme's directory (in this case I typed "cd /usr/share/themes/Radiance/metacity-1"), open the themes metacity file (sudo gedit metacity-theme-1.xml), edit left and right width values in the "General window layout" section from this:[INDENT]<!-- General window layout -->
<frame_geometry name="frame_geometry_normal" title_scale="medium" rounded_top_left="true" rounded_top_right="true"  rounded_bottom_left="true" rounded_bottom_right="true">
     <distance name="left_width" value="**1**"/>
    <distance name="right_width" value="**1**"/>

[/INDENT]to this:
[INDENT]<!-- General window layout -->
<frame_geometry name="frame_geometry_normal" title_scale="medium" rounded_top_left="true" rounded_top_right="true"  rounded_bottom_left="true" rounded_bottom_right="true">
     <distance name="left_width" value="**5**"/>
    <distance name="right_width" value="**5**"/>

[/INDENT]and save and exit gedit.

Hope this helps.

Thanks ddonohu2 for pointing me to the right place. I changed the widths to 10 just for grins. The side borders are indeed wider, but they show a gradient in color from top to bottom. To fix that I think I'll check out the Agate-theme XML to see how to use png images for borders.

At any rate, this is a heck of a lot easier than editing Msstyles files.:)

---

### Post by ddonohu2 on 2010-09-26
lol, I after I read this I changed mine to ten to see what it was like. I noticed earlier that the borders became an unpleasant grey colour when widened so I changed the "metacity-theme-1" Window frames and bottom border sections to look like this.

[INDENT]<!-- Window Frames -->

<draw_ops name="draw_frame">
    <rectangle color="#e0d6ba" x="0" y="0" width="width" height="height" filled="true"/>
</draw_ops>

<!--bottom border-->
<draw_ops name="bottom_edge">
<rectangle color="#e0d6ba" x="0" y="0" width="width" height="height" filled="true"/>
</draw_ops>

[/INDENT]The border this creates isn't a great looking alternative but I've hit the limit of my theme editing know-how, hopefully you'll have more luck using .png files.

---

