---
title: "Installing Google Earth"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by RedStarYellowSun on 2009-02-11
Since I wanted to install Google Earth in my system, I went to this website <[http://linuxchronicles.wordpress.com/2009/01/24/10-things-to-do-after-installing-ubuntu-810/]("http://linuxchronicles.wordpress.com/2009/01/24/10-things-to-do-after-installing-ubuntu-810/")> and followed the instructions in #6. I pasted into Terminal:```
wget http://dl.google.com/earth/client/current/GoogleEarthLinux.bin && chmod +x GoogleEarthLinux.bin && ./GoogleEarthLinux.bin
```
After the installation, I got the message:
> Install Complete
Congratulations!
The installation was successfully completed!
The product was installed in 
/home/jutumang/google-earth/
Type 'googleearth' to start the program
[_Q_uit]  [_S_tart]

I pressed "Start" and out came the error box:
> **Could Not Creat Folder**
Could not creat directory:
/root/.googeearth/Cache
[_O_K]

and, after pressing "OK":
> **NOTICE**
Google Earth could not write the current cache or myplaces file location.
The values will be set as follows:

My Places Path: "home/jutumang/.googleearth"
Cache Path: "home/jutumang/.googleearth/Cache"
[_O_K]

After pressing the "OK", the loading logo appeared. After it faded away, the approproiate windiws appeared, flickered, and suddenly disappeared.

What's wrong with my machine? Is there a way of fixing this?

Thank you for your time.

Take care,
RedStarYellowSun

---

### Post by Tatty on 2009-02-11
The easiest method is to get it from the medibutu repos:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by RedStarYellowSun on 2009-02-11
It still uses version 4.3, though. Will it update to verison 5 after I install?

RedStarYellowSun

---

### Post by RedStarYellowSun on 2009-02-11
Darn... the problem persists. Except, now, I have 2 "Google Earth" 's in Applications>Internet.

What would you advise?

RedStarYellowSun

---

### Post by nmccrina on 2009-02-11
from [http://www.google.com/support/forum/p/earth/thread?tid=7b1b524777b9b982&hl=en]("http://www.google.com/support/forum/p/earth/thread?tid=7b1b524777b9b982&hl=en")

1. find the libcrypto.so.0.9.8 file in the google-earth install directory
2. rename it to libcrypto-old or whatever
3. then symlink to the system libcrypto (while in the google-earth directory)

```
sudo ln -sv /usr/lib/libcrypto.so.0.9.8 ./
```

this let me start the program, but there were still issues with the display; however, my graphics card is subpar so maybe it was just me. The folks in the linked thread seemed happy. :P

---

### Post by Tatty on 2009-02-11
> **RedStarYellowSun said:**
> It still uses version 4.3, though. Will it update to verison 5 after I install?

If you want 5.x then you will have to go with the binary install.

Did you install it with sudo or not?  I suspect you may not want to do that, but without seeing the instructions you followed im not sure.

---

### Post by jemate18 on 2009-02-11
> **nmccrina said:**
> from [http://www.google.com/support/forum/p/earth/thread?tid=7b1b524777b9b982&hl=en]("http://www.google.com/support/forum/p/earth/thread?tid=7b1b524777b9b982&hl=en")

1. find the libcrypto.so.0.9.8 file in the google-earth install directory
2. rename it to libcrypto-old or whatever
3. then symlink to the system libcrypto (while in the google-earth directory)

```
sudo ln -sv /usr/lib/libcrypto.so.0.9.8 ./
```

this let me start the program, but there were still issues with the display; however, my graphics card is subpar so maybe it was just me. The folks in the linked thread seemed happy. :P

This solved my problem initially, but gives my google earth a 100% cpu usage.....

---

### Post by RedStarYellowSun on 2009-02-11
Well, the good news is that it solved the problem of Google Earth flickering suddenly dying AND the my CPU is not on 100% while the program runs. But, the graphics is horrible and there are still 2 "Google Earth" 's on my Applications>Internet menu.

Is there a way of fixing this?

Thanks for your progress and your time.

RedStarYellowSun

---

### Post by RedStarYellowSun on 2009-02-11
Well, Google Earth told me to update it. it seems that the new version 5 works, thought the graphics is horrible. It is the old version 4.3 that flickers and dies. This one, I want to remove.

Thanks again.

RedStarYellowSun

PS: I installed the 4.3 from medibuntu. I hope this helps.

---

### Post by RedStarYellowSun on 2009-02-11
Good news!
I just killed the old version and am left with the v5 that works!
Now, the only issues left are the graphics and the error messages from my first post..
What would you guys advise?

Thanks for the help.

Take care,
RedStarYellowSun

---

### Post by RedStarYellowSun on 2009-02-11
SOLVED!

Thanks for the assistance. It was greatly appreciated.

Take care,
RedStarYellowSun

---

