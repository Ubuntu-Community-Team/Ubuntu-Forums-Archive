---
title: "how to change GDM background"
date: 2010-08-06
forum: New to Ubuntu
---

### Post by carrarin on 2010-08-06
Hey everyone,

I want to change the background on the login screen (GDM).
How do I do this?

THanks

---

### Post by Matt__ on 2010-08-06
I changed mine via ubuntu-tweak.

```
sudo apt-get install ubuntu-tweak
```

or [download directly here](http://launchpad.net/ubuntu-tweak/0.5.x/0.5.5/+download/ubuntu-tweak_0.5.5-1~lucid1_all.deb)  (downloads and opens a .deb)

---

### Post by KdotJ on 2010-08-08
> **Matt__ said:**
> I changed mine via ubuntu-tweak.

```
sudo apt-get install ubuntu-tweak
```


Doesn't work, says it cannot find package

---

### Post by KdotJ on 2010-08-08
And just to add, I downloaded the ubuntu-tweak deb file and installed no problems. However, when I select a new background image for the GDM, after reboot there is no background image, it's just purple (not the default background, just solid dark purple).

Any ideas?
thanks

---

### Post by Matt__ on 2010-08-08
hmmm..is the image the same size as your screen resolution?

I dont honestly know why it wouldnt show, but try that and give it a couple of tries :P

//edit  what format of image are you using by the way?

---

### Post by KdotJ on 2010-08-08
Thanks for your quick reply,

The image I am trying to use is a PNG file, and it is the same image I use for my desktop wallpaper so I'm guessing the resolution shouldn't be an issue?

---

### Post by JKyleOKC on 2010-08-08
This link may help: [https://launchpad.net/gdm2setup](https://launchpad.net/gdm2setup)

I've downloaded the package and used it to replace the background for the login screen, successfully. However I'm still looking for a way to move the user-list dialog box away from dead center of the screen.

---

### Post by sylvainrb on 2010-08-08
This works as I've used it myself
[http://www.ubuntugeek.com/how-do-you-change-the-boot-splash-screen-image-for-10-04-lucid-lynx.html]("http://www.ubuntugeek.com/how-do-you-change-the-boot-splash-screen-image-for-10-04-lucid-lynx.html")

One thing to do before you start is to save the image you want as a background to your /usr/share/background/ folder i believe...

---

