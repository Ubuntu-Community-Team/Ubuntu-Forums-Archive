---
title: "Burning DVD straight over network"
date: 2006-12-20
forum: Networking &amp; Wireless
---

### Post by grogling on 2006-12-20
Is there any way of allowing DVD burning software to see the SMB shares that have been created on the desktop, so they can burn stuff straight from a network drive without having to copy the files locally first.

Regards

Glen Greig

---

### Post by Stupid kid on 2006-12-20
you can make it through pipe

for example if you want to burning an iso file form [http://xxxx/xxx.iso](http://xxxx/xxx.iso)
or [ftp://xxxx/xxx.iso](ftp://xxxx/xxx.iso) ,

#for cd
curl [http://xxxx/xxx.iso](http://xxxx/xxx.iso) | cdrecord -v speed=0 dev=0,0,0 fs=8m -data-

#dvd
curl [http://xxxx/xxx.iso](http://xxxx/xxx.iso) | growisofs -z /dev/hdd=/dev/stdin

[color]
i can't explain them ,but it practises right
[/code]

---

