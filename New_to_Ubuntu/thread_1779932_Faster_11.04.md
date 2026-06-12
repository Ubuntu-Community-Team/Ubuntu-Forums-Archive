---
title: "Faster 11.04"
date: 2011-06-11
forum: New to Ubuntu
---

### Post by Kakym on 2011-06-11
I've noticed a number of posts seeking a faster ubuntu, initially I was disappointed with the speed/responsiveness so I started removing things that I don't use as follows:

[1]Fonts removal

sudo apt-get --purge autoremove ttf-kochi-mincho ttf-kochi-gothic ttf-arabeyes ttf-arphic-ukai ttf-arphic-uming ttf-baekmuk ttf-bengali-fonts ttf-devanagari-fonts ttf-gentium ttf-gujarati-fonts ttf-indic-fonts ttf-kannada-fonts ttf-kochi-gothic ttf-lao ttf-malayalam-fonts ttf-mgopen ttf-oriya-fonts ttf-punjabi-fonts ttf-tamil-fonts ttf-telugu-fonts ttf-thai-tlwg ttf-unfonts-core ttf-indic-fonts-core ttf-wqy-zenhei cmap-adobe-japan1 ttf-khmeros-core ttf-takao-pgothic ttf-wqy-microhei

[2] Software removal

sudo apt-get --purge autoremove aisleriot gnome-bluetooth empathy gbrainy gwibber yelp im-switch gnomine onboard transmission-gtk gnome-orca at-spi bluez bluez-cups brltty empathy-common telepathy-butterfly telepathy-gabble telepathy-haze telepathy-idle telepathy-logger telepathy-mission-control-5 telepathy-salut transmission-common bluez-alsa bluez-gstreamer brltty-x11 nautilus-sendto-empathy python-pyatspi

[3] Tidying up

Then I run sudo gnome-search-tool and search for each of the removed software packages and delete the files / folders that the search identifies [despite what people say about Linux a lot of folders/files appear to get left behind] 

Now I know the above is rather a blunt attack on the system but so far it appears to have worked for me and ubuntu is quick and responsive. I undertook this process with the attitude that if it breaks I'll just reinstall.

I have also removed ubuntu one and would appreciate advice on other packages that can be removed.

Now I wouldn't recommend this approach because at some point you are going to break the operating system, but I also do not consider that it is worthwhile having software running that you are not going to use.

---

### Post by ojdon on 2011-06-11
Ah thanks for these tips, I'm always searching for ways to keep Ubuntu slim without the need to use the minimal CD. Thanks a lot! 

Does anyone else reading this thread have similar tips?

---

### Post by 3rdalbum on 2011-06-11
> **Kakym said:**
> I've noticed a number of posts seeking a faster ubuntu, initially I was disappointed with the speed/responsiveness so I started removing things that I don't use as follows:

[1]Fonts removal

sudo apt-get --purge autoremove ttf-kochi-mincho ttf-kochi-gothic ttf-arabeyes ttf-arphic-ukai ttf-arphic-uming ttf-baekmuk ttf-bengali-fonts ttf-devanagari-fonts ttf-gentium ttf-gujarati-fonts ttf-indic-fonts ttf-kannada-fonts ttf-kochi-gothic ttf-lao ttf-malayalam-fonts ttf-mgopen ttf-oriya-fonts ttf-punjabi-fonts ttf-tamil-fonts ttf-telugu-fonts ttf-thai-tlwg ttf-unfonts-core ttf-indic-fonts-core ttf-wqy-zenhei cmap-adobe-japan1 ttf-khmeros-core ttf-takao-pgothic ttf-wqy-microhei

[2] Software removal

sudo apt-get --purge autoremove aisleriot gnome-bluetooth empathy gbrainy gwibber yelp im-switch gnomine onboard transmission-gtk gnome-orca at-spi bluez bluez-cups brltty empathy-common telepathy-butterfly telepathy-gabble telepathy-haze telepathy-idle telepathy-logger telepathy-mission-control-5 telepathy-salut transmission-common bluez-alsa bluez-gstreamer brltty-x11 nautilus-sendto-empathy python-pyatspi


Now I wouldn't recommend this approach because at some point you are going to break the operating system, but I also do not consider that it is worthwhile having software running that you are not going to use.

But almost none of that is actually running. Only the Bluetooth-related stuff is likely to be running in an ordinary Gnome session. Programs sitting on disk and not being executed do not take up CPU cycles or RAM. Fonts take up so little RAM that I don't think it's worthwhile to remove them either.

Either you happened to have a problem with your Bluetooth stack that was causing high CPU use, or you are experiencing a placebo effect.

A much less invasive approach would have been to take a look at the System Monitor to see what program(s) were taking up a large percentage of CPU time, and then kill them.

---

### Post by cchhrriiss121212 on 2011-06-11
Install preload
Install a lighter DE like LXDE or XFCE

---

