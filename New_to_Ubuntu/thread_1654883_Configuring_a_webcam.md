---
title: "Configuring a webcam"
date: 2010-12-29
forum: New to Ubuntu
---

### Post by Maelzel on 2010-12-29
Hello community,

I got a wb-6120 webcam for Christmas and I am attempting to configure it. I installed Skype then uninstalled it and re-installed it while attempting to get my webcam working and now the options when I right click the icon are all darkened (for whatever reason). But anyway, I put wine on my computer and used the autorun to install the drivers that came on the disk for the webcam, but am still unable to get the webcam or the mic to work on Skype. Has anyone dealt with similar problems?

Thanks.

---

### Post by no2498 on 2010-12-29
try this if it comes on get cheese and get the cam working before using it in/on skype

 click system, preferences
go down the list to multimedia systems selector, start it click video
try v4l and v4l2 click the bottom test button for each 1

---

### Post by Maelzel on 2011-01-05
> **no2498 said:**
> try this if it comes on get cheese and get the cam working before using it in/on skype

 click system, preferences
go down the list to multimedia systems selector, start it click video
try v4l and v4l2 click the bottom test button for each 1

Thanks for the tips, I'll try it. The method I used was installing Wine and using that to run the driver disc's setup.exe . I uninstalled the drivers and wine but may attempt your method.

Does anyone know of another way to run an executable?

Also, it seems like it would be a lot more productive to post actual assistance or walk away from the computer than to troll someone in a new user forum.

---

### Post by cariboo on 2011-01-05
To see if your web cam is detected and the correct driver loaded, could open an Applications->Accessories->Terminal and type:

```
dmesg | tail -n15
```

 just after you have plugged the web cam in, and paste the output in your next post.

Linux has gotten much better at hardware detection, and in most cases web cams now work out of the box.

---

