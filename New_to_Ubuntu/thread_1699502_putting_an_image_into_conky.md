---
title: "putting an image into conky?"
date: 2011-03-03
forum: New to Ubuntu
---

### Post by mick_86 on 2011-03-03
how do i put an image or icon into conky?

tried this but it didn't work:

${image ~/home/michael/DownloadsDrive-Ubuntu-64.png -p 250,0 -s 80x80}

---

### Post by wojox on 2011-03-03
> **mick_86 said:**
> how do i put an image or icon into conky?

tried this but it didn't work:

${image ~/home/michael/DownloadsDrive-Ubuntu-64.png -p 250,0 -s 80x80}

Try:

```
${image /home/michael/DownloadsDrive-Ubuntu-64.png -p 250,0 -s 80x80}
```

I think that tilda ~ was throwing you off.

---

### Post by TeoBigusGeekus on 2011-03-03
> **mick_86 said:**
> ${image ~/home/michael/DownloadsDrive-Ubuntu-64.png -p 250,0 -s 80x80}

There's no folder ~/home/michael etc.
It's either
```
~/Downloads...
```
or
```
/home/michael/Downloads...
```

Try again with
```
${image ~/DownloadsDrive-Ubuntu-64.png -p 250,0 -s 80x80}
```

EDIT: I'm definitely getting old.

---

### Post by mick_86 on 2011-03-03
neither of them worked, is there a chance i need to install something to support images on my conky?

---

### Post by wojox on 2011-03-03
No, what's the name of the image and what directory is it in?

---

### Post by mick_86 on 2011-03-04
> **wojox said:**
> No, what's the name of the image and what directory is it in?

the name of the image is Drive-Ubuntu-64.png
location is /home/michael/Downloads

---

### Post by TeoBigusGeekus on 2011-03-04
```
${image ~/Downloads/Drive-Ubuntu-64.png -p 250,0 -s 80x80}
```
You've forgotten the slash between Downloads and the name of your image.

---

### Post by mick_86 on 2011-03-04
> **TeoBigusGeekus said:**
> ```
${image ~/Downloads/Drive-Ubuntu-64.png -p 250,0 -s 80x80}
```
You've forgotten the slash between Downloads and the name of your image.

that didnt work either. i'll post the whole script if that makes life easier.

```
# Use Xft?
use_xft yes
xftfont Trebuchet MS:size=8
xftalpha 0.8
text_buffer_size 2048

# Update interval in seconds
update_interval 1

override_utf8_locale yes

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
    own_window yes
    own_window_transparent yes
    own_window_type desktop
    own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 180 

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_margin 5

# border width
border_width 1

# Default colors and also border colors
default_color black
own_window_colour black

# Text alignment, other possible values are commented
alignment top_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 35
gap_y 50

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer none

# my colors
color0 White
color1 Ivory
color2 Ivory2
color3 Ivory3
color4 Tan1
color5 Tan2
color6 Gray
color7 AntiqueWhite4
color8 DarkSlateGray
color9 Black

TEXT
${image ~/Downloads/Drive-Ubuntu-64.png -p 250,0 -s 80x80}

${color black}${font :size=14} Ubuntu 10.10 


${color red}${font :size=8} SYSTEM ${hr 2}

${color black}${font :size=8}CPU: ${cpu cpu}% ${alignr}${cpubar 8,60 cpu}
RAM: $memperc% ${alignr}${membar 8,60}
Uptime: ${alignr}${uptime}

${color red}${font :size=8}DATE & TIME ${hr 2}

${color black}${font :size=8}${alignc 35}${font Trebuchet MS:size=26}${time %H:%M}${font}
${alignc}${time %a %d %b %Y}

${color red}${font :size=8}HD ${hr 2}

${color black}${font :size=8}Home:
${fs_free /home}/${fs_size /home} ${alignr}${fs_bar 8,60 /home}

${color red}${font :size=8}${hr 2}

${color black}${font :size=10} "The most overlooked 
advantage of owning a computer 
is that if they foul up there's 
no law against whacking them 
round a bit. "
                  - Eric Porterfield.

```

---

### Post by TeoBigusGeekus on 2011-03-04
Tried it, didn't work either.
Try with a different image.

---

### Post by mick_86 on 2011-03-04
> **TeoBigusGeekus said:**
> Tried it, didn't work either.
Try with a different image.

tried that aswell 5 minutes ago still didn't work. thanks for trying.

---

### Post by TeoBigusGeekus on 2011-03-04
Perhaps using a jpg instead of a png?
Just a thought.

---

### Post by mick_86 on 2011-03-04
> **TeoBigusGeekus said:**
> Perhaps using a jpg instead of a png?
Just a thought.

tried three different ones now, a jpg, a png, and a gif.

none of them worked.

---

### Post by TeoBigusGeekus on 2011-03-04
The thing is, I didn't get any error message when using your conkyrc.

One last shot - try changing the position from -p 250,0 to -p 250,200 (for example).

---

### Post by mick_86 on 2011-03-04
> **TeoBigusGeekus said:**
> The thing is, I didn't get any error message when using your conkyrc.

One last shot - try changing the position from -p 250,0 to -p 250,200 (for example).

tried that aswell, didn't work either.

---

### Post by wojox on 2011-03-04
Works here. Mess around with the positioning settings.

```

# Use Xft?
use_xft yes
xftfont Trebuchet MS:size=8
xftalpha 0.8
text_buffer_size 2048

# Update interval in seconds
update_interval 1

override_utf8_locale yes

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
    own_window yes
    own_window_transparent yes
    own_window_type desktop
    own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 180 

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_margin 5

# border width
border_width 1

# Default colors and also border colors
default_color black
own_window_colour black

# Text alignment, other possible values are commented
alignment top_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 35
gap_y 50

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer none

# my colors
color0 White
color1 Ivory
color2 Ivory2
color3 Ivory3
color4 Tan1
color5 Tan2
color6 Gray
color7 AntiqueWhite4
color8 DarkSlateGray
color9 Black

TEXT
${image /home/wojox/pictures/Drive_Ubuntu.png}

${color black}${font :size=14} Ubuntu 10.10 


${color red}${font :size=8} SYSTEM ${hr 2}

${color black}${font :size=8}CPU: ${cpu cpu}% ${alignr}${cpubar 8,60 cpu}
RAM: $memperc% ${alignr}${membar 8,60}
Uptime: ${alignr}${uptime}

${color red}${font :size=8}DATE & TIME ${hr 2}

${color black}${font :size=8}${alignc 35}${font Trebuchet MS:size=26}${time %H:%M}${font}
${alignc}${time %a %d %b %Y}

${color red}${font :size=8}HD ${hr 2}

${color black}${font :size=8}Home:
${fs_free /home}/${fs_size /home} ${alignr}${fs_bar 8,60 /home}

${color red}${font :size=8}${hr 2}

${color black}${font :size=10} "The most overlooked 
advantage of owning a computer 
is that if they foul up there's 
no law against whacking them 
round a bit. "
                  - Eric Porterfield.

```

---

### Post by spillin_dylan on 2011-03-04
I think this should work.  I'm wondering if Conky is having trouble on the tilde (~), and writing out the entire path will do it.  Also, have you made sure that the image file name is exactly correct, including upper- and lower-case letters?  Remember, Linux is "Case Sensitive"

```
${image /home/michael/Downloads/Drive-Ubuntu-64.png -p 250,0 -s 80x80}
```

---

