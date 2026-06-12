---
title: "syslinux.cfg"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by Hippytaff on 2010-10-10
Is my syslinux.cfg corrupt? got this when trying to edit it in nano
[quote]

 	[SIZE=2]
[/SIZE]
 	 	 		[SIZE=2] 			 				label ubnentry0
menu label ^Back..
kernel /ubnkern
append initrd=/ubninit

^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@  ^@^@^@^@^@^@^@^@^@^@^@^@^@^@^$[/SIZE] [SIZE=2]
&#65533;^Z,1&#65533;^V&#65533;&#65533;<Dw^F,;r&#65533;&#65533;
<&#65533;r&#65533;<&#65533;w&#65533;,{W&#65533;&#65533;^F^E&#65533;&#54720;=^@t2&#34240;&#65533;^Rt-&#34240;U^W&#34240;&#65533;^T&#46528;^TW&#65533;^@~&#34240;V^W&#65533;68.&#34240;O^W&#65533;      &#65533;&#34240;I^W&#65533;$
fY^f&#65533;\.f-^@&#65533;^@^@v^H1&#1211;&#65533;&#65533;&#65533;&#1659;^Vf&#65533;>d.&#65533;^@0&#65533;&#65533;&#65533;&#1199;&#65533;&#65533;^R&#65533;>l.^@t^C&#65533;9^A&#65533;@  #&#65533;>&#65533;&#65533;^@t     &#65533;^F1&#65533;1&#65533;$

[/SIZE]

---

### Post by cariboo on 2010-10-10
It looks like you are trying to open the wrong file. It's supposed to look like this:

```
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
```

Are you sure you're trying to edit /syslinux/syslinux.cfg?

---

### Post by Hippytaff on 2010-10-10
I'm looking in /media/hp_3457W

it's there as syslinux.cfg...is this the wrong one?

---

