---
title: "saving a wallpaper -not so simple"
date: 2010-07-18
forum: New to Ubuntu
---

### Post by rburkartjo on 2010-07-18
i recently had some wallpapers but somehow deleted the file. at the time i deleted the file i had a wallpaper set on the desktop that i really like. it is still set as the desktop wallpaper but i know if i change to another it will be gone. how can i find the file so i can save know it has to be somewhere/tks

note if i go the appearance preferences/background it is not shown

---

### Post by bigsmitty64 on 2010-07-18
hmmmm....you could have a poke around in 

```
/usr/share/backgrounds
```not sure if this will help but it's all I got :) But I wonder where they are kept if you right click a pic (say, on a website)and then choose set as background without actually saving it? Hopefully someone else will know. Good luck.

---

### Post by Mike3 on 2010-07-18
Note: "Your user name" and phrases like that are asking you to double click on the name you see when you log on to Ubuntu.
     
     Click on the places menu, the second to top left menu, and click on your user name. It will take you to your home folder, and you shuld see a file named "Firefox_wallpaper.png" (w/o the quotes) and that should be you wallpaper. Copy that file to a new location, say your pictures folder in "/home/YOURUSERNAME/Pictures" and rename it to a more suitable filename, just like you would in Windows, right click, Rename..., and Viola! Enter the new filename, just remember to keep the original file format tag in the name (whatever comes after the period.) like ".jpg" ".tiff" or ".png"
     
     There may be a second option for you to recover more wallpapers, but I'm not sure if it will work. If you haven't cleared you cache in Firefox (I assume you're using it, if not please post a reply of what browser you're using) you can check it to see if some of you pictures have been cached be Mozilla Firefox. The browser caches files on a web page, like your wallpapers, for instance, so it can access them directly from your hard drive or memory after you've visited a page, so it doesn't have to download them from the server again. To get to the cache, you will need to open nautilus, by clicking on the "Places" menu, and click "Computer." Click "View" in Nautiluse's Menu Bar, and make sure "Show Hidden Files" is checked. If not, click it to check it. Double click "home", then "your user name" and ".mozilla" (the period or dot denotes a hidden file) then "firefox" and then some random letters and numbers followed by ".default". This is Firefox's profile folder, where it stores you info, passwords, and cache. Then double click on "Cache" and see if you can find your wallpaper(s). If you find them, copy them to a new location and rename them.

---

### Post by rburkartjo on 2010-07-18
mike tks it was in the firefox cache.appreciate it

---

### Post by Mike3 on 2010-07-18
Your welcome! :popcorn:

---

### Post by bigsmitty64 on 2010-07-18
> **Mike3 said:**
> 
     
     Click on the places menu, the second to top left menu, and click on your user name. It will take you to your home folder, and you shuld see a file named "Firefox_wallpaper.png"

DOH! I have seen that a hundred times! Thats what happens when you over think it I guess. :) Thanks from me too!

O.P If your still around, you should mark this as solved in the "thread tools" at the top right of the thread, as this will no doubt come up again and will be a big help to someone!

---

