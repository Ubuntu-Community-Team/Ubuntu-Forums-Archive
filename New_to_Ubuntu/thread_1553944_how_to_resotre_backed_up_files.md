---
title: "how to resotre backed up files"
date: 2010-08-15
forum: New to Ubuntu
---

### Post by fremantle on 2010-08-15
i used the following commands from a tutorial to back up some files
[PHP]sudo cp /usr/lib/compiz/libanimation.so /usr/lib/compiz/libanimation.so.bak 
sudo cp /usr/lib/compiz/libanimation.a /usr/lib/compiz/libanimation.a.bak 
sudo cp /usr/share/compiz/animation.xml /usr/share/compiz/animation.xml.bak[/PHP]then i made some changes to the original files. but the tutorial didnt work so now i want to restore my original files. what should be the command to do that?

---

### Post by Dreigo42 on 2010-08-15
I don't claim to be an expert but the cp (copy) command put a copy of the file and renamed it with .bak added on. This left two copys, the original and the backup. I would simply reverse the order. You did cp file.ext to file.ext.bak so you need to do cp file.ext.bak to file.ext

---

