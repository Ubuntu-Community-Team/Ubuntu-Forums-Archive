---
title: "Looking for compression/Extractor software"
date: 2010-10-07
forum: New to Ubuntu
---

### Post by zcahfg2 on 2010-10-07
Hello,
I recently moved into Ubuntu, and enjoying so far trying to figure my way into this magnificent operating system.

I am looking for a software that extracts/compresses many files separately just like in Win Rar. I need this feature for Comix when viewing comic books, as Comix only opens next achieves automatically and I have many extracted images in number of folders. Unfortunately Archive Manager lacks in this feature.

It would be the best if this software provides an option to choose between compress/extract as a whole and separately when right clicked number of files.

Thanks a lot :)

---

### Post by Quackers on 2010-10-07
Welcome to UbuntuForums :-)
If you go to System > Admin > Synaptic Package Manager and in the search box type "rar" you will see several options come up in the main window. Rar, unrar and 7zip I believe are there.
In Synaptic it is usually a good idea to right-click on the program you want to install and mark it for complete installation (that way all dependencies are installed as well) then click on the Apply button near the top.

---

### Post by Locke_99GS on 2010-10-07
Similarly, you can get RAR plugins for file-roller via the new Software Centre.

---

### Post by zcahfg2 on 2010-10-07
Thanks a lot both of you :)

Here is quick review of comic viewers for those are interested :

Comix
Pro:
1. Manual zoom mode - Great !! 
2. Library - Takes time to load up thumbnails when you have 100+ comics in one folder and ignores any files that isn't compressed tho. But is convenient managing comics.

Con:
1. Flipping page can be really annoying, 
a. single click flips the page, does not work while if page is scrolling down/need very short time after scroll.

b. double click flips two pages at once. Occasionally the viewer takes up to few seconds loading up a new page esp when image is large, in that interval if you click another time it flips two pages. When combined with 'a' it can be very annoying.

i.e. single click while you just viewed the page -> time lag you believe it is flipping to the next page and you stay waiting for few seconds until you realise it isn't, or you click again and it flips twice.

If you enable 'scroll down to next page' option, you have to scroll down, stop and scroll once again to reach next page. Sometimes it even flips to the next page even you did not scroll down the page properly.
Not so flawless when it comes to this.
May require some time until we get used to this feature.

2. Cannot open folders, you have to run image files from the folder.

Omaque
Pro: 
1. Simple interface, 
2. do not have to flip to the next page, next pages are loaded so you can continuously scroll down.

Con:
Cannot drag and drop. Only support Zip and RaR. (Although it failed to open mine in my workspace.)
has to be image files : i.e. select whole images not a folder.

Buggy.  
In my case whole menu disappeared and I couldn't get it back despite re-installation. Thus couldn't open anymore files.

Nice simple program but loading file can be a problem.

Qcomicbook
Pro:
1. Provide thumbnail views on full screen mode. (slightly more convenient than Honeyview)

2. do not have to flip to the next page, next pages are loaded so you can continuously scroll down.

3. can load up both compressed files and folders.

Con:
1. Scrolling down to next page is buggy at the moment, scroll down once and it jumps up to the current page again.
2. No manual zoom. Fixed size options you can choose but quite limited. 
3. Assuming you load up few books, reach the end the program does not tell the book is finished. Nor thumbnail viewer shows its filename. It automatically loads up new book. 

Will be a great viewer if the bug is fixed.

