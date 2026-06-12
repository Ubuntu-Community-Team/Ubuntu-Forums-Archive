---
title: "conky+imlib2 not working"
date: 2010-10-28
forum: New to Ubuntu
---

### Post by a.sarkar on 2010-10-28
Dear All,
I am trying to insert an image in conky. But it's not showing up properly. Instead of showing the full image, it's just showing a slice of the image. See attached screenshot.
This happens not just with this image, but with any other image too.
 The image dimension is 300x300 and the file size is 20K.

My conkyrc file is
```
 
background no
use_xft yes
xftfont Bitstream Vera Sans Mono:size=9
xftalpha 0.8
mail_spool $MAIL
update_interval 3.0
total_run_times 0
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 180 5
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes
stippled_borders 8
border_width 1

default_color yellow
color0 white
color1 green
color2 red
default_shade_color grey
default_outline_color yellow

alignment top_left
gap_x 150
gap_y 130

no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 2
override_utf8_locale no
use_spacer none
text_buffer_size 1024

TEXT
${image /home/username/.conky/folder.jpg -p 20,20 -s 100x100}

```I am using lucid lynx as my distro with conky-all installed.
The conky --version shows:
```

Conky 1.8.0 compiled Fri Apr 23 10:38:37 UTC 2010 for Linux 2.6.24-27-server (i686)

Compiled in features:

System config file: /etc/conky/conky.conf
Package library path: /usr/lib/conky

 X11:
  * Xdamage extension
  * XDBE (double buffer extension)
  * Xft
  * ARGB visual

 Music detection:
  * MPD
  * MOC

 General:
  * math
  * hddtemp
  * portmon
  * Curl
  * RSS
  * Weather (METAR)
  * Weather (XOAP)
  * wireless
  * support for IBM/Lenovo notebooks
  * nvidia
  * eve-online
  * config-output
  * Imlib2
  * ALSA mixer support
  * apcupsd
  * iostats
  * ncurses
  * Lua

  Lua bindings:
   * Cairo
   * Imlib2

```Any help in this regard would be appreciated. 
Thanks in advance.

---

### Post by a.sarkar on 2010-10-30
Solved it myself :P.

Change 
```
minimum_size 180 5
```to
```
minimum_size 175 100
```and it's working. Come to think of it, it was kind of obvious. :oops:.

Now I have a small conky window which shows my audacious current playing info along with album art. See attached screenshot. 

Yeah conky rocks. 
:guitar:

---

