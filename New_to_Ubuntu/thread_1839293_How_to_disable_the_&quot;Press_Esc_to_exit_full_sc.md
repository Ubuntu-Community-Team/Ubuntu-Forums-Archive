---
title: "How to disable the &quot;Press Esc to exit full screen mode&quot; message?"
date: 2011-09-05
forum: New to Ubuntu
---

### Post by susanne260 on 2011-09-05
Is there a way to disable the "Press Esc to exit full screen mode" message when watching flash videos in Ubuntu?

[IMG]http://img269.imageshack.us/img269/5163/pic1pa.jpg[/IMG]

It just gets annoying after a while to see it over and over again. And it pops up right in the middle of the screen, thus blocking the most important area. Anyone who has watched short flash videos in fullscreen would understand.

I tried to google the problem and only found solutions for windows, but can it also be disabled in Ubuntu? =)

---

### Post by Mex5150 on 2011-12-05
Hi

Did anybody ever find a way to fix this? It's so annoying!

-Mex

---

### Post by arzali on 2011-12-06
Just used the patcherfrom here [http://forum.videohelp.com/threads/304807-How-to-remove-annoying-Press-Esc-to-message-in-Flash-Video](http://forum.videohelp.com/threads/304807-How-to-remove-annoying-Press-Esc-to-message-in-Flash-Video) with wine and patched libflashplayer.so and it works :D

---

### Post by Mex5150 on 2011-12-07
> **arzali said:**
> Just used the patcherfrom here [http://forum.videohelp.com/threads/304807-How-to-remove-annoying-Press-Esc-to-message-in-Flash-Video](http://forum.videohelp.com/threads/304807-How-to-remove-annoying-Press-Esc-to-message-in-Flash-Video) with wine and patched libflashplayer.so and it works :DNot here I'm afraid ;^<

---

### Post by arzali on 2011-12-07
> **Mex5150 said:**
> Not here I'm afraid ;^<
What distro/browser and which version of flash are you using?
Im using firefox 11 with flash 11.1 r102 so it should work with older version.
Are you sure you patched the right plugin? (i have 4 versions)
try ```
about:plugins
``` (type that as url)
if you are lucky it will tell you the location of your plugin.

---

### Post by Mex5150 on 2011-12-08
> **arzali said:**
> What distro/browser and which version of flash are you using?
Im using firefox 11 with flash 11.1 r102 so it should work with older version.
try ```
about:plugins
``` (type that as url)
Ubuntu 'Natty' 11.04
FireFox 8.0
Shockwave Flash 11.1 r102
All from the software centre (with the exception of the OS itself, which was off an iso)
> Are you sure you patched the right plugin? (i have 4 versions)No idea at all, I just ran the updater from wine and hoped for the best LOL

-Mex

---

### Post by arzali on 2011-12-08
How i did it:
Run:
```
cp /usr/lib/flashplugin-installer/libflashplayer.so ~/
```open Flash Fullscreen Patcher.exe with wine
choose "Other"
set filetypes to "All Files"
select libflashplayer.so from your home folder
You will get a confirmation that the file is successfully patched
Close the patcher
run
```
sudo cp ~/libflashplayer.so /usr/lib/flashplugin-installer/
```

---

### Post by Mex5150 on 2011-12-08
> **arzali said:**
> How i did it:
Run:
```
cp /usr/lib/flashplugin-installer/libflashplayer.so ~/
```open Flash Fullscreen Patcher.exe with wine
choose "Other"
set filetypes to "All Files"
select libflashplayer.so from your home folder
You will get a confirmation that the file is successfully patched
Close the patcher
run
```
sudo cp ~/libflashplayer.so /usr/lib/flashplugin-installer/
```
Brilliant! That did it, thanks. Will I have to repeat this every time there is a flash update, or will it stay now?

-Mex

---

### Post by arzali on 2011-12-08
No problem :)

> **Mex5150 said:**
> Will I have to  repeat this every time there is a flash update, or will it stay now?
Unfortunately you have to repeat this every update

---

### Post by Mex5150 on 2011-12-08
> **arzali said:**
> No problem :)


Unfortunately you have to repeat this every update
I better save the instructions then LOL

---

