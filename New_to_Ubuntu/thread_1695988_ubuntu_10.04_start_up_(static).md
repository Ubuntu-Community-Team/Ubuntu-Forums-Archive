---
title: "ubuntu 10.04 start up (static?)"
date: 2011-02-26
forum: New to Ubuntu
---

### Post by WhatAreHackers on 2011-02-26
You know when it starts up, it says Ubuntu and it's logo.... for some reason it's just the purple background, with some static line.  Is there a problem with my Ubuntu? it's been doing this for some time now.

---

### Post by acrazyplayer on 2011-02-26
If it doesn't affect anything then it only matters if you care about it. If you want to get rid of the problem altogether then simply disable the splash screen from the grub options.

do this in a terminal

"gksu gedit /etc/default/grub" then remove the word "splash" after the word "quiet"

save and then run "sudo update-grub" for it to take effect

---

