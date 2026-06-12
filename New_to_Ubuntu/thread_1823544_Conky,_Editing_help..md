---
title: "Conky, Editing help."
date: 2011-08-12
forum: New to Ubuntu
---

### Post by amiacamal on 2011-08-12
TL;DR --> just read the last bit...


So far i have installed conky, and got it to a stage where i "can" edit it (with a great deal of help from zealibib slaughter) but now im not sure what to do.

first thing, The config file i got from a friend has a transparent background. That'd be great if i wasnt using a wallpaper slideshow, text is unreadable on certain wallpapers. how do i change the transparency level?

Personally i like mine on the right side of the screen, it takes up the entire height of the screen (but only a small amount of width), so if i want to add pieces i need to expand to the left...?


what useful things have people got working with their conky setups? 
Im not looking for peoples actual config files, just ideas and a little help on how exactly to add sections :)

---

### Post by Ozymandias_117 on 2011-08-12
Weather, currently playing, disk usage, CPU usage, network traffic, RAM usage, internal temperatures, top processes for RAM and/or CPU, and a clock are common things in conky setups.

---

### Post by amiacamal on 2011-08-12
I think i have most of that, except the weather, which i dont need really, cos all it ever does in Ireland is rain :P

My friend also had a nice section that monitors ... i dunno, some download website, and displays the 5 newest threads. Its quite nice really

---

### Post by Ozymandias_117 on 2011-08-12
That would be an rss feed most likely

---

### Post by amiacamal on 2011-08-12
Probably... Any ideas  how to add more? Im sure I can find more of those that are useful :)

---

### Post by Frogs Hair on 2011-08-12
These are examples ! Make a backup of the .conkyrc before experimenting .

Change position: The position of the configuration is normally at the top of the.rc . top_right , bottom_right , and so on . Look for the line in the box .
```
alignment top_left
```

Change color: The first thing I would do is add a background by changing the window from , transparent_yes to transparent_no 

```
own_window yes
own_window_colour 000000	# Black
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_transparent yes
own_window_type normal 	## normal

```

This is a list of colors from an .conkyrc. (example)

```
background yes
border_margin 5
border_width 5
color0 555555			#
color1 FCAF3E			# zolty
color2 2a2a2a			# braz
color3 a82553			# rozowy f71f84
color4 5e1014			# bordowy
color5 64574e			# braz
color6 2a2a2a			# szary
color7 8888CC			#  (COOL)
color8 9d9c61			# zolto-szary
color9 525276			# niebiesko-szary

```

This is one way to add color to a block of text , numbers may be used also . 
```
${color slate grey}
```

This indicates the color is the same later in the block of text as in the beginning .
```
${color }
``` 

Look at examples in the Conky thread in the Community Cafe .

---

