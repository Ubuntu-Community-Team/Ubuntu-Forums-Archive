---
title: "modprobe ndiswrapper: operation not permitted"
date: 2005-07-22
forum: Networking &amp; Wireless
---

### Post by OneSeventeen on 2005-07-22
After installing ndiswrapper from source, and running:
ndiswrapper -i myfile.inf
then I run:
ndiswrapper -l

it just sits there doing nothing until I hit control+c

if I try modprobe ndiswrapper then it tells me "Operation not permitted"

any ideas why?  This is on an hp zv6000 laptop, and I've done this exact method on a different laptop (same model number) in the past with no problems.

---

### Post by damonw5 on 2005-07-22
[QUOTE=OneSeventeen]After installing ndiswrapper from source, and running:
ndiswrapper -i myfile.inf
then I run:
ndiswrapper -l

it just sits there doing nothing until I hit control+c

if I try modprobe ndiswrapper then it tells me "Operation not permitted"

any ideas why?  This is on an hp zv6000 laptop, and I've done this exact method on a different laptop (same model number) in the past with no problems.[/QUOTE]
 Silly question, but are you typing "sudo" at the beginning of those commands? Example: "sudo modprobe ndiswrapper"

---

