---
title: "how to package an ubuntu theme"
date: 2011-07-27
forum: New to Ubuntu
---

### Post by cybuntu on 2011-07-27
I've made a very cool theme and want to upload it to the Internet.  thing is, i don't know how to make it that .tar.gz file you get when you download a theme.

in short, how do i package the theme i just made, wallpaper and all?

---

### Post by Frogs Hair on 2011-07-27
From the terminal . tar -pczf name_of_your_archive.tar.gz /path/to/directory .

Gzip should be installed by default , so you can right click the file , select compress from the context menu . Next , enter file name , type , location , and select create .

---

### Post by kaldor on 2011-07-27
[LIST]
[*]Right-click the folder you want to turn into a tar.gz. 
[*]Select Compress
[*]Change .zip to .tar.gz in the menu that comes up
[/LIST]

Edit: like in the above post :)

---

