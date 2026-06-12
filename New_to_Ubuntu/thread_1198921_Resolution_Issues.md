---
title: "Resolution Issues"
date: 2009-06-28
forum: New to Ubuntu
---

### Post by wickedshiv on 2009-06-28
[SIZE=4]Last night I added another monitor to watch a movie on my tv and had to turn the resolution way down. When I turned on my laptop today I couldn't get my resolution any higher than 1024 x 768 and it looks terrible and my login screen is illegible. I surfed the forums and tried to find a solution but couldn't get anything to work. Someone help me. I'm new to Ubuntu so I need step by step instructions here.[/SIZE]

---

### Post by swisstone198 on 2009-06-28
Run

sudo dpkg-reconfigure -phigh xserver-xorg

this should give you the higher resolution options again.

---

### Post by wickedshiv on 2009-06-28
I tried that but it only said stuff about the keyboard and mouse and nothing changed in my resolution options.

---

### Post by uluru13 on 2009-07-20
my problem is quite similar.
my screen resolution is detected and set perfectly by default.

but whenever i d/c my screen my ubuntu will bootup in 800&600 resolution which is very annoying on VNC.

i want my vnc in higher resolution, how do i permenantly define my resolution?

---

