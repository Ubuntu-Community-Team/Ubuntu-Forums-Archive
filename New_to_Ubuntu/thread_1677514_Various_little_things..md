---
title: "Various little things."
date: 2011-01-28
forum: New to Ubuntu
---

### Post by Gms9810 on 2011-01-28
Hi all,
Although I've been working with computers since the 70s and know Windows better than some folks I AM new with Linux. I recently acquired a completely spare computer that I don't need and I decided to dedicate it completely to Linux So I downloaded Ubuntu 10.10 and set it up on the other computer. 
 I thought I understood some things about Linux that I don't, right now I'm having two problems that I guess I need help with. For the sake of simplicity I'll only address one right now. For the most part I planned to use the Linux computer to just learn new software and "Linux stuff" but I did want some common applications on them. One of those is Gimp. I thought I could just copy the scripts and brushes from my XP computer to the Ubuntu via a CD or USB stick but when I copy them and try to paste them into the ubuntu Gimp the paste option is grayed out. I tried sending some up and back down via FTP and even the graphic files (jpg, png, etc) won't work. 
So after that long narrative I come to the point: Am I missing something basic?
If you read this far, thanks.

---

### Post by sffvba[e0rt on 2011-01-28
Hi,

I suspect you are trying to copy/paste into a folder that is owned by "root" so you won't have privileges to do that... in terminal type "sudo nautilus" and enter your password (note, nothing will appear when entering your password, but when done hit enter), use this to do your copy/paste and see how that works ;)


404

---

### Post by idi0tf0wl on 2011-01-28
It could be you've got some bogus file ownership problems. Try pointing your terminal to the directory where all the stuff you're moving is (do you know what I mean by this?) and type:
```
sudo chown -R YOURUSERNAME *
``` where YOURUSERNAME is, well, your username (everything is caps sensitive).

If that sounds cryptic, do this step by step:

1. Move all the stuff into a folder on your Desktop called "tmp" and type this into a terminal:
```
sudo chown -R YOURUSERNAME ~/Desktop/tmp
```

Then try doing what you're trying to do and report back.

P.S. - I might be totally wrong about this, but hey, you wanted to learn some "Linux stuff" right? Well, welcome to the command line!

---

### Post by sisco311 on 2011-01-28
> **not found said:**
> Hi,

I suspect you are trying to copy/paste into a folder that is owned by "root" so you won't have privileges to do that... in terminal type "sudo nautilus" and enter your password (note, nothing will appear when entering your password, but when done hit enter), use this to do your copy/paste and see how that works ;)


404

For GUI applications one should use gksudo:
```
gksudo nautilus
```

@OP:

Welcome to the forums!

Here are some useful links:
[uhelp]community/RootSudo[/uhelp]
[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)

---

### Post by Guilden_NL on 2011-01-28
[QUOTE=sisco311;10407401]For GUI applications one should use gksudo:
```
gksudo nautilus
```

Yeow, you're fast! You just beat me to it!  

I still use the GUI a lot, 16 yrs on in Linux.  I type enough during the day, when I am on my systems at night, I like to look at what I am doing.  Not only that, I usually have a fried brain by then and don't have to think as much!

---

### Post by sffvba[e0rt on 2011-01-28
> **sisco311 said:**
> For GUI applications one should use gksudo:
```
gksudo nautilus
```@OP:

Welcome to the forums!

Here are some useful links:
[uhelp]community/RootSudo[/uhelp]
[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)

Ah yes... I tend to forget to use gksudo which is the absolute right way to do it... however sudo would also work, even if it is wrong :P


404

---

### Post by sisco311 on 2011-01-28
> **not found said:**
> however sudo would also work, even if it is wrong :P


Yep, most of the time it's fine, some of the time is extremely bad.
[http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

---

### Post by sisco311 on 2011-01-28
Oh, and to answer the OP's question. :)

Most likely you are trying to copy the files to GIMP's system wide config directory **/usr/share/gimp/2.0/**, hence you need root privileges. 

As a regular user, you can copy the files to your personal config directory **~/.gimp-2.6/** (You may have to press Ctrl+H in the file manager to list hidden files). Of course, in this case, other users won't have access to the scripts & brushes.

---

