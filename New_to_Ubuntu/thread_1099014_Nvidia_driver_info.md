---
title: "Nvidia driver info"
date: 2009-03-17
forum: New to Ubuntu
---

### Post by ipburbank on 2009-03-17
Hello all, I asked this in the IRC but didn't get a reply. I just downloaded and ran the .sh from the Nvidia website to install a new driver 180 or something like that. However I want to see what version it is, but I can't find it. Hardware Drivers just tells me that a different driver is installed, but not which.

~any help is appreciated, Istvan.

---

### Post by Sealbhach on 2009-03-17
Run 
```

sudo apt-get install nvidia-settings
```

Then when you look in your menu System/Administration you will see an Nvidia Settings application. Open that and it will display the current driver version.


.

---

### Post by ipburbank on 2009-03-17
Ok, I must have done something wrong...
I ran the .sh using this tutorial - [http://ubuntuforums.org/archive/index.php/t-1067420.html](http://ubuntuforums.org/archive/index.php/t-1067420.html)

But when I create a new xorg it always gives me an error on boot so I manually paste in some extra stuff that I found to make it work, but now it says when I open nvidia-settings that I do not 'appear to be using an x'... huh?

---

