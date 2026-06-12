---
title: "lightscribe labeler won't launch"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by Sisyphus48 on 2009-04-28
Hi;
I downloaded the deb packages from the LightScribe website for the system software and the labeler.  I then installed them in that order.  The only starter that appeared in my menus was LightScribe(Simple Labeler) under Applications.  When I click it I get:** Error   Could not launch menu item   Failed to execute child process ":" (No such file or directory).**  The download seemed to go fine as well as the installing process.  I have Ibex.  Does anyone know what the problem is???

---

### Post by MysticGold04 on 2009-04-28
I've downloaded them too for Hardy, but I've yet to use the labeler.  I'm going to burn some ISO's to a DVD so I'll check it out and see.  I do remember having to go find the application manually though, and create my own launcher.

---

### Post by Sisyphus48 on 2009-04-29
Thx, I'd appreciate any help I can get!

---

### Post by mike555 on 2009-04-29
Make sure it points to the right place ..... it's in "   OPT   " file folder.....

---

### Post by MysticGold04 on 2009-04-30
Check here, make sure you have the right files, etc.... 

[https://help.ubuntu.com/community/LightScribe](https://help.ubuntu.com/community/LightScribe)

I tested mine today, seems to work okay.  I'm kinda disappointed that you cannot change the size of the font, but its functional.

---

### Post by Sisyphus48 on 2009-04-30
Many thanks to [COLOR="DarkOrange"]MysticGold04[/COLOR] and [COLOR="SeaGreen"]Mike555[/COLOR].  Due to your assistance I was able to track down the problem.  I have the right files and the launcher points to the right place, : /opt/lightscribeApplications/SimpleLabeler/SimpleLabeler, but it simply didn't launch.  However, by going to the location and clicking on the correct file it launched and worked perfectly! Thanks again for taking the time to help me.

---

### Post by MysticGold04 on 2009-05-05
> **Sisyphus48 said:**
> Many thanks to [COLOR="DarkOrange"]MysticGold04[/COLOR] and [COLOR="SeaGreen"]Mike555[/COLOR].  Due to your assistance I was able to track down the problem.  I have the right files and the launcher points to the right place, : /opt/lightscribeApplications/SimpleLabeler/SimpleLabeler, but it simply didn't launch.  However, by going to the location and clicking on the correct file it launched and worked perfectly! Thanks again for taking the time to help me.

No problem, man.. thats what we're here for!  Another reason why I love this forum... being able to give back and help another linux enthusiast! :guitar:

---

