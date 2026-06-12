---
title: "Change my Trsh icon?"
date: 2009-09-12
forum: New to Ubuntu
---

### Post by R3fr4cti0n on 2009-09-12
i installed ubuntu studio, on top of jaunty, i downloaded a png icon i would like to use but i can not figure out how to replace my current icon on my panel.
thanks!

---

### Post by NoaHall on 2009-09-12
Right click -> Click the blank image on the left -> find and select file.

---

### Post by dumblebee100 on 2009-09-12
you need to edit some system files ..

I will tell you how ..but its tricky unless you understand what ru doing 

well goto your icons folder ..
generally they will be under 
/usr/share/icons 
or
~/.icons

then search for your icon theme ....I think you are using ubuntu studio theme ..so icons are also the same theme 

so goto that folder and then preview the icons under apps ( suppose you got a png for firefox you need to check in apps and even network manager or bluetooth ) since you want to change icons in panel ..you dont need to look in more places other than apps folder ...you may also need to check status folder

so check all the sizes and see which icon size is getting displayed in your panel right now 

if you didnt change anything from default setup of gnome-panel ..then its size would be 24 I think so ...so you need to check for apps icons in 16 and 22 sizes ...if you found out which icon is getting displayed then backup that icons( like icon_name.png.bak)  and then replace your downloaded png with the original ones ..keep in mind that you have to give the same name ...as original to display correctly 
if your icon theme has .svg files then try to download .svg icon to replace ..otherwise png icons doesnt scale like svg and may look ugly at other sizes

---

### Post by R3fr4cti0n on 2009-09-12
well i found the trash icon in /usr/share/icons/ubuntu studio/scalable/satus, however there are 7 of them, so what ones do i replace with the new icons?

/usr/share/icons/UbuntuStudio/scalable/status/stock_trash_full.svg
/usr/share/icons/UbuntuStudio/scalable/status/trashcan_full.svg
/usr/share/icons/UbuntuStudio/scalable/status/user-trash-full.svg
/usr/share/icons/UbuntuStudio/scalable/status/xfce-trash_full.svg/
usr/share/icons/UbuntuStudio/scalable/status/gnome-stock-trash-full.svg
/usr/share/icons/UbuntuStudio/scalable/status/gnome-fs-trash-full.svg
/usr/share/icons/UbuntuStudio/scalable/status/edittrash.svg

---

### Post by R3fr4cti0n on 2009-09-12
bump

---

### Post by R3fr4cti0n on 2009-09-12
bump

---

### Post by dumblebee100 on 2009-09-15
> **R3fr4cti0n said:**
> bump

what's bump?

---

### Post by dumblebee100 on 2009-09-15
after reading your post ..I tried to redo my gnome panel ..
I was successful to some extent ..
I mean I could change the icons for some notification apps but for some applets I couldnt do it ..

well this is my screenshot

---

### Post by the.dark.lord on 2009-09-15
> **dumblebee100 said:**
> what's bump?

Abbreviation for "bring up my post". Used to get the thread up the list, to enhance visibility.

---

### Post by dumblebee100 on 2009-09-15
> **R3fr4cti0n said:**
> well i found the trash icon in /usr/share/icons/ubuntu studio/scalable/satus, however there are 7 of them, so what ones do i replace with the new icons?

/usr/share/icons/UbuntuStudio/scalable/status/stock_trash_full.svg
/usr/share/icons/UbuntuStudio/scalable/status/trashcan_full.svg
/usr/share/icons/UbuntuStudio/scalable/status/user-trash-full.svg
/usr/share/icons/UbuntuStudio/scalable/status/xfce-trash_full.svg/
usr/share/icons/UbuntuStudio/scalable/status/gnome-stock-trash-full.svg
/usr/share/icons/UbuntuStudio/scalable/status/gnome-fs-trash-full.svg
/usr/share/icons/UbuntuStudio/scalable/status/edittrash.svg

give me some other details 
please goto the icon theme location and post the details of 
```
ls -l *trash*.svg
```

if u can do it by yourself then note this point 

the files which does have sym links should be left and the file which doesnt have sym links should be replaced 

because all other icons which are sym linked will get the image from the source image ..in our view its file which dont have any sym link ...

in my status folder I found two files which dont have symlinks

so replacing both of them would change icons for ubuntu studio theme ..for scalable size 

user-trash.svg
user-trash-full.svg

remaining all other images regarding trash are symlinks to these images 

so replacing these two will work for u .

I will tell u easy method ..in nautilus enable previews and then goto the icon theme folder 

then goto status and see icons related to trash and note down icons which dont have shortcut symbol on the right top 
replace them with ur preferred icons ..and ur done ..

keep in mind ...if ur replacing svg then replace it with a svg ....I dont know why ..Im working on it

---

### Post by durand on 2009-09-15
I would suggest that you copy the UbuntuStudio icon theme to home/.icons and then edit the icons there. If you use nautilus, you can easily preview the icons and know which ones to replace.

If your icon is a png, you will need to use an svg as a replacement. So, install [inkscape]("apt://inkscape"), move your icon to a permanent location. Open inkscape. Then drag and drop it into inkscape. Use the align tools to align it properly. If you go to document properties, you can set the size of the document as well to make sure it's a good replacement for the svg. Then save it as an svg and replace it with the other svg.

My trash icons look like this:
> 
lrwxrwxrwx 1 root root     19 Jul 18 02:03 edittrash.svg -> user-trash-full.svg
lrwxrwxrwx 1 root root     19 Jul 18 02:03 gnome-fs-trash-full.svg -> user-trash-full.svg
lrwxrwxrwx 1 root root     19 Jul 18 02:03 gnome-stock-trash-full.svg -> user-trash-full.svg
lrwxrwxrwx 1 root root     19 Jul 18 02:03 stock_trash_full.svg -> user-trash-full.svg
lrwxrwxrwx 1 root root     19 Jul 18 02:03 trashcan_full.svg -> user-trash-full.svg
-rw-r--r-- 1 root root  36473 Jul 18 02:03 user-trash-full.svg
lrwxrwxrwx 1 root root     19 Jul 18 02:03 xfce-trash_full.svg -> user-trash-full.svg

Yours will be different but similar. You can see that user-trash-full.svg is the actual file and the others are just symlinks (clones) of it. So just replace that one with your new svg and it should change them all.

BTW, I'm assuming that you know about icon themes? They allow you to change all the icons at once. Look at gnome-look.org for more.

If you need more help, just ask. I'm not sure how much you know about this sort of stuff.

---

