---
title: "screen resolution"
date: 2009-12-03
forum: New to Ubuntu
---

### Post by karmicgaz on 2009-12-03
My screen resolution will not save, have added screenshot(hopefully) I am a newby so please be gentle with me!

---

### Post by Junkieman on 2009-12-03
Hi. Okay I have no experience with troubleshooting nVidia on Ubuntu (yet). My guess is that your xorg.conf file is broken. [This thread]("http://ubuntuforums.org/showthread.php?t=670645") includes instructions to restore your xorg.conf file :)

---

### Post by karmicgaz on 2009-12-03
tried that in terminal (was that right?) same problem!

---

### Post by bsharp on 2009-12-03
One of the problems I have noticed for several releases is that nvidia-settings starts without root privileges from the menu. I'm surprised it hasn't been addressed yet.
Alt+F2 and:
```
gksudo nvidia-settings
```

Make your changes and save your xorg.conf like normal.

---

### Post by karmicgaz on 2009-12-03
Ok, I told you I was a newby! I just don't want to waste any more money on bill gates! I hit "alt f2" like you said. I tried "run interminal" it disappeared! I tried "run" on it's own, it disappeared! I want to learn but it will take time. I thank you for your help but really, I am dumb and should be considered so!

---

### Post by bsharp on 2009-12-03
Could you open a terminal, run the command

```
sudo nvidia-settings
```

and post the output?

---

### Post by karmicgaz on 2009-12-03
hopefully

---

### Post by Junkieman on 2009-12-03
> **karmicgaz said:**
> Ok, I told you I was a newby! I just don't want to waste any more money on bill gates! I hit "alt f2" like you said. I tried "run interminal" it disappeared! I tried "run" on it's own, it disappeared! I want to learn but it will take time. I thank you for your help but really, I am dumb and should be considered so!
To open a terminal, use the main menu Applications -> Accesories -> Terminal. You can get the same result by pressing alt+F2 and entering 'gnome-terminal'. Both will work.

---

### Post by Junkieman on 2009-12-03
> **karmicgaz said:**
> hopefully
It looks like a typo, try 'nvidia-settings' (not nvid_ea_-settings)

---

### Post by bsharp on 2009-12-03
> **karmicgaz said:**
> hopefully

You typed "sudo nvidea-settings" when it should be "sudo nvidia-settings"

---

### Post by karmicgaz on 2009-12-03
that is what I did! That is the result I got!

---

### Post by karmicgaz on 2009-12-03
Thankyou. I am dumber than even I thought! Have been her, gone to settings, changed resolution, but on restart, it's gone!

---

### Post by bsharp on 2009-12-03
```
sudo nvidia-settings
```

and see the attached picture below.

---

### Post by karmicgaz on 2009-12-03
*I may be stupid,but i'm not that stupid! Of course I saved changes!*I have to turn in now, 6month old boy and full time job make late nights out of the question. Thanks for all your help and I will try again tomorrow for more advise.

---

### Post by bsharp on 2009-12-03
> **karmicgaz said:**
> ***I may be stupid,but i'm not that stupid! Of course I saved changes!***I have to turn in now, 6month old boy and full time job make late nights out of the question. Thanks for all your help and I will try again tomorrow for more advise.

[IMG]http://www.sherv.net/cm/emo/angry/angry.gif[/IMG]
One thing I've learned:
> Never under estimate the stupidity of the end user.

Good luck with your problem.

---

### Post by MooPi on 2009-12-03
bnice bsharp.  Remember that Ubuntu is all inclusive for the betterment of all men.
Okay that's a bit sappy but you should get the picture. For Linux to be successful and populate the world with fruitful computers we shouldn't insult the noobs.;)

---

### Post by dearingj on 2009-12-03
> **karmicgaz said:**
> Thankyou. I am dumber than even I thought! Have been her, gone to settings, changed resolution, but on restart, it's gone!

I found this with a Google search:
[[How-to] Make nVidia settings persistent and retain the settings in Ubuntu 9.10 Karmic Koala]("http://sathyasays.com/2009/11/21/how-to-make-nvidia-settings-persistent-and-retain-the-settings-in-ubuntu-9-10-karmic-koala/")

Note that those instructions are for Ubuntu 9.10. Is that the version of Ubuntu you're using?

---

### Post by karmicgaz on 2009-12-04
I think the link you sent probably does it. So I thank you. But it made very little sense to me so I intend to do more research, try to understand more and come back to this soon. Hopefully!

---

### Post by karmicgaz on 2009-12-06
Ok, back again, hope somebody reads this, I still have the same problem of my nvidia graphics program "failing to parse Xorg conf" when I try to save new settings. The last help given by dearingj(thanks for trying) doesn't work (the commands given don't do as described) something to do with it being an upstart job/cannot stop gdm/no Xorg file to move? I attach the screenshot again so you can see what I get when trying to save changes after applying them. I may be a noob but I can follow commands, so I know I did exactly as described.
Oops no screenshot. Never mind it's further up the thread.

---

### Post by karmicgaz on 2009-12-06
[ATTACH]138765[/ATTACH]
finally the screenshot. HELP!

---

