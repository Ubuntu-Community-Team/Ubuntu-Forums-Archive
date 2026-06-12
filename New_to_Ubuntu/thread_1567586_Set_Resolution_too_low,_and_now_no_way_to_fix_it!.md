---
title: "Set Resolution too low, and now no way to fix it!"
date: 2010-09-04
forum: New to Ubuntu
---

### Post by TygerTung on 2010-09-04
Hi,

I have been trying to get xubuntu going on this computer which I have plugged into an old TV.

However, I was playing around with the resolution in an effort to make the text readable. Unfortunatly I set the resolution to something like 320x200 and there is no way to change it back as the screen area is so small that I can only see one icon on at the top and that is it, and I can see no way of moving the window up any more to get to the resolution one!

Can anyone help!

---

### Post by Brinstar on 2010-09-04
> **TygerTung said:**
> Hi,

I have been trying to get xubuntu going on this computer which I have plugged into an old TV.

However, I was playing around with the resolution in an effort to make the text readable. Unfortunatly I set the resolution to something like 320x200 and there is no way to change it back as the screen area is so small that I can only see one icon on at the top and that is it, and I can see no way of moving the window up any more to get to the resolution one!

Can anyone help!

ctrl-alt-f1 should get you to a terminal from where you can edit the xorg.conf and then do 

```
sudo /etc/init.d/gdm restart
```

---

### Post by Ronok on 2010-09-04
also...

you might try a look at:

1) ctrl-alt-f1
2) enter name and pass
3) type: " **man xrandr** "
4) type: " xrandr " to see a list of available screen resolutions
5) try: " sudo xrandr -s (and some rez X some rez) to change it
6) ctrl-alt-**f7** to get back to the desk top

hope that helps
[Ronok]("http://www.gongkuo.com/index.htm")

---

### Post by candtalan on 2010-09-04
also, you can hold the alt key down and click drag the visible screen around, although the other suggetions here will proably hlp you fix things faster
hth

---

### Post by realzippy on 2010-09-04
Run in terminal:

```
rm ~/.config/monitors.xml
```

..deletes the file that was created when setting resolution.

---

