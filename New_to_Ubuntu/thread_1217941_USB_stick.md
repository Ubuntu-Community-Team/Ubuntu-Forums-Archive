---
title: "USB stick"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by Drenriza on 2009-07-20
I have an strange 4gb usb stick. When you open it, it only shows 984mb. It has been tryed in windows to reformat it without luck.

Is their anyone who can tell me how to clean it and put FAT32 on it again.

---

### Post by nothingspecial on 2009-07-20
```
sudo apt-get install gparted
```

Then system > administration > partition editor

unmount the usb stick. I think it`s right click.

Remove any partitions on there then make a new one that fills the whole stick.

I`d unplug any other usb drives you have before you do this. Accidents can happen.

---

### Post by allenbradley on 2009-07-20
Plug your drive in. Now type :```
sudo fdisk -l
``` and post the output.

*Damn*

---

### Post by aloshbennett on 2009-07-20
Check for hidden files. (Using CTRL + H in Nautillus or ls -a if you are at command prompt)

---

### Post by Drenriza on 2009-07-20
Thanks for the reply guys, but after a search on google.dk/com or w/e. Then i found a post where gparted was recormended. And it worked like a charm 10secs and done:)

As reply #1 recomendended

---

### Post by CaptainMark on 2009-07-20
My usb doesnt work after it went through the washing machine, damn they dont make em like they used to.

---