Honey view: 
[http://www.honeyview.org/](http://www.honeyview.org/)
It is a windows program but it works flawlessly under wine.

Pro:
1. Provides number of filters to enhance images.
2. Easy to configure sharpness, smoothness of the image.
3. Love its hotkey to jump into next book straight away.
4. Nice transparent 'Docky' type toolbar providing few 'jump back/or/forward 10 pages' 'previous/next files', while viewing an image. 
5. Hotkeys to change viewing options of the image and many others.

Con:
1. Since it works under wine it does not provide 'view in honeyview' when right clicked a image file like on Windows.
Tho there are no. of ways to counter this problem.
2. Seem to operate slightly slower than in windows but still faster than majority of viewers above. It can look faster if you disable 'show blur images while loading' in option.
3. Manual zooming not as strong as Comix but its fixed view options are more than enough.

Have to admit it is biased because I used this viewer for 5 years and now I am too used to the hotkeys. But it never showed a single bug during that period. I will use Honeyview for my main viewer for now and try and see new Comix version.

Guide to add honey view.exe manually into applications under wine in menu : [http://ubuntuforums.org/showthread.php?t=548684](http://ubuntuforums.org/showthread.php?t=548684)


Does anyone know how to change icon of any wine applications?
Tried Rar just now, although installed it was not added to the application menu, tried to open manually with gnome-do but failed to respond.

---

### Post by sandyd on 2010-10-07
> **zcahfg2 said:**
> Thanks a lot both of you :)

Here is quick review of comic viewers for those are interested :

Comix
Pro:
1. Manual zoom mode - Great !! 
2. Library - Takes time to load up thumbnails when you have 100+ comics in one folder and ignores any files that isn't compressed tho. But is convenient managing comics.

Con:
1. Flipping page can be really annoying, 
a. single click flips the page, does not work while if page is scrolling down/need very short time after scroll.

b. double click flips two pages at once. Occasionally the viewer takes up to few seconds loading up a new page esp when image is large, in that interval if you click another time it flips two pages. When combined with 'a' it can be very annoying.

i.e. single click while you just viewed the page -> time lag you believe it is flipping to the next page and you stay waiting for few seconds until you realise it isn't, or you click again and it flips twice.

If you enable 'scroll down to next page' option, you have to scroll down, stop and scroll once again to reach next page. Sometimes it even flips to the next page even you did not scroll down the page properly.
Not so flawless when it comes to this.
May require some time until we get used to this feature.

2. Cannot open folders, you have to run image files from the folder.

Omaque
Pro: 
1. Simple interface, 
2. do not have to flip to the next page, next pages are loaded so you can continuously scroll down.

Con:
Cannot drag and drop. Only support Zip and RaR. (Although it failed to open mine in my workspace.)
has to be image files : i.e. select whole images not a folder.

Buggy.  
In my case whole menu disappeared and I couldn't get it back despite re-installation. Thus couldn't open anymore files.

Nice simple program but loading file can be a problem.

Qcomicbook
Pro:
1. Provide thumbnail views on full screen mode. (slightly more convenient than Honeyview)

2. do not have to flip to the next page, next pages are loaded so you can continuously scroll down.

3. can load up both compressed files and folders.

Con:
1. Scrolling down to next page is buggy at the moment, scroll down once and it jumps up to the current page again.
2. No manual zoom. Fixed size options you can choose but quite limited. 
3. Assuming you load up few books, reach the end the program does not tell the book is finished. Nor thumbnail viewer shows its filename. It automatically loads up new book. 

Will be a great viewer if the bug is fixed.

Honey view: 
[http://www.honeyview.org/](http://www.honeyview.org/)
It is a windows program but it works flawlessly under wine.

Pro:
1. Provides number of filters to enhance images.
2. Easy to configure sharpness, smoothness of the image.
3. Love its hotkey to jump into next book straight away.
4. Nice transparent 'Docky' type toolbar providing few 'jump back/or/forward 10 pages' 'previous/next files', while viewing an image. 
5. Hotkeys to change viewing options of the image and many others.

Con:
1. Since it works under wine it does not provide 'view in honeyview' when right clicked a image file like on Windows.
Tho there are no. of ways to counter this problem.
2. Seem to operate slightly slower than in windows but still faster than majority of viewers above. It can look faster if you disable 'show blur images while loading' in option.
3. Manual zooming not as strong as Comix but its fixed view options are more than enough.

Have to admit it is biased because I used this viewer for 5 years and now I am too used to the hotkeys. But it never showed a single bug during that period. I will use Honeyview for my main viewer for now and try and see new Comix version.

Guide to add honey view.exe manually into applications under wine in menu : [http://ubuntuforums.org/showthread.php?t=548684](http://ubuntuforums.org/showthread.php?t=548684)


Does anyone know how to change icon of any wine applications?
Tried Rar just now, although installed it was not added to the application menu, tried to open manually with gnome-do but failed to respond.
rar is a commandline program

you can do this..
```

cd /path/to/directory
rar e *.rar
```
to extract them all.

are you using kubuntu or ubuntu?

---

### Post by zcahfg2 on 2010-10-07
Thanks,
I am using Ubuntu, 
Is there a command to compress each folders separately too?

---

### Post by sandyd on 2010-10-07
> **zcahfg2 said:**
> Thanks,
I am using Ubuntu, 
Is there a command to compress each folders separately too?

yeah.
theirs the file-roller.
its installled by default.
I dont know how it works because I have pure-kde, but perhaps someone can elaborate...

(and no, I don't even know if its included in the "right click menu")

---

### Post by zcahfg2 on 2010-10-08
Thanks a lot
File roller supports extracting multiple files perfectly,
shame it cannot compress multiple files separately though, but again I wouldn't mind now having Honeyview.

---

