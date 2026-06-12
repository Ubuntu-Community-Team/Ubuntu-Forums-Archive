---
title: "911    /etc/grub.d/ file damaged"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by Brandon_oma#692 on 2010-02-06
Im messed up [COLOR=#8b0000]00_header[/COLOR] when i start ubuntu i get a command screen with sh grub 
 
i think i changed
 
set default=0
set timeout=5
set root=(hd0,5)
search --fs-uuid --set b02e1934-12dd-418a
if font /usr/share/grub/ascii.pff ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  terminal gfxterm
 
to
 
set default=1
set timeout=60
set root=(hd0,5)
search --fs-uuid --set b02e1934-12dd-418a
if font /usr/share/grub/ascii.pff ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  terminal gfxterm
 
 
can i fix this
thanks

---

