---
title: "Another NVIDIA thread"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by f800Rider on 2009-01-27
Using Ubuntu 8.10

I just installed nvidia drivers, activated, and restarted.  Now my display has a blue hue and I can't seem to fix it.  I've tried changing the hue in my nvidia x server settings... no luck.  I know there are many posts about nvidia and I've been looking through and trying things for about a day now with no results.  

Anyone else experienced this or have an idea on how to fix it?

Baby steps on solutions are appreciated too, I'm new to Linux.

---

### Post by f800Rider on 2009-01-27
bump... any ideas... anyone....

---

### Post by Dev'olution on 2009-01-27
It may not necessarily be your graphics card. 

Can you try posting a screenshot? If it doesnt show a hue on here, then it may be the way the card is talking to the monitor. Regardless I think it's a driver issue.

---

### Post by overdrank on 2009-01-27
Hi and welcome, what is the model of the graphics card? Could you post a screen shot of the issue you are describing?
Which driver did you install.

---

### Post by f800Rider on 2009-01-27
Thanks for the responses and interest.  The driver: NVIDIA accelerated graphics driver version 177.  And I'm attaching a screen shot,  Probably bad quality because I took it with my phone and I can't tell how it looks because my display is messed up...  The card is the geForce 6200 DDR2

[IMG]http://ubuntuforums.org/picture.php?albumid=880&pictureid=2974[/IMG]

Thanks again

---

### Post by f800Rider on 2009-01-27
Apologies, here is the **screen shot**, not a picture of my screen...

[IMG]http://ubuntuforums.org/picture.php?albumid=880&pictureid=2975[/IMG]

---

### Post by pedja_portugalac on 2009-01-27
Try to disable that driver. System > Administration > Hardware drivers. The driver that come with ubuntu is OK if you are not using special 3D effects. And then try to enable it again if you want.

---

### Post by f800Rider on 2009-01-27
> **pedja_portugalac said:**
> Try to disable that driver. System > Administration > Hardware drivers. The driver that come with ubuntu is OK if you are not using special 3D effects. And then try to enable it again if you want.

Right now I have deactivated the driver and I have color again, but the display will only go as large as 800 x 600.  I saw on my screen shot above that it does not have the blue hue.  I'm thinking it is definitely driver issues for two reasons, the same card worked fine with this monitor when using Windows XP, and when I power the computer on and off the Ubuntu loading screen is in perfect color.

I will try reactivating the driver and continue to work on the problem.  I will update the thread if I find the solution.

---

### Post by overdrank on 2009-01-27
Just a thought does that card need additional power. There was a user today that installed a nvidia card and did not plug in the extra power.

---

### Post by f800Rider on 2009-01-27
> **overdrank said:**
> Just a thought does that card need additional power. There was a user today that installed a nvidia card and did not plug in the extra power.

I don't think it does, never needed it before.

---

