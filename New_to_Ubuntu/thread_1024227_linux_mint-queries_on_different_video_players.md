---
title: "linux mint-queries on different video players"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by irish66 on 2008-12-28
Hi girls, some questions on video players.
Kaffeine. Does anyone know how to increase the font size of subtitle text.
Mpplayer. i get the following error message when trying to play videos
error opening/initialazing the selected video_out (-vo) device

---

### Post by blueridgedog on 2008-12-29
No help on your direct questions, but I use VLC with success and satisfaction.

---

### Post by irish66 on 2008-12-30
ok, thanks anyhow. I have VLc too

---

### Post by tjwoosta on 2008-12-30
you can change mplayers video output in the config file

there is an example config file in /etc/mplayer/example.conf


when you see this
> 
# Specify default video driver (see -vo help for a list).
#vo=xv



you can uncomment the line that says vo=xv so it looks like this

> 
# Specify default video driver (see -vo help for a list).
vo=xv


also you can change the value from xv to something else

open a seperate terminal and type 
```
mplayer -vo help
```
(this will give you a list of available video outputs)

so for instance i have set mine to use X11 video output

here is what my config looks like

> # Specify default video driver (see -vo help for a list).
vo=x11


---

